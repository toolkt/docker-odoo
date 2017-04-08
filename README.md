# docker-odoo
Custom Docker Images for Odoo


Pulling the Image
```sh
#Get the image
git clone https://github.com/toolkt/docker-odoo.git docker-odoo


For Odoo 8.0
```sh
#Build the image
docker build -t toolkt/odoo:8.0 .


#Run the container
docker run -it --name odoo8 -v /opt/docker/config/odoo8:/etc/odoo -v /opt/odoo/addons/8.0/:/mnt/extra-addons -p 8069:8069 --link db:db toolkt/odoo:8.0 --  -u dmpi_base -d dmpi_test


#Stop and Start the service
docker stop odoo8 && docker start -a odoo8


#Enter the terminal of the container
docker exec -it odoo8 bash


#Commit the running container to the image and then to Docker
docker login
docker commit CONTAINER_ID toolkt/odoo:8.0
docker push toolkt/odoo:8.0

```


For Odoo 9.0
```sh
#Build the image
cd /opt/docker/dockerfiles/docker-odoo/9.0/
docker build -t toolkt/odoo:9.0 .

#Run Postgres for Odoo 9.0 Modules
docker stop db
docker run -d -e POSTGRES_USER=odoo9 -e POSTGRES_PASSWORD=odoo9 -p 5432:5432 --name db9 postgres:9.5

#Run the container
docker run -it --name odoo9 -v /opt/docker/config/odoo9:/etc/odoo -v /opt/odoo/addons/9.0:/mnt/extra-addons -p 8069:8069 --link db9:db toolkt/odoo:9.0  --  -u all -d rps_smr


#Stop and Start the service
docker stop odoo9 && docker start -a odoo9


#Stop and Delete the service
docker stop odoo9 && docker rm odoo9

#Enter the terminal of the container
docker exec -it odoo9 bash

#Delete Image
docker rmi toolkt/odoo:9.0


#Commit the running container to the image and then to Docker
docker login
docker commit CONTAINER_ID toolkt/odoo:9.0
docker push toolkt/odoo:9.0

```


For Odoo 10.0
```sh
#Build the image
cd /opt/docker/dockerfiles/docker-odoo/10.0/
docker build -t toolkt/odoo:10.0 .

#Run Postgres for Odoo 10.0 Modules
docker stop db
docker run -d -e POSTGRES_USER=odoo10 -e POSTGRES_PASSWORD=odoo10 -p 5432:5432 --name db10 postgres:9.5

#Run the container
docker run -it --name odoo10 -v /opt/docker/config/odoo10:/etc/odoo -v /opt/odoo/addons/10.0:/mnt/extra-addons -p 8060:8069 --link db10:db toolkt/odoo:10.0 -- -u all -d rps_smr


#Stop and Start the service
docker stop odoo10 && docker start -a odoo10


#Stop and Delete the service
docker stop odoo10 && docker rm odoo10

#Enter the terminal of the container
docker exec -it odoo10 bash

#Delete Image
docker rmi toolkt/odoo:10.0


#Commit the running container to the image and then to Docker
docker login
docker commit CONTAINER_ID toolkt/odoo:10.0
docker push toolkt/odoo:10.0

```