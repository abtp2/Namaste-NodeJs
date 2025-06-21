
# DevTinder - AWS EC2 Frontend Deployment 🚀  

## 📌 Code Demonstration Links  
🔗 **Backend Repository:** [DevTinder Backend](https://github.com/akshadjaiswal/devTinder-backend)  
🔗 **Frontend Repository:** [DevTinder Frontend](https://github.com/akshadjaiswal/devTinder-frontend)  

---

## 📌 Overview  
The goal is to **deploy the DevTinder frontend on an AWS EC2 instance**, making it publicly accessible. This deployment involves setting up a cloud server, installing necessary dependencies, building the frontend, and configuring Nginx as a web server.  

This ensures the **DevTinder frontend is hosted on a secure, scalable cloud infrastructure**, optimizing performance and availability.  

---

## ✅ Steps Completed  

### **1️⃣ Setting Up AWS Console Account & EC2 Instance**  
- Created an **AWS account** and completed the **sign-up process**.  
- Logged into the **AWS Management Console** and navigated to the **EC2 service**.  
- Selected **Launch Instance** and configured the **new instance**.  
- Named the instance **DevTinder** and selected **Ubuntu** as the OS.  

### **2️⃣ Configuring Key Pair for Secure Login**  
- Created a **Key Pair** for secure authentication.  
- Downloaded the **private key file** and stored it securely.  
- Configured permissions to allow SSH login using the key pair.  

### **3️⃣ Launching the EC2 Instance**  
- Clicked **Launch Instance** to start the new server.  
- Waited for the **instance state to change to "Running"**.  
- Verified the instance health with **2/2 status checks passed**.  

### **4️⃣ Connecting to the EC2 Instance via SSH**  
- Opened a terminal and logged into the instance using the **private key**.  
- Verified the connection and accessed the server successfully.  

### **5️⃣ Installing Node.js on the Server**  
- Checked the local development machine’s **Node.js version**.  
- Installed the same version on the EC2 instance using **package manager**.  
- Verified the installation to ensure Node.js and npm are working correctly.  

### **6️⃣ Cloning DevTinder Repositories on the Server**  
- Installed **Git** and cloned the **DevTinder Frontend & Backend** repositories.  
- Navigated into the frontend project directory for further setup.  

### **7️⃣ Installing Dependencies & Building the Frontend**  
- Installed all required **npm packages** for the frontend project.  
- Built the frontend project for **production use**.  
- Verified that the **dist folder was generated** after the build process.  

### **8️⃣ Installing & Configuring Nginx**  
- Installed **Nginx**, a web server to serve the frontend files.  
- Started the Nginx service and ensured it runs automatically on system reboot.  
- Checked the **default Nginx page** to verify the server is active.  

### **9️⃣ Deploying the Frontend on Nginx**  
- Removed the default Nginx files and replaced them with the **built frontend files**.  
- Copied the **dist folder contents** into the Nginx web directory.  
- Restarted Nginx to apply the changes and ensure the frontend is being served correctly.  

### **🔟 Enabling Port 80 for Public Access**  
- Navigated to **AWS Security Groups** to configure inbound rules.  
- Allowed **HTTP traffic on port 80** to make the frontend publicly accessible.  
- Verified deployment by accessing the **public IP address of the instance**.  

---

## 🖥️ Required Commands 
 
### **1️⃣ Connect to AWS EC2 via SSH**

Ensure you have your AWS key pair (`your-key.pem`) and connect to your EC2 instance using the following command:

```
ssh -i your-key.pem ubuntu@your-ec2-public-ip
```
----------

### **2️⃣ Install Node.js (Matching Local Version)**

To install Node.js (matching the version on your local development machine), run:

```
curl -fsSL https://deb.nodesource.com/setup_20.x | sudo -E bash -
sudo apt-get install -y nodejs
```

Verify installation:

```
node -v
npm -v
```
----------

### **3️⃣ Clone DevTinder Frontend & Backend Repositories**

Navigate to your home directory and clone both repositories:

```
git clone https://github.com/akshadjaiswal/devTinder-frontend.git
git clone https://github.com/akshadjaiswal/devTinder-backend.git
cd devTinder-frontend
```
----------

### **4️⃣ Install Dependencies & Build the Frontend**

Once inside the frontend directory, install dependencies and build the project:

```
npm install
npm run build
```
This will generate the production build inside the `dist` folder.

----------

### **5️⃣ Install & Start Nginx**

Install and start the Nginx web server:

```
sudo apt update
sudo apt install nginx -y
sudo systemctl start nginx
sudo systemctl enable nginx
```
----------

### **6️⃣ Deploy Frontend to Nginx Web Directory**

Replace the default Nginx web directory with your built frontend:

```
sudo scp -r dist/* /var/www/html/
sudo systemctl restart nginx
```
----------

### **7️⃣ Enable Port 80 in AWS Security Group**

To allow HTTP traffic, update your security group settings:

1.  Navigate to **AWS Console > EC2 > Security Groups**.  
2.  Edit inbound rules and add a rule:   
    -   **Type**: HTTP   
    -   **Port**: 80
    -   **Source**: Anywhere (0.0.0.0/0)      
3.  Save changes and refresh your EC2 instance.

Your frontend should now be accessible via your EC2 public IP.

## 🎯 **Next Steps**

-   **Deploy the Backend on AWS**: Set up the backend and database.  
-   **Enable HTTPS with SSL**: Install and configure an SSL certificate for secure connections.
-   **Optimize Nginx for Performance**: Improve caching, compression, and response times.
-   **Set Up a Custom Domain**: Use AWS Route 53 to assign a custom domain.
-   **Monitor & Scale**: Configure AWS monitoring tools and auto-scaling for handling high traffic.
    
----------

## 🔥 **Conclusion**

The DevTinder frontend is now successfully deployed on AWS EC2 using Nginx. The application is publicly accessible via the EC2 instance’s public IP. Further improvements such as backend deployment, SSL, and custom domain setup will follow to enhance performance and security. 🚀

----------