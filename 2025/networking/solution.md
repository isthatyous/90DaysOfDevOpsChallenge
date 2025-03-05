# 🌐 Open Systems Interconnection (OSI MODEL)

The OSI Model consists of **7 layers**, each serving a specific function in network communication.

## 📌 Layers of the OSI Model

| **Layers**            | **Purpose**                                                                                         | **Protocols** |
|----------------------|-------------------------------------------------------------------------------------------------|--------------|
| **1. Physical Layer** | - Provides transmission medium (wired, wireless) for sending data.  <br> - Handles transmission mode (simplex, duplex, full-duplex).  <br> - Synchronization and data representation (bit level: `0` = low voltage, `1` = high voltage).  <br> - Line configuration (point-to-point, multi-point).  <br> - Defines physical topology (Bus, Star, Ring, Hybrid). | No Protocol Used <br> (Underlying LAN and WAN technology) |
| **2. Data Link Layer** | - Responsible for **node-to-node delivery**.  <br> - Adds **Header & Trailer** to the datagram.  <br> - **Header contains:** MAC address of sender & receiver.  <br> - Provides **physical addressing, flow control, and error control** (Error detection, retransmission, correction). | 
| **3. Network Layer** | - Responsible for **host-to-host delivery**.  <br> - Uses **logical addressing** (IP Address).  <br> - **Header contains:** IP address of sender & receiver.  <br> - Performs **fragmentation** (breaking large packets).  <br> - Handles **routing** (sending packets to final destination). | IP, ARP, RARP, ICMP |
| **4. Transport Layer** | - Responsible for **process-to-process (port-to-port) delivery**.  <br> - **Header contains:** Port address of sender & receiver (which port the app runs on).  <br> - Handles **segmentation & reassembly, flow control, and error control**. | TCP, UDP |
| **5. Session Layer** | - **Manages, maintains, synchronizes, and terminates** communication sessions.  <br> - Implements **checkpointing** to detect errors. | |
| **6. Presentation Layer** | - Handles **encryption, decryption, and compression**.  <br> - Manages **syntax & semantics** of exchanged information. | |
| **7. Application Layer** | - Enables **file transfer, mail transfer, and directory services**. | FTP, DNS, SMTP, POP3 |

---

## 🚀 TASK 1  --> Real-World Examples of Protocols Used in Each Layer

### **Application Layer**
- **HTTP** → Used when browsing the internet (e.g., `https://swe.shivamcodes.me`).
- **SMTP** → Used for sending emails (e.g., Gmail).

### **Presentation Layer**
- **SSL/TLS** → Secure video streaming (Netflix, YouTube).
- **MP4, JPEG** → Compression for media files.
- **UTF-8** → Character encoding.

### **Session Layer**
- **SSH** → Secure remote login.
- **Video Calls** → Maintains active communication sessions.

### **Transport Layer**
- **TCP** → Used in **YouTube video playback, email transfer** (Ensures reliable delivery).
- **UDP** → Used in **live streaming, video calls, online gaming** (Packet loss is acceptable).

### **Network Layer**
- **IP** → Assigns an IP address to your device for internet communication.

### **Data Link Layer**
- **MAC Address** → Used in **Wi-Fi adapters, Ethernet cables** for router communication.

### **Physical Layer**
- **Fiber Optics, Radio Waves** → Transmit data between devices.

---

# 🔥 Protocols and Ports for DevOps

## 📌 Common Network Protocols & Their Port Numbers

| **Protocol** | **Port Number** | **Purpose in DevOps** |
|-------------|--------------|--------------------|
| **HTTP**  | 80  | Used in CI/CD pipelines, webhooks, and testing web applications. |
| **HTTPS** | 443 | Secure communication for cloud deployments (SSL/TLS). |
| **FTP**   | 21  | Transfer application artifacts, logs, and backups. |
| **SSH**   | 22  | Secure remote access, automation with Ansible, secure Git operations. |
| **DNS**   | 53  | Resolving domain names (used in Kubernetes service discovery). |

---

## Task 2  --> 🔥 How These Protocols Help in DevOps

