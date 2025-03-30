# Active-Directory-Infrastructure-Preparation

![image](https://github.com/user-attachments/assets/e2d78ecf-468d-4d2b-8fc4-d839bf116ed9)

<h2>Discription </h2>

In this project we will lay the ground work or infrastructure foundation which will allow us to use Active Directory.

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Computer)
- Remote Desktop

<h2>Operating Systems Used </h2>

- Windows 10</b> (21H2)
- Windows Server 2022 Azure Edition

<h2>Project Steps</h2>
 
1. Create Resource Group

Create -> Select Resource Group -> Enter Name -> Select Region -> Review and Create

![image](https://github.com/user-attachments/assets/febd0e4b-a93c-43bd-b2ac-607ccca1e6f9)

![image](https://github.com/user-attachments/assets/88707e6c-e92b-4d18-8e10-03a821ad1cc5)

2. Create Virtual Network (VNet)

Create -> Put in Resource Group (previously created) -> Enter Vnet Name -> Select Region (same as Resource Group) -> Review and Create

![image](https://github.com/user-attachments/assets/90ef332b-2f4a-4b4d-87f2-cffd371d5f70)
![image](https://github.com/user-attachments/assets/56d133ca-eb8e-4a8a-a6b8-2fbe271aa1d2)

3. Create first Virtual Machine (Vm) Domain Controller

Create -> Put in Resource Group (previously created) -> Enter (Vm) Name "Domain Controller" -> Select Region (same as before) -> Select Image: Windows Server 2022 "Azure Edition" -> *Note* Size: Standard, 2vcpus, 8 gib memory -> Username/Password -> Check "License" -> Next to Disk -> Next to Networking -> Select VNet (previously created) -> Review and Create -> Create

![image](https://github.com/user-attachments/assets/2a35ed8e-6a20-4c96-ae27-b66adc62011d)
![image](https://github.com/user-attachments/assets/08a4a036-29c7-481b-adf0-4fd73865bea3)
![image](https://github.com/user-attachments/assets/165d994c-cbc5-4de7-9f3f-d68ff45cc1a3)
![image](https://github.com/user-attachments/assets/abd135ec-03f8-4803-824a-6c4be8ac801d)
![image](https://github.com/user-attachments/assets/cab15a85-a856-494d-bb3a-bf23712b3193)

4. Create Second Virtual Machine (Vm) Client-1

Create -> Put in Resource Group (previously created) -> Enter (Vm) Name "Client-1" -> Select Region (same as before) -> Select Image: Windows 10 Pro Version 22H2 -> *Note* Size: Standard, 2vcpus, 8 gib memory -> Username/Password -> Check "License" -> Next to Disk -> Next to Networking-> Select VNet (previously created) -> Review and Create -> Create

![image](https://github.com/user-attachments/assets/311db171-7a28-4cb6-ad1e-aad2e1057df5)

5. Modify Dc-1 Ip Settings

Go to Vm in Azure -> Dc-1 -> Networking -> Network settings -> Virtual Nic Card -> "ipconfig" -> Choose Static -> Save
  
6. Login to Dc-1
  
Go to Vm in Azure -> Dc-1 -> Public Ip Address -> Remote Desktop -> Enter Username/Password
  
7. Modify Dc-1 Firewall
  
Rt click Start -> Run -> Type "wf.msc" -> Enter -> Windows Defender Firewall Properties -> Public Profile tab -> Firewall State Switch to "Off" -> Private Profile tab -> Firewall State Switch to "Off" -> Domain Profile tab -> Firewall State Switch to "Off" -> Apply -> Ok

8. Modify Client-1 Ip settings (Change to Dc-1 private Ip address)

Go to Vm in Azure -> Dc-1 -> Copy Private Ip Address -> Go to Vm in Azure -> Client-1 -> Networking -> Network settings -> Virtual Nic Card -> DNS Server -> Select Custom -> Paste/Enter Dc-1 Privet Ip Address -> Save
  
9. Reset Client-1

Go to Vm in Azure -> Client-1 -> Restart

10. Login to client-1

Go to Vm in Azure -> Client-1 -> Public Ip address -> Remote Desktop -> Enter Username/Password
   
11. Ping Dc-1 from client-1

Client-1 -> Search bar -> Type "Powereshell" -> Run -> Type "ping paste/enter Dc-1 public Ip address" -> Enter
   
If the ping succeds there will be a reply and timeout. If the ping didn't go through them a reply and "Destination host Unreactable" is displayed. This means that the Domain Controller's Windows Firewall is still running.

12. Check client-1 Ip Address Changed

Client-1 -> Powereshell -> Type "ipconfig /all" -> Enter

The data results will disply Dc-1's Private Ip address for Client-1's Private Ip address.

Congratulations on successfully setting up the infrastructure for the cnotinuing labs to deploy and use Active Directory.
  
   
   

   
