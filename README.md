# Linux Notes

## Session 1: Introduction to Linux & Essential Commands

### 1. What is Linux?

Linux is an open-source, Unix-like operating system kernel. Linux distributions combine the kernel with system utilities and software to provide a complete operating system.

Features of Linux

- Open-source and customizable
- Multiuser and multitasking
- Secure permission model
- Stable and reliable
- Command-line and GUI support
- Widely used in cloud, servers and DevOps

### 2. Popular Linux Distributions

| Distribution | Common use               | Package manager |
| ------------ | ------------------------ | --------------- |
| Ubuntu       | Cloud, servers, desktops | apt             |
| Debian       | Stable servers           | apt             |
| RHEL         | Enterprise servers       | dnf             |
| Amazon Linux | AWS EC2                  | dnf             |
| Rocky Linux  | Enterprise workloads     | dnf             |
| Fedora       | Development              | dnf             |

### 3. Linux vs Windows

| Linux                            | Windows                                |
| -------------------------------- | -------------------------------------- |
| Mostly open-source distributions | Proprietary operating system           |
| Bash and other shells            | PowerShell and CMD                     |
| Case-sensitive filenames         | Usually case-insensitive               |
| `/home` user directories         | `C:\Users` user directories            |
| Commonly used for servers        | Commonly used for desktops and servers |

### 4. Kernel vs Shell

| Component | Description                                |
| --------- | ------------------------------------------ |
| Kernel    | Manages CPU, memory, devices and processes |
| Shell     | Interprets user commands                   |
| Bash      | Common Linux command shell                 |
| Terminal  | Interface used to interact with a shell    |

### 5. Essential Linux Commands

| Command    | Purpose                                 |
| ---------- | --------------------------------------- |
| `pwd`      | Current directory                       |
| `ls`       | List files                              |
| `ls -la`   | Detailed listing including hidden files |
| `cd /home` | Change directory                        |
| `whoami`   | Current username                        |
| `uname -a` | Kernel and system information           |
| `hostname` | System hostname                         |
| `date`     | Current date and time                   |
| `clear`    | Clear terminal                          |
| `history`  | Command history                         |

AWS EC2 SSH Login

```
chmod 400 mykey.pem
ssh -i mykey.pem ec2-user@PUBLIC_IP
```

For Ubuntu EC2, use `ubuntu` instead of `ec2-user`.

Points to Remember

- Linux is widely used in AWS, Azure and Kubernetes.
- Root is the superuser.
- Commands and filenames are case-sensitive.
- SSH uses TCP port 22 by default.

## Session 2: Linux File System Hierarchy

### 1. Important Linux Directories

| Directory | Purpose                        |
| --------- | ------------------------------ |
| `/`       | Root directory                 |
| `/home`   | Regular user home directories  |
| `/root`   | Root user's home               |
| `/etc`    | System configuration           |
| `/var`    | Logs and variable data         |
| `/tmp`    | Temporary files                |
| `/usr`    | Applications and utilities     |
| `/bin`    | Essential user commands        |
| `/sbin`   | System administration commands |
| `/dev`    | Device files                   |
| `/proc`   | Process and kernel information |
| `/boot`   | Boot files                     |
| `/mnt`    | Temporary mount points         |

### 2. Home vs Working Directory

| Home directory              | Working directory            |
| --------------------------- | ---------------------------- |
| Default location for a user | Current location in terminal |
| `echo $HOME`                | `pwd`                        |
| `cd ~`                      | `cd /var/log`                |

### 3. Directory Commands

```
pwd
ls
ls -l
ls -a
cd /etc
cd ..
cd ~
cd -
mkdir demo
mkdir -p project/src
rmdir demo
```

### 4. Absolute vs Relative Path

| Path     | Example                 |
| -------- | ----------------------- |
| Absolute | `/home/ubuntu/file.txt` |
| Relative | `docs/file.txt`         |
| Parent   | `../file.txt`           |
| Current  | `./script.sh`           |

Points to Remember

- `/` is the filesystem root.
- `~` represents the current user's home.
- `.` means current directory.
- `..` means parent directory.
- Absolute paths start with `/`.

## Session 3: Linux Text Editors

### 1. Types of Editors

| Editor | Description                       |
| ------ | --------------------------------- |
| vi     | Terminal-based editor             |
| vim    | Enhanced vi editor                |
| nano   | Beginner-friendly terminal editor |

### 2. vi / vim Commands

```
vi file.txt
```

| Key     | Action                |
| ------- | --------------------- |
| `i`     | Insert mode           |
| `Esc`   | Return to normal mode |
| `:w`    | Save                  |
| `:q`    | Quit                  |
| `:wq`   | Save and quit         |
| `:q!`   | Quit without saving   |
| `dd`    | Delete line           |
| `yy`    | Copy line             |
| `p`     | Paste                 |
| `u`     | Undo                  |
| `/word` | Search word           |
| `G`     | Last line             |
| `gg`    | First line            |

