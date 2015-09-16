# Getting Started on the Command Line



## Supplemental Reading
* [File System Tree] 
* [Paths]
* [Permissions]
* [Redirection]
* [Streams, Pipes, and Redirects]
* [TLDP: About files and the file system]

## Basic commands

### `man`
Displays the manual entry for the specified command.

The following looks up the manual page for the `pwd` command
```sh
$ man pwd
```
### `pwd`
Prints the current working directory which shows us where we are located in the [File System Tree].

```sh
$ pwd
/home/pi
```
### `ls`
Lists the contents of the current working directory.
```sh
$ ls
Documents	hello.txt
```

`ls` supports many command line options (see `man ls` for more information).  

`-l` is used to show a long listing of the files in a directory.  It will also show the file's permissions and owner.

```sh
$ ls -l
drwxr-xr-x  2 cory cory  4096 Jul 29 14:28 Documents
-rw-r--r--  1 cory cory 20644 Sep 16 11:45 hello.txt
```

### `cd`
Takes one argument for a path and moves to that location in the [File System Tree].  
In this example tell `cd` to move us to the `/etc` directory.
```sh
$ cd /etc
$ pwd
/etc
```
If we wanted to go to our home directory we could `cd /home/pi` or use the `~`, which represents the current user's home directory.
```sh
$ cd ~
$ pwd
/home/pi
```
If we wanted to move 'up' a directory, we can use the `..` to represent the directory 'above' us.
```sh
$ cd ..
$ pwd
/home
```
### `mkdir` 
Takes at least one argument for the directory that is being created.
```sh
$ cd ~
$ mkdir CSCI_211
$ cd CSCI_211
$ pwd
/home/pi/CSCI_211
```

### `sudo`
Used to run a command as a superuser (`root`).


### `rm`
Deletes a file or directory.
```sh
$ ls
myFile.txt
$ rm myFile.txt
$ ls

```

### `shutdown`
Used to shutdown or reboot the system.

To shutdown: 
```sh
$ sudo shutdown -h now
```

To reboot:
```sh
$ sudo shutdown -r now
```

For more options please see `man shutdown`.

## Paths
>***A unique location to a file or folder.  Paths in Linux start off at the root ```/``` of the filesystem.***

###Absolute
An absolute path specifies the location of a file or folder from the root of the file system.

For Example:
```sh
/var/log
/home/pi/Documents/helloWorld.txt
/etc/apache2
```

###Relative
A relative path specifies the location of a file or folder as it relates to the current working directory.  The current working directory represents the folder you are currently in.

To see your current working directory (cwd) use the ```pwd``` command.

For example, if our cwd is ```/home/pi``` and we want to change directory to /```home/pi/Documents``` we could:
```sh
$ cd Documents
$ pwd
$ /home/pi/Documents
```

If our cwd is ```/home/pi``` and we want to change directory to Alice's home directory we could:
```sh
$ cd ../Alice
$ pwd
/home/Alice
```

## Standard Streams
Linux shells use 3 standard streams.  Specifically:

* **stdin** - standard input stream, provides input to the shell.  This is typically the keyboard.
* **stdout** - standard output stream, provides output for the shell.  This is typically displayed on a monitor.
* **stderr** - standard error stream, provides a seperate stream for reporting errors.  This is also typically displayed on a monitor.

## Redirection
By default, Linux applications get their input from stdin and their output goes to stdout.  It is sometimes desireable to redirect either or both of the streams to a different location.

For example, suppose we wanted to take the output of the `ps` command and place it in a file:
```sh
$ ps > psdata.txt
```

We many also want to redirect stdin to come from a file rather then the keyboard.  We can do that as well.  Suppose we have a text file, `text.txt`, that contains the letters a - g randomly ordered with a single character on each line.  To sort that file we can use the sort command.
```sh
$ sort < text.txt
a
b
c
d
e
f
g
```

[File System Tree]: <http://www.tldp.org/LDP/intro-linux/html/images/FS-layout.png>
[TLDP: About files and the file system]: <http://www.tldp.org/LDP/intro-linux/html/sect_03_01.html

[Paths]: <http://www.linuxnix.com/2012/07/abslute-path-vs-relative-path-in-linuxunix.html>

[Permissions]: <http://linuxcommand.org/lts0070.php>

[Redirection]: <https://en.wikipedia.org/wiki/Redirection_(computing)>

[Streams, Pipes, and Redirects]: <http://www.ibm.com/developerworks/library/l-lpic1-v3-103-4/>
