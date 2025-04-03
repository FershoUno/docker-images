# README

Deploy an easy Socks5 server with Docker by following one of the following instructions

### Docker Run

Run the following command line to deploy microsocks 

    docker run -d --name microsocks -p 8080:1080 -e USERNAME=MyProxyUser -e PASSWORD=MyP4ssw0rdPr0xy fershouno/microsocks:latest

### Docker Compose

Create the docker-compose.yaml file and add the following content if you  want to deploy it this way
    
    services:
    microsocks:
        image: fershouno/microsocks:latest
        container_name: microsocks
        ports:
        - "1080:1080"
        environment:
        USERNAME: MyProxyUser
        PASSWORD: MyP4ssw0rdPr0xy
        restart: unless-stopped


### Using .env

Create a .env file with the following contents

    USERNAME=MyProxyUser
    PASSWORD=MyP4ssw0rdPr0xy
    PORT=1080


Create a docker-compose.yaml file with the following contents

    services:
    microsocks:
        image: fershouno/microsocks:latest
        container_name: microsocks
        ports:
        - "${PORT:-8080}:1080"
        environment:
        - USERNAME=${USERNAME:-user}
        - PASSWORD=${PASSWORD:-pass}
        restart: unless-stopped


