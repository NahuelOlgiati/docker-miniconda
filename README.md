# docker-miniconda

## for build
sh build.sh

## for x11 forwarding
docker run -d --rm --name x11-bridge -e MODE="tcp" -e XPRA_HTML="yes" -e DISPLAY=:14 -p 10000:10000 nahuelolgiati/xpra3

## for run miniconda3
docker run -it --rm --volumes-from x11-bridge -e DISPLAY=:14 -v /tmp/.X11-unix:/tmp/.x11-unix -v ~/iraf/data:/home/iraf/data nahuelolgiati/miniconda3 /bin/bash

## user permissions
for MYGID: echo $(id -g ${USER})
for MYUID: echo $(id -u ${USER})
groupmod --gid MYGID iraf
usermod  --uid MYUID iraf
su iraf

## for run iraf/ds9
iraf

## see on
http://localhost:10000

## public image
https://hub.docker.com/r/nahuelolgiati/miniconda3
