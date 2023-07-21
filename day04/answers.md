## Basic Linux Shell Scripting for DevOps Engineer

**1:** Kernel

The kernel is a heart of an operating system. It acts as the bridge between the software applications and the hardware of a computer system. The primary role of the kernel is to manage system resources and provide an interface for applications to interact with the hardware.

Responsibility of kernel is to establish communication between your hardware and software. It has 4 primary responsibility

- Device Management
- Memory Management
- Process Management
- Handling System related calls


**2:** Shell

A shell is special user program which provide an interface to user to use operating system services. Shell accept human readable commands from user and convert them into something which kernel can understand. It is a command language interpreter that execute commands read from input devices such as keyboards or from files. The shell gets started when the user logs in or start the terminal.

**3:** Linux Shell Scripting

Shell scripting refers to the process of writing and executing scripts using a shell, which is a command-line interpreter or a user interface for accessing the operating system's services.

A shell script is a computer program designed to be run by a linux shell, a command-line interpreter. The various dialects of shell scripts are considered to be scripting languages. Typical operations performed by shell scripts include file manipulation, program execution, and printing text.

**4:** Shell Scripting for DevOps

Shell scripting for DevOps enables automation of deployment, configuration management, CI/CD pipelines, monitoring, logging, and performance optimization tasks. Shell scripting languages, such as Bash, are used for automating tasks in DevOps workflows.

Some of the roles performed by DevOps engineer are
- Infrastructure management
- Codebase management
- Configuration Management
- Automation

These roles can be performed using the help of shell scripting.

**5:** What is `#!/bin/bash?` can we write `#!/bin/sh` as well?

`#!/bin/bash` is called a shebang, also known as a hashbang or interpretor directive. It is the first line of a script that tells the system on how to execute the script. `#!/bin/bash` indicates that the script should be executed using the Bash shell.

While `#!/bin/sh` indicates that the script should be executed using the default shell. 

So both the shebang are different, we can write `#!/bin/sh` instead of `#!/bin/bash` if the systems default shell is bash otherwise we would have to specify the shebang depending upon our requirement.


**6:** Write a Shell Script which prints `I will complete #90DaysOofDevOps challenge`

```shell
vim task.sh
```

```shell
#!/bin/bash

echo "I will complete #90DaysOfDevOps challenge"
```

You can execute the above script using the command `bash task.sh` or `./task.sh`

> Note: To execute the script using `./task.sh` it should have the executable permissions and an appropriate shebang at the begining of the script, To give read, write and execute permission to the owner we can use the following command `chmod 700 task.sh`

**7:** Write a Shell Script to take user input, input from arguments and print the variables.

```shell
#!/bin/bash

echo -n "Enter your name: "
read user_name

arg1=$1
arg2=$2

echo "User input: $user_name"
echo "Command-line argument 1: $arg1"
echo "Command-line argument 2: $arg2"
```

**8:** Write an Example of If else in Shell Scripting by comparing 2 numbers


```shell
#!/bin/bash

echo -n "Enter the first number: "
read num1

echo -n "Enter the second number: "
read num2


if [ $num1 -gt $num2 ] 
then
	echo "$num1 is greater than $num2"
	
elif [ $num1 -lt $num2 ] 
then
	echo "$num2 is greater than $num1"

else
	echo "Both the numbers are equal"

fi

```


