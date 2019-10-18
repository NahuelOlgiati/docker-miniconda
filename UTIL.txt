#Commands
##Change extension
find . -name "*.FIT" -exec rename 's/.FIT$/.fit/' {} \;

##Generate csv files
find ./dark -name '*.fit' -exec basename \{} \; > ./dark/dark_filenames.csv

#Info
https://www.youtube.com/watch?v=B8GtcE9G1io
http://hea-www.harvard.edu/~saku/CCDprocessCfA.pdf
http://ast.noao.edu/sites/default/files/IRAF_beginners_guide.pdf
http://www.covingtoninnovations.com/dslr/newdslr/#Arithmetic


#Docker Install
##https://docs.docker.com/install/linux/docker-ce/ubuntu/
sudo apt-get update

sudo apt-get install -y \
    apt-transport-https \
    ca-certificates \
    curl \
    gnupg-agent \
    software-properties-common

curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -

sudo apt-key fingerprint 0EBFCD88

sudo add-apt-repository \
   "deb [arch=amd64] https://download.docker.com/linux/ubuntu \
   $(lsb_release -cs) \
   stable"

sudo apt-get update

sudo apt-get install -y docker-ce docker-ce-cli containerd.io

docker --version

sudo groupadd docker

sudo usermod -aG docker $USER

newgrp docker 

docker run hello-world
