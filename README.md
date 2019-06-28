# cuteradio

Cuteradio is the main repository for a simple Qt-based Internet radio that runs on a Raspberry Pi 3. This repository contains five submodules. Each submodule corresponds to a Yocto layer and is added as a subdirectory to the directory _cuteradio/sources_. Cuteradio is currently based on the Yocto release _thud_.

We must install Docker before we can run the Yocto build. Docker installation is described [here](https://www.embeddeduse.com/2019/02/11/using-docker-containers-for-yocto-builds/#install). We execute the Yocto build in the [Docker container CROPS](https://hub.docker.com/u/crops/) as described in the blog post [Yocto Builds with CROPS Containers](https://www.embeddeduse.com/2019/05/06/yocto-builds-with-crops-containers/).

We create a work directory at a place of our choice and clone the main repository with all its submodules.

    host$ mkdir work-cuteradio
    host$ cd work-cuteradio
    host$ git clone --recurse-submodules https://github.com/bstubert/cuteradio.git

For convenience, we copy the helper script _./cuteradio/ycr_ to the path _~/bin_, which is included in _PATH_. 

    host$ cp ./cuteradio/ycr ~/bin


The call

    host$ ./cuteradio/ycr <yocto-command>

spins up the CROPS container, enters the Yocto build environement and executes the _<yocto-command>_.

For example, if we want to run Yocto commands interactively in the build environment, we execute the following command. 

    host$ ycr bash
    pokyuser@fd206ebcd9d6:/work-cuteradio/build$

The second line is in the Linux environment provided by the CROPS container. So, we could run bitbake to build the Cuteradio image.

    pokyuser@fd206ebcd9d6:/work-cuteradio/build$ bitbake cuteradio-image

We exit the container with the command:

    pokyuser@fd206ebcd9d6:/work-cuteradio/build$ exit


We can also start the Yocto build with a single command:

    host$ ycr bitbake cuteradio-image


