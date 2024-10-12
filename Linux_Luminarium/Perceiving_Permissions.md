# Perceiving Permissions

This module is about perceiving permissions in Linux.

![](https://i.imgur.com/xZUb8Y2.png)

- [Perceiving Permissions](#perceiving-permissions)
  - [Changing File Ownership](#changing-file-ownership)
  - [Groups and files](#groups-and-files)
  - [Fun With Group Names](#fun-with-group-names)
  - [Changing Permissions](#changing-permissions)
  - [Executable Files](#executable-files)
  - [Permission Tweaking Practice](#permission-tweaking-practice)
  - [Permisson Setting Practice](#permisson-setting-practice)
  - [The SUID Bit](#the-suid-bit)
  - [Completion](#completion)
 
## Changing File Ownership

In this challenge, we have to change the owner of the `/flag` file as the `hacker` user in order to access the flag and hence get it. 

> [!NOTE]
> The `chown` command can typically only be used by the `root` user.

I run `chown hacker /flag` to change the owner of `/flag` as `hacker`. 

Then I run `cat /flag` to print out the flag as I can access it now.

```
hacker@permissions~changing-file-ownership:~$ chown hacker /flag
hacker@permissions~changing-file-ownership:~$ cat /flag
pwn.college{gB0kF2k5OHe9umd3HPjpPjSQlo1.dFTM2QDL1QjN0czW}
```

## Groups and files

In this challenge, the `/flag` file is owned by `root` user and only members of the `root` group can access it. We need to change the group owner to `hacker` in order to access it.

> [!NOTE]
> The `chgroup` command can be used to change group ownership. It can typically only be used by the `root` user.

I run `chgrp hacker /flag` to change the group ownership. 

Then I run `cat /flag` to print the flag - `pwn.college{c2sZOpza2eLQnUKvhunzKDWrmZE.dFzNyUDL1QjN0czW}`

```
hacker@permissions~groups-and-files:~$ chgrp hacker /flag
hacker@permissions~groups-and-files:~$ cat /flag
pwn.college{c2sZOpza2eLQnUKvhunzKDWrmZE.dFzNyUDL1QjN0czW}
```

## Fun With Group Names

In this challenge, we need to change the group owner of the file `/flag` to the group which our user `hacker` belongs to, in order to get our flag

I use the `id` command to find out which group `hacker` belongs to. 
```
hacker@permissions~fun-with-groups-names:~$ id
uid=1000(hacker) gid=1000(grp18739) groups=1000(grp18739)
```
The group `hacker` belongs to is `grp18739` so I run `chgrp grp18739 /flag` to change the group ownership.

Finally I run `cat /flag` to get the flag - `pwn.college{8_H1TB-VSwdHdIMIS1HYHUdNOGV.dJzNyUDL1QjN0czW}`

```
hacker@permissions~fun-with-groups-names:~$ id
uid=1000(hacker) gid=1000(grp18739) groups=1000(grp18739)
hacker@permissions~fun-with-groups-names:~$ chgrp grp18739 /flag
hacker@permissions~fun-with-groups-names:~$ cat /flag
pwn.college{8_H1TB-VSwdHdIMIS1HYHUdNOGV.dJzNyUDL1QjN0czW}
```

## Changing Permissions


In this challenge, we need to modify the permissions of the file `/flag` in order to get our flag.

> [!NOTE]
> `chmod` allows you to tweak permissions with the mode format of `WHO+/-WHAT`, where `WHO` is user/group/other and `WHAT` is read/write/execute.

I run `chmod o+r /flag` to allow all the users to read the file. 

Then I run `cat /flag` to print out the flag - `pwn.college{swFLvm287Zhid46TGr4I9fhGEiP.dNzNyUDL1QjN0czW}`

```
hacker@permissions~changing-permissions:~$ chmod o+r /flag
hacker@permissions~changing-permissions:~$ cat /flag
pwn.college{swFLvm287Zhid46TGr4I9fhGEiP.dNzNyUDL1QjN0czW}
```

## Executable Files

In this challenge, we need to modify the permissions of the file `/flag` in order to get our flag.

The file is owned by `hacker` but the owner doesn't have execution permissions so we can run `chmod u+x /challenge/run` to give the owner permission to run the file.

Then I run `/challenge/run` which gives me the flag - `pwn.college{I-UwcTPt6cegfkAWQpSqY9VHVjF.dJTM2QDL1QjN0czW}`

```
hacker@permissions~executable-files:~$ chmod u+x /challenge/run
hacker@permissions~executable-files:~$ /challenge/run
Successful execution! Here is your flag:
pwn.college{I-UwcTPt6cegfkAWQpSqY9VHVjF.dJTM2QDL1QjN0czW}
```

## Permission Tweaking Practice

We need to change the permissions of the /challenge/pwn file in specific ways a few times in a row in order to get our flag.

**Round 0:**
```
Current permissions of "/challenge/pwn": rw-r--r--
Needed permissions of "/challenge/pwn": rw-rw-r--
```
I run `chmod g+w /challenge/pwn` to set the required permissions

**Round 1:**
```
Current permissions of "/challenge/pwn": rw-rw-r--
Needed permissions of "/challenge/pwn": ------r--
```
I run `chmod ug-rw /challenge/pwn` to set the required permissions

**Round 2:**
```
Current permissions of "/challenge/pwn": ------r--
Needed permissions of "/challenge/pwn": ------rw-
```
I run `chmod o+w /challenge/pwn` to set the required permissions

**Round 3:**
```
Current permissions of "/challenge/pwn": ------rw-
Needed permissions of "/challenge/pwn": ---------
```
I run `chmod o-rw /challenge/pwn` to set the required permissions

**Round 4:**
```
Current permissions of "/challenge/pwn": ---------
Needed permissions of "/challenge/pwn": rwxrwxrwx
```
I run `chmod ugo+rwx /challenge/pwn` to set the required permissions

**Round 5:**
```
Current permissions of "/challenge/pwn": rwxrwxrwx
Needed permissions of "/challenge/pwn": -w--w-rwx
```
I run `chmod u-rx,g-rx /challenge/pwn` to set the required permissions

**Round 6:**
```
Current permissions of "/challenge/pwn": -w--w-rwx
Needed permissions of "/challenge/pwn": -w-rw-rwx
```
I run `chmod g+r /challenge/pwn` to set the required permissions

**Round 7:**
```
Current permissions of "/challenge/pwn":  -w-rw-rwx
Needed permissions of "/challenge/pwn":  -wxrwxrwx
```
I run `chmod u+x,g+x /challenge/pwn` to set the required permissions

Finally I run `chmod u+r /flag` to make the flag readable and run `cat /flag` to get the flag - `pwn.college{85J77gKN0PNeUI6i5_FMRmYRZ_k.dBTM2QDL1QjN0czW}` 

## Permisson Setting Practice

We need to change the permissions of the /challenge/pwn file in specific ways a few times in a row in order to get our flag.

**Round 0:**
```
Current permissions of "/challenge/pwn": rw-r--r--
Needed permissions of "/challenge/pwn": r-xr--rw-
```
I run `chmod u=rx,o=rw /challenge/pwn` to set the required permissions

**Round 1:**
```
Current permissions of "/challenge/pwn": r-xr--rw-
Needed permissions of "/challenge/pwn": rw---xrwx
```
I run `chmod u=rw,g=x,o=rwx /challenge/pwn` to set the required permissions

**Round 2:**
```
Current permissions of "/challenge/pwn": rw---xrwx
Needed permissions of "/challenge/pwn": r-x-wxr-x
```
I run `chmod u=rx,g=wx,o=rx /challenge/pwn` to set the required permissions

**Round 3:**
```
Current permissions of "/challenge/pwn": r-x-wxr-x
Needed permissions of "/challenge/pwn": rw----r--
```
I run `chmod u=rw,g=-,o=r /challenge/pwn` to set the required permissions

**Round 4:**
```
Current permissions of "/challenge/pwn": rw----r--
Needed permissions of "/challenge/pwn": r-xrw---x
```
I run `chmod u=rx,g=rw,o=x /challenge/pwn` to set the required permissions

**Round 5:**
```
Current permissions of "/challenge/pwn": r-xrw---x
Needed permissions of "/challenge/pwn": r------wx
```
I run `chmod u=r,g=-,o=wx /challenge/pwn` to set the required permissions

**Round 6:**
```
Current permissions of "/challenge/pwn": r------wx
Needed permissions of "/challenge/pwn": ----wxr-x
```
I run `chmod u=-,g=wx,o=rx /challenge/pwn` to set the required permissions

**Round 7:**
```
Current permissions of "/challenge/pwn": ----wxr-x
Needed permissions of "/challenge/pwn": r--rw-rw-
```
I run `chmod u=r,g=rw,o=rw /challenge/pwn` to set the required permissions

Finally I run `chmod u+r /flag` to make the flag readable and run `cat /flag` to get the flag - `pwn.college{kZhe2ejVyOMg_tTNt2KeSt9gq9h.dNTM5QDL1QjN0czW}` 

## The SUID Bit

In this challenge, we need to add the SUID bit to `/challenge/getroot` in order to spawn a root shell where we can `cat` out the file.

I run `chmod u+s /challenge/getroot` to add the SUID bit. Then I run `/challenge/getroot` to spawn the root shell.

Finally I run `cat /flag` to get the flag - `pwn.college{oticOUFpRwMUdn9cti6V2Lkbntk.dNTM2QDL1QjN0czW}`

```
hacker@permissions~the-suid-bit:~$ chmod u+s /challenge/getroot
hacker@permissions~the-suid-bit:~$ /challenge/getroot
SUCCESS! You have set the suid bit on this program, and it is running as root! 
Here is your shell...
root@permissions~the-suid-bit:~# cat /flag
pwn.college{oticOUFpRwMUdn9cti6V2Lkbntk.dNTM2QDL1QjN0czW}
```

## Completion

![](https://i.imgur.com/vmMhrAz.png)