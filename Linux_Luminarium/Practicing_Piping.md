# Practicing Piping

This module is about piping.

![](https://i.imgur.com/C96SHFH.png)

- [Practicing Piping](#practicing-piping)
  - [Redirecting output](#redirecting-output)
  - [Redirecting more output](#redirecting-more-output)
  - [Appending output](#appending-output)
  - [Redirecting errors](#redirecting-errors)
  - [Redirecting input](#redirecting-input)
  - [Grepping stored results](#grepping-stored-results)
  - [Grepping live output](#grepping-live-output)
  - [Grepping errors](#grepping-errors)
  - [Duplicating piped data with tee](#duplicating-piped-data-with-tee)
  - [Writing to multiple programs](#writing-to-multiple-programs)
  - [Split-piping stderr and stdout](#split-piping-stderr-and-stdout)
  - [Completion](#completion)

## Redirecting output 

In this challenge, we are required to write `PWN` to the file `COLLEGE`.

We can run `echo PWN > COLLEGE` to write the message `PWN` to the file `COLLEGE`. Running this gives us the flag - `pwn.college{szoxMZp5jK4htt90ivjLZJMHlzq.dRjN1QDL1QjN0czW}`

```
hacker@piping~redirecting-output:~$ echo PWN > COLLEGE
Correct! You successfully redirected 'PWN' to the file 'COLLEGE'! Here is your 
flag:
pwn.college{szoxMZp5jK4htt90ivjLZJMHlzq.dRjN1QDL1QjN0czW}
hacker@piping~redirecting-output:~$ 
```

## Redirecting more output

In this challenge, we are required to redirect the output of the command `/challenge/run` into a file called `myflag`.

We can run `/challenge/run > myflag` to write the output into the file `myflag`.

```
hacker@piping~redirecting-more-output:~$ /challenge/run > myflag
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge will check that output is redirected to a specific file path : myflag
[INFO] - the challenge will output a reward file if all the tests pass : /flag

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /flag file.

[TEST] You should have redirected my stdout to a file called myflag. Checking...

[PASS] The file at the other end of my stdout looks okay!
[PASS] Success! You have satisfied all execution requirements.
```
We can get our flag by printing out the contents using `cat myflag`.

```
hacker@piping~redirecting-more-output:~$ cat myflag
[FLAG] Here is your flag:
[FLAG] pwn.college{sgKLXK338lrguqbWJGQ1TyJirdV.dVjN1QDL1QjN0czW}
```

## Appending output

In this challenge, we are required to redirect the output of the command `/challenge/run` in append mode (>>) to `/home/hacker/the-flag` to get the complete flag.

We can run `/challenge/run >> /home/hacker/the-flag` to redirect the output to the file.

We can then run `cat /home/hacker/the-flag` to get the flag - `pwn.college{IbcLUrU6eeBYre-BUtzMcKYT0vB.ddDM5QDL1QjN0czW}`

```
hacker@piping~appending-output:~$ cat /home/hacker/the-flag
 | 
\|/ This is the first half:
 v 
pwn.college{IbcLUrU6eeBYre-BUtzMcKYT0vB.ddDM5QDL1QjN0czW}
                              ^
     that is the second half /|\
                              |

```

> [!NOTE]
> Append mode will keep appending to the same file, but > will create a new output file every time, deleting the old contents.

## Redirecting errors

In this challenge, we are required to redirect the output to `myflag` and redirect the errors to `instructions`

I ran `/challenge/run > myflag 2> instructions` 

Then I printed out the `myflag` using `cat myflag` to get the flag - `pwn.college{UP_JfmmoL6OexVNoHiEAN2djbAM.ddjN1QDL1QjN0czW}`

```
hacker@piping~redirecting-errors:~$ cat myflag

[FLAG] Here is your flag:
[FLAG] pwn.college{UP_JfmmoL6OexVNoHiEAN2djbAM.ddjN1QDL1QjN0czW}
```

## Redirecting input

In this challenge, we are required to redirect a file called `PWN` that contains `COLLEGE` to the command `/challenge/run` to get our flag.

I ran `echo COLLEGE > PWN` to create the file that we need to redirect.

Then I ran `/challenge/run < PWN` and got the flag - `pwn.college{AAK_sCtaVfCyjuztl00ExJ5dmh9.dBzN1QDL1QjN0czW}`

```
hacker@piping~redirecting-input:~$ echo COLLEGE > PWN
hacker@piping~redirecting-input:~$ /challenge/run < PWN
Reading from standard input...
Correct! You have redirected the PWN file into my standard input, and I read 
the value 'COLLEGE' out of it!
Here is your flag:
pwn.college{AAK_sCtaVfCyjuztl00ExJ5dmh9.dBzN1QDL1QjN0czW}
```
## Grepping stored results

In this challenge, we are required to redirect the output of `/challenge/run` to `/tmp.data.txt` and then search for our flag in the data file. 

I ran the command **`/challenge/run > /tmp.data.txt`** to redirect the output.

The file has hundred thousand lines of text so I used grep to search for the string `pwn.college` as all the flags start with it. Running **`grep pwn.college /tmp/data.txt`** gave the flag - `pwn.college{YPwmGusEKEMr5FrhzR8Im5lsoK7.dhTM4QDL1QjN0czW}`

```
hacker@piping~grepping-stored-results:~$ grep pwn.college /tmp/data.txt
pwn.college{YPwmGusEKEMr5FrhzR8Im5lsoK7.dhTM4QDL1QjN0czW}
```

## Grepping live output

Similar to the last challenge, we are required to look for our flag in the output using the piping (|) operator.

We can run the command `/challenge/run | grep pwn.college` where `|` is the piping operator. Running this gives us the flag - `pwn.college{0KuRxyHpvlWM0ATJqcvvsArCVf-.dlTM4QDL1QjN0czW}`

```
hacker@piping~grepping-live-output:~$ /challenge/run | grep pwn.college
pwn.college{0KuRxyHpvlWM0ATJqcvvsArCVf-.dlTM4QDL1QjN0czW}
```

## Grepping errors

In this challenge, we are required to look for our flag in the error stream of the `/challenge/run` command using grep.

> [!NOTE]
>The piping operator `!` only redirects standard output so we need to convert standard error to standard output. We can use `>&` operator to achieve this.
>
>The `>&` operator redirects a file descriptor to another file descriptor.

We can run `/challenge/run 2>&1 | grep pwn.college` which gives us the flag - `pwn.college{ATXM8e9cqDsu0n9lud6NAopm7Gp.dVDM5QDL1QjN0czW}`

```
hacker@piping~grepping-errors:~$ /challenge/run 2>&1 | grep pwn.college
pwn.college{ATXM8e9cqDsu0n9lud6NAopm7Gp.dVDM5QDL1QjN0czW}
```

## Duplicating piped data with tee 

In this challenge, we are supposed to pipe the output of `/challenge/pwn` into `/challenge/college` but we also need to read the output of `/challenge/pwn` to find out the argument that will give the flag. 

>[!NOTE]
> We need to pipe the output into both a file and a command. We can use the `tee` command to achieve this. 
> The `tee` command duplicates data flowing through your pipes to any number of files provided on the command

We can run **`/challenge/pwn | tee output | /challenge/college`** and then `cat output` which outputs:

```
Usage: /challenge/pwn --secret [SECRET_ARG]

SECRET_ARG should be "461ZnB_Y"
```

We can see that we must pass in the `secret` argument with the value `461ZnB_Y` into `/challenge/pwn` to get our flag. 

Running **`/challenge/pwn --secret 461ZnB_Y | /challenge/college`** gives us the flag - `pwn.college{461ZnB_YKhruFgjx_uS_oKTLvXO.dFjM5QDL1QjN0czW}`

```
hacker@piping~duplicating-piped-data-with-tee:~$ /challenge/pwn --secret 461ZnB_Y | /challenge/college
Processing...
Correct! Passing secret value to /challenge/college...
Great job! Here is your flag:
pwn.college{461ZnB_YKhruFgjx_uS_oKTLvXO.dFjM5QDL1QjN0czW}
```

## Writing to multiple programs

In this challenge, we need to pipe the output of `/challenge/hack` into both `/challenge/the` and `/challenge/planet`.

> [!NOTE]
> The `tee` command is designed to write to files and to standard output.
>
> We can write one of the commands as >(command) to pass it in as a file.


We can run `/challenge/hack | tee >(/challenge/the) | /challenge/planet` which will give us the flag - `pwn.college{AKmvvvukL_g3jO_xJjgVCdOqIiZ.dBDO0UDL1QjN0czW}`

```
hacker@piping~writing-to-multiple-programs:~$ /challenge/hack | tee >(/challenge/the) | /challenge/planet
Congratulations, you have duplicated data into the input of two programs! Here 
is your flag:
pwn.college{AKmvvvukL_g3jO_xJjgVCdOqIiZ.dBDO0UDL1QjN0czW}
```

## Split-piping stderr and stdout

In this challenge, we are supposed to pipe out the standard error of `/challenge/hack` into `/challenge/the` and the standard output into `/challenge/planet`

We can run `/challenge/hack 2> >(/challenge/the) | /challenge/planet`  which will give us the flag - `pwn.college{IWaxmi1mPEBlQXd2m8t4tvzN7-a.dFDNwYDL1QjN0czW}`

```
hacker@piping~split-piping-stderr-and-stdout:~$ /challenge/hack 2> >(/challenge/the) | /challenge/planet
Congratulations, you have learned a redirection technique that even experts 
struggle with! Here is your flag:
pwn.college{IWaxmi1mPEBlQXd2m8t4tvzN7-a.dFDNwYDL1QjN0czW}
```

## Completion

![](https://i.imgur.com/j7qyJ5V.png)