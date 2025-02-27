

# Objectives of the IP2 have been achieved as outlined below:

## 1. Minimalist Base image selection: 
    Both client and Backend containers are running of node:16- alpine3:16 images 
    Packages and depenencies were clean installed(npm ci to ensure the installed packages match the package-lock.json exactly) and caches cleared on Production environment: npm install --production && npm cache clean --force) reducing the final image size.
    

## 2. Versioned images pushed to Docker Hub: 
    Reconfiguration done on the Dockerfile reduce the image size - The Dockerfiles have multi-stage builds to separate build from prod to further reduce the final image size. 
    With each significant reconfiguration on the respective Dockerfile, in an attempt to build lighter functional images, versioned images have been uplaoded to the repos below:
    ![image](https://github.com/user-attachments/assets/d58a6d8d-c910-4435-bc0a-37d814659901)
    
   ### Client app image: https://hub.docker.com/repository/docker/kajuju/ip2-app-frontend/
       ![image](https://github.com/user-attachments/assets/81b049de-706c-4180-abc0-65ae347e3011)

   ### Backend app image: https://hub.docker.com/repository/docker/kajuju/ip2-app-backend/
       ![image](https://github.com/user-attachments/assets/a7aec309-a7e9-4291-9514-cce6bd5e219c)

    The latest images have been used on the compose file.

## 3. Dockerfiles:
    Client and Backend nodes added to respecive directories on the repo : https://github.com/geekydee/Wk4-IP2/tree/main 

## 4. Docker compose: 
    compose file addedd to Github repo. docker-compose.yaml 

   ### Container Networking: 
    All containers are attached to the network below to ensure the services can communicate.
        networks:
        ip2-app-net:
            name: ip2-app-net
            driver: bridge
            attachable: true
            ipam:
            config:
                - subnet: 172.18.0.0/16
                ip_range: 172.18.0.0/16

   ### Persistent storage :
    A Volume added was attached to the mongodb container and mapped to the data folder to ensure the data persists even after teardown.
        volumes:
            ip2-mongo-data:
                name: ip2-mongo-data