### 3. nano Commands

```
nano file.txt
```

| Shortcut | Action   |
| -------- | -------- |
| Ctrl + O | Save     |
| Ctrl + X | Exit     |
| Ctrl + W | Search   |
| Ctrl + K | Cut line |
| Ctrl + U | Paste    |

Points to Remember

- vi has normal, insert and visual modes.
- nano is easier for beginners.
- `Esc` returns vim to normal mode.
- Use `:wq` to save and exit vi.

## Session 4: Linux Text Processing

### 1. File Management and Viewing

| Command              | Purpose                |
| -------------------- | ---------------------- |
| `touch file.txt`     | Create empty file      |
| `cat file.txt`       | Display content        |
| `less file.txt`      | Scroll through file    |
| `more file.txt`      | View file page by page |
| `head -n 5 file.txt` | First 5 lines          |
| `tail -n 5 file.txt` | Last 5 lines           |
| `tail -f app.log`    | Monitor log            |
| `cp a.txt b.txt`     | Copy file              |
| `mv a.txt b.txt`     | Move or rename         |
| `rm file.txt`        | Delete file            |

### 2. Redirection and Pipes

```
echo "Hello Linux" > file.txt
echo "Welcome" >> file.txt
cat file.txt
cat file.txt | grep Hello
ls > files.txt
```

| Operator | Purpose                        |
| -------- | ------------------------------ |
| `>`      | Overwrite output               |
| `>>`     | Append output                  |
| `<`      | Input redirection              |
| `\\|`    | Pipe output                    |
| `&&`     | Run next command if successful |
| `;`      | Run commands sequentially      |

### 3. Text Processing Commands

```
wc -l file.txt
wc -w file.txt
grep "error" app.log
grep -i "error" app.log
grep -n "error" app.log
sort names.txt
sort names.txt | uniq
sort names.txt | uniq -c
cut -d ',' -f1 users.csv
```

Points to Remember

- `grep` searches patterns.
- `wc` counts lines, words and bytes.
- `sort` arranges data.
- `uniq` removes adjacent duplicate lines.
- `cut` extracts fields.
- `>` overwrites; `>>` appends.

## Session 5: User and Group Management

### 1. Types of Linux Users

| Type    | Purpose                        |
| ------- | ------------------------------ |
| Root    | Full administrative access     |
| System  | Runs services and applications |
| Regular | Normal user activities         |

### 2. User Management Commands

```
sudo useradd -m john
sudo passwd john
id john
sudo usermod -s /bin/bash john
sudo userdel -r john
```

### 3. Group Management Commands

```
sudo groupadd developers
sudo usermod -aG developers john
groups john
getent group developers
sudo gpasswd -d john developers
sudo groupdel developers
```

### 4. Important Account Files

| File           | Purpose                   |
| -------------- | ------------------------- |
| `/etc/passwd`  | User account information  |
| `/etc/shadow`  | Password hashes and aging |
| `/etc/group`   | Group information         |
| `/etc/sudoers` | Sudo authorization        |

### 5. Switching Users

```
su - john
sudo -i
sudo whoami
whoami
```

Points to Remember

- UID 0 identifies root.
- Use `sudo` for privileged commands.
- `usermod -aG` adds supplementary group membership.
- Never edit `/etc/shadow` casually.
- Follow least-privilege access.

## Session 6: Linux File Permissions

### 1. Permission Types

| Permission | Symbol | Value |
| ---------- | ------ | ----- |
| Read       | r      | 4     |
| Write      | w      | 2     |
| Execute    | x      | 1     |

### 2. Permission Examples

| Numeric | Symbolic  | Meaning                         |
| ------- | --------- | ------------------------------- |
| 777     | rwxrwxrwx | Everyone full access            |
| 755     | rwxr-xr-x | Owner full, others read/execute |
| 700     | rwx------ | Owner full access               |
| 644     | rw-r--r-- | Owner write, others read        |
| 600     | rw------- | Owner read/write                |
| 400     | r-------- | Owner read only                 |

### 3. Commands

```
ls -l
chmod 755 script.sh
chmod +x script.sh
chmod u+x script.sh
chmod o-r file.txt
sudo chown john file.txt
sudo chown john:developers file.txt
sudo chgrp developers file.txt
```

### 4. Access Control Lists

```
getfacl file.txt
setfacl -m u:john:rw file.txt
setfacl -x u:john file.txt
```

Points to Remember

- Permissions apply to owner, group and others.
- `chmod` changes permissions.
- `chown` changes ownership.
- `chgrp` changes group ownership.
- ACLs provide additional access rules.
- Avoid `777` for sensitive files.

## Session 7: Shell Scripting Fundamentals

### 1. What is Shell Scripting?

Shell scripting automates repetitive Linux tasks using commands, variables and control structures.

### 2. Basic Shell Script

```
#!/bin/bash

echo "Hello Linux"
echo "Current User: $(whoami)"
echo "Hostname: $(hostname)"
```

Run:

