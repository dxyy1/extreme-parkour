# Docker
This guide assumes you have already installed [Docker](https://docs.docker.com/engine/install/ubuntu/) and [nvidia-docker2](https://docs.nvidia.com/datacenter/cloud-native/container-toolkit/install-guide.html) if you have an Nvidia GPU.

## Github
Clone the repository
```
git clone https://github.com/mcx/extreme-parkour.git
```

## Dockerfile
Build the Docker image from the Dockerfile

```
cd extreme-parkour/
docker build -t parkour -f docker/parkour.Dockerfile .
chmod a+x docker/run_parkour.bash
docker/run_parkour.bash
```

## Train
Verify the installation can train the policy
```
cd ~/legged_gym/legged_gym/scripts
python train.py --exptid xxx-xx-WHATEVER --device cuda:0 --no_wandb
```

## Pre-trained models
Play base policies
```
cd ~/legged_gym/legged_gym/scripts
python play.py --exptid 051-40
python play.py --exptid 051-40
python play.py --exptid 051-40
```

## Docker
Do the following steps to get into the container subsequently once it has been created

Run this to allow for GUI once per session (i.e. after every reboot)
```
xhost +si:localuser:$USER
xhost +local:docker
```
Then start the container and enter it
```
docker start parkour
docker exec -it parkour bash
```

## Clean Slate
To delete the container, run
```
docker rm -f parkour
```

