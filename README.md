# VerilogSimulationEnv
Don't wanna use ADFP if I'm not doing synthesis.

## Set up environment
```
docker build -t [image_name] .
```
```
xhost +local:docker

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
## verilator (recommended)
verilator --binary -Wno-fatal [TESTBED/PATTERN/DESIGN.v] --top [top_module_name] --trace
./obj_dir/V[top_module_name]
gtkwave [dumped.vcd] &
```
```
## iverilog
iverilog -o [complied_file_name] [TESTBED/PATTERN/DESIGN.v]
vvp [complied_file_name]
gtkwave [dumped.vcd] &
```