```
chmod +x script.sh
./script.sh
```

### 3. Variables

```
#!/bin/bash

name="Linux"
echo "Welcome to $name"
echo "Home: $HOME"
echo "User: $USER"
```

### 4. User Input

```
#!/bin/bash

read -p "Enter your name: " name
echo "Hello $name"
```

### 5. Arithmetic Operators

```
a=10
b=5

echo $((a+b))
echo $((a-b))
echo $((a*b))
echo $((a/b))
echo $((a%b))
```

| Operator | Purpose        |
| -------- | -------------- |
| `+`      | Addition       |
| `-`      | Subtraction    |
| `*`      | Multiplication |
| `/`      | Division       |
| `%`      | Modulus        |

Points to Remember

- `#!/bin/bash` specifies Bash interpreter.
- Variables are assigned without spaces around `=`.
- `$variable` retrieves values.
- `read` accepts user input.
- `$(( ))` performs integer arithmetic.

## Session 8: Shell Scripting Control Flow

### 1. If-Else Statement

```
#!/bin/bash

read -p "Enter number: " num

if [ "$num" -gt 10 ]; then
    echo "Greater than 10"
else
    echo "10 or less"
fi
```

### 2. elif Statement

```
if [ "$num" -gt 10 ]; then
    echo "Greater"
elif [ "$num" -eq 10 ]; then
    echo "Equal"
else
    echo "Smaller"
fi
```

### 3. Case Statement

```
read -p "Enter choice: " choice

case "$choice" in
    1) echo "Start" ;;
    2) echo "Stop" ;;
    *) echo "Invalid choice" ;;
esac
```

### 4. For Loop

```
for i in 1 2 3 4 5
do
    echo "$i"
done
```

### 5. While Loop

```
i=1

while [ "$i" -le 5 ]
do
    echo "$i"
    i=$((i+1))
done
```

### 6. Until Loop

```
i=1

until [ "$i" -gt 5 ]
do
    echo "$i"
    i=$((i+1))
done
```

### 7. Functions

```
#!/bin/bash

greet() {
    echo "Hello Linux"
}

greet
```

### 8. Comparison Operators

| Operator | Meaning          |
| -------- | ---------------- |
| `-eq`    | Equal            |
| `-ne`    | Not equal        |
| `-gt`    | Greater than     |
| `-lt`    | Less than        |
| `-ge`    | Greater or equal |
| `-le`    | Less or equal    |

Points to Remember

- `if` performs conditional checks.
- `case` handles multiple choices.
- `for` iterates over values.
- `while` repeats while a condition is true.
- `until` repeats until a condition becomes true.
- `break` exits a loop; `continue` skips to the next iteration.

## Session 9: Linux System Administration

### 1. Process Management

| Command           | Purpose                                  |
| ----------------- | ---------------------------------------- |
| `ps aux`          | List processes                           |
| `top`             | Live process monitoring                  |
| `htop`            | Interactive process viewer, if installed |
| `kill PID`        | Terminate process                        |
| `kill -9 PID`     | Force termination                        |
| `pgrep nginx`     | Find process IDs                         |
| `free -h`         | Memory usage                             |
| `df -h`           | Filesystem disk usage                    |
| `du -sh /var/log` | Directory size                           |
| `uptime`          | System uptime and load                   |

### 2. Service Management

```
sudo systemctl start nginx
sudo systemctl stop nginx
sudo systemctl restart nginx
sudo systemctl status nginx
sudo systemctl enable nginx
sudo systemctl disable nginx
```

### 3. Package Management

| Ubuntu/Debian            | RHEL/Amazon Linux        |
| ------------------------ | ------------------------ |
| `sudo apt update`        | `sudo dnf check-update`  |
| `sudo apt install nginx` | `sudo dnf install nginx` |
| `sudo apt remove nginx`  | `sudo dnf remove nginx`  |
| `sudo apt upgrade`       | `sudo dnf upgrade`       |

### 4. Backup and Archive

```
tar -cvf backup.tar /home/ubuntu
tar -xvf backup.tar
tar -czvf backup.tar.gz /home/ubuntu
tar -xzvf backup.tar.gz
```

### 5. Log Management

```
journalctl -xe
journalctl -u nginx
journalctl -f
tail -f /var/log/syslog
```

On RHEL-based systems, `/var/log/messages` is commonly used instead of `/var/log/syslog`.

### 6. Cron Jobs

```
crontab -e
crontab -l
```

Example:

```
0 2 * * * /home/ubuntu/backup.sh
```

Runs the script every day at 2 AM, according to the cron environment's configured timezone.

Points to Remember

- `systemctl` manages systemd services.
- `journalctl` displays systemd logs.
- `tar` creates and extracts archives.
- `cron` schedules recurring tasks.
- Check memory, CPU, disk and logs during troubleshooting.

## Session 10: IPv4 Addressing

### 1. What is IPv4?

IPv4 is a 32-bit addressing protocol used to identify network interfaces.

Example: `192.168.1.10`

