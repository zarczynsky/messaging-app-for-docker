# test-docker-x-container-communication
Simple example to test tcp communication from one docker container to the other

This contains 2 node containers. One is a tcp server. The other is a client. When you start it up, the server container starts. The client container waits for the server port to be ready, and then tries to contact it. After contacting, the client process will exit. You'll need to end the server process with ctrl-c.

## Important things to note: 
- Docker uses dynamic IP addresses. So you target the other containers with the container name instead of IP and then docker will substitute it magically.
- `/code` is a volume that is mounted. Basically like a shared folder that both containers use.

## To rebuild the images from local and start the docker containers
`$ docker-compose up --build`

This is a great pattern for easily trying things out locally because it builds the docker images and composes the services from all the local files. This allows for quick and easy iteration and experimentation.

## Success
This is what success looks like
```
Attaching to dockertestportcommunication_tcp_server_1, dockertestportcommunication_tcp_client_1
tcp_client_1  | READY
tcp_server_1  | Server listening on tcp_server:6969
tcp_server_1  | CONNECTED: 172.18.0.3:38627
tcp_server_1  | CLOSED: 172.18.0.3 38627
tcp_server_1  | CONNECTED: 172.18.0.3:59718
tcp_client_1  | CONNECTED TO: tcp_server:6969
tcp_server_1  | DATA 172.18.0.3: I am Chuck Norris!
tcp_client_1  | DATA: You said "I am Chuck Norris!"
tcp_client_1  | Connection closed
tcp_server_1  | CLOSED: 172.18.0.3 59718
dockertestportcommunication_tcp_client_1 exited with code 0
```
