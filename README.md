# E-commerce Application Deployment on Amazon Linux

## 📌 Overview
This repository provides a fully automated **Bash script** for deploying an **E-commerce web application** on an **Amazon Linux EC2 instance**. The script installs and configures **MariaDB, Apache, and FirewallD**, ensuring a secure and production-ready environment.

## 🚀 Features
- ✅ **Automated Deployment** of a PHP-based E-commerce App
- 🔧 **Installs & Configures MariaDB** for Database Management
- 🌐 **Sets Up Apache Web Server** for Hosting the Application
- 🔒 **Configures FirewallD** for Security (Ports 80 & 3306)
- 📜 **Supports Amazon Linux 2 & Amazon Linux 2023**

---

## 🛠️ Prerequisites
Before running the script, ensure you have:
- **An AWS EC2 instance** running **Amazon Linux 2 or Amazon Linux 2023**
- **SSH access** to the instance via **PuTTY**
- **Sudo/root privileges** on the instance
- **An active internet connection** (to install packages and clone the repository)

---

## 📌 Installation & Setup

### **1️⃣ Launch an Amazon Linux EC2 Instance**
1. Log in to the **AWS Management Console**.
2. Navigate to **EC2 Dashboard** → **Instances** → **Launch Instance**.
3. Choose an **Amazon Linux 2** or **Amazon Linux 2023** AMI.
4. Select an **instance type** (e.g., `t2.micro` for free tier).
5. Configure security groups:
   - **Allow SSH (22)** for remote access.
   - **Allow HTTP (80)** for the web application.
   - **Allow MySQL (3306)** if you need remote database access.
6. Launch the instance and connect using **PuTTY**:
   - Convert your `.pem` key to `.ppk` using PuTTYgen.
   - Open **PuTTY**, enter your EC2 public IP, and use the `.ppk` key for authentication.

---

### **2️⃣ Clone the Repository & Run the Script**
1. **Clone this repository** into your EC2 instance:
   ```bash
   git clone https://github.com/your-repo/ecommerce-deployment.git
   cd ecommerce-deployment
   ```
2. **Give execute permission** to the script:
   ```bash
   chmod +x deploy.sh
   ```
3. **Run the script with sudo privileges:**
   ```bash
   sudo ./deploy.sh
   ```

The script will:
✅ Install and configure **MariaDB**
✅ Set up **FirewallD rules**
✅ Deploy the **Apache web server**
✅ Clone and configure the **E-commerce web application**

---

## ✅ Verification & Testing

### **Check Running Services**
Ensure that **MariaDB, Apache, and FirewallD** are running:
```bash
sudo systemctl status mariadb
sudo systemctl status httpd
sudo systemctl status firewalld
```

### **Verify Database Setup**
Log in to MariaDB and check if the **ecomdb** database exists:
```bash
sudo mysql -e "SHOW DATABASES;"
```
Check if **products** are inserted:
```bash
sudo mysql -e "USE ecomdb; SELECT * FROM products;"
```

### **Verify Firewall Rules**
Ensure **ports 80 and 3306** are open:
```bash
sudo firewall-cmd --list-all
```

### **Verify Web Application**
Open your browser and visit:
```
http://your-ec2-public-ip
```
The **E-commerce application** should be displayed.

---

## ⚠️ Troubleshooting

### **MariaDB fails to install**
- Run `cat /etc/os-release` to check the Amazon Linux version.
- If using **Amazon Linux 2023**, ensure the **MariaDB repository is added** (done in the script).

### **Web application does not load**
- Check if **Apache is running**:
  ```bash
  sudo systemctl restart httpd
  ```
- Check **firewall rules** and ensure port 80 is open.

---

## 📜 License
This project is open-source and available under the **MIT License**.

---

## 💡 Author
Developed by **Taqwa Elsayed Mohammed**

---

## 🤝 Contributing
Feel free to open issues or submit pull requests to improve this script!



![image](https://github.com/user-attachments/assets/0af533a1-4307-41b3-8e2c-9100544aac6e)
![image](https://github.com/user-attachments/assets/12587826-b511-42bc-b50e-24a2b2e5deaa)



