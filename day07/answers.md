## Understanding Package Manager and systmectl

**1: Package manager in Linux?**
 
A package manager is a software tool or system that automates the process of installing, updating, configuring, and removing software packages on a Linux distribution. It simplifies the management of software by handling dependencies, versioning, and ensuring proper installation procedures. A software package is a compressed archive containing files and metadata required to install a specific application or software on a Linux system.

The package manager can be a graphical application like a software center or a command line tool like apt-get or pacman.


**2: Package**
 
A package is usually referred to an application but it could be a GUI application, command line tool or a software library (required by other software programs). A package is essentially an archive file containing the binary executable, configuration file and sometimes information about the dependencies.

**3: Different kinds of package managers**

Package Managers differ based on packaging system but same packaging system may have more than one package manager.

For example, RPM has Yum and DNF package managers. For DEB, you have apt-get, aptitude command line based package managers.


**4: Installing docker and jenkins**

```shell
# Installing docker

sudo apt-get update

sudo apt-get install docker.io

sudo usermod -aG docker $USER

```

> Note: By default, Docker commands require root (sudo) privileges. If you want to run Docker commands without using sudo, you can add your user to the "docker" group, in the above scipt the last command will serve that purpose.

`docker --version` command can be used to check if docker is installed or not.

```shell
sudo apt-get update

sudo apt-get install openjdk-17-jdk

sudo apt-get install nginx
```

We require java and a web server to run jenkins on our machine therefore we have done that in the above script. You can use `java --version` command to check if java is installed or not, if java is not installed it terminal will provide various methods to install different versions of the java development kit (jdk). Use `nginx -v` command to check if it's installed correctly.


```shell

# Installing jenkins

curl -fsSL https://pkg.jenkins.io/debian/jenkins.io-2023.key | sudo tee \
  /usr/share/keyrings/jenkins-keyring.asc > /dev/null

echo deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] \
  https://pkg.jenkins.io/debian binary/ | sudo tee \
  /etc/apt/sources.list.d/jenkins.list > /dev/null

sudo apt-get update

sudo apt-get install jenkins

```

You can also refer [this](https://www.jenkins.io/doc/book/installing/linux/#debianubuntu) official documentation on how to install jenkins

> Note: If you run into [this](https://stackoverflow.com/questions/70541720/jenkins-has-no-installation-candidate-error-while-trying-to-install-jenkins-on) error, refer the first answer and don't forget to run `sudo apt-get update` command before installing jenkins using `sudo pat-get install jenkins`.


**6:**

Check the status of docker service in your system 

```shell
sudo systemctl status docker
```

**7:**

```shell
sudo systemctl status jenkins
```

![Jenkins status](/day07/images/Screenshot%20from%202023-07-24%2019-52-20.png)

```shell
sudo systemctl stop jenkins
```

![Jenkins stopped](/day07/images/Screenshot%20from%202023-07-24%2019-55-03.png)


**8:**

`systemctl` is used to examine and control the state of “systemd” system and service manager. systemd is system and service manager for Unix like operating systems(most of the distributions, not all).

`systemctl` is a command-line utility used to control and interact with the systemd system and service manager. With systemctl, you can start, stop, restart, enable, disable, and query the status of system services and other systemd units. It is the primary tool for managing services and working with the systemd init system.

Common systemctl commands include:

- `systemctl start service_name`: Start a service.
- `systemctl stop service_name`: Stop a service.
- `systemctl restart service_name`: Restart a service.
- `systemctl enable service_name`: Enable a service to start at boot.
- `systemctl disable service_name`: Disable a service from starting at boot.
- `systemctl status service_name`: Check the status of a service.
- `systemctl list-units`: List all active units and their statuses.


`service` command is a legacy tool used for managing system services and daemons. It provides a simplified and uniform interface to start, stop, restart, enable, and disable services on different Linux distributions that follow the System V init system. However, with the widespread adoption of systemd, the use of the service command is becoming less common, and it is recommended to use systemctl instead.

```shell
# Syntax
# sudo service [service_name] [action]

sudo service docker status

```