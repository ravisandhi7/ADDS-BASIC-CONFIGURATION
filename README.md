

# Active Directory Lab Setup


## 📌 Project Overview


This project demonstrates a complete basic Active Directory Domain Services (AD DS) lab setup using Windows Server and Windows client machines.


The lab includes:


- Active Directory Domain Services (AD DS)


- DHCP Server Configuration


- Domain Join


- Active Directory User Creation


- Additional Domain Controller (ADC)


- Active Directory Replication



# 🖥️ Lab Environment


| Device | Role | IP Address |


|---|---|---|


| ROOTDC | Primary Domain Controller | Server1 | 10.0.0.1 |


| ADC | Additional Domain Controller | Server2 | 10.0.0.2 |


| PC1 | Domain Client | DHCP |


| Domain Name | AD Domain | ravikumar.online |


# ⚙️ Step 1 — Install Active Directory Domain Services


## On ROOTDC


Open:


Server Manager


### Install Roles


- Active Directory Domain Services


### Promote Server to Domain Controller


Select:


Add a new forest


### Domain Name


ravikumar.online


Set:


- DSRM Password

  
- Restart after installation


## 🌐 Step 2 — Configure Static IP Address


## ROOTDC Configuration


IP Address : 10.0.0.1


Subnet Mask: 255.0.0.0


# 💻 Step 3 — Join Client PC to Domain


## Join Domain

Open:


System Properties > Change Settings > Change


Select:


- Domain
  

Enter:


ravikumar.online


Provide domain administrator credentials.


Restart PC after successful join.


# 📡 Step 4 — Configure DHCP Server


## Install DHCP Role

Open:


Add Roles and Features


Install:


- DHCP Server


## Create DHCP Scope


Start IP   : 10.0.0.150


End IP     : 10.0.0.165


Subnet     : 255.0.0.0


Domain Name: ravikumar.online


Authorize DHCP after installation.


![IPCONFIG](screenshots/dhcp/SCOPE_FOR_DHCP.png)


![IPCONFIG](screenshots/dhcp/IP_RELEASED_TO_PC1.png)


![IPCONFIG](screenshots/dhcp/PING_AFTER_DHCP_IP.png)


![IPCONFIG](screenshots/dhcp/RESERVED_IP_TO_PC1.png)


# 👥 Step 5 — Create Active Directory Users


Open:


Server Manager > Tools > Active Directory Users and Computers


![IPCONFIG](screenshots/users/USER_CREATED_IN_ROOTDC.png)


# 🏢 Step 6 — Create Additional Domain Controller (ADC)


## Configure ADC Static IP


IP Address : 10.0.0.2


Subnet Mask: 255.0.0.0


## Join ADC to Domain


ravikumar.online


Restart the server.


# 🔄 Step 7 — Promote ADC to Domain Controller

Install:


- Active Directory Domain Services


Select:


Add a domain controller to an existing domain


![IPCONFIG](screenshots/adc_to_rootdc/SERVER2_IN_WORKGROUP.png)


![IPCONFIG](screenshots/adc_to_rootdc/ADDING_SERVER2_TO_ROOTDC.png)


![IPCONFIG](screenshots/adc_to_rootdc/USERNAME_AND_PASSWORD_FOR_ADDING_ADC_TO_ROOTDC.png)


![IPCONFIG](screenshots/adc_to_rootdc/ENTERING_DSRM_PASSWORD.png)


![IPCONFIG](screenshots/adc_to_rootdc/REPLICATION_FROM_SERVER1_TO_SERVER2.png)


![IPCONFIG](screenshots/adc_to_rootdc/LOCATION_OF_NTDS_SYSVOL.png)


![IPCONFIG](screenshots/adc_to_rootdc/PREREQUISITE_CHECK_PASS.png)


![IPCONFIG](screenshots/adc_to_rootdc/SERVER2_ADDED_TO_DOMAIN.png)


Domain:


ravikumar.online


Enable:


- DNS Server

  
- Global Catalog (GC)


Restart after promotion.


# ✅ Step 8 — Verify Replication


## Check Replication Summary


repadmin /replsummary


![IPCONFIG](screenshots/replication/USER_CREATED_IN_ADC.png)


![IPCONFIG](screenshots/replication/USER2-REPLICATED_TO_ROOTDC.png)


## Force Replication


repadmin /syncall /AdeP


## Verify Domain Controllers


Get-ADDomainController -Filter *


Expected:


- ROOTDC

- ADC
 

# 🛠️ Useful Commands


## Check IP Configuration


ipconfig /all


## Verify DNS


nslookup ravikumar.online


## Test Connectivity


ping 10.0.0.160


## Force Group Policy Update


gpupdate /force


# 📚 Features Implemented


- Active Directory Domain Services
- DNS Server
- DHCP Server
- Domain Join
- Active Directory Users
- Additional Domain Controller
- Active Directory Replication
- Centralized Authentication


# 📖 Technologies Used

- Windows Server
- Active Directory
- DHCP
- PowerShell
- VirtualBox
  

# 👨‍💻 Author

Ravi Kumar

Windows Server & Active Directory Lab Project
