# VerilogPatternGenerationEnv
Don't wanna use ADFP if I'm not doing synthesis.

## Set up environment
```
docker build -t [image_name] .
```
```
xhost +local:docker # Run this on your host first!

docker run -id \
    --restart=always \
    --name [container_name] \
    -v [local_dir_AbsPath_to_be_mounted]:/root \
    -e DISPLAY=$DISPLAY \
    -v /tmp/.X11-unix:/tmp/.X11-unix:rw \
    --net=host \
    [image_name]
```
## Create new terminal
```
docker exec -it [container_name] /bin/bash
```
## RTL simulation & debug w/ waveform
```
iverilog -o [complied_file_name] [TESTBED/PATTERN/DESIGN.v]
vvp [complied_file_name]
gtkwave [dumped.vcd] &
```
