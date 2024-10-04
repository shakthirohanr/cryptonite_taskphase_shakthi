# Digesting Documentation

This module is about understanding documentation.

![](https://i.imgur.com/tOx0pNn.png)

- [Digesting Documentation](#digesting-documentation)
  - [Learning From Documentation 📖](#learning-from-documentation-)
  - [Learning Complex Usage :ledger:](#learning-complex-usage-ledger)
  - [Reading Manuals :books:](#reading-manuals-books)
  - [Searching Manuals 🔍](#searching-manuals-)
  - [Searching For Manuals 🔍](#searching-for-manuals-)
  - [Helpful Programs 🙋‍♂️](#helpful-programs-️)
  - [Help for Builtins 🙋‍♂️](#help-for-builtins-️)
  - [Completion](#completion)

## Learning From Documentation 📖

In this challenge, we need to run the command with an argument to get our flag.

I run the command - `/challenge/challenge` with the argument `--a` - **`/challenge/challenge --a`**. 

The program gave the flag - `pwn.college{U3mIDnyMXcoNSRYFE0beEgRiIv1.dRjM5QDL1QjN0czW}`.

```
hacker@man~learning-from-documentation:~$ /challenge/challenge --giveflag
Correct argument! Here is your flag:
pwn.college{U3mIDnyMXcoNSRYFE0beEgRiIv1.dRjM5QDL1QjN0czW}
```

## Learning Complex Usage :ledger:

In this challenge, we are required to run the command with an argument that itself has an argument to get our flag.

The argument `--printfile` expects the address of the file to be read so I run the command - **`/challenge/challenge --printfile /flag`** where `--printfile` is the argument for the command and `/flag` is the argument for `--printfile`. 

```
hacker@man~learning-complex-usage:~$ /challenge/challenge --printfile /flag
Correct argument! Here is the /flag file:
pwn.college{Qdt7iSOjFe_wWYxOPhs8Fgw__70.dVjM5QDL1QjN0czW}
```

## Reading Manuals :books:

In this challenge, we are required to read the man page for `challenge` and find the secret option which will give us the flag.

I use `man challenge` to read the documentation and find that we need to pass in the argument - `--qqzozb NUM` where `NUM` needs to be 335 for the flag to be printed out. Therefore I run `/challenge/challenge --qqzozb 335` which gives me the flag - `pwn.college{YGqOIqzo-zbdCxJ3dP-bSF3G55M.dRTM4QDL1QjN0czW}`.

```
hacker@man~reading-manuals:~$ /challenge/challenge --qqzozb 335
Correct usage! Your flag: pwn.college{YGqOIqzo-zbdCxJ3dP-bSF3G55M.dRTM4QDL1QjN0czW}
```

## Searching Manuals 🔍

In this challenge, we are required to search for the argument that will give us the flag in the man page for `challenge`.

I use `man challenge` to open the documentation and search for the word flag using `/flag` and find that the argument - `--spcfjc` will give us the flag. There I run `/challenge/challenge --spcfjc` which gives me the flag - `pwn.college{guGwfHDH4eOJRQmp98lHZg8PfwY.dVTM4QDL1QjN0czW}`.

```
hacker@man~searching-manuals:~$ man challenge
hacker@man~searching-manuals:~$ /challenge/challenge --spcfjc
Initializing...
Correct usage! Your flag: pwn.college{guGwfHDH4eOJRQmp98lHZg8PfwY.dVTM4QDL1QjN0czW}
```

## Searching For Manuals 🔍

In this challenge, we are supposed to learn how to search for man pages in the man database using the documentation for man and get our flag.

I use `man man` to open the documentation and found out that `man -k STRING` can be used to search for a string in the man database so I use `man -k flag` which gives the output:
```
dpkg-buildflags (1)  - returns build flags to use during package build
Dpkg::BuildFlags (3perl) - query build flags
fegetexceptflag (3)  - floating-point rounding and exception handling
fesetexceptflag (3)  - floating-point rounding and exception handling
hmbptdjcza (1)       - print the flag!
i386 (8)             - change reported architecture in new program environment and/or set personality flags
ioctl_iflags (2)     - ioctl() operations for inode flags
linux32 (1)          - change reported architecture in new program environment and/or set personality flags
linux64 (1)          - change reported architecture in new program environment and/or set personality flags
pcap-config (1)      - write libpcap compiler and linker flags to standard output
security_compute_av_flags (3) - query the SELinux policy database in the kernel
security_compute_av_flags_raw (3) - query the SELinux policy database in the kernel
set_matchpathcon_flags (3) - set flags controlling the operation of matchpathcon or matchpathcon_index and configure the behaviour of validity checking and error displaying
set_matchpathcon_invalidcon (3) - set flags controlling the operation of matchpathcon or matchpathcon_index and configure the behaviour of validity checking and error displaying
set_matchpathcon_printf (3) - set flags controlling the operation of matchpathcon or matchpathcon_index and configure the behaviour of validity checking and error displaying
setarch (1)          - change reported architecture in new program environment and/or set personality flags
setarch (8)          - change reported architecture in new program environment and/or set personality flags
x86_64 (8)           - change reported architecture in new program environment and/or set personality flags
```
I run `man hmbptdjcza` and find:
```
       --hmbptd NUM
              print the flag if NUM is 466
```
Therefore I run `/challenge/challenge --hmbptd 466` to get the flag - `pwn.college{46_EAWW6_0LhmB2FT8AbZ41ptS4.dZTM4QDL1QjN0czW}`

```
hacker@man~searching-for-manuals:~$ /challenge/challenge --hmbptd 466
Correct usage! Your flag: pwn.college{46_EAWW6_0LhmB2FT8AbZ41ptS4.dZTM4QDL1QjN0czW}
```

## Helpful Programs 🙋‍♂️

In this challenge, we are required to read the documentation for `/challenge/challenge` using the `--help` argument and find the argument that will give us the flag.

I use `/challenge/challenge --help` and find:
```
usage: a challenge to make you ask for help [-h] [--fortune] [-v] [-g GIVE_THE_FLAG] [-p]

optional arguments:
  -h, --help            show this help message and exit
  --fortune             read your fortune
  -v, --version         get the version number
  -g GIVE_THE_FLAG, --give-the-flag GIVE_THE_FLAG
                        get the flag, if given the correct value
  -p, --print-value     print the value that will cause the -g option to give you the flag
```
We see that the `-g` argument will give us the flag but it requires a value to be passed in. We can see that `-p` argument will give us the value that will cause -g option to give us the flag. So I run `/challenge/challenge -p` to get the required value.
```
hacker@man~helpful-programs:~$ /challenge/challenge -p
The secret value is: 878
```
I run `/challenge/challenge -g 878` and get the flag - `pwn.college{w8LKtaqZ_klmOxmcdO7xML84FnN.ddjM4QDL1QjN0czW}`.
```
hacker@man~helpful-programs:~$ /challenge/challenge -g 878
Correct usage! Your flag: pwn.college{w8LKtaqZ_klmOxmcdO7xML84FnN.ddjM4QDL1QjN0czW}
```

## Help for Builtins 🙋‍♂️

In this challenge, our command `challenge` is a shell builtin. We need to use the `help` command to find out the argument that will give us the flag.

I use `help challenge` which prints:
```
challenge: challenge [--fortune] [--version] [--secret SECRET]
    This builtin command will read you the flag, given the right arguments!
    
    Options:
      --fortune         display a fortune
      --version         display the version
      --secret VALUE    prints the flag, if VALUE is correct

    You must be sure to provide the right value to --secret. That value
    is "gG95ByCX".
```
Therefore I run `challenge --secret gG95ByCX` to get the flag - `pwn.college{gG95ByCX8iW-KKsjkOTC2Gnpgg3.dRTM5QDL1QjN0czW}`.

```
hacker@man~help-for-builtins:~$ challenge --secret gG95ByCX
Correct! Here is your flag!
pwn.college{gG95ByCX8iW-KKsjkOTC2Gnpgg3.dRTM5QDL1QjN0czW}
```
## Completion 

![](https://i.imgur.com/dzcelSS.png)