# 🚀 AWS EC2 Instance Hosting Guide

This guide explains how to host a website on an AWS EC2 instance step by step.

---

## 🖥️ Steps to Host a Website on AWS EC2

### 1️⃣ Launch an EC2 Instance
1. Log in to your **AWS Management Console**.
2. Go to **EC2** and click **Launch Instance**.
3. Select an Amazon Machine Image (AMI), like **Amazon Linux 2** or **Ubuntu**.
4. Choose an instance type, for example, **t2.micro** for the free tier.
5. Configure the instance settings and click **Next** until you reach the **Review and Launch** section.

### 2️⃣ Review and Launch the Instance
1. Review the details and make sure everything looks good.
2. Click **Launch**.
3. When prompted, create or select a key pair for SSH access to the instance.
4. Download the `.pem` file for SSH access.
5. Click **Launch Instances** to finish.

### 3️⃣ Access Your EC2 Instance
1. Go to the **Instances** page in EC2 and find your instance.
2. Copy the **Public IP address** or **Public DNS**.
3. Use SSH to connect to your instance:
    ```bash
    ssh -i "your-key.pem" ec2-user@your-instance-public-ip
    ```

### 4️⃣ Install Web Server (Apache/Nginx)
1. **Update the package manager:**
    ```bash
    sudo yum update -y
    ```
2. **Install Apache Web Server:**
    ```bash
    sudo yum install httpd -y
    ```
   For Ubuntu or Debian, use:
    ```bash
    sudo apt-get update
    sudo apt-get install apache2 -y
    ```
3. **Start the Apache web server:**
    ```bash
    sudo systemctl start httpd
    sudo systemctl enable httpd
    ```

### 5️⃣ Upload Your Website Files
1. Transfer your website files (e.g., `index.html`, `style.css`, etc.) to the `/var/www/html` directory on the EC2 instance.
2. Use SCP or an FTP client like FileZilla to upload.
    Example command for SCP:
    ```bash
    scp -i "your-key.pem" index.html ec2-user@your-instance-public-ip:/var/www/html/
    ```
3. **Set file permissions:**
    ```bash
    sudo chmod 755 /var/www/html/*
    ```

### 6️⃣ Access Your Website
1. Go to the **Public IP** or **Public DNS** of your EC2 instance in your browser:
    ```bash
    http://your-instance-public-ip
    ```
2. Your website should now be live and accessible!

---

## 📝 Notes
- Ensure your files (like `index.html`) are correctly linked if using CSS, JS, or images.
- Make sure your **Security Group** allows traffic on port 80 (HTTP) for public access.
- For custom domains, you can configure Route 53 or update the DNS settings for your domain.

---

## 🎉 Congratulations!
Your website is now hosted on **AWS EC2** and accessible via the internet. Share the public IP or DNS to showcase your website!

