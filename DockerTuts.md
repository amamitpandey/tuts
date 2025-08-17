Docker is a kind of small virtual machine, but not having self resources like RAM, but docker use local machine access and work like isolated. 
Docker is advance version of virtual machine which use container based concept and share a cloned image where other can use it easily.
container use hardware resources with help of hypervisor and OS. it uses resources dynamically not pre allocate resources like RAM, processor etc.  



Docker Command List:

docker run nginx // to start or run new container 
docker run -p 8080:80 nginx // to map a container internal port with external machine, nginx port no is 80 and                   			       docker container port no is 8080 
docker ps  // to see running container 
docker ps -a // all stop container 
ufw allow 8080 // allow container port to access - Uncomplicated Firewall
docker stop <first few letters of Container ID>
docker run -d nginx // starts nginx docker container in background
docker rm CID
docker rm -f CID/name // delete a running container forcefully
docker start CID/name
 
touch this.txt
docker cp this.txt <first few letters of Container ID>:th.txt // form external machine to cotainer
docker exec -it <first few letters of Container ID> bash // use bash inside of container, normal lunix Debian OS

docker cp <first few letters of Container ID>:mine.txt this.txt // copy from container to source
docker exec -it <Container_ID> bash // executes a command inside an existing container
docker commit <Container_ID> 

docker images 
docker image ls aa
docker system prune  // remove unused container 

# docker-compose.yml
docker-compose pull
docker-compose up -d
docker-compose logs web
docker-compose down -v

# After adding Dockerfile
docker build -t posthog-ubuntu-image .
docker run -it posthog-ubuntu-image

# for mongo run
docker run -d -p 27017:27017 --name mymongo mongo



Cheatsheet Link: https://dockerlabs.collabnix.com/docker/cheatsheet/
