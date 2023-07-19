## Basic Linux Commands

**1:** 
Check your present working directory

pws stands for present working directory
```shell
pwd
```


**2:** 
List all files and directory including hidden files

The `-l` and `-a` are flags or options that modify the behavior of the command. Flags are used to enable or disable specific features or provide additional information.

> Note: You can often find information about available flags and their meanings by referring to the command's manual page. For example, to view the manual page for the `ls` command, you can use the `man ls` command in the terminal. `-l` stands for long format `-a` stands for all


```shell
ls -la
```

**3:** 
Create a nested directory A/B/C/D/E

The `-p` flag stand for parent, it allows us to create directory and parent directory in a single command when used with `mkdir`

```shell
mkdir -p A/B/C/D/E
```