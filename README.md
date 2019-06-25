# cuteradio

Clone the repo:

    $ mkdir work-cuteradio
    $ cd work-cuteradio
    /work-cuteradio$ git clone --recurse-submodules https://github.com/fkromer/cuteradio.git

Install the helper script `ycr` into the user's local binary directory:

    /work-cuteradio$ cp cuteradio/ycr ~/.local/bin
    /work-cuteradio$ chmod +x ~/.local/bin/ycr

    wget -O ~/.local/bin/ycr https://github.com/fkromer/cuteradio/blob/master/ycr
    chmod +x ~/.local/bin/ycr

Change the directory paths for all BBLAYERS in
`/work-cuteradio/cuteradio/sources/meta-cuteradio/custom/bblayers.conf.sample` to the directory `/work-cuteradio` inside the container:

    /work-cuteradio$ $ sed -i 's/\/home\/cuteradio\/yocto\/input/\/work-cuteradio/g' cuteradio/sources/meta-cuteradio/custom/bblayers.conf.sample

sed -i 's/home/work-cuteradio/g' cuteradio/sources/meta-cuteradio/custom/bblayers.conf.sample

Check if the file contains the adjusted directory paths with
`/work-cuteradio$ cat cuteradio/sources/meta-cuteradio/custom/bblayers.conf.sample`.

    BBLAYERS ?= " \
       /work-cuteradio/cuteradio/sources/poky/meta \
       /work-cuteradio/cuteradio/sources/poky/meta-poky \
    ...

The file lines to change correspond to the meta-layer configuration which can
be found in the
[github repository meta-cuteradio](https://github.com/bstubert/meta-cuteradio/blob/master/custom/bblayers.conf.sample#L9L15).

To enter the bash in the docker container execute:

    /work-cuteradio$ ycr bash
    pokyuser@26fea839ba24:/work-cuteradio/build$

To build an image execute:

    /work-cuteradio$ ycr bitbake cuteradio-image

The full documentation can be found in the blog post
[Yocto Builds with CROPS Containers](https://www.embeddeduse.com/2019/05/06/yocto-builds-with-crops-containers/).
