# Comprehending Commands

This module goes over some common and usefull Linux commands.

![](https://i.imgur.com/0zxdWKJ.png)

- [Comprehending Commands](#comprehending-commands)
  - [cat: not the pet, but the command! :cat:](#cat-not-the-pet-but-the-command-cat)
  - [catting absolute paths :cat2:](#catting-absolute-paths-cat2)
  - [more catting practice :smile\_cat:](#more-catting-practice-smile_cat)
  - [grepping for a needle in a haystack :sewing\_needle:](#grepping-for-a-needle-in-a-haystack-sewing_needle)
  - [listing files :page\_with\_curl:](#listing-files-page_with_curl)
  - [touching files :file\_folder:](#touching-files-file_folder)
  - [removing files :wastebasket:](#removing-files-wastebasket)
  - [hidden files 🫣](#hidden-files-)
  - [An Epic Filesystem Quest :open\_file\_folder:](#an-epic-filesystem-quest-open_file_folder)
  - [making directories 📁](#making-directories-)
  - [finding files 🔎](#finding-files-)
  - [linking files :link:](#linking-files-link)

## cat: not the pet, but the command! :cat:

This challenge requires us to read the `flag` file located in the home directory to get our flag.

We can use the `cat` command with the relative address as the argument - `cat flag`. Running the command retrieves the flag - `pwn.college{oz6pmm4Z4VQ4S-iVGf8kHjt6Ra7.dFzN1QDL1QjN0czW}`

```
hacker@commands~cat-not-the-pet-but-the-command:~$ cat flag
pwn.college{oz6pmm4Z4VQ4S-iVGf8kHjt6Ra7.dFzN1QDL1QjN0czW}
```
## catting absolute paths :cat2:

This challenge requires us to the `flag` file located in the root directory to get our flag.

We can use the `cat` command with the absolute address as the argument - `cat /flag`. Running the command retrieves the flag - `pwn.college{suJRP2awWxRm_j1jxDdWrLd6PHC.dlTM5QDL1QjN0czW}`

```
hacker@commands~catting-absolute-paths:~$ cat /flag
pwn.college{suJRP2awWxRm_j1jxDdWrLd6PHC.dlTM5QDL1QjN0czW}
```
## more catting practice :smile_cat:

When we log into ssh for the challenge it tells us that the flag is located in the `/usr/share/texmf/flag` file. 

We can use the `cat` command with the absolute address as the argument - `cat /usr/share/texmf/flag`. Running the command retrieves the flag - `pwn.college{8KoG2Xg-0mM8Jy3AAH5yEyryM1o.dBjM5QDL1QjN0czW}`

```
Connected!                                                                        
You cannot use the 'cd' command in this level, and must retrieve the flag by 
absolute path. Plus, I hid the flag in a different directory! You can find it 
in the file /usr/share/texmf/flag. Go cat it out **without** cding into that 
directory!
hacker@commands~more-catting-practice:~$ cat /usr/share/texmf/flag
pwn.college{8KoG2Xg-0mM8Jy3AAH5yEyryM1o.dBjM5QDL1QjN0czW}
```
## grepping for a needle in a haystack :sewing_needle:

In this challenge we are required to find our flag in a file containing a lot of data. The absolute path of the file is `/challenge/data.txt`.

We can use the `grep` command with the first argument as the search string and the second argument as the absolute path of the file we want to search -  `grep pwn.college /challenge/data.txt`. Running this command gives us the flag - `pwn.college{4bLRs3Ok20NZ2hFO8Faa0ZHV1JN.ddTM4QDL1QjN0czW}`

```
hacker@commands~grepping-for-a-needle-in-a-haystack:~$ grep pwn.college /challenge/data.txt
pwn.college{4bLRs3Ok20NZ2hFO8Faa0ZHV1JN.ddTM4QDL1QjN0czW}
```
## listing files :page_with_curl:

In this challenge, our file containing the file is located in the `/challenge` directory but we don't know the name of the file.

I used the `ls` command to list the files in the `/challenge` directory and it returned `5967-renamed-run-32567  DESCRIPTION.md`. I ran the `5967-renamed-run-32567` file and got the flag - `pwn.college{Eo9l2O2QgNfhzOH_b4Ras0-YUn5.dhjM4QDL1QjN0czW}`.

```
hacker@commands~listing-files:~$ ls /challenge
5967-renamed-run-32567  DESCRIPTION.md
hacker@commands~listing-files:~$ /challenge/5967-renamed-run-32567
Yahaha, you found me! Here is your flag:
pwn.college{Eo9l2O2QgNfhzOH_b4Ras0-YUn5.dhjM4QDL1QjN0czW}

```
## touching files :file_folder:

In this challenge, we are required to create two files:  `/tmp/pwn` and `/tmp/college` and run the program in order to get our flag.

I used the `touch` command to create the required files and then ran the program which returned the flag - `pwn.college{kr8TpJE5NZjSpuRR5MNY1jOeafF.dBzM4QDL1QjN0czW}`

```
hacker@commands~touching-files:~$ touch /tmp/pwn
hacker@commands~touching-files:~$ touch /tmp/college
hacker@commands~touching-files:~$ /challenge/run
Success! Here is your flag:
pwn.college{kr8TpJE5NZjSpuRR5MNY1jOeafF.dBzM4QDL1QjN0czW}
```
## removing files :wastebasket:

In this challenge, we are required to delete the `delete_me` file located in the home directory and run the program in order to get our flag.

I used the `rm` command giving the relative path as the first argument to delete the file - `rm delete_me` and then ran the program which gave me the flag - `pwn.college{waR3OyvPzct-ROEG3XyROtL618f.dZTOwUDL1QjN0czW}`.

```
hacker@commands~removing-files:~$ rm delete_me
hacker@commands~removing-files:~$ /challenge/check
Excellent removal. Here is your reward:
pwn.college{waR3OyvPzct-ROEG3XyROtL618f.dZTOwUDL1QjN0czW}
```
## hidden files 🫣

In this challenge, in order to get the flag we should print out the contents of the file hidden as a dot-prepended file in the root directory 

I changed my cwd to the root directory using the `cd` command. Then I used the `ls -a` command to list all the files and found the required file - `.flag-4474164323883`. Running `cat .flag-4474164323883` gives us the flag - `pwn.college{4nYF7V8QCRdzGO_9f93JnTu2BTP.dBTN4QDL1QjN0czW}`

```
hacker@commands~hidden-files:~$ cd /
hacker@commands~hidden-files:/$ ls -a
.  ..  .dockerenv  .flag-4474164323883  bin  boot  challenge  dev  etc  home  lib  lib32  lib64  libx32  media  mnt  nix  opt  proc  root  run  sbin  srv  sys  tmp  usr  var
hacker@commands~hidden-files:/$ cat .flag-4474164323883
pwn.college{4nYF7V8QCRdzGO_9f93JnTu2BTP.dBTN4QDL1QjN0czW}
```
## An Epic Filesystem Quest :open_file_folder:

In this challenge, we are required to find the hidden file which contains our flag. 

I change my directory to the root directory as per the clue given. Running `ls` gives the output:
```
hacker@commands~an-epic-filesystem-quest:/$ ls
MEMO  bin  boot  challenge  dev  etc  flag  home  lib  lib32  lib64  libx32  media  mnt  nix  opt  proc  root  run  sbin  srv  sys  tmp  usr  var
```
I print out the contents of the `MEMO` file using `cat`. The output is:
```
Yahaha, you found me!
The next clue is in: /opt/capstone/.git/logs/refs/remotes

The next clue is **delayed** --- it will not become readable until you enter the directory with 'cd'.
```
I cd into `/opt/capstone/.git/logs/refs/remotes` and use `ls` to list out the contents of the folder. I print out the contents of the `BLUEPRINT` file using `cat`. The output is:
```
Lucky listing!
The next clue is in: /etc/apt/trusted.gpg.d

The next clue is **delayed** --- it will not become readable until you enter the directory with 'cd'.
```
I cd into `/etc/apt/trusted.gpg.d` and use ls. I print out the contents of the `LEAD` file using `cat`. The output is:
```
Lucky listing!
The next clue is in: /usr/include/x86_64-linux-gnu/c++/9/ext
```
I cd into `/usr/include/x86_64-linux-gnu/c++/9/ext` and use ls. I print out the contents of the `ALERT` file using `cat`. The output is:
```
Yahaha, you found me!
The next clue is in: /usr/lib/python3/dist-packages/prompt_toolkit/key_binding/bindings

The next clue is **delayed** --- it will not become readable until you enter the directory with 'cd'.
```
I cd into `usr/lib/python3/dist-packages/prompt_toolkit/key_binding/bindings` and use ls. I print out the contents of `INFO` file using `cat`. The output is:
```
Lucky listing!
The next clue is in: /usr/lib/debug/.build-id/c3

Watch out! The next clue is **trapped**. You'll need to read it out without 'cd'ing into the directory; otherwise, the clue will self destruct!
```
I use `ls /usr/lib/debug/.build-id/c3` and find a file called `CUE-TRAPPED`. I print out the contents using `cat /usr/lib/debug/.build-id/c3/CUE-TRAPPED`. The output is:
```
The next clue is in: /usr/share/help/cs/gedit

Watch out! The next clue is **trapped**. You'll need to read it out without 'cd'ing into the directory; otherwise, the clue will self destruct!
```
I use `ls /usr/lib/debug/.build-id/c3` and find a file called `TRACE-TRAPPED`. I print out the contents using `cat /usr/share/help/cs/gedit/TRACE-TRAPPED`. The output is:
```
Great sleuthing!
The next clue is in: /opt/aflplusplus/nyx_mode/QEMU-Nyx/target

Watch out! The next clue is **trapped**. You'll need to read it out without 'cd'ing into the directory; otherwise, the clue will self destruct!
```
I use `ls /opt/aflplusplus/nyx_mode/QEMU-Nyx/target` and find a file called `POINTER-TRAPPED`. I print out the contents using `cat /opt/aflplusplus/nyx_mode/QEMU-Nyx/target/POINTER-TRAPPED`. The output is:
```
Yahaha, you found me!
The next clue is in: /opt/linux/linux-5.4/tools/perf/pmu-events/arch/x86/westmereep-dp

The next clue is **hidden** --- its filename starts with a '.' character. You'll need to look for it using special options to 'ls'.
```
I use `ls -a /opt/linux/linux-5.4/tools/perf/pmu-events/arch/x86/westmereep-dp` since it is a hidden file. I find a file called `.SNIPPET`. I print out the contents using `/opt/linux/linux-5.4/tools/perf/pmu-events/arch/x86/westmereep-dp/.SNIPPET`. The output is:
```
CONGRATULATIONS! Your perserverence has paid off, and you have found the flag!
It is: pwn.college{Qr1C5jotUwZsVHzwa98mPrGwPT2.dljM4QDL1QjN0czW}
```
I finally found the flag - `pwn.college{Qr1C5jotUwZsVHzwa98mPrGwPT2.dljM4QDL1QjN0czW}`

## making directories 📁

In this challenge we are required to create `/tmp/pwn` directory and make a college file in it and then run `/challenge/run` to get our flag.

I use the `mkdir` command to create the directory - **`mkdir /tmp/pwn`** 

Then I use the `touch` command to create a file named `college` in the same directory - **`touch /tmp/pwn/college`**

Finally I run `/challenge/run` and get the flag - `pwn.college{8Qh2li9I6MPQTWTdOeDsryHsMJR.dFzM4QDL1QjN0czW}`

```
hacker@commands~making-directories:~$ mkdir /tmp/pwn
hacker@commands~making-directories:~$ touch /tmp/pwn/college
hacker@commands~making-directories:~$ /challenge/run
Success! Here is your flag:
pwn.college{8Qh2li9I6MPQTWTdOeDsryHsMJR.dFzM4QDL1QjN0czW}
```
## finding files 🔎

In this challenge, the file containing our flag is hidden somewhere in the root directory. The name of the file is `flag`.

I used the find command passing in the root directory as the address and `flag` as the name - **`find / -name flag`**. The output is: 
```
hacker@commands~finding-files:~$ find / -name flag
find: ‘/root’: Permission denied
find: ‘/proc/1/task/1/fd’: Permission denied
find: ‘/proc/1/task/1/fdinfo’: Permission denied
find: ‘/proc/1/task/1/ns’: Permission denied
find: ‘/proc/1/fd’: Permission denied
find: ‘/proc/1/map_files’: Permission denied
find: ‘/proc/1/fdinfo’: Permission denied
find: ‘/proc/1/ns’: Permission denied
find: ‘/proc/7/task/7/fd’: Permission denied
find: ‘/proc/7/task/7/fdinfo’: Permission denied
find: ‘/proc/7/task/7/ns’: Permission denied
find: ‘/proc/7/fd’: Permission denied
find: ‘/proc/7/map_files’: Permission denied
find: ‘/proc/7/fdinfo’: Permission denied
find: ‘/proc/7/ns’: Permission denied
find: ‘/var/log/private’: Permission denied
find: ‘/var/log/apache2’: Permission denied
find: ‘/var/log/mysql’: Permission denied
find: ‘/var/cache/ldconfig’: Permission denied
find: ‘/var/cache/apt/archives/partial’: Permission denied
find: ‘/var/cache/private’: Permission denied
find: ‘/var/lib/apt/lists/partial’: Permission denied
find: ‘/var/lib/php/sessions’: Permission denied
find: ‘/var/lib/mysql-files’: Permission denied
find: ‘/var/lib/private’: Permission denied
find: ‘/var/lib/mysql-keyring’: Permission denied
find: ‘/var/lib/mysql’: Permission denied
find: ‘/tmp/tmp.XvrUsDZh8M’: Permission denied
find: ‘/run/mysqld’: Permission denied
find: ‘/run/sudo’: Permission denied
find: ‘/etc/ssl/private’: Permission denied
/usr/local/lib/python3.8/dist-packages/pwnlib/flag
/usr/local/share/radare2/5.9.5/flag
/opt/linux/linux-5.4/include/config/need/dma/flag
/opt/pwndbg/.venv/lib/python3.8/site-packages/pwnlib/flag
/opt/radare2/libr/flag
/nix/store/pmvk2bk4p550w182rjfm529kfqddnvh3-python3.11-pwntools-4.12.0/lib/python3.11/site-packages/pwnlib/flag
/nix/store/1yagn5s8sf7kcs2hkccgf8d0wxlrv5sz-radare2-5.9.0/share/radare2/5.9.0/flag
```
I try to print out the contents of all the files using `cat` and find the flag in `/opt/linux/linux-5.4/include/config/need/dma/flag`. 

## linking files :link: 

In this challenge our flag is located in `/flag`. We need to run `/challenge/catflag` to print out the flag. 

I link `/home/hacker/not-the-flag` to `/flag` and then run `/challenge/catflag` to get the flag - `pwn.college{MBqLJfgNl4p72VhQLXpgbECUYdr.dlTM1UDL1QjN0czW}`.
