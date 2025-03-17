
## Return path in header
```
userModel addedUser = repo.saveUserData(arrayNew);
        URI uriLocation = ServletUriComponentsBuilder
                .fromCurrentRequest()
                .path("/{id}")
                .buildAndExpand(addedUser.getId())
                .toUri();
        return ResponseEntity.created(uriLocation).build();
        
        
```
## to implement default error/exception handler :

**in controller**
``` 

if(repo.findUser(id)==null){
            throw new UserNotFoundException("There is no user for " + id + " id");
  }
```

## create a class UserNotFoundException

**in class**
```

@ResponseStatus(HttpStatus.NOT_FOUND)
public class UserNotFoundException extends RuntimeException {
    public UserNotFoundException(String s) {
        super(s);
    }

}
```

## creating a customized error handler

create a model 

```
public class exceptionModel {
    private Date date;
    private String message;
    private String status;
    private String details;

    public exceptionModel(Date date, String message, String status, String details) {
        this.date = date;
        this.message = message;
        this.status = status;
        this.details = details;
    }

    public String getMessage() {
        return message;
    }

    public Date getDate() {
        return date;
    }

    public void setDate(Date date) {
        this.date = date;
    }

    public String getStatus() {
        return status;
    }

    public void setStatus(String status) {
        this.status = status;
    }

    public String getDetails() {
        return details;
    }

    public void setDetails(String details) {
        this.details = details;
    }

    @Override
    public String toString() {
        return "exceptionModel{" +
                "date=" + date +
                ", message='" + message + '\'' +
                ", status='" + status + '\'' +
                ", details='" + details + '\'' +
                '}';
    }
}

```

**create specific exception class**
```

create a class UserNotFoundException

@ResponseStatus(HttpStatus.NOT_FOUND)
public class UserNotFoundException extends RuntimeException {
    public UserNotFoundException(String s) {
        super(s);
    }

}
```

**create customize exception handle for all controller**

```
@RestController
@ControllerAdvice
public class customizeExceptionHandler extends ResponseEntityExceptionHandler {


    @ExceptionHandler(UserNotFoundException.class)
    public final ResponseEntity<Object> allExceptionHandler(Exception ex, WebRequest request) throws Exception {
        exceptionModel excectionRes = new exceptionModel(new Date(), ex.getMessage(), HttpStatus.NOT_FOUND.toString(), request.getDescription(false));
        return new ResponseEntity(excectionRes, HttpStatus.NOT_FOUND);
    }
}
```
## authentication using header like login
```
    @GetMapping("/authUser")
    public String authUser(@RequestHeader String customUid, @RequestHeader String emailId) {

        System.out.println(customUid.getClass()); // get data type
        if (customUid.equals("abcd1234")) {
            return "Authenticate successfully : true";
        } else {
            return "Authenticate Unsuccessfully";
        }
    }
    
 ``` 
  
## using this we return path in header

```
        URI uriLocation = ServletUriComponentsBuilder
                .fromCurrentRequest()
                .path("/{id}")
                .buildAndExpand(addedUser.getId())
                .toUri();

        HttpHeaders responseHeaders = new HttpHeaders();
        responseHeaders.setLocation(uriLocation);
        responseHeaders.set("MyResponseHeader", "MyValue");
        // using model based class return multi type JSON
        ResponseModel responseBody = new ResponseModel("success", "Registered successfully", addedUser);

        return new ResponseEntity(responseBody, responseHeaders, HttpStatus.CREATED);
        
 ```
 
 

