# Chaining Commands

This module is about chaining commands in Linux.

![](https://i.imgur.com/4eFTe2Z.png)

- [Chaining Commands](#chaining-commands)
  - [Chaining with Semicolons](#chaining-with-semicolons)
  - [Your First Shell Script](#your-first-shell-script)
  - [Redirecting Script Output](#redirecting-script-output)
  - [Executable Shell Scripts](#executable-shell-scripts)
  - [Completion](#completion)

## Chaining with Semicolons

In this challenge, we should chain the commands `/challenge/pwn` and `/challenge/college` in order to get the flag.

> [!NOTE]
> We can use `;` to chain commands in Linux.

I run **`/challenge/pwn; /challenge/college`** to get the flag - `pwn.college{YldWmvjDN6xJlOKkgR__2MeDGei.dVTN4QDL1QjN0czW}`

```
hacker@chaining~chaining-with-semicolons:~$ /challenge/pwn; /challenge/college
Yes! You chained /challenge/pwn and /challenge/college! Here is your flag:
pwn.college{YldWmvjDN6xJlOKkgR__2MeDGei.dVTN4QDL1QjN0czW}
```

## Your First Shell Script

In this challenge, we should add our commands to a bash file called `x.sh` and run it in order to get our flag.

I use the popular command line text editor [nano](https://www.nano-editor.org/) to edit `x.sh` 

![](https://i.imgur.com/92AZ4A3.png)

Finally I run `bash x.sh` to run the file and get the flag - `pwn.college{IbBGoV1i4FLThRdWwwC2helY0Rs.dFzN4QDL1QjN0czW}`

## Redirecting Script Output

Similar to the previous challenge, we need to create a bash file and pipe the output of the script into `/challenge/solve`

I create a bash file called `x.sh` like the previous challenge using [nano](https://www.nano-editor.org/).

I run **`bash x.sh | /challenge/solve`** to pipe the output of the script into `/challenge/solve` and get the flag - `pwn.college{8j02sMO4U2wv7ngLjMWa6OP3OCe.dhTM5QDL1QjN0czW}`

```
hacker@chaining~redirecting-script-output:~$ bash x.sh | /challenge/solve
Correct! Here is your flag:
pwn.college{8j02sMO4U2wv7ngLjMWa6OP3OCe.dhTM5QDL1QjN0czW}
```

## Executable Shell Scripts

In this challenge, we are supposed to create a bash script that calls `/challenge/solve` and run it without explicitly invoking bash.

> [!NOTE]
> We can directly run a bash file without using the `bash` command by making the file executable

I create a bash file called `x.sh` like the previous challenge using [nano](https://www.nano-editor.org/).

Using the knowledge I gained in the previous challenges, I utilise the `chmod` command to make the file executable - **`chmod u+x x.sh`**

Finally I run **`./x.sh`** to get the flag - `pwn.college{gWjlzQlgNbcQ8ibin30vA-NhAz8.dRzNyUDL1QjN0czW}`

```
hacker@chaining~executable-shell-scripts:~$ nano x.sh
hacker@chaining~executable-shell-scripts:~$ ls
COLLEGE  Desktop  PWN  f  instructions  mgflag  my-flag  myfile  myflag  not-the-flag  output  p  the-flag  x.sh
hacker@chaining~executable-shell-scripts:~$ chmod u+x x.sh
hacker@chaining~executable-shell-scripts:~$ ./x.sh
Congratulations on your shell script execution! Your flag:
pwn.college{gWjlzQlgNbcQ8ibin30vA-NhAz8.dRzNyUDL1QjN0czW}
```

## Completion

![](https://i.imgur.com/DwyOh6h.png)