# System

## Service

`systemctl restart docker` will restart it.  To start if it is down `systemctl start docker`.  The command `systemctl status docker` will return information on the status of the service.


## Memory
free
(h)top
ps
ps -ef
fdisk (exit=q)
du

## The /proc folder

``` cd /proc
    cat meminfo
    cat partitions
    cat cpuinfo
```
