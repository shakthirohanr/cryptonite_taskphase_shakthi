# Untangling Users

This module is about users in Linux.

![](https://i.imgur.com/SasIjuN.png)

- [Untangling Users](#untangling-users)
  - [Becoming root with su](#becoming-root-with-su)
  - [Other users with su](#other-users-with-su)
  - [Cracking passwords](#cracking-passwords)
  - [Using su](#using-su)
  - [Completion](#completion)

## Becoming root with su 

In this challenge, we have to start a root shell in order to get our flag.

I run **`su`** and provide the password `hack-the-planet` to start the root shell.

Then I run **`cat /flag`** in the root shell to get the flag - `pwn.college{E5Rtjp41YCCH4m4TSkw3ihPBArH.dVTN0UDL1QjN0czW}`

```
hacker@users~becoming-root-with-su:~$ su
Password: 
root@users~becoming-root-with-su:/home/hacker# cat /flag
pwn.college{E5Rtjp41YCCH4m4TSkw3ihPBArH.dVTN0UDL1QjN0czW}
```

## Other users with su

In this challenge, we have to switch the user to `zardus` and run `/challenge/run` to get our flag.

I run **`su zardus`** and provie the password - `dont-hack-me` to switch to the user to `zardus` 

Then I run **`/challenge/run`** to get the flag - `pwn.college{IKE4pDZ521SBuNEelxDgFTmBEpy.dZTN0UDL1QjN0czW}`

```
hacker@users~other-users-with-su:~$ su zardus
Password: 
zardus@users~other-users-with-su:/home/hacker$ /challenge/run
Congratulations, you have become Zardus! Here is your flag:
pwn.college{IKE4pDZ521SBuNEelxDgFTmBEpy.dZTN0UDL1QjN0czW}
```

## Cracking passwords

In this challenge, we have to crack the password for the `zardus` user in the `/challenge/shadow-leak` file and login to the `zardus` user.

> [!NOTE]
> We can use the popular [John The Ripper](https://www.openwall.com/john/) to crack the leaked shadow file and get the password.

I run **`john /challenge/shadow-leak`** and get the password: 

```
zardus@users~cracking-passwords:/home/hacker$ john /challenge/shadow-leak
Created directory: /home/zardus/.john
Loaded 1 password hash (crypt, generic crypt(3) [?/64])
Press 'q' or Ctrl-C to abort, almost any other key for status
aardvark         (zardus)
1g 0:00:00:20 100% 2/3 0.04835g/s 281.5p/s 281.5c/s 281.5C/s Johnson..buzz
Use the "--show" option to display all of the cracked passwords reliably
Session completed
```

Then I switch my user to `zardus` using the password `aardvark`. Finally I run `/challenge/run` to get the flag - `pwn.college{wxstv1_Mmj8tLd_JHuQ8RD8QJoq.ddTN0UDL1QjN0czW}`

```
hacker@users~cracking-passwords:~$ su zardus
Password: 
zardus@users~cracking-passwords:/home/hacker$ /challenge/run
Congratulations, you have become Zardus! Here is your flag:
pwn.college{wxstv1_Mmj8tLd_JHuQ8RD8QJoq.ddTN0UDL1QjN0czW}
```

## Using su

In this challenge, we are supposed to use `sudo` to read the flag. 

I run `sudo cat /flag` to get the flag - `pwn.college{MZ3irWaFJjAuz_b3I0G3_jvum7M.dhTN0UDL1QjN0czW}`

```
hacker@users~using-sudo:~$ sudo cat /flag
pwn.college{MZ3irWaFJjAuz_b3I0G3_jvum7M.dhTN0UDL1QjN0czW}
```

## Completion

![](https://i.imgur.com/jongpiZ.png)