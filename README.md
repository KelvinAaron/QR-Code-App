This repository provides a lightweight environment to demonstrate web server setup and basic load balancing using Docker containers. The stack consists of two web servers (web-01 and web-02) and a load balancer (lb-01) connected to a custom Docker network. Each service runs Ubuntu 24.04 with SSH enabled to allow you to install and configure additional software.

You can find the source code for the app here https://github.com/KelvinAaron/QR-Code-source-code.git

**Requirements**
Docker and Docker Compose installed on your machine
At least 2 GB of free RAM and a few hundred megabytes of disk space
Setup
Clone the repository:

git clone <repo-url>

cd QR-Code-App

Bring up the lab environment (builds the images on first run):

docker compose up -d --build

Verify that the containers are running:

docker compose ps

You should see web-01, web-02, and lb-01 online. The services are attached to the lablan network with the following addresses:

Container	IP	Exposed Ports
web-01	172.20.0.11	2211 (SSH), 8080 (HTTP)
web-02	172.20.0.12	2212 (SSH), 8081 (HTTP)
lb-01	172.20.0.10	2210 (SSH), 8082 (HTTP)

Visit http://localhost:8082 to see the app running

From the app you can generate a qr code or read generate qr codes

Visit this link for a video on how to use the app: https://youtu.be/FqBNk4yc0Os

curl -I http://localhost:8082 
Repeated requests should alternate between web-01 and web-02 and the X-Served-By header in the output will reveal which server handled each request.



docker compose down
Enjoy your QR Code App!
