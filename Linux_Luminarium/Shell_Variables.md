# Shell Variables

This module is about shell variables.

![](https://i.imgur.com/YP7i5cE.png)

- [Shell Variables](#shell-variables)
  - [Printing Variables](#printing-variables)
  - [Setting Variables](#setting-variables)
  - [Multi-word Variables](#multi-word-variables)
  - [Exporting Variables](#exporting-variables)
  - [Printing Exported Variables](#printing-exported-variables)
  - [Storing Command Output](#storing-command-output)
  - [Reading Input](#reading-input)
  - [Reading Files](#reading-files)
  - [Completion](#completion)

## Printing Variables 

In this challenge, we are supposed to print out the variable `FLAG` to get our flag.

We can print out variables with echo by prepending the variable name with `$`. Running **`echo $FLAG`** gives us the flag - `pwn.college{MqcNbjalOZqD3Talb_f1F6OjXLi.ddTN1QDL1QjN0czW}`

```
hacker@variables~printing-variables:~$ echo $FLAG
pwn.college{MqcNbjalOZqD3Talb_f1F6OjXLi.ddTN1QDL1QjN0czW}
```

## Setting Variables

In this challenge, we are supposed to write the value `COLLEGE` to the variable `PWN` to get our flag.

We can set the `PWN` variable to `COLLEGE` by running **`PWN=COLLEGE`** which gives us the flag - `pwn.college{EAxLD158PIbzkvPOqlZA0wIvsRC.dlTN1QDL1QjN0czW}`

```
hacker@variables~setting-variables:~$ PWN=COLLEGE
You've set the PWN variable properly! As promised, here is the flag:
pwn.college{EAxLD158PIbzkvPOqlZA0wIvsRC.dlTN1QDL1QjN0czW}
```

## Multi-word Variables

In this challenge, we are supposed to write the value `COLLEGE YEAH` to the variable `PWN` to get our flag.

> [!NOTE]
> When the shell sees a space, it ends the variable assignment and interprets the next word as a command.
>
> We can overcome this by quoting the text.

We can run `PWN="COLLEGE YEAH" which gives us the flag - `pwn.college{AtF2QOEKPF79DSBrLjTDg4BnKg2.dBjN1QDL1QjN0czW}`

```
hacker@variables~multi-word-variables:~$ PWN="COLLEGE YEAH"
You've set the PWN variable properly! As promised, here is the flag:
pwn.college{AtF2QOEKPF79DSBrLjTDg4BnKg2.dBjN1QDL1QjN0czW}
```

## Exporting Variables

In this challenge, we must invoke `/challenge/run` with the PWN variable exported and set to the value COLLEGE, and the COLLEGE variable set to the value PWN but not exported.

We can run `export PWN=COLLEGE` to export the `PWN` variable amd we can run `COLLEGE=PWN` to set the `COLLEGE` variable.

But `/challenge/run` has to be run in a shell process where `COLLEGE` variable is not inherited so we can create a child process using `sh` where only the variable `PWN` will be available.

Running `/challenge/run` in the newly created child process gives us the flag - `pwn.college{4XG1qpsPJC9pXoB5dggvYDytyMp.dJjN1QDL1QjN0czW}`

 ```
 hacker@variables~exporting-variables:~$ export PWN=COLLEGE
You've set the PWN variable to the proper value!
hacker@variables~exporting-variables:~$ COLLEGE=PWN
You've set the PWN variable to the proper value!
You've set the COLLEGE variable to the proper value!
hacker@variables~exporting-variables:~$ sh
sh-5.2$ /challenge/run
CORRECT!
You have exported PWN=COLLEGE and set, but not exported, COLLEGE=PWN. Great 
job! Here is your flag:
pwn.college{4XG1qpsPJC9pXoB5dggvYDytyMp.dJjN1QDL1QjN0czW}
```

## Printing Exported Variables

In this challenge, we must print out all the exported variables and look for the `FLAG` variable.

We can use the piping concepts we learnt in the previous module and run **`env | grep FLAG`** which outputs:

```
hacker@variables~printing-exported-variables:~$ env | grep FLAG
FLAG=pwn.college{4v98omxzO33QzSeFbRXpYhtWfMy.dhTN1QDL1QjN0czW}
```

## Storing Command Output 

In this challenge, we are supposed to store the output of `/challenge/run` in a variable called `PWN` and we must print it out in order to get our flag.

We can run `PWN=$(/challenge/run)` to store the output of `/challenge/run` in `PWN`. We can then use `echo $PWN` to print out our flag - `pwn.college{sebq7zeMhNIq23gCHqX1SxrZZqm.dVzN0UDL1QjN0czW}`

```
hacker@variables~storing-command-output:~$ PWN=$(/challenge/run)
Congratulations! You have read the flag into the PWN variable. Now print it out 
and submit it!
hacker@variables~storing-command-output:~$ echo $PWN
pwn.college{sebq7zeMhNIq23gCHqX1SxrZZqm.dVzN0UDL1QjN0czW}
```

## Reading Input

In this challenge, we are supposed to use the `read` command to write the value `COLLEGE` to the variable `PWN`.

We can run `read -p "Enter:" PWN` and enter `COLLEGE` which will give us the flag - `pwn.college{gyXum4x46mp_p2mH4TWMP1kTVkE.dhzN1QDL1QjN0czW}`

```
hacker@variables~reading-input:~$ read -p "Enter:" PWN
Enter:COLLEGE
You've set the PWN variable properly! As promised, here is the flag:
pwn.college{gyXum4x46mp_p2mH4TWMP1kTVkE.dhzN1QDL1QjN0czW}
```

## Reading Files

In this challenge, we supposed to read the output of `/challenge/read_me` into `PWN` to get our flag.

We can use the `<` operator we learnt from the previous to pipe the ouput of `/challenge/read_me` into the input stream of `read`. 

Running **`read PWN < /challenge/read_me`** gives us the flag - `pwn.college{UvToHYwkgjURSfk63v-__UcF8d3.dBjM4QDL1QjN0czW}`

```
hacker@variables~reading-files:~$ read PWN < /challenge/read_me
You've set the PWN variable properly! As promised, here is the flag:
pwn.college{UvToHYwkgjURSfk63v-__UcF8d3.dBjM4QDL1QjN0czW}
```

## Completion

![](https://i.imgur.com/iHZAcsp.png)