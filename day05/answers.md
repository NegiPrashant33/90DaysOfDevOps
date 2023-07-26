## Advanced Linux Shell Scripting for DevOps Engineers with User management

**1:**

While creating the script for task 1 we will make sure to handle any exceptinons such as 
- There must be 3 arguments given by the user
- Start and end range should be integers
- Start range should be less then end range

```shell
#!/bin/bash

if [ $# -ne 3 ]; then
	echo "Enter 3 arguments directory name, start range and end range"
	exit 1
fi

base_dir=$1
start_range=$2
end_range=$3

if ! [[ $start_range =~ ^[0-9]+$ ]] || ! [[ $end_range =~ ^[0-9]+$ ]]; then
    echo "Error: Start and end range must be integers."
    exit 1
fi

if [ $start_range -gt $end_range ]; then
    echo "Error: Start range must be less than or equal to end range."
    exit 1
fi

for ((i=start_range; i<=end_range; i++)); do
	dir_name=${base_dir}${i}
	mkdir $dir_name
	echo "Created directory: $dir_name"
done

```


**2:**

**Creating a backup of my scripts directory**

```shell
#!/bin/bash

src=/home/prashant/scripts
tgt=/home/prashant/backups
filename=$(date + "%d-%m-%Y").tar.gz

echo "Backup started for $filename"

tar -cvf $tgt/$filename $src

echo "Backup completed"

```

- `-c`: create, it tells tar command to create a new archive
- `-v`: verbose, it enables the tar command to display the progress and details of the archiving process.
- `-f`: This flag is used to specify the filename of the archive that will be created.

Use `tar -xf <file name>` command to unzip the file

- `-x`: Extract files from the archive.
- `-f`: Specify the filename of the archive to be extracted.



**3:**

**Crontab** : Crontab (cron table) is a configuration file that allows users to schedule and automate the execution of commands or scripts at specific intervals. It is commonly used for scheduling repetitive tasks, such as system maintenance, backups, or running periodic scripts.

- enter `crontab -e` command and select your preffered editor
- `0 9 * * * /home/prashant/backup.sh`, this will automate the task of running the backup.sh script every day at 9 a.m

> Note: You can refer [crontab guru](https://crontab.guru/) website to easily set up your 
crontab script according to your need.

**4:**
User Management

User management in Linux refers to the process of creating, modifying, and managing user accounts and user-related configurations on a Linux system. It involves actions such as creating new user accounts, setting passwords, managing user groups, assigning permissions, and controlling user access to various system resources.

**5:**

In this script we have created a function to create users by taking Username as input, after creating users we have extracted their names from the /etc/passwd direcory

```shell
#!/bin/bash

createUsers() {
	echo -n "Enter a username for user $1: "
	read username
	useradd -m $username
}

createUsers 1
createUsers 2

# Extracting user name from /etc/passwd
echo "The following users were added"
tail -n 2 /etc/passwd | awk -F":" '{print $1}'


```

> Note: to delete a user we can use the command `sudo userdel username
`