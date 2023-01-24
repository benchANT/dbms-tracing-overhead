# dbslower versions

## Overview

### Active
In the Active version, the probes only detect the start and end of queries, but the program does not do anything with them.
### Process
In the Process version, the probes detect the start and end of queries, the queries are read and their runtime is 
calculated, but they do not get printed to the command line
### Persist
In the Process version, the probes detect the start and end of queries and the queries are written to the command line 
with the PID of the process that executed them and their runtime

## Requirements
* bison 
* build-essential 
* cmake 
* flex 
* git 
* libedit-dev
* libllvm12 
* llvm-12-dev 
* libclang-12-dev 
* python 
* zlib1g-dev 
* libelf-dev 
* libfl-dev 
* python3-distutils
* systemtap-sdt-dev
* [BCC](https://github.com/iovisor/bcc/blob/master/INSTALL.md)

The dbslower_*.py files have to be copied to the bcc/tools directory and can be executed using the command
`python3 dbslower.py -x <Path tho binary file> -m 0 <DBMS name> > <logfile.txt>` e.g. `python3 dbslower.py -x /usr/local/mysql/bin/mysqld -m 0 mysql > log.txt`
for MySQL. The -m 0 flag tells the program to trace all incoming queries slower than 0 ms to get a full log. Redirecting
the output of the program to a file is optional, but reduces the overhead.