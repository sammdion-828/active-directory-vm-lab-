# active-directory-vm-lab-
# Active Directory Setup and Configuration on AWS Windows Server
---
## Overview
This guide provides step-by-step instructions to deploy and configure Active Directory Domain Services (AD DS) on a Windows Server virtual machine (VM) hosted in Amazon Web Services (AWS).
---
### Watch Me Build This Lab Here!

---

## Prerequisites
- AWS account with appropriate permissions
- Existing or new Virtual Private Cloud (VPC)
- Security Group allowing RDP (port 3389)
- Key pair for RDP authentication
- Windows Server 2019 or 2022 AMI

---

## Steps

### 1. Launch the Windows Server Instance
1. Sign in to the **AWS Management Console**.
2. Go to **EC2 Dashboard → Instances → Launch Instance**.
   
 ![Screenshot 2025-10-26 144838](https://github.com/user-attachments/assets/b38af19e-d6af-4d56-bb83-f43195f0608e)

3. Choose **Microsoft Windows Server 2022 Base or Higher** AMI.
4. Select an instance type (e.g., `t3.medium` or larger).

 ![Screenshot 2025-10-26 145039](https://github.com/user-attachments/assets/a60ee6e6-0e7b-44c2-9e79-dcbfbe6feb38)
 ![Screenshot 2025-10-26 145428](https://github.com/user-attachments/assets/31479ed5-8a29-4adc-bf93-678446a22813)
 
5. Configure **network settings**:
   - Place the instance in your target VPC and subnet.
   - Enable **Auto-assign Public IP** if accessing over the internet.
6. Attach or create a **key pair** for RDP access.
7. Configure the **security group** to allow:
   - TCP 3389 (RDP) from your IP
  
![Screenshot 2025-10-26 145743](https://github.com/user-attachments/assets/3d43550f-2943-4547-9877-1b9486302a4b)

8. Launch the instance.

![Screenshot 2025-10-26 145851](https://github.com/user-attachments/assets/40075ad0-f5b5-42aa-9b4b-3595ddbf11d5)



### 2. Connect to the Instance via RDP
1. Retrieve the **Administrator password** from the EC2 console.
2. Decrypt the password using your key pair.
3. Use **Remote Desktop Connection** to connect with:
4. Verify network connectivity and Windows setup.

 ---
 ![Connect Using RDP step 6](https://github.com/user-attachments/assets/e9a54699-42c1-46ed-92b1-9a93f70d8265)



![Decrypt Password step 7](https://github.com/user-attachments/assets/dcd1ca72-1ce4-4a7f-8fbd-1a7f9ac40c6b)



![Connect to Machine step 8](https://github.com/user-attachments/assets/92f84ab0-4433-4263-b06d-6f5679c6c0ed)


### 3. Install Active Directory Domain Services (AD DS) 
1. In **Server Manager**, select:
   2. Proceed through the wizard:
- Select **Role-based or feature-based installation**.
- Choose your server.
- Check **Active Directory Domain Services**.
- Add required features and install.

---
![Configure ADDS step 9](https://github.com/user-attachments/assets/54267271-470e-418a-a05e-8f620e0f729e)


![Add roles and features Wizard step 10](https://github.com/user-attachments/assets/af09f24c-5a4b-42f1-9bd9-cac96c2bcd65)


![Add features Screen shot step 11](https://github.com/user-attachments/assets/17c0df69-4dd9-4cf3-aad6-85d672a24bae)


### 4. Promote the Server to a Domain Controller
1. After installation, click the **flag icon** in Server Manager.
2. Select **Promote this server to a domain controller**.
3. Choose:
- **Add a new forest** (if creating a new domain)
- Provide a **Root Domain Name** (e.g., `advmlab.local`)
4. Set a **Directory Services Restore Mode (DSRM)** password.
5. Complete the wizard and restart the server.

---
![Promote to domain controller step 12](https://github.com/user-attachments/assets/df166076-83fb-4398-ae2e-21041ba62c56)


![Domain Name step 13](https://github.com/user-attachments/assets/5f0e6bef-02d6-4a97-9eb0-2e884f94ab86)


![Install SS step 14](https://github.com/user-attachments/assets/e3e6fa8c-559a-4ed2-b252-c83e499fc138)


### 5. Verify AD DS Configuration
1. Log in again after reboot.
2. Open **Server Manager → AD DS** role.
3. Launch **Active Directory Users and Computers (ADUC)**.
4. Confirm your domain name and structure.
5. Create Organizational Units (OUs) and test user accounts.
   
---

### 6. Create Additional Users or Join Other Devices
- Create new users in **Active Directory Users and Computers**
---

## Cleanup (Optional)
If testing only, terminate your EC2 instance to avoid charges.

---



