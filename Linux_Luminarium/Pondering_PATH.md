# Pondering PATH

This module is about the PATH variable in Linux.

![](https://i.imgur.com/2qrhy1S.png)

- [Pondering PATH](#pondering-path)
  - [The PATH Variable](#the-path-variable)
  - [Setting PATH](#setting-path)
  - [Adding Commands](#adding-commands)
  - [Hijacking Commands](#hijacking-commands)
  - [Completion](#completion)

## The PATH Variable

In this challenge, we are supposed to make it so that `/challenge/run` cannot use the `rm` command in order to get our flag.

> [!NOTE]
> The shell will search for programs corresponding to commands in a special variable called the `PATH` variable.

We can set the value of the `PATH` variable to an empty string to prevent the program from accessing the `rm` command. The program 
`/challenge/run` will be a child process of our shell so we can export the `PATH` variable since child processes inherit the variables of the parent shell

I run **`export PATH=""`** to export the `PATH` variable as a empty string.

Then I run **`/challenge/run`** to get the flag - `pwn.college{wfjcWqqZFJPVuUkuqzumqwEsqGY.dZzNwUDL1QjN0czW}`

```
hacker@path~the-path-variable:~$ export PATH=""
hacker@path~the-path-variable:~$ /challenge/run
Trying to remove /flag...
/challenge/run: line 4: rm: No such file or directory
The flag is still there! I might as well give it to you!
pwn.college{wfjcWqqZFJPVuUkuqzumqwEsqGY.dZzNwUDL1QjN0czW}
```

## Setting PATH

In this challenge, the program `/challenge/run` will run the win command via its bare name, but this command exists in the `/challenge/more_commands/` directory, which is not initially in the `PATH` variable. Therefore we need to add the path to the `PATH` variable to get our flag.

I run **`PATH=/challenge/more_commands/`** to set the path variable.

Then I run **`/challenge/run`** to get the flag - `pwn.college{U-JGAnEWnk3KdWHbeAy0Jxd7_kx.dVzNyUDL1QjN0czW}`

```
hacker@path~setting-path:~$ PATH=/challenge/more_commands/
hacker@path~setting-path:~$ /challenge/run
Invoking 'win'....
Congratulations! You properly set the flag and 'win' has launched!
pwn.college{U-JGAnEWnk3KdWHbeAy0Jxd7_kx.dVzNyUDL1QjN0czW}
```

## Adding Commands

In this challenge, we need to trick `/challenge/run` into printing the flag by modifying the `win` file. 

I used [nano](https://www.nano-editor.org/) to create a file named `win` in the home directory:

```
read FLAG < /flag
echo $FLAG
```
> [!NOTE]
> Since we are modifying the `PATH` variable, the system can't find comamnds like `cat`. Therefore we have to use alternative methods to print out the flag.
>
> One such method is the `read` command which reads the contents of a file into a variable. We can then print out the variable using `echo`
>

I made it executabe for all users by running **`chmod o+x win`**

Then I modify the PATH variable - `PATH=~/`

Finally I run **`/challenge/run`** to get the flag - `pwn.college{QYA-gOygwdqwBtDa0EbC7Ax3wXn.dZzNyUDL1QjN0czW}`

```
hacker@path~adding-commands:~$ nano win
hacker@path~adding-commands:~$ chmod u+x win
hacker@path~adding-commands:~$ PATH=~/
hacker@path~adding-commands:~$ /challenge/run
Invoking 'win'....
pwn.college{QYA-gOygwdqwBtDa0EbC7Ax3wXn.dZzNyUDL1QjN0czW}
```

## Hijacking Commands

In this challenge, we need to trick `/challenge/run` into printing the flag by changing the `rm` comamnd.

> [!NOTE]
> To get the flag, we could create a file named rm that would display the flag. Subsequently, we could manipulate the PATH environment variable to prioritize our custom rm command, thereby deceiving /challenge/run into executing it and revealing the flag.

I used [nano](https://www.nano-editor.org/) to create a file named `rm` in the home directory:

```
read FLAG < /flag
echo $FLAG
```
I made it executabe for all users by running **`chmod o+x rm`**

Then I modify the PATH variable - `PATH=~/`

Finally I run `/challenge/run` to get the flag - `pwn.college{0dCFIPi5NC4yrgcolhhY1PN8HD3.ddzNyUDL1QjN0czW}`

```
hacker@path~hijacking-commands:~$ nano rm
hacker@path~hijacking-commands:~$ chmod o+x rm
hacker@path~hijacking-commands:~$ PATH=~/
hacker@path~hijacking-commands:~$ /challenge/run
Trying to remove /flag...
pwn.college{0dCFIPi5NC4yrgcolhhY1PN8HD3.ddzNyUDL1QjN0czW}
```

## Completion

![](https://i.imgur.com/jAfKoBU.png)