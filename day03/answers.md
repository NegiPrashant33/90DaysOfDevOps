## Basic Linux Commands

**1:** 
To  view what's written in a file

`cat <file name>` command is used to view whats written in a file

```shell
cat notes.txt
```

**2:**
To change the access permission of a file

`chmod` command is used to change the access permission of a file, it stands for change mode

- `chmod <options> <permissions> <file name>` (grant permissions like read [r], write [w], execute [x] to a file or directory)
    
    
    chmod is divided into 3 categories
    
    - what are the permissions for the user/owner [u]
    - what are the permissions for the group [g]
    - what are the permissions for other (neither part of the group nor owner) [o]
    
    **Permissions** can be granted in two ways
    
    **Symbolic Mode**: The symbolic mode allows you to specify permissions using symbols and operators. The symbols are:
    
    - `u` for the user/owner permissions
    - `g` for the group permissions
    - `o` for others (everyone else) permissions
    - `a` for all (u+g+o) permissions
    
    The operators are:
    
    - `+` to add permissions
    - `-` to remove permissions
    - `=` to set permissions explicitly
    
    Example 
    ```shell
    chmod u+rw file.txt
    ```
    
    **Numeric Mode**: The numeric mode allows you to specify permissions using octal (base-8) values. Each digit represents a set of permissions:
    
    - 4 for read permission
    - 2 for write permission
    - 1 for execute permission
    
    You can add the values together to represent multiple permissions

    Example 
    ```shell
    chmod 700 file.txt
    ```
    

**3:**
To check which commands you have run till now

```shell
history
```


**4:**
To remove a directory

prashant --> directory name

- If the directory is empty
```shell
rmdir prashant
```

- If the directory is not empty
```shell
rm -r prashant

rm -rf prashant
```

`-r` flag stands for recusively, this flag will remove all the contents of the directory, `-f` flag stands for force which forces removal of directory without prompting for permission

**5:**
To create a fruits.txt file and to view the content.

We can create a new file and insert content in it using the vi or vim text editors, and to view the content we can use the `cat` command

Below are some important points on how to use the vim text editor

- `vim <file name>` (open the file using vim text editor, if file does not exist it will be created)

    - **i**: Enter Insert mode to start editing the file.
    - **Esc**: Exit Insert mode and return to Normal mode, Esc is used to enter a mode, when you open the file press Esc and then i to enter the insert mode
    - **:w**: Save the changes made to the file.
    - **:q**: Quit the editor if no unsaved changes exist.
    - **:q!**: Quit the editor and discard any unsaved changes.
    - **:wq** or **:x**: Save the changes and exit the editor.

```shell
vim fruits.txt
cat fruits.txt
```


**6:**
Add content in devops.txt (One in each line) - Apple, Mango, Banana, Cherry, Kiwi, Orange, Guava.

```shell
vim devops.txt
```
As instructed in point 5 insert the content in devops.txt file and save it.

**7:**
To Show only top three fruits from the file.

```shell
head -n 3 devops.txt
```
`-n` flag is used to mention the number of lines 

**8:**
To Show only bottom three fruits from the file.

```shell
tail -n 3 devops.txt
```

**9:**
To create another file Colors.txt and to view the content.

```shell
vim colors.txt
cat colors.txt
```

**10:**
Add content in Colors.txt (One in each line) - Red, Pink, White, Black, Blue, Orange, Purple, Grey

Using the vim editor insert the content to colors.txt file, refer point 5 to understand how to use vim

```shell
vim colors.txt
```

**11:**
To find the difference between fruits.txt and Colors.txt file.

```shell
diff -u devops.txt colors.txt
```


