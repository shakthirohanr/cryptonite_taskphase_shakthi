# Bandit 

The Bandit wargame is aimed at absolute beginners. It will teach the basics needed to be able to play other wargames.

- [Bandit](#bandit)
  - [Level 0-1](#level-0-1)
  - [Level 1-2](#level-1-2)
  - [Level 2-3](#level-2-3)
  - [Level 3-4](#level-3-4)
  - [Level 4-5](#level-4-5)
  - [Level 5-6](#level-5-6)
  - [Level 6-7](#level-6-7)
  - [Level 7-8](#level-7-8)
  - [Level 8-9](#level-8-9)
  - [Level 9-10](#level-9-10)
  - [Level 10-11](#level-10-11)

## Level 0-1

In this challenge, the password for the next level is stored in a file named `readme` in the home directory.

I run **`cat readme`** to get the password - `ZjLjTmM6FvvyRnrb2rfNWOZOTa6ip5If`

```
bandit0@bandit:~$ cat readme
The password you are looking for is: ZjLjTmM6FvvyRnrb2rfNWOZOTa6ip5If
```

## Level 1-2

In this challenge, the password for the next level is stored in a file named `-` in the home directory.

We cannot directly reference the file as its name is a special character. I use the implicit entries provided in Linux and run **`cat ./-`** to get the password - `263JGJPfgU6LtdEvgfWU1XP5yac29mFx`

```
bandit1@bandit:~$ cat ./-
263JGJPfgU6LtdEvgfWU1XP5yac29mFx
```

## Level 2-3

In this challenge, the password for the next level is stored in a file named `spaces in this filename` in the home directory. 

>  [!NOTE]
>  We can enclose a string in "" to pass it as a single argument.

I run **`cat "spaces in this filename"`** to get the flag - `MNk8KNH3Usiio41PRUEoDFPqfxLPlSmx`

```
bandit2@bandit:~$ cat "spaces in this filename"
MNk8KNH3Usiio41PRUEoDFPqfxLPlSmx
```

## Level 3-4

In this challenge, the password for the next level is stored in a hidden file in the `inhere` directory.

I cd to `inhere` and run **`ls -a`** to get the hidden file - `...Hiding-From-You`

Then I run **`cat ...Hiding-From-You`** to get the flag - `2WmrDFRmJIq3IPxneAaMGhap0pFhF3NJ`

```
bandit3@bandit:~$ cd inhere
bandit3@bandit:~/inhere$ ls -a
.  ..  ...Hiding-From-You
bandit3@bandit:~/inhere$ cat ...Hiding-From-You
2WmrDFRmJIq3IPxneAaMGhap0pFhF3NJ
```

## Level 4-5

In this challenge, the password for the next level is stored in one of the files in `inhere` directory

I cd to `inhere`, then run **`ls`** and notice that a lot of files are present. But only one of the files has human readable text which is our password. 

> [!NOTE]
> The `file` command can be used to describe the contents of a file in Linux.

I run `file ./*` to get the content of the files:
```
./-file00: data
./-file01: data
./-file02: data
./-file03: data
./-file04: data
./-file05: data
./-file06: data
./-file07: ASCII text
./-file08: data
./-file09: data
```

ASCII text is readable by humans so I run **`cat ./-file07`** to get the password - `4oQYVPkxZOOEOO5pTW81FB8j8lxXGUQw`

## Level 5-6

In this challenge, the password for the next level is stored in a file in the `inhere` directory and is:
-  human-readable
- 1033 bytes in size
- not executable

> [!NOTE]
> In the `find` comamnd in Linux:
> 
> There is a flag for readable files - `readable`
>
> There is a size command where we can specify the size of the file - `size` 

I cd to `inhere` and run `find -readable -size 1033c` where `c` stands for bytes. It returns a file address which matches the parameters - `./maybehere07/.file2` 

Then I run **`cat ./maybehere07/.file2`** to get the password - `HWasnPhtq9AVKe0dmk45nxy20cvUa6EG`

```
bandit5@bandit:~$ cd inhere
bandit5@bandit:~/inhere$ find -readable -size 1033c
./maybehere07/.file2
bandit5@bandit:~/inhere$ cat ./maybehere07/.file2
HWasnPhtq9AVKe0dmk45nxy20cvUa6EG
```

## Level 6-7

In this challenge, the password for the next level is stored in a file in the `inhere` directory and is:

- owned by user bandit7
- owned by group bandit6
- 33 bytes in size

I found out that the `find` command has arguments to filter out the owner - `user` and the group the file belongs to - `group`. 

I ran **`find / -user bandit7 -group bandit6 -size 33c`** but this produces a lot of errors as it tries to access files that it doesn't have permissions to access.

We can pipe the standard error output of the command into `/dev/null` to view the output.

> [!NOTE]
> NULL is a special device on Linux which destroys all that data that is send to it.
>

I ran `find / -user bandit7 -group bandit6 -size 33c 2> /dev/null` and get the required file - `/var/lib/dpkg/info/bandit7.password`

Finally I ran `cat /var/lib/dpkg/info/bandit7.password` to get the flag - `morbNTDkSW6jIlUc0ymOdMaLnOlFVAaj`

## Level 7-8 

In this challenge, the password for the next level is next to the word `millionth` in the `data.txt` file in the home directory.

I piped the output of cat into grep and searched for the word `millionth` 

Running **`cat data.txt | grep millionth`** returned:
```
millionth	dfwvzFQi4mU0wfNbFOe9RoWskMLg7eEc

```

The password is `dfwvzFQi4mU0wfNbFOe9RoWskMLg7eEc`

## Level 8-9

In this challenge, the password for the next level is stored in the file `data.txt` and is the only line of text that occurs only once.

I saw the commands that may be needed to use and noticed the command `uniq`. I used google to lookup the command found out that it returns unique lines in the input file.

> [!NOTE]
> `uniq` isn’t able to detect the duplicate lines unless they are adjacent to each other. The content in the file must be therefore sorted before using uniq or you can simply use sort -u instead of uniq command.  

Therefore I sort the data and pipe it into `uniq`.

I ran **`sort data.txt | uniq -u`** which gave me the password - `4CKMh1JI91bUIZZPXDqGanal4xvAg0JM`

## Level 9-10

In this challenge, the password for the next level is stored in the file `data.txt` in one of the few human-readable strings, preceded by several ‘=’ characters.

We can use the `strings` command, commonly used in CTF's to look for human readable strings in a file. Then we can pipe it into grep and search for `=`

I analysed the output of **`strings data.txt | grep =`** and got the password - `FGUW5ilLVJrxX9kMYMmlN4MgbpfMiqey`

## Level 10-11

In this challenge, the password for the next level is stored in the file `data.txt`, which contains base64 encoded data.

I read the man page of the command `base64` and found that `-d` flag is used to decode Base64 from an input stream.

I ran `base64 -d data.txt` which gave the following output:
```
The password is dtR173fZKb0RRsDFSGsg2RWnpNVj3qRr
```

There the password is indeed `dtR173fZKb0RRsDFSGsg2RWnpNVj3qRr`


