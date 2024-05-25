# What's this
These are the congifure and build files help to run Python on RuxOS using CPython interpreter.

The Python execute file and lib files are placed in 'rootfs/'. The 'rootfs/' is a minimal rootfs for RuxOS in this application using 9pfs.

# How to build

Copy this directory to 'ruxos/apps/c' and change its name to 'python3'

## Dynamic Loading

Python3 depends on the dynamic loading, config the python args and envs in axbuild.mk


## Quick Start

1. Extract and compile python source and third-party libraries

```sh
chmod +x build.sh
./build.sh
```

2. Copy the musl libc dynamic loader to './rootfs/lib/'

3. Run

change directory to 'ruxos/' directory

run the python terminal
```sh
make A=apps/c/python3 ARCH=aarch64 V9P=y NET=y MUSL=y LOG=off SMP=4 run
```

run the python file:

copy python source file into rootfs and config axbuild.mk to:

```txt
app-objs=main.o
ARGS=/bin/python3.11,<souce_path>
ENVS=PYTHONLIB=/lib,PYTHONHOME=/
V9P_PATH=${APP}/rootfs
```