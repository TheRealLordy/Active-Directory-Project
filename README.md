# Active Directory VM Project

This project demonstrates the setup and configuration of an Active Directory (AD) environment using Windows Server and VirtualBox. The lab simulates a basic network with a Domain Controller (DC), DHCP, NAT, and a client machine.

---

## 🛠️ Project Overview

- Setting up a Windows Server VM in VirtualBox as a Domain Controller.
- Configuring DHCP and NAT for internal network management.
- Adding a Windows 10 client to the domain.

---

## 📜 Step-by-Step Implementation

### 1. **Windows Server Installation and Network Configuration**

- Installed a Windows Server VM in VirtualBox.
- Configured two **Network Interface Cards (NICs):**
  - **NIC 1 (NAT):** Connects to the host machine's internet.
  - **NIC 2 (Internal Network):** Connects to the private network where the client VM will communicate.
- Assigned a static IP address to the internal NIC for managing the private network.

![Network Diagram](https://github.com/user-attachments/assets/51b7d854-123f-44b7-a344-707aa2a12493)


---

### 2. **Installing Active Directory Domain Services (AD DS)**

#### What is AD DS?

Active Directory Domain Services (AD DS) is a Microsoft service that provides centralized authentication, authorization, and directory management in a networked environment.
![AD-DS Install](https://github.com/user-attachments/assets/f9a49be0-146c-4225-8f7b-8778d6334f31)

#### Installation Steps

- Used **Server Manager** to install the AD DS Role.
- Promoted the server as a **Domain Controller (DC)** by creating a new forest.
  - **Forest:** A collection of one or more domains sharing a common schema and configuration.

#### Domain Creation

- Assigned a custom domain name during the promotion process.
- Verified that the login screen now displays **[Domain Name]\Administrator**.

![MyDomainloginpage](https://github.com/user-attachments/assets/842fd4b1-527e-48a0-954e-dd947c71093c)



---

### 3. **Configuring Organizational Units (OUs)**

#### What is an Organizational Unit (OU)?

An **OU (Organizational Unit)** is a container within Active Directory used to group users, groups, and computers for easier management and application of group policies.

#### Steps Taken

- Opened **Active Directory Users and Computers**.
- Created a new OU named **"ADMINS"** to store admin accounts and other users.
- Created a custom admin user and added it to the **Domain Admins** group.
- 
![UserAdminset](https://github.com/user-attachments/assets/293ecc75-7ec2-4c04-995d-7259bc0c25fc)

#### Verification

- Verified that the new admin account works by logging in with it.




---

### 4. **Setting Up Remote Access Services (RAS) and NAT**

#### Purpose of RAS and NAT

- **RAS (Remote Access Service):** Allows users to connect to private networks securely.
- **NAT (Network Address Translation):** Enables devices in the private network to access the internet.

#### Installation Steps

![Installing-RAS](https://github.com/user-attachments/assets/35b44c26-79fb-4c4c-a0fc-0fceecbd6cbf)

- Added the **Remote Access Role** via **Server Manager**.
- Configured **Routing and Remote Access** to set up NAT.




---

### 5. **Installing and Configuring DHCP**

#### What is DHCP?

**Dynamic Host Configuration Protocol (DHCP)** is a service that automatically assigns IP addresses and other network configuration parameters to devices in a network.

#### Configuration Steps

- Installed the **DHCP Role** using **Server Manager**.
- Configured a DHCP scope:
  - **IP Range:** 172.16.0.100 - 172.16.0.200
  - **Subnet Mask:** 255.255.255.0 (/24)

![DHCS ConfigPic](https://github.com/user-attachments/assets/a7da8615-5e9a-4f32-9cfd-9279f2350c6a)

---

### 6. **Automating User Account Creation**

#### Generating User Accounts

- Used a custom script to generate multiple user accounts with random names and a common password for lab purposes.

![RunningSCriptToCreateUsers](https://github.com/user-attachments/assets/326ee757-2cd1-42f0-b47d-e4dbcda61638)

---

### 7. **Adding a Windows 10 Client to the Domain**

#### Steps

- Created a **Windows 10 VM** as a client.
- Configured the client VM to use the **Internal Network NIC**.

#### Verification

- Verified that:
  - The DHCP server assigned the client an IP address.
  - The client successfully joined the domain.
- Confirmed that the client appears in the **Active Directory Users and Computers** tab.

![ClientConnectedIntoAD](https://github.com/user-attachments/assets/0d4207bc-ed4a-4264-98be-899cdeaab788)


---

## ✅ Results

- Successfully configured an Active Directory environment with a Domain Controller, DHCP, and NAT.
- Verified the addition of a Windows 10 client to the domain.
- Automated the creation of user accounts using a script.

This lab demonstrates a functional Active Directory setup that mirrors real-world scenarios for centralized network management.
