Documenting My Experience with Setting Up NGINX on Ubuntu
As an aspiring Cloud Security Engineer, I embarked on an essential task of setting up NGINX on a fresh Ubuntu server during my internship. This task was part of my DevOps training and provided me with valuable hands-on experience. It allowed me to deepen my understanding of web server configuration, troubleshooting, and network management—skills that are essential in cloud security and DevSecOps.

Approach to Completing the Task
My task began by installing the NGINX web server on a clean Ubuntu virtual machine (VM). The installation process was straightforward, and I used the following commands to update the package lists and install NGINX:

bash
Copy
Edit
sudo apt update
sudo apt install nginx
After successfully installing NGINX, I ensured that the service was up and running. I used systemctl commands to start NGINX and set it to auto-start on boot. Once the service was running, I accessed the default page by navigating to http://<your-server-ip>, which confirmed that NGINX was successfully installed and configured.

The next step was to personalize the default page to display a custom message. I edited the index.html file in the /var/www/html/ directory, replacing the default content with a message that read:

"Welcome to DevOps Stage 0 - Phangasasa Muhlaba/HexHaven"

This task allowed me to familiarize myself with basic NGINX configurations, specifically serving static HTML files. I gained a deeper understanding of the role of NGINX in web services, which is foundational to DevOps and cloud security.

Challenges Faced and Solutions Implemented
During this task, I faced several challenges that required me to dig deeper into Ubuntu's system management and NGINX configurations:

Firewall Configuration Issues:
Initially, I couldn’t access the web page from my host machine. After some troubleshooting, I realized that the firewall on the Ubuntu VM was blocking incoming HTTP traffic. I resolved this by configuring the firewall to allow HTTP traffic on port 80 with the following command:

bash
Copy
Edit
sudo ufw allow 80/tcp
Port Forwarding:
Since the VM was hosted on a local network, I had to set up port forwarding to make the NGINX server accessible externally. After configuring the network settings in VirtualBox to forward traffic on port 80 to my VM, I tested the setup and successfully accessed the server from my host machine.

NGINX Configuration to Listen on Port 80:
By default, NGINX was configured to listen on port 8080, but for this task, I needed it to listen on the standard HTTP port, 80. To achieve this, I edited the NGINX configuration file located at /etc/nginx/sites-available/default, changing the listen directive to:

nginx
Copy
Edit
listen 80;
After saving the changes and restarting NGINX, the server was accessible on port 80 as expected.

Personal Growth and Learning from the Task
This task significantly contributed to my personal growth and understanding of key technical concepts:

Web Server Management: Configuring NGINX provided hands-on experience with web server administration. I gained insights into how NGINX serves static content, manages incoming requests, and handles network traffic. These skills will be crucial as I progress in my studies and career as a Cloud Security Engineer.

Understanding DevOps Workflows: The task helped me understand how web services are deployed and managed in DevOps environments. I learned how essential tasks like configuration management, security, and monitoring are intertwined in a DevOps pipeline.

Networking and Firewall Configuration: The task deepened my knowledge of networking, especially in setting up proper firewall rules and port forwarding. This experience will serve as a solid foundation for my future work in securing cloud environments and ensuring that web servers are safely accessible from external networks.

Screenshot of Deployed NGINX Server
Here is a screenshot of the deployed NGINX server displaying my custom HTML page:
![NGINX Server Screenshot](https://drive.google.com/uc?export=view&id=1Svt2dWJlkGFKvN0e5iwwjpNpgOJbt8RC)



Conclusion
Successfully completing this task was not just about configuring a web server, but also about understanding the bigger picture of how DevOps practices, web services, and security are interrelated. It provided me with real-world insights into managing and troubleshooting web servers, tasks I will certainly encounter throughout my career.

As I continue to develop my skills in cloud security and DevSecOps, this experience will undoubtedly contribute to my professional growth. Moreover, understanding the role of web servers in the broader DevOps pipeline has reinforced my goal of becoming a Cloud Security Architect.

For anyone looking to dive deeper into DevOps, web server management, and automation, starting with tasks like these is invaluable. It provides the technical foundation required for more complex roles. If you're interested in pursuing a career in DevOps or cloud engineering, roles like DevOps Engineers or Azure DevOps Engineers might be an excellent fit for you.
