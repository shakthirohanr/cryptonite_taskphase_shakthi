# File Globbing 

This module is about file globbing.

![](https://i.imgur.com/zXPSJY8.png)

- [File Globbing](#file-globbing)
  - [Matching with \*](#matching-with-)
  - [Matching with ?](#matching-with--1)
  - [Matching with \[\]](#matching-with--2)
  - [Matching paths with \[\]](#matching-paths-with-)
  - [Missing globs](#missing-globs)
  - [Exclusionary globbing](#exclusionary-globbing)
  - [Completion](#completion)

## Matching with * 
 
In this challenge, we are supposed to change our cwd to `/challenge` and execute the `run` file to get our flag. But we can only pass in 4 characters to the cd command.

I run the command `cd /ch*` to change my cwd to `/challenge` and then I execute `./run` to get the flag - `pwn.college{0bU5BCEylyhCTMDd4tS41I4A3I-.dFjM4QDL1QjN0czW}`

```
hacker@globbing~matching-with-:~$ cd /ch*
hacker@globbing~matching-with-:/challenge$ ./run
You ran me with the working directory of /challenge! Here is your flag:
pwn.college{0bU5BCEylyhCTMDd4tS41I4A3I-.dFjM4QDL1QjN0czW}
```

## Matching with ? 

In this challenge, we are suppposed to change our cwd to `/challenge` and execute the `run` file to get our flag. But we need to use the `?` character instead of c and l in the argument to cd.

I run the command `cd /?ha??enge` to change my cwd to `/challenge` and execute the `./run` file to get the flag - `pwn.college{ERxxy2RjZA1P5_4oH5id6No6WcO.dJjM4QDL1QjN0czW}`

```
hacker@globbing~matching-with-:~$ cd /?ha??enge
hacker@globbing~matching-with-:/challenge$ ./run
You ran me with the working directory of /challenge! Here is your flag:
pwn.college{ERxxy2RjZA1P5_4oH5id6No6WcO.dJjM4QDL1QjN0czW}
```

## Matching with []

In this challenge, we are supposed to change our cwd to `/challenge/files` and execute the `run` file with a single argument that bracket-globs into file_b, file_a, file_s, and file_h.

I run `cd /challenge/files` to change my cwd to `/challenge/files`. 

We can use `[]` globbing to include `file_a, file_b, file_s, file_h` so I run `/challenge/run file_[bash]` to get the flag -  `pwn.college{0n_31O6oQk9lFPZ3JpelYEs_Ha8.dNjM4QDL1QjN0czW}`

```
hacker@globbing~matching-with-:~$ cd /challenge/files
hacker@globbing~matching-with-:/challenge/files$ /challenge/run file_[bash]
You got it! Here is your flag!
pwn.college{0n_31O6oQk9lFPZ3JpelYEs_Ha8.dNjM4QDL1QjN0czW}
```

## Matching paths with []

Like the previous challenge, we are supposed to execute `/challenge/run` with a single argument that bracket-globs into the absolute paths to the file_b, file_a, file_s, and file_h files but from our home directory.

I run `/challenge/run /challenge/files/file_[bash]` to get the flag - `pwn.college{gg7X5E-7h8rWec6CltvctY3UbHn.dRjM4QDL1QjN0czW}`

```
hacker@globbing~matching-paths-with-:~$ /challenge/run /challenge/files/file_[bash]
You got it! Here is your flag!
pwn.college{gg7X5E-7h8rWec6CltvctY3UbHn.dRjM4QDL1QjN0czW}
```

## Missing globs

In this challenge, we are supposed to change our cwd to `/challenge/files` and execute the `/challenge/run` file with a single argument that bracket-globs into "challenging", "educational", and "pwning" files.

I run `cd /challenge/files` to change my cwd to `/challenge/files`. 

The argument has to less than or equal to 6 characters so I run `/challenge/run [cep]*` to the flag - `pwn.college{MBWnMYtsF3jUBvc_IQPp0MBgKMV.dVjM4QDL1QjN0czW}`

```
hacker@globbing~mixing-globs:~$ cd /challenge/files
hacker@globbing~mixing-globs:/challenge/files$ /challenge/run [cep]*
You got it! Here is your flag!
pwn.college{MBWnMYtsF3jUBvc_IQPp0MBgKMV.dVjM4QDL1QjN0czW}
```

## Exclusionary globbing

In this challenge, we are supposed to change our cwd to `/challenge/files` and execute the `/challenge/run` file with a single argument that bracket-globs into every file that **does not start** with p,w and n.

I run `cd /challenge/files` to change my cwd to `/challenge/files`. 

We can use `!` to invert the glob so that it ignores the files that start with p,w and n. Therefore I run `/challenge/run [!pwn]*` to get the flag - `pwn.college{owvnUNKbBo-C6Qs3gZFcgblO-ys.dZjM4QDL1QjN0czW}`

```
hacker@globbing~exclusionary-globbing:~$ cd /challenge/files
hacker@globbing~exclusionary-globbing:/challenge/files$ /challenge/run [!pwn]*
You got it! Here is your flag!
```

## Completion 

![](https://i.imgur.com/qfGMsE7.png)