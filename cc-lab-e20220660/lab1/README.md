# Cloud Lab 1 — Amazon EC2

- **Student name:** Keo Chanponlork
- **Student ID:** e20220660
- **Learner Lab user name:** voclabs/user5619537=KEO_CHANPONLORK
- **Date completed:** 2026-10-22

---

## Part 1.1 — An Amazon EC2 Walkthrough

### 1. Security group

![Security group](images/01-security-group.png)

I created `aws-bootstrap-security-group` with two inbound rules: SSH on port 22 and HTTP on port 80.

### 2. Key pair

![Key pair](images/02-key-pair.png)

I created the RSA key pair `aws-bootstrap-key-pair` in `.pem` format to log in to the instance over SSH.

### 3. Instance details

![Instance details](images/03-instance-details.png)

The instance `aws-bootstrap-instance` is a `t2.micro` and is _Running_, with public IP `54.80.103.242`.

### 4. Browser test

![Browser test](images/04-browser-test.png)

Opening `http://54.80.103.242` in the browser shows the _Hello World from Educative_ page from the web server.

### 5. SSH connection

![SSH connection](images/05-ssh-connection.png)

I connected from my Mac terminal with SSH. `whoami` shows `ec2-user` and `hostname` shows `ip-172-31-46-251.ec2.internal`.

---

## Part 1.2 — Set Up an EC2 Web Solution (Challenge)

### 6. Challenge launch

![Challenge launch](images/06-challenge-launch.png)

I launched the instance `ec2-challenge-instance` with the Amazon Linux 2023 AMI (64-bit x86), type `t2.micro`, the new key pair `ec2-challenge-key-pair`, and a 10 GiB gp3 root volume.

![Challenge storage](images/06b-challenge-storage.png)

### 7. Challenge security group

![Challenge security group](images/07-challenge-security-group.png)

I created `ec2-challenge-sg` with two inbound rules from Anywhere-IPv4: SSH on port 22 for remote configuration and HTTP on port 80 for web access.

### 8. Challenge instance

![Challenge instance](images/08-challenge-instance.png)

The instance `ec2-challenge-instance` is _Running_, with public IP `54.234.152.20`.

### 9. Challenge terminal

![Challenge terminal](images/09-challenge-terminal.png)

I connected over SSH from my Mac terminal and installed Apache by hand:

    ssh -i ~/.ssh/ec2-challenge-key-pair.pem ec2-user@ec2-54-234-152-20.compute-1.amazonaws.com
    sudo dnf update -y
    sudo dnf install -y httpd
    sudo systemctl start httpd
    sudo systemctl enable httpd
    echo "Welcome to the EC2 Challenge" | sudo tee /var/www/html/index.html
    cat /var/www/html/index.html

### 10. Challenge browser

![Challenge browser](images/10-challenge-browser.png)

Opening `http://54.234.152.20` in the browser shows the _Welcome to the EC2 Challenge_ page.