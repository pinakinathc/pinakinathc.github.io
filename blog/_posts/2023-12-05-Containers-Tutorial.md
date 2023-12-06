---
title: A Short Tutorial on How to Use Containers
layout: post
comments: false
mathjax: true
header: true
author: pinaki
date: December 05, 2023
permalink: /containers-tutorial/
---

<!--more-->

*In this blog, I will explain how to use docker in a computer that already has docker installed. This should be fairly quick read for people with less time. For inquisitive minds, I will also explain how to setup Docker in a computer for others to use. Finally, I shall explain about a variation of Docker popular in HPC, known as Singularity. This tutorial is focused towards users of docker and not developers.*

## [Motivation](#motivation)

Think of Docker as a better version of your Anaconda or Miniconda. It wraps all your libraries (python, C++, etc.) into a `Docker Image` (this is usually a folder or one file). This docker image is equivalent to your conda environment. You can create a seperate docker image for each of your projects. For AI/ML projects using PyTorch+cuda a docker image usually takes approx. 13GB disk space. You can create a docker image in your laptop (or some desktop used for debugging). Then transfer this docker image to any GPU server (HPC) and it will run without any issues.

The benefit of using docker is, previously, we created a miniconda environment in our local desktop. Then, to run our code for 2/3 days in a GPU server, we had to re-install the packages (especially some packages were build using cuda-11.7 but your server had cuda-11.3, etc.)

## [How to use Docker](#how-to-use-docker)

