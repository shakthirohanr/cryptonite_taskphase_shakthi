# Processes and Jobs

This module is about processes and jobs.

![](https://i.imgur.com/W2XRc1y.png)

- [Processes and Jobs](#processes-and-jobs)
  - [Listing Processes](#listing-processes)
  - [Killing Processes](#killing-processes)
  - [Interupting Processes](#interupting-processes)
  - [Suspending Processes](#suspending-processes)
  - [Resuming Processes](#resuming-processes)
  - [Backgrounding Processes](#backgrounding-processes)
  - [Foregrounding Processes](#foregrounding-processes)
  - [Starting Backgrounded Processes](#starting-backgrounded-processes)
  - [Process Exit Codes](#process-exit-codes)
  - [Submission](#submission)

## Listing Processes

In this challenge, `/challenge/run` has been renamed to a random filename and we must use the process snapshot to find it and hence get our flag.

I run `ps aux` which displays:

```
hacker@processes~listing-processes:~$ ps aux
USER         PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root           1  0.1  0.0   1056   640 ?        Ss   18:40   0:00 /sbin/docker-init -- /nix/var/nix/profiles/default/bin/dojo-init /run/dojo/bin/sleep 6h
root           7  0.0  0.0   5052  2240 ?        S    18:40   0:00 /run/dojo/bin/sleep 6h
root          68  0.0  0.0   4132  2560 ?        S    18:40   0:00 /challenge/4421-run-20024
root          72  0.0  0.0   2744  1600 ?        S    18:40   0:00 sleep 6h
hacker        73  0.1  0.0   5240  3840 pts/0    Ss   18:40   0:00 /run/dojo/bin/ssh-entrypoint
hacker        90  0.0  0.0   7868  3520 pts/0    R+   18:40   0:00 ps aux
```

I run `/challenge/4421-run-20024` which gives the flag - `pwn.college{UTi7gLJp7FY1TMteT64fQeOguUa.dhzM4QDL1QjN0czW}`

## Killing Processes

In this challenge, `/challenge/run` will refuse to run while `/challenge/dont_run` is running therefore we must kill the `/challenge/dont_run` process and run `/challenge/run` to get our flag. 

I use `ps aux | grep /challenge/dont_run` which displays:

```
hacker       138  0.0  0.0   4140  2560 pts/2    S+   18:52   0:00 grep --color=auto /challenge/dont_run
```

The `pid` of the process is `138` so I use `kill 138` to kill the process.

Then I run `/challenge/run` which gives the flag - `pwn.college{UqiLoiecfrU-3VIwCOZtplqd02i.dJDN4QDL1QjN0czW}`

## Interupting Processes

In this challenge, we must "interrupt" the process `/challenge/run` to get our flag.

I run `/challenge/run` to start the process and then hotkey `Ctrl+C` to interrupt the process to get the flag - `pwn.college{Qu60g_trS9GEBUHGqc_EXl8ST5p.dNDN4QDL1QjN0czW}`

```
hacker@processes~interrupting-processes:~$ /challenge/run
I could give you the flag... but I won't, until this process exits. Remember, 
you can force me to exit with Ctrl-C. Try it now!
^C
Good job! You have used Ctrl-C to interrupt this process! Here is your flag:
pwn.college{Qu60g_trS9GEBUHGqc_EXl8ST5p.dNDN4QDL1QjN0czW}
```

## Suspending Processes

In this challenge, we must suspend the process `/challenge/run` as it requires another copy of it running in the terminal to print out the flag.

I run `/challenge/run` to start the process and then hotkey `Ctrl+Z` to suspend the process. 

Then I run `/challenge/run` again which gives me the flag - `pwn.college{cJK9Rm8iSBjZbaj9j4Q-3rcqiEF.dVDN4QDL1QjN0czW}`

## Resuming Processes 

In this challenge, we must suspend the process `/challenge/run` and resume it in order to get our flag.

I run `/challenge/run` to start the process and then hotkey `Ctrl+Z` to suspend the process. 

Then I run `fg` to resume the process which gives me the flag - `pwn.college{U2KKEiwRDBPurxzLMsXW1VhiHrO.dZDN4QDL1QjN0czW}`

## Backgrounding Processes

In this challenge, we must run a process of `/challenge/run` in the background and run another process of `/challenge/run` in order to get our flag.

I run `/challenge/run` and hotkey `Ctrl+Z` to suspend the process. Then I run `bg` to make it run in the background.

Finally I run another process of `/challenge/run` which gives me the flag - `pwn.college{QU9KvsR7TkP7-Ani-XQOCCJHtm9.ddDN4QDL1QjN0czW}`

## Foregrounding Processes

In this challenge, we must foreground a process of `/challenge/run` running in the background to get our flag.

I run `/challenge/run` and hotkey `Ctrl+Z` to suspend the process. Then I run `bg` to make it run in the background.

Finally I run `fg` to foreground the process. Following the instructions of the program gives me the flag - `pwn.college{s8Ms_KjwV2dFWkMNFEDcjY0OaIb.dhDN4QDL1QjN0czW}`

## Starting Backgrounded Processes

In this challenge, we must run `/challenge/run` backgrounded in order to get our flag.

> [!NOTE]
> We can add `&` at the end of a command to run it in the background.

I run `/challenge/run &` and get the flag - `pwn.college{UIVCgN_0hjWQENdfA62NXKXe57V.dlDN4QDL1QjN0czW}`

## Process Exit Codes

In this challenge, we must get the exit code of the process `/challenge/get-code` and pass in the exit code as an argument to `/challenge/submit-code` to get our flag.

I run `/challenge/get-code` and then run `echo $?` to get the exit code of the process. The exit code is `105`.

Lastly I run `/challenge/submit-code 105` which gives me the flag - `pwn.college{QHAhvAp8qK39NWTdHAfdQbip_db.dljN4UDL1QjN0czW}`

## Submission

![](https://i.imgur.com/So0Bodp.png)