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

| **Protocol** | **Port Number** | **Purpose in DevOps** |
|-------------|--------------|--------------------|
| **HTTP**  | 80  | Used in CI/CD pipelines, webhooks, and testing web applications. |
| **HTTPS** | 443 | Secure communication for cloud deployments (SSL/TLS). |
| **FTP**   | 21  | Transfer application artifacts, logs, and backups. |
| **SSH**   | 22  | Secure remote access, automation with Ansible, secure Git operations. |
| **DNS**   | 53  | Resolving domain names (used in Kubernetes service discovery). |

---

## TASK 2  --> 🔥 How These Protocols Help in DevOps

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

                                                                                                                                                                                                                                    
# TASK 4 --> 🚀 Essential Networking Commands for DevOps Engineers  

---

## 📌 Networking Commands and Their Use Cases  

| Command   | Description  | Scenario When these command are Used by DevOps Engineers |
|-----------|-------------|-----------------------------------------|
| **ping**  | The `ping` command checks the connectivity between two network devices by sending ICMP Echo Request packets and waiting for ICMP Echo Reply responses.  | ✔️ **Checking Server Availability**: Before deploying or troubleshooting, ensure a server is online and reachable. <br> ✔️ **Diagnosing Network Issues**: If an application is slow or unreachable, use `ping` to check latency & packet loss. <br> ✔️ **Domain Resolution Check**: If a website isn't loading, check if the domain resolves to an IP. <br> ✔️ **Automated Health Checks**: Automate health checks in CI/CD scripts to verify server reachability before deployments. |
| **traceroute / tracert**  | The `traceroute` (Linux/macOS) or `tracert` (Windows) command maps the path that packets take from your machine to a destination by showing all the routers (hops) in between.  | ✔️ **Network Latency Analysis**: If an application is slow, use `traceroute` to find where the delay occurs. <br> ✔️ **Debugging Routing Issues**: If a website or service is unreachable, check if packets are being blocked or misrouted. <br> ✔️ **Packet Drop Analysis**: If `* * *` appears in the output, that hop is dropping packets (firewall or dead route). |
| **netstat**  | The `netstat` (Network Statistics) command monitors network connections, displaying active ports, routing tables, and network statistics. It helps identify open ports, running services, and network-related issues.  | ✔️ **Check Active Network Connections**: List all active TCP and UDP connections. <br> ✔️ **Port Monitoring**: Check which ports your system is listening on. <br> ✔️ **Service Availability**: Verify if a specific service is running on port 80. <br> ✔️ **Find Process Using a Port (Linux)**: Identify which process (PID) is using a specific port. |
| **dig / nslookup**  | The `dig` (Domain Information Groper) and `nslookup` commands query DNS (Domain Name System) records, helping resolve domain names to IP addresses and retrieve detailed DNS information.  | ✔️ **Find IP Address of a Domain**: Helps verify if a domain is resolving correctly. <br> ✔️ **Check Specific DNS Records**: Fetch `A`, `MX`, `CNAME`, or `NS` records. <br> ✔️ **Troubleshoot DNS Issues**: Verify domain configurations and propagation. |
| **curl**  | The `curl` (Client URL) command is used to transfer data between a client and a server using various protocols like HTTP, HTTPS, FTP, SCP, and SFTP. It is commonly used for testing API endpoints, downloading files, and troubleshooting network connections.  | ✔️ **Testing API Endpoints**: Make HTTP requests to verify API responses. <br> ✔️ **Downloading Files**: Retrieve files from a URL using `curl`. <br> ✔️ **Checking Response Headers**: Inspect headers for debugging and security analysis. |

---
















































































































































































































































































                                            
                                       
