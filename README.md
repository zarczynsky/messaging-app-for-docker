# test-docker-x-container-communication
Simple example to test tcp communication from one docker container to the other

This contains 2 node containers. One is a tcp server. The other is a client. When you start it up, the server container starts. The client container waits for the server port to be ready, and then tries to contact it. After contacting, the client process will exit. You'll need to end the server process with ctrl-c.

## Important things to note: 
- Docker uses dynamic IP addresses. So you target the other containers with the container name instead of IP and then docker will substitute it magically.
- `/code` is a volume that is mounted. Basically like a shared folder that both containers use.

## To rebuild the images from local and start the docker containers
`$ docker-compose up --build`

This is a great pattern for easily trying things out locally because it builds the docker images and composes the services from all the local files. This allows for quick and easy iteration and experimentation.
