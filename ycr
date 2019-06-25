#!/bin/bash
cmd="export TEMPLATECONF=/work-cuteradio/cuteradio/sources/meta-cuteradio/custom 
&& source /work-cuteradio/cuteradio/sources/poky/oe-init-build-env build 
&& $@"
docker run --rm -it -v ${PWD}:/work-cuteradio crops/poky:ubuntu-16.04 \
    --workdir=/work-cuteradio --cmd "${cmd}"
