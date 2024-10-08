# Pondering Paths

This module familiarizes us with the Linux file system.

![](https://i.imgur.com/AFklwkH.png)

- [Pondering Paths](#pondering-paths)
  - [The Root](#the-root)
  - [Program and absolute paths](#program-and-absolute-paths)
  - [Position thy self](#position-thy-self)
  - [Position elsewhere](#position-elsewhere)
  - [Position yet elsewhere](#position-yet-elsewhere)
  - [implicit relative paths, from /](#implicit-relative-paths-from-)
  - [explicit relative paths, from /](#explicit-relative-paths-from-)
  - [implicit relative path](#implicit-relative-path)
  - [home sweet home](#home-sweet-home)
  - [Completion](#completion)

## The Root

In Linux the filesystem starts at `/`. In this challenge we must run the file `pwn` to retrieve our flag but the file `pwn` is located in the root level and not in our current directory.

So we should run the file using its absolute path - `/pwn`. Running the file gives us the flag - `pwn.college{YhMNpErKX_rpDe-CXqn179gHRZr.dhzN5QDL1QjN0czW}`.
```
hacker@paths~the-root:~$ /pwn
BOOM!!!
Here is your flag:
pwn.college{YhMNpErKX_rpDe-CXqn179gHRZr.dhzN5QDL1QjN0czW}
```
## Program and absolute paths

In this challenge, the program `run` that will give us the flag is located in the `challenge` directory which in turn is located in the root directory. 

We should run the program using its absolute path which is `/challenge/run`. When we run the program it returns the flag - `pwn.college{wgHLYUJ57xURm9CUV7ioGPr90j2.dVDN1QDL1QjN0czW}`
```
hacker@paths~program-and-absolute-paths:~$ /challenge/run
Correct!!!
/challenge/run is an absolute path! Here is your flag:
pwn.college{wgHLYUJ57xURm9CUV7ioGPr90j2.dVDN1QDL1QjN0czW}

```
## Position thy self

I ran the command `/challenge/run` but it told me that I am not in the correct directory. It told me that the challenge directory is located in `/var/log`.

So I used `cd /var/log` to change my current directory to the `/var/log` directory and then ran the initial command which returned the flag - `pwn.college{wuSfjA7V88uhpqmgv6TiTRP0AQ5.dZDN1QDL1QjN0czW}`
```
hacker@paths~position-thy-self:~$ /challenge/run
Incorrect...
You are not currently in the /var/log directory.
Please use the `cd` utility to change directory appropriately.
hacker@paths~position-thy-self:~$ cd /var/log 
hacker@paths~position-thy-self:/var/log$ /challenge/run
Correct!!!
/challenge/run is an absolute path, invoked from the right directory!
Here is your flag:
pwn.college{wuSfjA7V88uhpqmgv6TiTRP0AQ5.dZDN1QDL1QjN0czW}

```
## Position elsewhere

This challenge is very similar to the previous challenge. The challenge directory is located in `/var/lib/apt/lists`.

I used `cd /var/lib/apt/lists` to go into that directory and then ran the initial command which returned the flag - `pwn.college{wchQJlLYM3HPiiG2NSu1Vt31yyO.ddDN1QDL1QjN0czW}`.
```
hacker@paths~position-elsewhere:~$ /challenge/run
Incorrect...
You are not currently in the /var/lib/apt/lists directory.
Please use the `cd` utility to change directory appropriately.
hacker@paths~position-elsewhere:~$ cd /var/lib/apt/lists
hacker@paths~position-elsewhere:/var/lib/apt/lists$ /challenge/run
Correct!!!
/challenge/run is an absolute path, invoked from the right directory!
Here is your flag:
pwn.college{wchQJlLYM3HPiiG2NSu1Vt31yyO.ddDN1QDL1QjN0czW}
```
## Position yet elsewhere

This challenge is similar to the previous two challenges. The challenge directory is located in `/var/log`.

I used `cd /var/log` to go into the `/var/log` directory and then ran the initial command which returned the flag - `pwn.college{ErPTRM5yWEadtJsfaZE-1I3Fx-W.dhDN1QDL1QjN0czW}`.
```
hacker@paths~position-yet-elsewhere:~$ /challenge/run
Incorrect...
You are not currently in the /var/log directory.
Please use the `cd` utility to change directory appropriately.
hacker@paths~position-yet-elsewhere:~$ cd /var/log
hacker@paths~position-yet-elsewhere:/var/log$ /challenge/run
Correct!!!
/challenge/run is an absolute path, invoked from the right directory!
Here is your flag:
pwn.college{ErPTRM5yWEadtJsfaZE-1I3Fx-W.dhDN1QDL1QjN0czW}
```
## implicit relative paths, from /

In this challenge they ask us to change our current working directory to the root directory and then run the program using its relative path. 

We can change our cwd to the root directory by using `cd /` and then we can run the program using its relative path - `challenge/run`. Running the program using its relative path gives us the flag - `pwn.college{o2gzdkiBtBdfHBcw6Jzq4It-wGn.dlDN1QDL1QjN0czW}`.
```
hacker@paths~implicit-relative-paths-from-:~$ cd /
hacker@paths~implicit-relative-paths-from-:/$ challenge/run
Correct!!!
challenge/run is a relative path, invoked from the right directory!
Here is your flag:
pwn.college{o2gzdkiBtBdfHBcw6Jzq4It-wGn.dlDN1QDL1QjN0czW}
```
## explicit relative paths, from /

In this challenge they ask us to run the program using its relative path and implicit entries that can be referenced in Linux. The program's absolute path is `/challenge/run`

So we change our cwd to the root directory by using `cd /`. Then when we run `challenge/run`, it tells us that the relative path should start with `.` so we can run the command `./challenge/run` to access our program. 

**Note:**
The command `./challenge/run` is the same as `/challenge/run`. The `.` refers to the current directory in Linux.

Running the program gives us the flag - `pwn.college{ApsSZJ0--pKmpLQqJhZGMOx-JAz.dBTN1QDL1QjN0czW}`.
```
hacker@paths~explicit-relative-paths-from-:~$ cd /
hacker@paths~explicit-relative-paths-from-:/$ challenge/run
Incorrect...
This challenge must be called with a relative path that explicitly starts with a `.`!
hacker@paths~explicit-relative-paths-from-:/$ ./challenge/run
Correct!!!
./challenge/run is a relative path, invoked from the right directory!
Here is your flag:
pwn.college{ApsSZJ0--pKmpLQqJhZGMOx-JAz.dBTN1QDL1QjN0czW}
```
## implicit relative path

In this challenge they ask us to run the program from the `/challenge` directory. But Linux explicitly avoids automatically looking in the current directory when you provide a "naked" path due to security reasons.

We change our cwd to `/challenge` using the required command. Then when we run the program `run`, we get an error. We can overcome this error by explicitly calling the program using `./run`. Running the program gives us the flag - `pwn.college{g8_P6Oc7_3vlP1QhlYS0AvdhFmu.dFTN1QDL1QjN0czW}`.
```
hacker@paths~implicit-relative-path:~$ cd /challenge
hacker@paths~implicit-relative-path:/challenge$ run
ssh-entrypoint: run: command not found
hacker@paths~implicit-relative-path:/challenge$ ./run
Correct!!!
./run is a relative path, invoked from the right directory!
Here is your flag:
pwn.college{g8_P6Oc7_3vlP1QhlYS0AvdhFmu.dFTN1QDL1QjN0czW}
```
## home sweet home
In this challenge they ask to run the program providing it an argument which is the path of a file in the home directory. 

The challenge constraints us to limit the length of the path to only 3 characters. The short hand operator `~` corresponds to the absolute path of the home directory so we can use `/challenge/run ~/f` where `~/f` is the absolute path of the file the program will copy our flag to.

Running the command gives us the flag - `pwn.college{U3I08I3eD1WlLacWdAtrxJY1xO2.dNzM4QDL1QjN0czW}`.
```
hacker@paths~home-sweet-home:~$ /challenge/run ~/f
Writing the file to /home/hacker/f!
... and reading it back to you:
pwn.college{U3I08I3eD1WlLacWdAtrxJY1xO2.dNzM4QDL1QjN0czW}
```

## Completion
![](https://i.imgur.com/rmvmv3Q.png)