### 2. IPv4 Address Classes

| Class | First octet | Historical default mask |
| ----- | ----------- | ----------------------- |
| A     | 1–126       | 255.0.0.0               |
| B     | 128–191     | 255.255.0.0             |
| C     | 192–223     | 255.255.255.0           |
| D     | 224–239     | Multicast               |
| E     | 240–255     | Reserved                |

Modern networks primarily use CIDR rather than classful addressing.

### 3. Public vs Private IP

| Public IP                                      | Private IP                             |
| ---------------------------------------------- | -------------------------------------- |
| Globally routable when allocated and permitted | Not routed on public Internet          |
| Used for Internet communication                | Used inside private networks           |
| Must be globally unique                        | Can be reused across separate networks |

### 4. Private IPv4 Ranges

| Range                         | CIDR |
| ----------------------------- | ---- |
| 10.0.0.0 – 10.255.255.255     | /8   |
| 172.16.0.0 – 172.31.255.255   | /12  |
| 192.168.0.0 – 192.168.255.255 | /16  |

### 5. Common Subnet Masks

| CIDR | Mask            | Total addresses |
| ---- | --------------- | --------------- |
| /8   | 255.0.0.0       | 16,777,216      |
| /16  | 255.255.0.0     | 65,536          |
| /24  | 255.255.255.0   | 256             |
| /25  | 255.255.255.128 | 128             |
| /26  | 255.255.255.192 | 64              |
| /27  | 255.255.255.224 | 32              |
| /28  | 255.255.255.240 | 16              |

Points to Remember

- IPv4 is 32-bit.
- Each octet ranges from 0 to 255.
- CIDR defines network prefix length.
- A subnet mask separates network and host portions.
- Public and private addressing have different routing purposes.

## Session 11: IPv4 Subnetting & IPv6

### 1. Subnetting

Subnetting divides a larger network into smaller logical networks.

Formulas

\\[ \text{Total IPv4 addresses}=2^{32-\text{prefix}} \\]

\\[ \text{Usable hosts}=2^{32-\text{prefix}}-2 \\]

The usable-host formula applies to conventional IPv4 subnets, excluding special `/31` and `/32` cases.

### 2. Subnetting Example

Network: `192.168.1.0/24`

Divide into 4 equal subnets:

| Subnet | Network          | Usable hosts |
| ------ | ---------------- | ------------ |
| 1      | 192.168.1.0/26   | 62           |
| 2      | 192.168.1.64/26  | 62           |
| 3      | 192.168.1.128/26 | 62           |
| 4      | 192.168.1.192/26 | 62           |

### 3. What is IPv6?

IPv6 is a 128-bit addressing protocol designed to provide a much larger address space than IPv4.

Example:

```
2001:db8:abcd:12::1
```

### 4. IPv6 Address Types

| Type      | Purpose                             |
| --------- | ----------------------------------- |
| Unicast   | One-to-one communication            |
| Multicast | One-to-many group communication     |
| Anycast   | One-to-nearest suitable destination |

### 5. IPv4 vs IPv6

| IPv4                       | IPv6                      |
| -------------------------- | ------------------------- |
| 32-bit                     | 128-bit                   |
| Dotted decimal             | Hexadecimal               |
| Example: 192.168.1.1       | Example: 2001:db8::1      |
| Broadcast supported        | No broadcast              |
| ARP for address resolution | Neighbor Discovery        |
| NAT widely used            | NAT generally unnecessary |

### 6. EUI-64

Modified EUI-64 is a method for deriving a 64-bit IPv6 interface identifier from a 48-bit MAC address. Modern systems commonly use privacy or stable address-generation methods instead.

Points to Remember

- Subnetting improves address allocation and network segmentation.
- IPv6 uses hexadecimal notation.
- IPv6 supports address compression with `::`.
- Dual stack allows IPv4 and IPv6 together.
- IPv6 supports SLAAC for automatic address configuration.

## Session 12: Linux Networking & Security

### 1. Network Inspection Commands

| Command                       | Purpose                    |
| ----------------------------- | -------------------------- |
| `ip addr`                     | Show IP addresses          |
| `ip link`                     | Show interfaces            |
| `ip route`                    | Show routing table         |
| `hostname -I`                 | Show host IP addresses     |
| `ping 8.8.8.8`                | Test ICMP reachability     |
| `traceroute google.com`       | Trace network path         |
| `nslookup google.com`         | DNS lookup                 |
| `dig google.com`              | Detailed DNS lookup        |
| `ss -tuln`                    | Listening TCP/UDP ports    |
| `ss -tulnp`                   | Ports with process details |
| `curl -I https://example.com` | HTTP header test           |

### 2. IP Configuration

```
ip addr show
ip route show
ip link show
```

Temporary IP configuration example:

```
sudo ip addr add 192.168.1.100/24 dev eth0
sudo ip link set eth0 up
```

Replace `eth0` with the actual interface name. Avoid changing IP addresses on remote servers without a recovery path.

