# docker-odoo
Custom Docker Images for Odoo

```sh

```

#Prerequisite: Run Postgres for Odoo Modules
```sh
docker stop db
docker run -d -e POSTGRES_USER=odoo -e POSTGRES_PASSWORD=odoo -p 5432:5432 --name db postgres:9.5
```

VERSION 8
#1. Get the files from Github
```sh
git clone https://github.com/toolkt/docker-odoo.git docker-odoo
```

#2 Build Odoo 8.0 Image
```sh
cd docker-odoo/8.0/
docker build -t toolkt/odoo:8.0 .
```

#3. Run the container
```sh
docker run -p 8069:8069 --name odoo8 --link db:db -t toolkt/odoo:8.0
```

Custom Options

```sh
#Run with custom attributes
docker run -it --name odoo8 -v /opt/docker/config/odoo8:/etc/odoo -v /opt/odoo/addons/8.0/:/mnt/extra-addons -p 8069:8069 --link db8:db toolkt/odoo:8.0 --  -u dmpi_base -d dmpi_test

#Stop and Start the service
docker stop odoo8 && docker start -a odoo8

#Enter the terminal of the container
docker exec -it odoo8 bash
```

#4, Push the image to docker hub
```sh
#Commit the running container to the image and then to Docker
docker login
docker commit odoo8 toolkt/odoo:8.0
docker push toolkt/odoo:8.0

```

VERSION 9

#1. Get the files from Github
```sh
git clone https://github.com/toolkt/docker-odoo.git docker-odoo
```

#2 Build Odoo 9.0 Image
```sh
cd docker-odoo/9.0/
docker build -t toolkt/odoo:9.0 .
```

#3. Run the container
```sh
docker run -p 8069:8069 --name odoo9 --link db:db -t toolkt/odoo:9.0
```

Custom Options

```sh
#Run with custom attributes
docker run -it --name odoo -v /opt/docker/config/odoo:/etc/odoo -v /opt/odoo/addons/9.0/:/mnt/extra-addons -p 8069:8069 --link db:db toolkt/odoo:9.0 --  -u module_name -d database_name

#Stop and Start the service
docker stop odoo8 && docker start -a odoo9

#Enter the terminal of the container
docker exec -it odoo9 bash
```

#4, Push the image to docker hub
```sh
#Commit the running container to the image and then to Docker
docker login
docker commit odoo8 toolkt/odoo:9.0
docker push toolkt/odoo:9.0

```



VERSION 10

#1. Get the files from Github
```sh
git clone https://github.com/toolkt/docker-odoo.git docker-odoo
```

#2 Build Odoo 10.0 Image
```sh
cd docker-odoo/10.0/
docker build -t toolkt/odoo:10.0 .
```

#3. Run the container
```sh
docker run -p 8069:8069 --name odoo10 --link db:db -t toolkt/odoo:10.0
```

Custom Options

```sh
#Run with custom attributes
docker run -it --name odoo -v /opt/docker/config/odoo:/etc/odoo -v /opt/odoo/addons/10.0/:/mnt/extra-addons -p 8069:8069 --link db:db toolkt/odoo:10.0 --  -u module_name -d database_name

#Stop and Start the service
docker stop odoo8 && docker start -a odoo10

#Enter the terminal of the container
docker exec -it odoo10 bash
```

#4, Push the image to docker hub
```sh
#Commit the running container to the image and then to Docker
docker login
docker commit odoo8 toolkt/odoo:10.0
docker push toolkt/odoo:10.0

```

















#Build the image
cd /opt/docker-odoo/9.0/
docker build -t toolkt/odoo:9.0 .

#Run Postgres for Odoo 9.0 Modules
docker stop db9
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
cd /opt/docker-odoo/10.0/
docker build -t toolkt/odoo:10.0 .

#Run Postgres for Odoo 10.0 Modules
docker stop db
docker run -d -e POSTGRES_USER=odoo10 -e POSTGRES_PASSWORD=odoo10 -p 5432:5432 --name db10 postgres:9.5

#Run the container
docker run -p 8069:8069 --name odoo10 --link db10:db -t toolkt/odoo:10.0

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
docker commit odoo10 toolkt/odoo:10.0
docker push toolkt/odoo:10.0

```