1. **HTTP/HTTPS**
   - Used in **REST API calls** for cloud services (AWS, Azure, Kubernetes).
   - Used in **webhooks** for automated deployments.

2. **FTP**
   - Transfers **logs, backups, configuration files**.
   - Deploys **static files** to web servers.

3. **SSH**
   - Provides **secure remote login** for CI/CD automation.
   - Used in **Ansible, Terraform, and remote scripting**.

4. **DNS**
   - Resolves domain names for distributed services.
   - Used in **Kubernetes service discovery (CoreDNS)**.

---

## 🚀 Why These Protocols Matter in DevOps
These protocols enable **secure, automated, and scalable** workflows, allowing teams to efficiently build, deploy, and monitor applications.

🔗 **Learn More**: [RFC Documentation](https://www.rfc-editor.org/)  
📌 **Follow Best Practices**: Always ensure **secure implementations** (e.g., SSH keys, TLS certificates).  

---

# TASK 3 -->  🔒 How to Create and Configure Security Groups in AWS EC2

## 📌 What is a Security Group?
A **Security Group** in AWS acts as a **virtual firewall** that controls **inbound and outbound** traffic to EC2 instances.

---

## 🚀 Step-by-Step Guide to Create and Configure Security Groups

### **Step 1: Launch an AWS EC2 Instance**
1. Log in to **AWS Management Console**.
2. Navigate to **EC2** from the AWS **Services** menu.
3. Click on **Launch Instance** → Select **Amazon Linux 2 AMI (Free Tier eligible)**.
4. Choose **Instance Type: `t2.micro` (Free Tier eligible)**.
5. Click **Next: Configure Security Group**.

---

### **Step 2: Create a New Security Group**
1. Select **Create a new security group**.
2. Give it a **name** (e.g., `my-security-group`).
3. Add a **description** (e.g., "Allow SSH and HTTP access").

---

### **Step 3: Configure Inbound Rules**
**Inbound rules** define what traffic is **allowed** to reach your EC2 instance.

| **Type**  | **Protocol** | **Port Range** | **Source** | **Purpose** |
|-----------|------------|--------------|---------|-------------|
| **SSH**   | TCP       | 22           | `My IP` | Secure remote access (Only allow your IP) |
| **HTTP**  | TCP       | 80           | `Anywhere (0.0.0.0/0)` | Allow public web traffic |
| **HTTPS** | TCP       | 443          | `Anywhere (0.0.0.0/0)` | Secure web access |

💡 **Tip**: Avoid allowing **SSH (22) from Anywhere (0.0.0.0/0)** for security reasons. Use **My IP** or a VPN.

---

### **Step 4: Configure Outbound Rules**
Outbound rules define what traffic your instance **can send**.

| **Type**  | **Protocol** | **Port Range** | **Destination** | **Purpose** |
|-----------|------------|--------------|--------------|-------------|
| **All Traffic** | All | All | Anywhere (0.0.0.0/0) | Allow all outbound traffic |

---

### **Step 5: Attach Security Group to EC2 Instance**
1. Go to **EC2 Dashboard** → **Instances**.
2. Select your **running instance**.
3. Click **Actions** → **Networking** → **Change Security Groups**.
4. Select the newly created **Security Group** → Click **Assign Security Groups**.

---

## 🔒 Best Practices for Security Groups
✔ **Follow the Principle of Least Privilege** – Only open necessary ports.  
✔ **Restrict SSH Access** – Avoid `0.0.0.0/0`, use `My IP`.  
✔ **Use Separate Security Groups** for different workloads (e.g., web, database).  
✔ **Enable CloudTrail** for logging security group changes.  

---

## 🎯 Conclusion
Security Groups play a **crucial role** in protecting AWS infrastructure by controlling network access.

🚀 **Next Steps**: Implement **IAM roles, VPC security, and AWS WAF** for enhanced security.

🔗 **Learn More**: [AWS Security Groups Documentation](https://docs.aws.amazon.com/vpc/latest/userguide/VPC_SecurityGroups.html)





















































































































































































































































































                                            
                                       
