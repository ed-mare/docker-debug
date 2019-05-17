# Attach a container with debug tools (strace, lsof) to a problematic docker container.
#
# Based on https://medium.com/@rothgar/how-to-debug-a-running-docker-container-from-a-separate-container-983f11740dc6
# and http://blog.johngoulah.com/2016/03/running-strace-in-docker/.
#
# Includes strace and lsof.
#
# Use the pid flag to attache to another container.
#
# --pid=""  : Set the PID (Process) Namespace mode for the container,
#             'container:<name|id>': joins another container's PID namespace
#             'host': use the host's PID namespace inside the container
#
# 
# Download... 
# curl -S https://raw.githubusercontent.com/ed-mare/docker-debug/master/general/Dockerfile > Dockerfile
#
# Build...
# docker build -t debugtools .
#
# Use...
# run -it --pid=container:<container> --net=container:<container> --cap-add sys_admin --cap-add sys_ptrace debugtools /bin/bash
#
# In bash session:
# ps aux # shows processes in container
# strace -p <pid>
# lsof
#
# Other tools to use...
#
# docker pull sysdig/sysdig
# run -it --pid=container:<container> --net=container:<container> --cap-add sys_admin --cap-add sys_ptrace  /bin/bash

FROM debian:stretch

# procps is for ps command
RUN apt-get update \
	&& apt-get install -y --no-install-recommends \
    ca-certificates \
    libssl-dev \
    curl \
    procps \
    lsof \
    strace \
	&& rm -rf /var/lib/apt/lists/*
