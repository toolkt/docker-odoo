# docker-odoo
Custom Docker Images for Odoo

Build the image
```sh
docker build -t toolkt/odoo:8.0 .
```

Run the container
```sh

docker run -it --name odoo8 -v /opt/docker/config/odoo8:/etc/odoo -v /opt/odoo/addons:/mnt/extra-addons -p 8069:8069 --link db:db toolkt/odoo:8.0 --  -u dmpi_base -d dmpi_test

docker stop odoo8 && docker start -a odoo8

```

Start & stop the service
```sh
docker stop odoo8
```

Enter the terminal of the container
```sh
docker exec -it odoo8 bash
```


Commit the running container to the image and then to Docker
```sh
docker login
#Enter Username and Password
docker commit CONTAINER_ID toolkt/odoo:8.0
docker push toolkt/odoo:8.0
```