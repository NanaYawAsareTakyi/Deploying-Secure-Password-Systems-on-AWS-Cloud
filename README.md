# Deploying-Secure-Password-Systems-on-AWS-Cloud
This project involves hosting a password manager on AWS Cloud with SSL configuration to ensure secure and scalable password management.

## Objective

To securely deploy a password manager on AWS Cloud, implementing SSL for encrypted communications, thereby enhancing the security and scalability of password management within the organization.

## Skills learned

 #### Cloud Computing:
   - Setting up and managing services on AWS Cloud.
   - Configuring and managing virtual machines on AWS.

#### Security:
   - Implementing SSL/TLS encryption for secure communications.
   - Understanding and applying best practices for cloud security.

#### Web Server Management:
   - Configuring Nginx for SSL.
   - Managing web server settings and security configurations.

#### Password Management:
   - Deploying and configuring a password manager.
   - Understanding the principles of secure password storage and management.

#### Network Configuration:
   - Setting up and managing security groups and firewall rules in AWS.
   - Configuring network settings for secure access.

#### Project Management:
  - Planning and executing a project from start to finish.
- Documenting configurations and procedures for future reference.

  ## Tools used
<img src="https://img.shields.io/badge/-AWS%20EC2-232F3E?&style=for-the-badge&logo=Amazon%20AWS&logoColor=white" />Instance in AWS CLoud used for hosting the password manager.

<img src="https://img.shields.io/badge/-Nginx-009639?&style=for-the-badge&logo=Nginx&logoColor=white" />Web server used for configuring SSL/TLS encryption.

<img src="https://img.shields.io/badge/-Passbolt-339966?&style=for-the-badge&logo=Passbolt&logoColor=white" />Password manager for managing and securely storing passwords.

<img src="https://img.shields.io/badge/-Ubuntu-E95420?&style=for-the-badge&logo=Ubuntu&logoColor=white" />Operating system used for generating keys and managing components such as Nginx and Passbolt.

<img src="https://img.shields.io/badge/-AWS%20Security%20Group-232F3E?&style=for-the-badge&logo=Amazon%20AWS&logoColor=white" />Virtual firewall used for controlling bidirectional traffic of EC2 instance.

<img src="https://img.shields.io/badge/-VirtualBox-183A61?&style=for-the-badge&logo=VirtualBox&logoColor=white" />Virtualization software used to run Ubuntu operating system.

## Workflow

I installed Passbolt on-premises for complete control over the environment and data, opting for the free community version which meets the project's needs effectively without incurring additional costs.

The images below displays these steps:

