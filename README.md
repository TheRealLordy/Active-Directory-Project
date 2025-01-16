Active Directory VM Project

This project demonstrates the setup and configuration of an Active Directory (AD) environment using Windows Server and VirtualBox. The lab simulates a basic network with a Domain Controller (DC), DHCP, NAT, and a client machine.
Network Diagram

1. Windows Server Installation and Network Configuration

    Installed a Windows Server VM in VirtualBox.

    Configured two Network Interface Cards (NICs) for the VM:
        NIC 1 (NAT): Connects to the host machine's internet.
        NIC 2 (Internal Network): Connects to the private network where the client VM will communicate.

    Assigned a static IP address to the internal NIC for managing the private network.

2. Installing Active Directory Domain Services (AD DS)
What is AD DS?

Active Directory Domain Services (AD DS) is a Microsoft service that provides centralized authentication, authorization, and directory management in a networked environment.
Installation Steps

    Used Server Manager to install the AD DS Role.
    Promoted the server as a Domain Controller (DC) by creating a new forest.
        Forest: A collection of one or more domains sharing a common schema and configuration.

Domain Creation

    Assigned a custom domain name during the promotion process.
    Verified that the login screen now displays [Domain Name]\Administrator.

3. Configuring Organizational Units (OUs)
What is an Organizational Unit (OU)?

An OU (Organizational Unit) is a container within Active Directory used to group users, groups, and computers for easier management and application of group policies.
Steps Taken

    Opened Active Directory Users and Computers.
    Created a new OU named "ADMINS" to store admin accounts and other users.
    Created a custom admin user and added it to the Domain Admins group.

    Verified that the new admin account works by logging in with it.

4. Setting Up Remote Access Services (RAS) and NAT
Purpose of RAS and NAT

    RAS (Remote Access Service): Allows users to connect to private networks securely.
    NAT (Network Address Translation): Enables devices in the private network to access the internet.

Installation Steps

    Added the Remote Access Role via Server Manager.
    Configured Routing and Remote Access to set up NAT.

5. Installing and Configuring DHCP
What is DHCP?

Dynamic Host Configuration Protocol (DHCP) is a service that automatically assigns IP addresses and other network configuration parameters to devices in a network.
Configuration Steps

    Installed the DHCP Role using Server Manager.
    Configured a DHCP scope:
        IP Range: 172.16.0.100 - 172.16.0.200
        Subnet Mask: 255.255.255.0 (/24)

6. Automating User Account Creation
Generating User Accounts

    Used a custom script to generate multiple user accounts with random names and a common password for lab purposes.

7. Adding a Windows 10 Client to the Domain
Steps

    Created a Windows 10 VM as a client.
    Configured the client VM to use the Internal Network NIC.
    Verified that:
        The DHCP server assigned the client an IP address.
        The client successfully joined the domain.

Results

    Confirmed that the client appears in the Active Directory Users and Computers tab.
