# Start the server on GCP
## setting a VM instance
Choose CoreOs stable, because it has docker on premise. 
Make the external IP address static.
Make sure to add fire wall rule to the instance, defaultly GCP don' t expose any port.
For simplicity just allow any income and outcome data because the server needs more port than you might know.

## Install docker image
[Instructions follow this link](https://hub.docker.com/r/itzg/minecraft-server/).
Use ```docker pull itzg/minecraft-server``` to pull image. ```docker run -d -e EULA=TRUE -e VERSION=1.12.2 -p 25565:25565 --name mc itzg/minecraft-server```
to start the server. Modify the server.properties file inside to close the online check. (```docker exec -it mc /bin/sh```)

## Connect the server from client
Download a client from anywhere, [VM external IP address]:25565 to connect the server.



