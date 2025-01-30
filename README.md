# My Experience with DevOps Stage 0 - NGINX Configuration

## Introduction

As part of the DevOps Stage 0 task, I was required to set up and configure NGINX on a fresh Ubuntu server. This experience helped me gain hands-on skills in web server setup, configuration, and deployment.

## Approach to Completing the Task

To complete this task, I followed these steps:

1. **Provisioned an Ubuntu Server** – I used a virtual machine to create a fresh Ubuntu environment.
2. **Installed NGINX** – I ran the following command to install NGINX:
   ```bash
   sudo apt update && sudo apt install nginx -y
   ```
3. **Started and Enabled NGINX** – I ensured that the web server was running with:
   ```bash
   sudo systemctl start nginx
   sudo systemctl enable nginx
   ```
4. **Created a Custom HTML Page** – I modified the default web page at `/var/www/html/index.html` with the required message:
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
       <p>For online documentation and support, please refer to <a href="http://nginx.org/">nginx.org</a>.<br/>
       Commercial support is available at <a href="http://nginx.com/">nginx.com</a>.</p>
       <p><em>Thank you for using NGINX.</em></p>
   </body>
   </html>
   ```
5. **Configured NGINX to Listen on Port 80** – Initially, it was running on port 8080. I modified the configuration file (`/etc/nginx/sites-available/default`) to ensure it listens on port 80:
   ```nginx
   server {
       listen 80 default_server;
       listen [::]:80 default_server;
       root /var/www/html;
       index index.html;
       server_name _;

       location / {
           try_files $uri $uri/ =404;
       }
   }
   ```
   After making changes, I restarted NGINX:
   ```bash
   sudo systemctl restart nginx
   ```

## Challenges and Solutions

- **Port Issue (Running on 8080 Instead of 80)**: Initially, NGINX was configured to listen on port 8080. To fix this, I modified the configuration file and restarted the service.
- **Firewall Blocking Requests**: I had to allow HTTP traffic using:
  ```bash
  sudo ufw allow 'Nginx Full'
  ```
- **Accessing the Server from a Different Network**: Since I was using a local IP (`192.168.x.x`), I ensured port forwarding was configured properly for external access.

## Final Results

My NGINX server is now successfully running and accessible at [**http://192.168.114.104/**](http://192.168.114.104/).

Here’s a screenshot of the deployed NGINX web page:

![Welcome to DevOps Stage 0 - KingTsonga - Microsoft​ Edge 2025_01_30 13_08_38](https://github.com/user-attachments/assets/176d9617-9c89-4253-95bf-ebd1b84dc210)

## Learning and Professional Growth

This task deepened my understanding of:

- Web server installation and configuration.
- Firewall and networking configurations.
- Practical DevOps skills for setting up infrastructure.

## References

I referenced the following links for guidance:

- [Azure DevOps Engineers](https://hng.tech/hire/azure-devops-engineers)
- [Cloud Engineers](https://hng.tech/hire/cloud-engineers)

This project was a great hands-on experience, reinforcing key DevOps concepts that align with my professional goals in Cloud Security and DevSecOps.