Remember, I am no expert on docker and it always best to learn from the people who developed it. So, if you can, learn from the official docs here: [docker get-started](https://docs.docker.com/get-started/02_our_app/)

I shall assume you already have docker installed in your debugging GPU machine and you are using this machine from your laptop using `vscode`. You do not need docker installed in your laptop, you only need it in your debugging GPU machine. If you do not have docker installed in your debugging GPU machine, go to [https://docs.docker.com/engine/install/ubuntu/](https://docs.docker.com/engine/install/ubuntu/).

**Step-1:** Pull an pre-built docker image from [hub.docker.com](https://hub.docker.com). 

I shall pull a docker with PyTorch2.0 and cuda 11.7 that you can find in this url: [https://hub.docker.com/r/pytorch/pytorch/tags](https://hub.docker.com/r/pytorch/pytorch/tags?page=1&name=11.7). Go to your debugging GPU desktop, open a terminal and type:

    $ docker pull pytorch/pytorch:2.0.1-cuda11.7-cudnn8-runtime

**Step-2:** Join your debugging GPU using `vscode` and install a bunch of vscode extensions: `Dev Containers`, `Docker`, `Remote - SSH`, `Remote - SSH: Editing Configurations Files`, and `Remote Explorer`.

**Step-3:** (1) Start your docker image, (2) Attach your codebase, (3) Attach your local GPUs. Open the terminal inside your vscode and type the following commands:

    $ docker image ls
    
    REPOSITORY        TAG                              IMAGE ID       CREATED         SIZE
    pytorch/pytorch   2.0.0-cuda11.7-cudnn8-runtime    372afdac2915   8 months ago    6.44GB
    pytorch/pytorch   1.12.1-cuda11.3-cudnn8-runtime   385dc33ab519   16 months ago   5.93GB
    pytorch/pytorch   1.9.0-cuda11.1-cudnn8-runtime    12da3f8ec2ec   2 years ago     7.92GB
    
    $ git clone https://github.com/pytorch/examples # Download dummy code examples to check your installation
    
    $ export IMAGE_ID=372afdac2915 # image ID of your docker image
    $ export PATH_TO_CODEBASE=$PWD/examples # absolute path to your codebase
    $ export CONTAINER_NAME=test_docker # when you start a docker image, a container is created, which you will run. Name that container.

    $ docker run -it -v $PATH_TO_CODEBASE:/workspace --gpus all --name test_docker $IMAGE_ID

    root@0524673faa63:/workspace# ls
    CODEOWNERS          LICENSE    dcgan        fast_neural_style  gcn       mnist                  mnist_rnn               run_python_examples.sh  super_resolution          vision_transformer
    CODE_OF_CONDUCT.md  README.md  distributed  fx                 imagenet  mnist_forward_forward  regression              runtime.txt             time_sequence_prediction  word_language_model
    CONTRIBUTING.md     cpp        docs         gat                legacy    mnist_hogwild          reinforcement_learning  siamese_network         vae
    
    root@0524673faa63:/workspace# cd mnist
    root@0524673faa63:/workspace/mnist# ls
    README.md  main.py  requirements.txt
    
    root@0524673faa63:/workspace/mnist# python main.py 
    Downloading http://yann.lecun.com/exdb/mnist/train-images-idx3-ubyte.gz
    Downloading http://yann.lecun.com/exdb/mnist/train-images-idx3-ubyte.gz to ../data/MNIST/raw/train-images-idx3-ubyte.gz
    100%|███████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████| 9912422/9912422 [00:00<00:00, 20142812.27it/s]
    Extracting ../data/MNIST/raw/train-images-idx3-ubyte.gz to ../data/MNIST/raw

    Downloading http://yann.lecun.com/exdb/mnist/train-labels-idx1-ubyte.gz
    Downloading http://yann.lecun.com/exdb/mnist/train-labels-idx1-ubyte.gz to ../data/MNIST/raw/train-labels-idx1-ubyte.gz
    100%|███████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████| 28881/28881 [00:00<00:00, 93181302.94it/s]
    Extracting ../data/MNIST/raw/train-labels-idx1-ubyte.gz to ../data/MNIST/raw
    ...
    ...

**Step-4**: In step-3, we executed mnist example using terminal. Now, we do the same using vscode as shown in the following video:

<iframe width="420" height="345" src="https://www.youtube.com/embed/_bm8tcI1Ee0">
</iframe>

## [Install Docker](#install-docker)

Follow the official tutorial here: [https://docs.docker.com/engine/install/ubuntu/](https://docs.docker.com/engine/install/ubuntu/)

The steps in the official tutorial is pretty straight-forward. In case you are stuck, send me an email and I will populate the steps.

## [Alternative of Docker -- Singularity Containers](#singularity)

<blockquote class="reddit-embed-bq" data-embed-showtitle="true" data-embed-height="680"><a href="https://www.reddit.com/r/docker/comments/7y2yp2/comment/dudgw7e/">Comment</a><br> by<a href="https://www.reddit.com/user/elbigdoggogoog/">u/elbigdoggogoog</a> from discussion<a href="https://www.reddit.com/r/docker/comments/7y2yp2/why_is_singularity_used_as_opposed_to_docker_in/"><no value=""></no></a><br> in<a href="https://www.reddit.com/r/docker/">docker</a></blockquote><script async="" src="https://embed.reddit.com/widgets.js" charset="UTF-8"></script>

<br>

So let's get `Singularity`. To install you can follow the official docs here at: [https://docs.sylabs.io/guides/latest/user-guide/quick_start.html](https://docs.sylabs.io/guides/latest/user-guide/quick_start.html)

I will write the steps for Ubuntu. Run the following commands in terminal:

    # Ensure repositories are up-to-date
    $ sudo apt-get update
    
    # Install debian packages for dependencies
    $ sudo apt-get install -y \
        autoconf \
        automake \
        cryptsetup \
        git \
        libfuse-dev \
        libglib2.0-dev \
        libseccomp-dev \
        libtool \
        pkg-config \
        runc \
        squashfs-tools \
        squashfs-tools-ng \
        uidmap \
        wget \
        zlib1g-dev

    # Install Go
    $ wget https://go.dev/dl/go1.21.5.linux-amd64.tar.gz
    $ rm -rf /usr/local/go && tar -C /usr/local -xzf go1.21.5.linux-amd64.tar.gz
    $ sudo echo "export PATH=$PATH:/usr/local/go/bin" >> $HOME/.profile

    # Check Go version
    $ go version

    # Install Singularity
    $ export VERSION=4.0.0 && \
    wget https://github.com/sylabs/singularity/releases/download/v${VERSION}/singularity-ce-${VERSION}.tar.gz && \
    tar -xzf singularity-ce-${VERSION}.tar.gz && \
    cd singularity-ce-${VERSION}

    $ ./mconfig && \
    make -C builddir && \
    sudo make -C builddir install

    # Check if Singularity is installed
    $ singularity help
    Linux container platform optimized for High Performance Computing (HPC) and
    Enterprise Performance Computing (EPC)

    Usage:
    singularity [global options...]

Now, we shall create a singularity container:

    # Build Singularity Container
    $ singularity build --sandbox test_singularity docker://pytorch/pytorch:2.0.0-cuda11.7-cudnn8-runtime

    # Run the container
    $ singularity shell  --nv --writable test_singularity