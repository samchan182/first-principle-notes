The reason why database existed is people need a place to handle data. Some data need to store permanently, some data need to read thousand times per second. 

Under the law of physics, it is a system arrange bytes in physical hardware. 

While you have many tables, charts, boxes, in order to retrieve a useful piece of information, you need to connect them in relationship. 

SQL (Structured Query Language) is a relational database. 

## How to choose your database?
There are some many types of database in industry. For example, 
- Oracle, Microsoft SQL server, both focus on enterprise business. 
- MySQL and PostgreSQL, both are open-source framework is widely used. 

You have to consider your database choice HEAVILY depend you needs. 

PostgreSQL often do more inside the database. Heavy analytical workloads.

MySQL often choose for read-heavy web application. 

## Mental model on debugging
Steps by Steps

- Is it connected? Check whether if your application is connecting with the database.
- Is the DB healthy? Check whether there's any configuration wrong of database itself. 
- Correct data input and output? Check whether you data is stored correctly, and retrieved data is what you want. 




`127.0.0.1` means only reachable from VM, not public internet. 

`172.18.0.4` means the address often used by containers talk to each other, it's docker's network. 

172.X also can be reachable from the host, but it's being used by stability and convenience. 

Since each container is like a sealed room inside the VM, `127.0.0.1:8082->80` means the container will open a secured tunnel for request to come in, the `127.0.0.1:8082` is the entry of the tunnel. The port `80` can think it as door number of the sealed room. 

docker debug commmand

#### Know all running docker

`docker ps`

#### Know container inner IP

`docker inspect -f '{{range .NetworkSettings.Networks}}{{.IPAddress}}{{end}}' TARGET-DOCKER-NAME`



