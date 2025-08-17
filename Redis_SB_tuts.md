### Redis Setup:
Download a Zip file from https://redis.io/downloads/
start, redis-server.exe & redis-cli.exe
```
$ping  // test 
$set name key_name
$get key_name 
$keys * // to all see data 
$type keyName 
$del keyName 

// storing as a string type, make all model serializable


$CONFIG SET maxmemory-policy volatile-ttl // nearest expiry time
$EXPIRE mykey 120 // expire in 120 mimisec
$TTL name_key // get expiry time
$CONFIG GET maxmemory // to get max memory size in redis-cli
$CONFIG SET maxmemory 100mb // set 100mb, can be set by spring boot code
```

Setup expiry time by new global config

### in pom.xml
```
		<dependency>
			<groupId>org.springframework.boot</groupId>
			<artifactId>spring-boot-starter-data-redis</artifactId>
		</dependency>

```

```
@Configuration
public class CacheConfig {
    @Bean
    public RedisCacheConfiguration cacheConfiguration() {
        return RedisCacheConfiguration.defaultCacheConfig()
                .entryTtl(Duration.ofMinutes(60));  // Set global TTL 60 minutes
    }
}
```

in application.propeties
```
spring.application.name=cache_Redis
spring.redis.host=localhost
spring.redis.port=6379
spring.servlet.multipart.max-file-size=100MB
spring.servlet.multipart.max-request-size=100MB

```
```
@SpringBootApplication
@EnableCaching // Enable caching
public class CacheRedisApplication {...
```

```
public class CachedFileModel implements Serializable {
    private byte[] content;
    private String contentType;
    private String originalFilename;

    public CachedFileModel() {}

    public CachedFileModel(byte[] content, String contentType, String originalFilename) {
        this.content = content;
        this.contentType = contentType;
        this.originalFilename = originalFilename;
    }

    public byte[] getContent() { return content; }
    public String getContentType() { return contentType; }
    public String getOriginalFilename() { return originalFilename; }

    public void setContent(byte[] content) { this.content = content; }
    public void setContentType(String contentType) { this.contentType = contentType; }
    public void setOriginalFilename(String originalFilename) { this.originalFilename = originalFilename; }
}

```
```
@RestController
@RequestMapping("/public/file")
public class FileCacheController {

    @Autowired
    private FileCacheService fileCacheService;

    @PostMapping("/upload")
    public ResponseEntity<String> uploadFile(@RequestParam("file") MultipartFile file,
                                             @RequestParam("id") String id) throws IOException {
        String contentType = file.getContentType();
        String originalFilename = file.getOriginalFilename();

        fileCacheService.saveFile(id, file.getBytes(), contentType, originalFilename);
        return ResponseEntity.ok("File cached with ID: " + id);
    }

    // pass ids like 1,2,3, with comma without square brackets
    // http://localhost:8080/public/file/download/11 for downloading file with id 11
    @PostMapping("/upload-multiple")
    public ResponseEntity<String> uploadMultipleFiles(@RequestParam("files") MultipartFile[] files,
                                                      @RequestParam("ids") List<Integer> ids) throws IOException {
        if (files.length != ids.size()) {
            return ResponseEntity.badRequest().body("Each file must have a matching ID.");
        }

        for (int i = 0; i < files.length; i++) {
            MultipartFile file = files[i];
            int id = ids.get(i);
            fileCacheService.saveFile(String.valueOf(id), file.getBytes(), file.getContentType(), file.getOriginalFilename());
        }

        return ResponseEntity.ok(files.length + " files uploaded and cached.");
    }


    @GetMapping("/download/{id}")
    public ResponseEntity<byte[]> downloadFile(@PathVariable String id) {
        CachedFileModel cached = fileCacheService.getFile(id);
        if (cached == null) {
            return ResponseEntity.status(HttpStatus.NOT_FOUND).build();
        }

        HttpHeaders headers = new HttpHeaders();
        headers.setContentType(MediaType.parseMediaType(
                cached.getContentType() != null ? cached.getContentType() : "application/octet-stream"));

        headers.setContentDisposition(ContentDisposition.attachment()
                .filename(cached.getOriginalFilename() != null ? cached.getOriginalFilename() : id)
                .build());

        return new ResponseEntity<>(cached.getContent(), headers, HttpStatus.OK);
    }

    @DeleteMapping("/evict/{id}")
    public ResponseEntity<String> evictFile(@PathVariable String id) {
        fileCacheService.evictFile(id);
        return ResponseEntity.ok("File evicted from cache.");
    }

}

```

```
@Service
public class FileCacheService {

    @Cacheable(value = "files", key = "#id")
    public CachedFileModel getFile(String id) {
        System.out.println("Cache miss for file id: " + id);
        return null;
    }

    @CachePut(value = "files", key = "#id")
    public CachedFileModel saveFile(String id, byte[] fileBytes, String contentType, String originalFilename) {
        System.out.println("Caching file with id: " + id);
        return new CachedFileModel(fileBytes, contentType, originalFilename);
    }

    @CacheEvict(value = "files", key = "#id")
    public void evictFile(String id) {
        System.out.println("Evicted file with id: " + id);
    }
}
```

# optional if not working with env, other wise setup in deployment.yml, val-env.yml for k8s

// add in app.java

    @Bean
    public LettuceConnectionFactory redisConnectionFactory() {
        RedisStandaloneConfiguration config = new RedisStandaloneConfiguration();
        config.setHostName("redis-server-master.catalog-x-supplier-int.svc.cluster.local.");
        config.setPort(6379);
        config.setPassword("redis-pass@123"); // <-- set password here

        return new LettuceConnectionFactory(config);
    }