### 3. Common Networking Ports

| Port | Protocol / Service           |
| ---- | ---------------------------- |
| 22   | SSH                          |
| 53   | DNS                          |
| 80   | HTTP                         |
| 443  | HTTPS                        |
| 3306 | MySQL                        |
| 5432 | PostgreSQL                   |
| 8080 | Common alternative HTTP port |

### 4. Firewall Commands

firewalld

```
sudo systemctl status firewalld
sudo firewall-cmd --list-all
sudo firewall-cmd --permanent --add-service=http
sudo firewall-cmd --reload
```

iptables

```
sudo iptables -L -n
sudo iptables -S
sudo iptables -A INPUT -p tcp --dport 8080 -j ACCEPT
```

The iptables example adds a runtime rule; persistence depends on the distribution and firewall configuration.

Points to Remember

- `ip` is preferred over legacy `ifconfig`.
- `ping` tests ICMP connectivity, not application availability.
- `dig` and `nslookup` troubleshoot DNS.
- `ss` displays sockets and listening ports.
- Firewalls control permitted network traffic.
- In AWS, Security Groups and NACLs also affect EC2 connectivity.

## Linux Commands – Quick Revision

| Category        | Commands                                  |
| --------------- | ----------------------------------------- |
| Navigation      | `pwd`, `ls`, `cd`                         |
| Files           | `touch`, `cp`, `mv`, `rm`, `mkdir`        |
| Viewing         | `cat`, `less`, `head`, `tail`             |
| Text processing | `grep`, `sort`, `uniq`, `cut`, `wc`       |
| Users           | `useradd`, `usermod`, `userdel`, `passwd` |
| Groups          | `groupadd`, `groupdel`, `groups`          |
| Permissions     | `chmod`, `chown`, `chgrp`, `setfacl`      |
| Processes       | `ps`, `top`, `kill`, `pgrep`              |
| Services        | `systemctl`, `journalctl`                 |
| Packages        | `apt`, `dnf`                              |
| Storage         | `df`, `du`, `tar`                         |
| Scheduling      | `crontab`                                 |
| Networking      | `ip`, `ping`, `ss`, `dig`, `curl`         |
| Firewall        | `iptables`, `firewall-cmd`                |

# AWS Notes

## 1. Introduction to AWS and Cloud Computing

Definitions

- Cloud Computing: Delivery of computing resources such as servers, storage, databases and networking over the internet on demand.
- AWS: Amazon Web Services, a cloud computing platform.
- EC2: Elastic Compute Cloud, a service that provides virtual servers.
- Region: A separate geographical area where AWS operates infrastructure.
- Availability Zone (AZ): An isolated location within an AWS Region, comprising one or more data centers.
- IaaS: Infrastructure as a Service, providing virtualized infrastructure.
- PaaS: Platform as a Service, providing a managed platform for applications.
- SaaS: Software as a Service, delivering ready-to-use applications.

Points to remember

- AWS follows a pay-as-you-go pricing model for many services.
- Regions contain multiple Availability Zones.
- EC2 is primarily an IaaS service.
- Windows EC2 commonly uses RDP on port 3389.
- Linux EC2 commonly uses SSH on port 22.
- IIS is Microsoft's web server.
- HTTP uses port 80 and HTTPS uses port 443.
- A public IP can be used to access an internet-facing website when routing and security permit.

## 2. EC2 Linux, Windows and AMI

Definitions

- EC2 Instance: A virtual machine running in AWS.
- AMI: Amazon Machine Image, a template used to launch EC2 instances.
- Instance Type: Determines an EC2 instance's CPU, memory and other resource characteristics.
- Key Pair: Public/private cryptographic keys used for authentication.
- Elastic IP: A static public IPv4 address allocated to an AWS account.
- PuTTY: An SSH client commonly used to connect to Linux servers.

Points to remember

- Linux SSH port: 22.
- Windows RDP port: 3389.
- Apache and Nginx are commonly used Linux web servers.
- AMIs can be copied between AWS Regions.
- AMIs can be shared with specific AWS accounts.
- EBS-backed EC2 instances generally need to be stopped before changing instance type.
- Stopping and starting an instance can change its automatically assigned public IPv4 address.
- AMIs are regional resources.

## 3. Elastic Load Balancing (ELB)

Definitions

- Load Balancer: Distributes incoming traffic across multiple targets.
- ALB: Application Load Balancer, operating at OSI Layer 7.
- NLB: Network Load Balancer, operating at OSI Layer 4.
- GWLB: Gateway Load Balancer, used to deploy and scale network appliances.
- Target Group: A collection of targets that receive traffic.
- Listener: Checks incoming connections on a configured protocol and port.
- Health Check: Determines whether a target is healthy enough to receive traffic.

Points to remember

- ALB supports HTTP and HTTPS traffic.
- NLB supports TCP, UDP and TLS traffic, among other configurations.
- ALB supports path-based and host-based routing.
- Load balancers provide DNS names.
- Only healthy targets normally receive traffic when healthy targets are available.
- An ALB can route traffic to EC2 instances through target groups.