![image](https://github.com/NanaYawAsareTakyi/Deploying-Secure-Password-Systems-on-AWS-Cloud/assets/173400465/86979ff8-534b-4452-b09b-b0843d7fb324)

![image](https://github.com/NanaYawAsareTakyi/Deploying-Secure-Password-Systems-on-AWS-Cloud/assets/173400465/a3082508-b344-4627-af81-bca6e99611dd)

After selecting these options, I deployed the Passbolt AMI to AWS Cloud.

An AMI or Amazon Machine Image is a template used to create virtual machines or instances in the AWS cloud environment. It includes the operating system, software, configuration, and any necessary data to launch a virtual server instance.

This is illustrated in the image below:

![image](https://github.com/NanaYawAsareTakyi/Deploying-Secure-Password-Systems-on-AWS-Cloud/assets/173400465/c2b8c1cd-86c5-43f5-af01-4ca7bca1cc0b)

Selecting this option redirects to the AWS Marketplace, I chose the option to continue to subscribe.

The image below illustrates this:

![image](https://github.com/NanaYawAsareTakyi/Deploying-Secure-Password-Systems-on-AWS-Cloud/assets/173400465/873c838d-be5b-418f-bffa-cdea4f774fe7)

On the launch page, options to select region as well as software version are provided. After selecting the appropriate configurations I continued to launch.

The image below illustrates this:

![image](https://github.com/NanaYawAsareTakyi/Deploying-Secure-Password-Systems-on-AWS-Cloud/assets/173400465/0991fbb0-52ae-4010-997e-1f5234c5d9a8)

On the next page, I left most of the configurations to default and only created a new security group and key pair.

The image below illustrates this:

![image](https://github.com/NanaYawAsareTakyi/Deploying-Secure-Password-Systems-on-AWS-Cloud/assets/173400465/51b4c09c-1b5b-4323-996b-155ef0dfaae6)

The security group acts as a virtual firewall for the EC2 instance to control inbound and outbound traffic. To achieve this I selected the option to create a new security group.
I configured the security group to allow all traffic. I will use HTTP and HTTPS to set up Passbolt later in the project and also open port 22 for SSH to manage the instance, connect to it and complete the setup.

This is illustrated in the image below:

![image](https://github.com/NanaYawAsareTakyi/Deploying-Secure-Password-Systems-on-AWS-Cloud/assets/173400465/6902a9f6-ff54-4d02-a920-5b75dfa2b5f9)


Next, I created a key pair for the EC2 instance. This consists of a private key and a public key used to secure and authenticate access to the instance. I initiated this process by clicking on the option to create a key pair in the EC2 console, which redirected me to the AWS Cloud platform. There, I clicked on the “action” icon and selected “import key pair.”

The image below illustrates this:

![image](https://github.com/NanaYawAsareTakyi/Deploying-Secure-Password-Systems-on-AWS-Cloud/assets/173400465/a38c276c-e0e6-4652-a899-9acf2aff8fba)

![image](https://github.com/NanaYawAsareTakyi/Deploying-Secure-Password-Systems-on-AWS-Cloud/assets/173400465/aef7c96b-b3d8-4b8d-8055-739573471186)

This opened a page where I could input the key name, upload the key pair file, and add tags.
This is illustrated in the image below:

![image](https://github.com/NanaYawAsareTakyi/Deploying-Secure-Password-Systems-on-AWS-Cloud/assets/173400465/68559093-6061-43eb-856a-4444ddecee80)

Before filling in the form, I needed to create the key. I used VirtualBox to create a virtual Ubuntu machine. To generate the keys, I opened the terminal and used the command `ssh-keygen`. I saved the key in the default location and chose to overwrite an existing key. I didn't set a passphrase, simply pressed "enter" on my keyboard, and generated the key.

The image below illustrates this:

![image](https://github.com/NanaYawAsareTakyi/Deploying-Secure-Password-Systems-on-AWS-Cloud/assets/173400465/fd076d6e-7ee0-4e5c-9c4c-8d7146e11228)

To view the key I used the “cat” command and input the location of the key: “cat ~/.ssh/id_rsa.pub”.
This is illustrated in the image below:

![image](https://github.com/NanaYawAsareTakyi/Deploying-Secure-Password-Systems-on-AWS-Cloud/assets/173400465/10c8a653-ca99-49ad-a7f9-cf6e163d40f9)

I then copied the public key and pasted it into the AWS Cloud import key page. Finally, I proceeded to import the key pair.
This is illustrated in the image below:

![image](https://github.com/NanaYawAsareTakyi/Deploying-Secure-Password-Systems-on-AWS-Cloud/assets/173400465/dabaac4d-0831-4c74-966d-075602685b1a)

A new key pair is created.

![image](https://github.com/NanaYawAsareTakyi/Deploying-Secure-Password-Systems-on-AWS-Cloud/assets/173400465/023fb34b-4877-4038-afc5-beae63954e5c)

The next step was to return to the AWS Marketplace Passbolt AMI launch page and launch the instance.
This is illustrated in the image below:

![image](https://github.com/NanaYawAsareTakyi/Deploying-Secure-Password-Systems-on-AWS-Cloud/assets/173400465/b689deae-f23e-466f-8f89-4316aaf4ffb6)

A notification of the successfully launched instance is provided on the page after clicking the launch icon.
This is illustrated below:

![image](https://github.com/NanaYawAsareTakyi/Deploying-Secure-Password-Systems-on-AWS-Cloud/assets/173400465/bc4aeeb6-c84c-4363-82f2-9381d134c99f)

The instance can be viewed in the EC2 console.
This is illustrated below:

![image](https://github.com/NanaYawAsareTakyi/Deploying-Secure-Password-Systems-on-AWS-Cloud/assets/173400465/30a0f92e-4c55-4fb6-b315-3841427e727e)

Having successfully installed Passbolt on the EC2 instance, the next step is to configure it accordingly.
By copying and pasting the IP address of the instance into a web browser, I was directed to the Passbolt web page. I clicked the “Get Started” icon, which took me to the configuration page.
This is illustrated below:

![image](https://github.com/NanaYawAsareTakyi/Deploying-Secure-Password-Systems-on-AWS-Cloud/assets/173400465/d011421b-8924-43ea-bb6e-5150cfeae66e)

The configuration page indicated that the environment and GPG were configured correctly; however, SSL was not enabled. SSL, or Secure Sockets Layer, is a crucial security technology for encrypting data transmitted between a server and a client. This ensures that data exchanged is secure and cannot be intercepted or read by unauthorized parties. Without configuring SSL for the Passbolt password manager, passwords would be sent in plaintext, which is highly insecure.
The image below illustrates this:

![image](https://github.com/NanaYawAsareTakyi/Deploying-Secure-Password-Systems-on-AWS-Cloud/assets/173400465/b6873216-3685-41c1-9578-70cdf72f6e80)

To configure SSL, I required a domain name. For this project, I purchased a domain name from Namecheap, which allowed me to associate the domain name with the IP address of the EC2 instance. I created a new A Record under the advanced DNS settings and input the IP address of the instance, saving the changes I had made.

DNS (Domain Name System) is a hierarchical and decentralized naming system used to translate human-readable domain names into machine-readable IP addresses. An A Record specifically maps a domain name to its corresponding IPv4 address.
This is illustrated below:

![image](https://github.com/NanaYawAsareTakyi/Deploying-Secure-Password-Systems-on-AWS-Cloud/assets/173400465/6e7f7889-1f60-4221-abbc-a1d14f49a668)

Next I set up Nginx for SSL, to do this I connected to the EC2 instance from the Ubuntu VM via ssh.
Nginx is a high-performance web server used for its efficiency, scalability, and security features. In setting up SSL, Nginx handles the encryption and decryption of web traffic efficiently, ensuring secure communication between clients and servers.
To connect to EC2 via ssh I used the command “ssh admin@” and input the IP address of the EC2 instance.
This is illustrated below:

![image](https://github.com/NanaYawAsareTakyi/Deploying-Secure-Password-Systems-on-AWS-Cloud/assets/173400465/8cb2a184-2755-4ef0-96d0-cd98f0e1e1f1)

![image](https://github.com/NanaYawAsareTakyi/Deploying-Secure-Password-Systems-on-AWS-Cloud/assets/173400465/0bc1ed9c-1d6f-43fd-9b05-3d1b26254868)


I opened the Nginx configuration file for Passbolt to make updates by using the command `sudo nano /etc/nginx/sites-enabled/nginx-passbolt.conf`.
This is illustrated below:

![image](https://github.com/NanaYawAsareTakyi/Deploying-Secure-Password-Systems-on-AWS-Cloud/assets/173400465/5044bbbd-1f77-4e2b-8008-6f56072e0a9c)

I updated the Nginx file with the server name of the domain. This step is crucial for correctly handling virtual hosts, ensuring proper request routing, matching SSL certificates with domains, and maintaining security and trust in the web server configuration.
This is illustrated below:

![image](https://github.com/NanaYawAsareTakyi/Deploying-Secure-Password-Systems-on-AWS-Cloud/assets/173400465/1190a5ae-555d-4a51-9b13-ed8ffe2f2728)

To set up SSL, I proceeded by inputting the command `sudo dpkg-reconfigure passbolt-ce-server`.
This is illustrated below:

![image](https://github.com/NanaYawAsareTakyi/Deploying-Secure-Password-Systems-on-AWS-Cloud/assets/173400465/b63c06f3-9135-4bce-8382-5f0d532e22c2)


I followed through with the configuration by selecting "Yes" or "No" based on personal preferences. For SSL key generation, I opted for the "auto" option to automate the process and minimize human error. Additionally, I inputted the domain name and email address to enable notifications about certificate expiry.

This is illustrated below:

![image](https://github.com/NanaYawAsareTakyi/Deploying-Secure-Password-Systems-on-AWS-Cloud/assets/173400465/448f1536-40fe-4436-b0b7-7514b2863e5b)

![image](https://github.com/NanaYawAsareTakyi/Deploying-Secure-Password-Systems-on-AWS-Cloud/assets/173400465/c2ea2395-e32d-47b7-bd13-5d4fd3076032)

![image](https://github.com/NanaYawAsareTakyi/Deploying-Secure-Password-Systems-on-AWS-Cloud/assets/173400465/806858b9-bf98-411d-8291-69cb03a9a06d)

![image](https://github.com/NanaYawAsareTakyi/Deploying-Secure-Password-Systems-on-AWS-Cloud/assets/173400465/17b10fad-e992-4082-8be3-fb42f15276e5)

![image](https://github.com/NanaYawAsareTakyi/Deploying-Secure-Password-Systems-on-AWS-Cloud/assets/173400465/423d3eb0-c3ac-46f8-94b3-66ceeab7eeb6)

At this point, SSL has been successfully enabled for the domain. This ensures secure communication between clients and the Passbolt server, protecting data transmitted over the network from unauthorized access.
This is illustrated below:

![image](https://github.com/NanaYawAsareTakyi/Deploying-Secure-Password-Systems-on-AWS-Cloud/assets/173400465/2a81fd21-2072-46ae-834c-215bd4416691)

![image](https://github.com/NanaYawAsareTakyi/Deploying-Secure-Password-Systems-on-AWS-Cloud/assets/173400465/40dbc374-7ce3-4fa3-9126-080c733c6e39)


I selected the “Start configuration” icon and proceeded to fill out the database configuration form on the next page. This database on the backend stores all necessary data for Passbolt to operate securely and efficiently.

This is illustrated below:

![image](https://github.com/NanaYawAsareTakyi/Deploying-Secure-Password-Systems-on-AWS-Cloud/assets/173400465/99ed2403-d3b8-42da-8f7f-cabb604f19fd)

I set up the SMTP server settings and created my user account as well.
This is illustrated below:

![image](https://github.com/NanaYawAsareTakyi/Deploying-Secure-Password-Systems-on-AWS-Cloud/assets/173400465/b18478d3-c03a-4fc7-81fb-814c23c851f3)

![image](https://github.com/NanaYawAsareTakyi/Deploying-Secure-Password-Systems-on-AWS-Cloud/assets/173400465/e101f74e-841f-42b0-8d72-bab3cfa0d7e0)

![image](https://github.com/NanaYawAsareTakyi/Deploying-Secure-Password-Systems-on-AWS-Cloud/assets/173400465/f15c6278-8f3d-4adc-a471-2f73bcf4db89)

I was redirected to the homepage where I downloaded a Passbolt extension for my browser, ensuring secure password management and access directly from the browser interface.

This is illustrated below:

![image](https://github.com/NanaYawAsareTakyi/Deploying-Secure-Password-Systems-on-AWS-Cloud/assets/173400465/07a4c0b1-6eff-4717-9176-414ef72e7359)

![image](https://github.com/NanaYawAsareTakyi/Deploying-Secure-Password-Systems-on-AWS-Cloud/assets/173400465/ecc6c681-6b3e-4b87-ba2a-25cea6303dc4)

Next, I created a strong security passphrase for the password manager to ensure the confidentiality of all stored passwords. After this step, upon clicking "Next," a recovery kit was automatically downloaded, providing a secure way to recover access to Passbolt in case of emergency or loss of access.
This is illustrated below:

![image](https://github.com/NanaYawAsareTakyi/Deploying-Secure-Password-Systems-on-AWS-Cloud/assets/173400465/c23ab351-0b91-43b0-a8c3-225d875bf897)

![image](https://github.com/NanaYawAsareTakyi/Deploying-Secure-Password-Systems-on-AWS-Cloud/assets/173400465/3b65b8c7-7913-4322-ad1b-e6373ff6318a)

Next, I selected a security token as an alternative authentication factor to enhance account security and protect against phishing attacks.
This is illustrated below:

![image](https://github.com/NanaYawAsareTakyi/Deploying-Secure-Password-Systems-on-AWS-Cloud/assets/173400465/f5bf64ac-4842-4e2d-b158-6ad574a07ead)

And that’s it! I successfully created a password manager hosted on an AWS EC2 instance, configured with SSL encryption for secure data transmission and enhanced account security features like multi-factor authentication.

![image](https://github.com/NanaYawAsareTakyi/Deploying-Secure-Password-Systems-on-AWS-Cloud/assets/173400465/b45c7d27-1ebc-4f98-a805-3145e3d3940c)


## Summary
In this project, Passbolt was hosted on AWS Cloud to securely manage passwords with high availability, reliability, and scalability. HTTPS encryption ensured secure data transmission, while domain hosting was configured for consistent access. The implementation included features for securely storing complex passwords, enhancing both data protection and user convenience, demonstrating a robust approach to modern password management using cloud infrastructure and advanced security practices.
