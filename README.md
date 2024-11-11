# Docker_Network
Docker Grid | Run Docker Containers and link them

Steps to follow: 
1. Pull images of Selenium Hub
> docker pull selenium/hub

2. Pull images of Selenium node Clients
> docker pull selenium/node-chrome
> docker pull selenium/node-firefox
> docker pull selenium/node-edge

3. Start Network: Docker Network create GRID Network
> docker network create gridnetwork

4. Create and run the containers and link them
docker run -d -p 4442-4444:4442-4444 --net grid --name selenium-hub selenium/hub:latest


# Selenium Grid Node with Chrome

How to run

1. Create a Docker Network 
> docker network create grid

2. Start the Hub using the created network
> docker run -d -p 4442-4444:4442-4444 --net grid --name selenium-hub selenium/hub:latest

For Chrome
> docker run -d --net grid -e SE_EVENT_BUS_HOST=selenium-hub  --shm-size="2g"  -e SE_EVENT_BUS_PUBLISH_PORT=4442  -e SE_EVENT_BUS_SUBSCRIBE_PORT=4443  selenium/node-chrome:latest

For Edge
> docker run -d --net networkgrid -e SE_EVENT_BUS_HOST=SeleniumHub  --shm-size="2g"  -e SE_EVENT_BUS_PUBLISH_PORT=4442  -e SE_EVENT_BUS_SUBSCRIBE_PORT=4443  selenium/node-edge:latest


3. Point your WebDriver tests to http://localhost:4444⁠
