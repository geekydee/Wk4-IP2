//This serves as a README file for the project.

Objectives of the IP2 have been achieved as outlined below:

1. Minimalist Base image selection:
a. Both client and Backend containers are running of node:18- alpine3:19
Node.js was further installed on Alpine Linux with the --no-cache option, to ensure that 'apk' doesn't cache the index of available packages, reducing the final image size.

b. Mongo container: 

2. Versioned images pushed to Docker Hub:
Reconfiguration done on the Docerfile reduce the image size  -
The Dockerfile has multi-stage builds to separate build from prod to further reduce the final image size.
With every Reconfigurations on the Dockerfile, in an attempt to build lighter functional images, versioned images have been uplaoded to the repos below:

Client app: https://hub.docker.com/repository/docker/kajuju/ip2-app-frontend/
backend app: https://hub.docker.com/repository/docker/kajuju/ip2-app-backend/

3. Config files:
client Dockerfile: https://github.com/geekydee/Wk4-IP2.git/WK-IP2/client/Dockerfile

Backend Dockerfile: https://github.com/geekydee/Wk4-IP2.git/Wk4-IP2/backend/Dockerfile

Docker compose :
	Conatiner Networking:
	Persistent storage : 

