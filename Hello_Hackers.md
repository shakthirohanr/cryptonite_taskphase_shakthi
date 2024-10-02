# Hello Hackers

This module was on executing commands in Linux.

![](https://i.imgur.com/KC9GHzf.png)

- [Hello Hackers](#hello-hackers)
  - [Intro to Commands](#intro-to-commands)
  - [Intro to Arguments](#intro-to-arguments)
  - [Completion](#completion)

## Intro to Commands
 In the given example, we invoked the `whoami` command which printed out the username.
 
 I invoked the `hello` command and retrieved the flag `pwn.college{cWOW6YQPJqpJPsXccfcGbQGlsje.ddjNyUDL1QjN0czW}`.

```
hacker@hello~intro-to-commands:~$ whoami
hacker
hacker@hello~intro-to-commands:~$ hello
Success! Here is your flag:
pwn.college{cWOW6YQPJqpJPsXccfcGbQGlsje.ddjNyUDL1QjN0czW}
```
## Intro to Arguments

In the given example, we ran `echo Hello` and the command printed `Hello`. The echo command is used to print out the argument provided to it. Here the command is `echo` and `Hello` is the argument.

As per the instructions I ran the `hello` command with the argument `hackers` which printed out the the flag `pwn.college{4eejKYlHLpaORzCqCDsQ5yO5g_D.dhjNyUDL1QjN0czW}`

```
hacker@hello~intro-to-arguments:~$ echo Hello
Hello
hacker@hello~intro-to-arguments:~$ hello hackers
Success! Here is your flag:
pwn.college{4eejKYlHLpaORzCqCDsQ5yO5g_D.dhjNyUDL1QjN0czW}
```

## Completion
![](https://i.imgur.com/p4dCEUp.png)