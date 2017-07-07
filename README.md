# test-docker-x-container-communication
Simple example to test tcp communication from one docker container to the other

This contains 2 node containers. One is a tcp server. The other is a client. When you start it up, the server container starts. The client container waits for the server port to be ready, and then tries to contact it. After contacting, the client process will exit. You'll need to end the server process with ctrl-c.
