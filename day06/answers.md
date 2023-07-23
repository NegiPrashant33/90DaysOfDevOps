## File permissions and Access Control List

**1:**

-ltr flag, here `-l` stands for long format, `-t` stands for time sorting and `-r` stands for reverse sorting
You'll get a long format listing of files and directories, sorted based on their modification time in reverse order (most recent files/directories at the bottom).

```shell
touch notes.txt

ls -ltr
```

Output of the followig code
```shell
ls -l notes.txt

-rw-rw-r-- 1 prashant prashant 0 Jul 22 13:06 notes.txt
```

- `-` represents that the file is a regular file, for directories it is represented by `d`
- the first `rw-` represent that the owner has read and write perimission, the second `rw-` represent that the group has read and write permission while the third `r--` represent that others that is people who are not owner or part of group have only read permission.
- first `prashant` represent the owner name
- second `prashant` represent the group here, each user by default is also seen as a group in linux
- `0` is the size of the file
- then the date at which it was created is shown
- at the end we have the file name


**2:** 

File Permissions

![Linux File Permission](https://pbs.twimg.com/media/FULaVQoUEAE4Unj.jpg:large)


**Every linux system has three type of owners**
- User: User is the person who creates a file or directory, anyone who creates a file or directory becomes it's owner by default.
- Group: A group contains multiple users.
- Others: Anyone who is not a user or part of the group comes under the category of others.


**Files and Directories have three type of permission in Linux**
- read
- write
- execute


Now 3 different File permission in linux are granted to 3 different types of people assosiated with the file as mentioned above

The `chmod` (Change Mode) command is used to change permissions for a file or directory .
There are two ways of granting file permission.

**Symbolic Mode**: The symbolic mode allows you to specify permissions using symbols and operators. The symbols are:

- `u` for the user/owner permissions
- `g` for the group permissions
- `o` for others (everyone else) permissions
- `a` for all (u+g+o) permissions

The operators are:

- `+` to add permissions
- `-` to remove permissions
- `=` to set permissions explicitly

Example `chmod u+rw file.txt`

**Numeric Mode**: The numeric mode allows you to specify permissions using octal (base-8) values. Each digit represents a set of permissions:

- 4 for read permission
- 2 for write permission
- 1 for execute permission

You can add the values together to represent multiple permissions

Example `chmod 700 file.txt`


**3:**

**Access Control List**

It allows us to give more specific set of permission to a file or directory without changing the base ownership or permission.

Here basically we are not changing the ownership or generic permission of the file or directory, but we will provide a spcific or special permission to a user or group

Why do we require ACL when we have commands like chmod, chown, chgrp

ACL is required to give special permission to a user or group, for example if a user (not part of any group) has only read permission for a file and we want to give him write permission as well then using `chmod` we can give him write acess to file by changing permissions for others, but this would also give write permission to any user who is not an owner and part of the group

This is the issue that Access control list solves.


- `getfacl`: (get file access control list) provide all the details about file permission and ownership realated information in readable format

```shell

getfacl notes.txt

# Output
# file: notes.txt
# owner: prashant
# group: prashant
user::rw-
group::rw-
other::r--

```

- `setfacl`: (set file access control list)

    Use cases
    - To change permission for a particular user
    ```shell
    setfacl -m u:piya:rw notes.txt
    ```
    `-m` stands for modification, `u` stands for user, `piya` is the user name, `rw` are the read and write permissions given and `notes.txt` is the file for which these permission are granted

    If we use `ls -l notes.txt` command we would see a plus (+) sign after the permissions which indicates that ACL is used, we can also use `getfacl` command to view the changes.

    - Adding permission for a specific group
    ```shell
    setacl -m g:devops:rwx nodeHealth.sh
    ```

    - To remove a specific entry
    ```shell
    setacl -x u:piya notes.txt
    # will remove all special permission for user piya
    ```

    - To remove all entries
    ```shell
    setfacl -b  notes.txt
    # will remove all the special permission
    ```

    - To give permission for all the files that are in a particular directory
    ```shell
    setfacl -Rm u:piya:rwx scripts/
    ```