## 4. Auto Scaling, Launch Templates and SNS

Definitions

- Auto Scaling: Automatically adjusts resource capacity based on demand or configuration.
- ASG: Auto Scaling Group, maintains and scales a group of EC2 instances.
- Launch Template: Stores EC2 launch configuration, such as AMI and instance type.
- SNS: Simple Notification Service, a managed publish/subscribe messaging service.
- Scaling Policy: Defines how capacity changes in response to metrics or other conditions.

Points to remember

- Minimum capacity: Lowest configured instance count.
- Desired capacity: Target number of instances.
- Maximum capacity: Highest configured instance count.
- Scale Out: Increase the number of instances.
- Scale In: Decrease the number of instances.
- SNS supports notification delivery through channels such as email and SMS.
- ASG can replace unhealthy instances.
- ASG can integrate with an Application Load Balancer.

Example: Minimum = 2, Desired = 3, Maximum = 5.

## 5. Amazon EBS

Definitions

- EBS: Elastic Block Store, persistent block storage primarily used with EC2.
- EBS Volume: A virtual block storage device.
- Root Volume: Storage containing the operating system.
- IOPS: Input/output operations per second.
- gp3: General Purpose SSD EBS volume type.

Points to remember

- EBS volumes are created in a specific Availability Zone.
- A standard EBS volume must be attached to an instance in the same AZ.
- EBS persists independently of the EC2 instance lifecycle, subject to deletion settings.
- EBS supports resizing volumes.
- EBS volume types include gp3, io2, st1 and sc1.
- An EBS volume generally attaches to one instance at a time; supported Multi-Attach configurations are exceptions.

## 6. EBS Snapshots

Definitions

- Snapshot: A point-in-time backup of an EBS volume.
- Incremental Backup: Stores changed blocks after the initial snapshot.
- Volume Restore: Creates a new EBS volume from a snapshot.

Points to remember

- EBS snapshots are incremental.
- Snapshots can be copied across Regions.
- Snapshots can be shared across AWS accounts subject to permissions and encryption restrictions.
- Snapshots are used for backup and disaster recovery.
- Snapshots are stored in AWS-managed storage backed by S3, not as ordinary user-visible S3 objects.
- Snapshots and AMIs are different: a snapshot backs up volume data; an AMI provides a launch template.

## 7. Amazon S3 Fundamentals

Definitions

- S3: Simple Storage Service, an object storage service.
- Bucket: A container for storing S3 objects.
- Object: Data stored in S3, consisting of content and metadata.
- Object Key: The identifier of an object within a bucket.
- Presigned URL: A time-limited URL granting access to an S3 operation using the signing principal's permissions.
- Static Website Hosting: Serving static website content such as HTML, CSS and JavaScript.

Points to remember

- S3 is object storage, not block storage.
- S3 is regional, with data stored redundantly across multiple AZs by default for standard storage.
- S3 supports object versioning.
- S3 supports presigned URLs.
- S3 static website endpoints support HTTP, not HTTPS directly.
- S3 Block Public Access should remain enabled unless public access is deliberately required and safely configured.
- S3 Standard is designed for 99.999999999% (11 nines) object durability.

## 8. S3 Versioning, Replication and Lifecycle

Definitions

- Versioning: Maintains multiple versions of an object.
- CRR: Cross-Region Replication, replicating objects between buckets in different Regions.
- SRR: Same-Region Replication, replicating objects within one Region.
- Lifecycle Rule: Automates object transitions or expiration.
- Storage Class: A storage option based on access frequency, performance and cost.

Important S3 storage classes

| Storage class              | Primary use                             |
| -------------------------- | --------------------------------------- |
| S3 Standard                | Frequently accessed data                |
| Intelligent-Tiering        | Changing or unknown access patterns     |
| Standard-IA                | Infrequently accessed data              |
| One Zone-IA                | Infrequently accessed, recreatable data |
| Glacier Instant Retrieval  | Archive with millisecond retrieval      |
| Glacier Flexible Retrieval | Archive with flexible retrieval times   |
| Glacier Deep Archive       | Long-term, rarely accessed archives     |

Points to remember

- Versioning protects against accidental overwrites and helps recover deleted objects.
- CRR requires versioning on source and destination buckets.
- Lifecycle rules help optimize storage costs.
- Archived objects may require restoration before they can be accessed.
- Replication is not a replacement for a complete backup strategy.

## 9. Amazon RDS and MySQL

Definitions

- Database: An organized collection of data.
- RDBMS: Relational Database Management System.
- RDS: Relational Database Service, a managed database service.
- MySQL: A relational database management system.
- SQL: Structured Query Language.
- Primary Key: A column or set of columns uniquely identifying each row.
- Multi-AZ: A deployment configuration supporting high availability.

Points to remember

