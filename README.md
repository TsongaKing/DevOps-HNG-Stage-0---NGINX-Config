# Deploying a Static Web Page with NGINX on an Azure Virtual Machine

## Introduction
As part of the HNG DevOps Stage 0 project, I deployed a simple static webpage using NGINX on an Azure Virtual Machine (VM). This task involved installing and configuring NGINX, serving a custom HTML page, and ensuring accessibility through a public IP. This blog post documents my approach, challenges faced, and key takeaways from the experience.

## Approach to Completing the Task

### 1. Setting Up the Virtual Machine
Since I am focusing on Azure for my cloud security journey, I decided to use an Azure Virtual Machine for this project. I launched a **Linux-based VM (Ubuntu 24.04.1 LTS - Live Server, AMD64)** and configured its network settings to allow HTTP traffic on port 80.

### 2. Installing NGINX
Once the VM was up and running, I accessed it via SSH and installed NGINX using the following commands:

```bash
sudo apt update
sudo apt install nginx -y
```

After installation, I verified that NGINX was running using:

```bash
sudo systemctl status nginx
```

If it wasn’t running, I started it with:

```bash
sudo systemctl start nginx
```

### 3. Creating a Custom HTML Page
To customize the default NGINX page, I created an `index.html` file inside the web root directory (`/var/www/html/`):

```bash
echo "Welcome to DevOps Stage 0 - Phangasasa Muhlaba / HexHaven" | sudo tee /var/www/html/index.html
```

For a more styled page, I replaced the content with a custom HTML file:

```html
<!DOCTYPE html>
<html>
<head>
    <title>Welcome to DevOps Stage 0</title>
    <style>
        html { color-scheme: light dark; }
        body { width: 35em; margin: 0 auto;
               font-family: Tahoma, Verdana, Arial, sans-serif;
               text-align: center; }
        h1 { color: #007BFF; }
    </style>
</head>
<body>
    <h1>Welcome to DevOps Stage 0 - Phangasasa Muhlaba / HexHaven</h1>
    <p>If you see this page, the NGINX web server is successfully installed and working. Further configuration is required.</p>
</body>
</html>
```

After saving the file, I restarted NGINX:

```bash
sudo systemctl restart nginx
```

### 4. Accessing the Web Page
With NGINX running, I accessed my webpage by entering the public IP address of my VM into a browser:

```bash
http://<your-server-ip>/
```

If the page did not load initially, I ensured that:
- The firewall allowed traffic on port 80:
  ```bash
  sudo ufw allow 'Nginx HTTP'
  ```
- The NGINX service was active and error-free:
  ```bash
  sudo systemctl status nginx
  ```

### 5. Screenshot of the Deployed Web Page
To visually confirm the successful deployment of the static webpage, here's a screenshot of the page accessed through the public IP of my Azure Virtual Machine:

![Welcome to DevOps Stage 0](https://github.com/user-attachments/assets/b566752f-1e98-471e-bbdc-87ce551a5733)

## Challenges Faced and Solutions

### 1. Firewall Blocking HTTP Requests
Initially, I couldn’t access my page via the browser. I resolved this by updating **Azure’s Network Security Group (NSG)** to allow inbound HTTP traffic on port 80.

### 2. NGINX Not Serving the New Page
After updating `index.html`, the old page persisted. Clearing the browser cache and restarting NGINX solved this issue.

### 3. Permission Issues
At one point, I encountered permission errors while modifying `/var/www/html/`. Using `sudo` resolved this.

## Learning Outcomes and Professional Growth
This task provided hands-on experience in:
- Deploying web services using NGINX
- Managing cloud-based Azure Virtual Machines
- Debugging network and server issues

These skills align with my goal of becoming a **Cloud Security Engineer** and strengthen my foundation for roles such as **Azure DevOps Engineer** or **Site Reliability Engineer**.

## Conclusion
This project reinforced my understanding of web server deployment and cloud infrastructure. Overcoming real-world challenges improved my troubleshooting skills and deepened my appreciation for DevOps practices. I look forward to more advanced projects integrating **CI/CD and security best practices** into cloud deployments.

📌 **References:**
- Azure DevOps Engineers
- Site Reliability Engineers

