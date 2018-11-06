# about

this is just a memo about minc.

# minc

## ./minc

basic process in create container which is written in shell script.

1. export environment variables
2. parse options
3. make temprary working directory
4. call minc-exec (./libexec/minc-exec)

## ./libexec/minc-exec

1. set process to trap signal
2. save setting in a file
3. make network namespace (vether and set NIC)
4. resolv.conf
5. bind cpu to this process
6. execute minc-cage (./libexec/minc-cage)
7. unshare namespaces
8. execute a command in a new netspace with minc-core (./libexec/minc-core)

## ./libexec/minc-cage

1. memory limitation
2. cpu limittation
3. PID limitation

## ./libexec/minc-core

1. set hostname
2. private-mount "/"
3. execute minc-coat (./libexec/minc-coat)
4. prepare root directory
5. make setting files
6. prepare special files (dev)
7. make tmp and fs
8. execute minc-leash (./libexec/minc-leash)

## ./libexec/minc-coat

1. make filesystem with overrayfs

## ./libexec/minc-leash

1. drop capability to prevent from breaking out