- RDS supports engines such as MySQL, PostgreSQL, MariaDB, Oracle and SQL Server.
- MySQL default port: 3306.
- AWS manages many database infrastructure tasks in RDS.
- Multi-AZ is primarily for high availability.
- Read Replicas help scale read workloads.
- SQL `CREATE TABLE` creates a table.
- SQL `INSERT INTO` inserts records.
- SQL `SELECT` retrieves data.

## 10. AWS IAM

Definitions

- IAM: Identity and Access Management, used to control access to AWS resources.
- IAM User: An identity representing a person or workload in an AWS account.
- IAM Group: A collection of IAM users.
- IAM Role: An identity with permissions that can be assumed temporarily.
- IAM Policy: A JSON document defining permissions.
- MFA: Multi-Factor Authentication.
- Root User: The original account identity with unrestricted account-level access.

Points to remember

- IAM is a global service.
- IAM policies commonly use `Effect`, `Action` and `Resource`.
- Explicit Deny overrides Allow.
- Access is implicitly denied unless allowed by applicable policies.
- Apply the principle of least privilege.
- Enable MFA for the root user and human users.
- IAM roles commonly provide temporary credentials.
- Avoid using root credentials for everyday administration.

## 11. CloudWatch and CloudTrail

Definitions

- CloudWatch: AWS monitoring and observability service for metrics, logs, alarms and more.
- CloudTrail: Records AWS account activity and API events.
- Metric: A time-series measurement.
- Alarm: Monitors a metric or expression and changes state based on configured conditions.
- Trail: A CloudTrail configuration delivering events to storage or analysis destinations.

| CloudWatch                          | CloudTrail                              |
| ----------------------------------- | --------------------------------------- |
| Monitors metrics and logs           | Records API and account activity        |
| Supports alarms                     | Supports auditing                       |
| Helps identify performance problems | Helps investigate who performed actions |
| Example: CPU utilization            | Example: `RunInstances` API event       |

Points to remember

- CloudWatch is commonly used for operational monitoring.
- CloudTrail is commonly used for auditing and security investigation.
- CloudWatch alarms can trigger SNS notifications.
- CloudTrail records management events and can be configured for data events.
- Both services can contribute to security monitoring.

## 12. Amazon VPC and Networking

Definitions

- VPC: Virtual Private Cloud, a logically isolated virtual network in AWS.
- Subnet: A range of IP addresses within a VPC, associated with one AZ.
- Public Subnet: A subnet whose route table has a route to an Internet Gateway.
- Private Subnet: A subnet without a direct route to an Internet Gateway.
- Internet Gateway (IGW): Enables internet connectivity for resources with suitable routes and addresses.
- NAT Gateway: Enables outbound connectivity for private resources without accepting unsolicited inbound internet connections.
- Route Table: A set of rules controlling network traffic routing.
- CIDR: Classless Inter-Domain Routing, a method for expressing IP address ranges.

Points to remember

- VPCs span Availability Zones within one Region.
- Subnets belong to one AZ.
- A public IPv4 address alone does not guarantee internet access.
- Public subnet route example: `0.0.0.0/0 → IGW`.
- Private subnet outbound route example: `0.0.0.0/0 → NAT Gateway`.
- NAT Gateway is commonly placed in a public subnet.
- Route tables determine where packets are forwarded.

## 13. VPC Peering

Definitions

- VPC Peering: A private network connection between two VPCs.
- Peering Requester: The VPC initiating a peering request.
- Peering Accepter: The VPC accepting the request.
- Non-Transitive Routing: Traffic cannot automatically pass through one peered VPC to reach another.

Points to remember

- VPC Peering supports same-Region and cross-Region connectivity.
- Peered VPCs cannot have overlapping IPv4 CIDR ranges.
- Route tables must include appropriate routes.
- Security Groups and NACLs must allow the traffic.
- VPC Peering does not support transitive routing.

## 14. CIDR, NACL and Security Groups

Definitions

- Security Group: A stateful virtual firewall controlling traffic at the network interface level.
- NACL: Network Access Control List, a stateless firewall controlling subnet traffic.
- CIDR Notation: An IP network address followed by a prefix length, such as `10.0.0.0/24`.
- Ephemeral Port: A temporary port used by a client connection.

| Feature        | Security Group                                | NACL                         |
| -------------- | --------------------------------------------- | ---------------------------- |
| State          | Stateful                                      | Stateless                    |
| Level          | Network interface                             | Subnet                       |
| Rules          | Allow only                                    | Allow and Deny               |
| Evaluation     | All applicable rules                          | Ascending rule number        |
| Return traffic | Automatically allowed for tracked connections | Must be explicitly permitted |

Points to remember

- `/24` represents 256 IPv4 addresses.
- `/16` represents 65,536 IPv4 addresses.
- AWS reserves five IPv4 addresses per subnet.
- `0.0.0.0/0` represents all IPv4 addresses.
- NACL rules are processed in ascending rule-number order.
- A Security Group cannot have an explicit Deny rule.
- NACLs require appropriate inbound and outbound rules.

