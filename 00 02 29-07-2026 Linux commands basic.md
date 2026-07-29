# Ubuntu EC2 Lab Notes – Python, Java, Node.js & Linux Basics

## Environment

* **Operating System:** Ubuntu 26.04 LTS
* **Platform:** AWS EC2
* **Architecture:** x86_64
* **Hostname:** `ip-172-31-25-68`

---

# 1. Basic Linux Commands

## Create a Directory

```bash
mkdir project
```

## List Files

```bash
ls
```

## Print Current Directory

```bash
pwd
```

## Change Directory

```bash
cd
cd /
```

## View Command History

```bash
history
```

## Clear Terminal

```bash
clear
```

---

# 2. Installing Tree Utility

Search directory structure visually.

## Install

```bash
sudo apt install tree -y
```

## Verify Installation

```bash
tree --version
```

## Display Directory Tree

```bash
tree
```

---

# 3. Python Installation

## Check Python Version

```bash
python --version
python3 --version
```

If `python` is unavailable:

```bash
sudo apt install python-is-python3 -y
```

Verify:

```bash
python --version
```

---

# 4. Nano Text Editor

## Install Nano

```bash
sudo apt install nano -y
```

## Verify

```bash
nano --version
```

---

# 5. Python Hello World Program

## Create File

```bash
touch helloworld.py
```

## Edit

```bash
nano helloworld.py
```

### Code

```python
print("Hello, World!")
```

## Save

* CTRL + O
* Enter
* CTRL + X

## Execute

```bash
python helloworld.py
```

### Output

```
Hello, World!
```

## View File

```bash
cat helloworld.py
```

---

# 6. Install Java (OpenJDK)

## Search Packages

```bash
sudo apt search openjdk
```

or

```bash
sudo apt search java-21
```

## Install Java

```bash
sudo apt install default-jdk-headless -y
```

## Verify

```bash
java --version
```

---

# 7. Java Hello World Program

## Create File

```bash
touch helloworld.java
```

## Edit File

```bash
nano helloworld.java
```

### Java Code

```java
public class helloworld {
    public static void main(String[] args) {
        System.out.println("Hello, World!");
    }
}
```

## Compile

```bash
javac helloworld.java
```

This creates:

```
helloworld.class
```

## Run Program

```bash
java helloworld
```

### Output

```
Hello, World!
```

## View Source Code

```bash
cat helloworld.java
```

---

# 8. Install Node.js using NVM

## Install NVM

```bash
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.40.6/install.sh | bash
```

Load NVM without restarting:

```bash
. "$HOME/.nvm/nvm.sh"
```

## Install Node.js

```bash
nvm install 24
```

## Verify

```bash
node -v
```

Example:

```
v24.18.0
```

Check npm:

```bash
npm -v
```

Example:

```
11.16.0
```

---

# 9. Working with Root User

Become root:

```bash
sudo su
```

or

```bash
sudo -i
```

Set root password:

```bash
sudo passwd
```

Exit root:

```bash
exit
```

---

# 10. Useful File Commands

Display file contents:

```bash
cat filename
```

Example:

```bash
cat helloworld.java
```

Create empty file:

```bash
touch filename
```

---

# 11. SSH Session Disconnect

During the lab, the SSH session disconnected with:

```
Connection reset by peer

client_loop: send disconnect: Broken pipe
```

### Reason

This usually happens because:

* Internet interruption
* Laptop sleep mode
* Idle SSH session timeout
* Network instability

Reconnect using:

```bash
ssh -i "key.pem" ubuntu@ec2-54-197-195-123.compute-1.amazonaws.com
```

---

# 12. Why Command History Was Lost

After reconnecting:

```bash
history
```

Output:

```
1 history
```

### Possible Reasons

* A new shell session started.
* Previous history was not yet written to `~/.bash_history`.
* SSH session ended unexpectedly before logout.
* History is normally saved when the shell exits cleanly.

---

# 13. Commands Practised

```bash
mkdir
ls
pwd
cd
history
clear
tree
tree --version
python --version
python3 --version
sudo apt install
nano
touch
cat
javac
java
curl
nvm
node
npm
sudo su
sudo -i
ssh
```

---

# Learning Summary

You successfully practised:

* Ubuntu Linux navigation
* Directory and file management
* Installing packages with APT
* Using Nano editor
* Running Python programs
* Installing OpenJDK
* Compiling and running Java applications
* Installing Node.js using NVM
* Working with root privileges
* Connecting to AWS EC2 using SSH
* Understanding SSH disconnections and shell history behaviour

---

# Lab Outcome

By the end of this exercise, you learned how to:

* Navigate Linux using essential commands.
* Install software packages on Ubuntu.
* Create and execute Python applications.
* Compile and run Java programs using `javac` and `java`.
* Install Node.js and npm using NVM.
* Connect securely to an AWS EC2 instance via SSH.
* Troubleshoot common SSH connection and terminal history issues.
