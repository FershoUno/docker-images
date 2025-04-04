# README

Deploy an easy Socks5 server with Docker by following one of the following instructions

### Docker Run

Run the following command line to deploy microsocks 

    docker run -d --name microsocks -p 1080:1080 -e USERNAME=MyProxyUser -e PASSWORD=MyPr0xyP4ssw0rd fershouno/microsocks:latest

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
        PASSWORD: MyPr0xyP4ssw0rd
        restart: unless-stopped


### Using .env

Create a .env file with the following contents

    USERNAME=MyProxyUser
    PASSWORD=MyPr0xyP4ssw0rd
    PORT=1080


Create a docker-compose.yaml file with the following contents

    services:
    microsocks:
        image: fershouno/microsocks:latest
        container_name: microsocks
        ports:
        - "${PORT:-1080}:1080"
        environment:
        - USERNAME=${USERNAME:-user}
        - PASSWORD=${PASSWORD:-pass}
        restart: unless-stopped