## 15. Amazon Route 53

Definitions

- Route 53: AWS DNS web service supporting domain registration, DNS routing and health checks.
- DNS: Domain Name System, translates domain names into records such as IP addresses.
- A Record: Maps a hostname to an IPv4 address.
- AAAA Record: Maps a hostname to an IPv6 address.
- CNAME: Maps one hostname to another hostname.
- Alias Record: Route 53-specific record that can point to supported AWS resources.
- TTL: Time To Live, controls DNS caching duration.

Points to remember

- Route 53 supports domain registration.
- Route 53 supports public and private hosted zones.
- An A record can point to an EC2 public IPv4 address.
- An Alias record can point to an ALB.
- CNAME records cannot be created at the zone apex.
- Routing policies include Simple, Weighted, Latency, Failover and Geolocation.

## 16. AWS CloudFormation and Lightsail

Definitions

- IaC: Infrastructure as Code, managing infrastructure through configuration files.
- CloudFormation: AWS service for provisioning infrastructure using templates.
- Template: JSON or YAML document describing infrastructure.
- Stack: A collection of AWS resources managed as one CloudFormation unit.
- Change Set: A preview of proposed stack changes.
- Lightsail: A simplified AWS service offering virtual servers and related resources.

Points to remember

- CloudFormation templates can be written in YAML or JSON.
- Common sections include `Parameters`, `Resources` and `Outputs`.
- `Resources` is the main section defining infrastructure.
- CloudFormation can create EC2 instances, S3 buckets and other supported resources.
- CloudFormation supports stack updates and rollback behavior.
- Lightsail is useful for simpler website and application deployments.

## 17. Amazon DynamoDB

Definitions

- DynamoDB: A fully managed, serverless NoSQL database service.
- Table: A collection of items.
- Item: A collection of attributes.
- Attribute: An individual data element.
- Partition Key: A key attribute used to determine data placement.
- Sort Key: An optional key attribute used with a partition key.
- On-Demand Capacity: Capacity mode that automatically accommodates workload demand.

Points to remember

- DynamoDB is a NoSQL database.
- DynamoDB does not require fixed schemas for non-key attributes.
- Every item must have a primary key.
- Primary keys can be simple or composite.
- DynamoDB supports low-latency reads and writes.
- DynamoDB supports both on-demand and provisioned capacity modes.

## 18. AWS Lambda

Definitions

- Lambda: A serverless compute service that runs code in response to events or invocations.
- Function: Code and configuration deployed to Lambda.
- Trigger: An event source or configuration that invokes a function.
- Execution Role: An IAM role granting the function permissions to AWS resources.
- Timeout: Maximum duration allowed for a function invocation.
- Cold Start: Initialization work needed when a new execution environment starts.

Points to remember

- Lambda does not require users to manage servers.
- Lambda supports runtimes including Python, Node.js and Java.
- Maximum function execution duration is 15 minutes.
- Lambda can integrate with S3, API Gateway, EventBridge and DynamoDB.
- Lambda pricing commonly depends on requests and execution resource usage.
- Lambda is suited to event-driven applications.

## 19. AWS Elastic Beanstalk

Definitions

- Elastic Beanstalk: A managed service for deploying and operating web applications.
- Application: A logical collection of application versions and environments.
- Environment: A deployment of an application version onto AWS resources.
- Environment Cloning: Creates a new environment using an existing environment's configuration.
- CNAME Swap: Exchanges environment URLs between two Elastic Beanstalk environments.

Points to remember

- Elastic Beanstalk simplifies application deployment.
- It provisions and manages supporting AWS resources.
- It supports platforms such as Java, Python, Node.js and .NET.
- Environment cloning is useful for testing and migration.
- CNAME swapping can support blue-green deployment strategies.
- Users retain responsibility for application code and relevant AWS resource costs.

## Quick Revision: AWS Important Ports

| Service              | Port | Protocol |
| -------------------- | ---- | -------- |
| SSH                  | 22   | TCP      |
| RDP                  | 3389 | TCP      |
| HTTP                 | 80   | TCP      |
| HTTPS                | 443  | TCP      |
| MySQL                | 3306 | TCP      |
| PostgreSQL           | 5432 | TCP      |
| DNS                  | 53   | UDP/TCP  |
| Microsoft SQL Server | 1433 | TCP      |

## 15 Most Important Exam Points

1. EC2 provides virtual servers.
2. S3 provides object storage.
3. EBS provides block storage.
4. RDS provides managed relational databases.
5. DynamoDB provides managed NoSQL databases.
6. IAM controls identities and permissions.
7. VPC provides logically isolated networking.
8. Security Groups are stateful.
9. NACLs are stateless.
10. ALB operates at Layer 7.
11. Auto Scaling adjusts EC2 capacity.
12. CloudWatch monitors metrics, logs and alarms.
13. CloudTrail records AWS API and account activity.
14. Route 53 provides DNS services.
15. CloudFormation automates infrastructure provisioning.

