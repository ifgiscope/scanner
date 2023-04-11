# README

Project for the course "Geoinformatics 8: Perspectives" at the ifgi Münster.
Based mainly upon [CityScoPy](https://github.com/CityScope/CS_CityScoPy)

Currently only working on Linux machines. The use of xhost is necessary even if the GUI is deactivated in the settings.

## How to use
Before starting the containers check the mounted video devices with `ls /dev | grep video` and adjust the docker-compose files according to your system and set the correct cameraID for the camera you want to use in cityscopy.json  

1. Run `xhost +local:docker` to allow docker conatiners access to the display via xhost.
2. If a new camera is used run `docker compose -f docker-compose.calibrate.yml up` and select the corners of the grid. Then run `docker compose -f docker-compose.calibrate.yml down`
3. Run `docker compose up`
4. To stop the application do a keyboard interrupt and run `docker compose down` or run docker compose down in a new terminal.


## Documentation dockerfile
The base image python:3.8-bullseye was chosen due to the good compatibilty with the used python packages.  
Only one RUN statement was used to avoid unecessary layers. In the RUN statement all necessary dependencies are installed and a non-root user is created. The user is part of the video group so that the container can use cameras.  
Afte ther RUN statement the user is changed from the root user to the newly created user.

## Documentation docker-compose 
Creates two containers, one with the actual CityScoPy program running and another with the UDP listener. The host network mode was chosen to enable the necessary use of the GUI via xhost. The temp directory for xhost is also mounted in the cityscopy container alongside the video devices. The display environment variable from the OS environment is consigned to the cityscopy container.  
The docker-comose.calibrate.yml file only creates a container to calibrate the camera for CityScoPy.  
All containers are mounted with the ./CS_CityScoPy-3.2/ directory as a volume.

## To Do's

[ ] (Maybe) Automate the device mounting. See [stackoverflow: docker-compose devices map all devices from local to container](https://stackoverflow.com/questions/73339141/docker-compose-devices-map-all-devices-from-local-to-container)  
[ ] Connect to a CityIO instance instead the local udp listener   
[ ] Test and adjust with a real grid  