# docker-miniconda
- Use miniconda3-centos
- continuum version under development

## for build
sh build.sh

## for x11 forwarding
docker run -d
--rm
--name x11-bridge
-e MODE="tcp"
-e XPRA_HTML="yes"
-e DISPLAY=:14
-p 10000:10000
jare/x11-bridge

## for run miniconda3
docker run -it
--rm
--volumes-from x11-bridge
-e DISPLAY=:14
-v /tmp/.X11-unix:/tmp/.x11-unix
-v ~/iraf/data:/home/iraf/data
miniconda3-centos
/bin/bash

## for run iraf/ds9
cd /home/iraf; conda activate iraf27; ds9 & printf "xgterm\n" | mkiraf; xgterm -sb -sl 5000 -geometry 80x48 -fn 10x20 -cr red -bg grey -e cl &

## see on http://localhost:10000

## public image
https://hub.docker.com/r/nahuelolgiati/miniconda3

## fit files
http://www.rawastrodata.com
