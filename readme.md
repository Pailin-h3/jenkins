1. install docker desktop
2. run below command to create network, recommend name: jenkins
    $docker network create <network_name>
3. you can check network by this command
    $decker network ls
4. create Dockerfile (I already created it)
5. cd to Dockerfile and run below command to build first image of jenkins, recommend name: jenkins-blueocean:1.0
    $docker build -t <image_name:image_version> .
6. run jenkins image in docker container, recommend container name: jenkins-blueocean
    $docker run --name <container_name> --restart=on-failure --detach  --network <network_name> --env DOCKER_HOST=tcp://docker:2376  --env DOCKER_CERT_PATH=/certs/client --env DOCKER_TLS_VERIFY=1 --volume jenkins-data:/var/jenkins_home  --volume jenkins-docker-certs:/certs/client:ro  --publish 8080:8080 --publish 50000:50000 <image_name:image_version or image_id>
7. now we should see jenkins is running on localhost:8080
8. to get into container
    $docker exec -it <container_name> bash