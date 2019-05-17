# docker-debug

Docker images for debugging containers or for accessing/debugging services.

1. redis/Dockerfile - For accessing redis. Includes redis-cli and Ruby with redis gem.
2. general/Dockerfile - Attach to other containers. Includes lsof, strace, ps. 


Other tools:

docker pull sysdig/sysdig
docker run -it --pid=container:yourcontainerid --net=container:yourcontainerid --cap-add sys_admin --cap-add sys_ptrace  /bin/bash
