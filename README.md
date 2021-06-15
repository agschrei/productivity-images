# Productivity container images

This repository contains blueprints for some docker images.  
Please note that these images are not intended for use as base images to build application deployments on top of.  
Instead, the images in this repository are intended for interactive use to get up and running quickly on new systems that have a docker daemon available.

## Base image  
This is the bare minimum I want to have in an interactive image, is based on ubuntu 20.04 and comes with the following things set up:  
- curl
- git
- python 3.8 and pip
- zsh (set up with [oh-my-zsh](https://github.com/ohmyzsh/ohmyzsh) and the [p10k](https://github.com/romkatv/powerlevel10k) theme)
- build-essential (including gcc and make)

To make installation of additional packages easier, the default user for this image is root.

## K8s image
This image adds on top of the minimal base image and provides the following:
- kubectl
- helm
A kubeconfig file is expected to be mounted at k8s/config