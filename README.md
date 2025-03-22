# Active-Directory-Installation-and-Infrastructure-Preparation

1. Create Resource Group
   - Create -> Select Resource Group -> enter Name -> select region -> review and Create

2. Create Virtual Network (VNet)
   - Create -> Put in Resource Group (previously created) -> Enter Vnet Name -> Select Region (same as Resource Group) -> Review and Create

3. Create first Virtual Machine (Vm) Domain Controooller
   - Create -> Put in Resource Group (previously created) -> Enter (Vm) Name "Domain Controller" -> select region (same as before) -> select Image: Windows Server 2022 "Azure Edition" -> *Note* Size: Standard, 2vcpus, 8 gib memory -> Username/Password -> check "License" -> Next to Disk -> Next to 
   Networking -> Select VNet (previously created) -> Review and Create -> Create

4. Create Second Virtual Machine (Vm) Client-1
   - Create -> Put in Resource Group (previously created) -> Enter (Vm) Name "Client-1" -> select region (same as before) -> select Image: Windows 10 Pro version 22H2 -> *Note* Size: Standard, 2vcpus, 8 gib memory -> Username/Password -> check "License" -> Next to Disk -> Next to Networking
     -> Select VNet (previously created) -> Review and Create -> Create

5. Modify Dc-1 Ip settings
   - Go to Vm in Azure -> Dc-1 -> Networking -> Network settings -> Virtual Nic Card -> "ipconfig" -> Choose Static -> Save
  
6. Login to Dc-1
    - Go to Vm in Azure -> Dc-1 -> Public Ip address -> Remote Desktop -> Enter Username/Password
  
7. Modify Dc-1 Firewall
   - Rt click Start -> Run -> Type "wf.msc" -> Enter -> Windows Defender Firewall Properties -> Public Profile tab -> Firewall State Switch to "Off" -> Private Profile tab -> Firewall State Switch to "Off" -> Domain Profile tab -> Firewall State Switch to "Off" -> Apply -> Ok

8. Modify Client-1 Ip settings (Change to Dc-1 private Ip address)
    - Go to Vm in Azure -> Dc-1 -> Copy Private Ip address -> Go to Vm in Azure -> Client-1 -> Networking -> Network settings -> Virtual Nic Card -> DNS server -> Select Custom -> Paste/Enter Dc-1 Privet Ip address -> Save
  
9. Reset Client-1
   - Go to Vm in Azure -> Client-1 -> Restart

10. Login to client-1
    - Go to Vm in Azure -> Client-1 -> Public Ip address -> Remote Desktop -> Enter Username/Password
   
11. Ping Dc-1 from client-1
    - Client-1 -> Search bar -> Type "Powereshell" -> Run -> Type "ping paste/enter Dc-1 public Ip address" -> Enter
   
If the ping succeds there will be a reply and timeout. If the ping didn't go through them a reply and "Destination host   Unreactable," this means that the Domain Controller's Windows Firewall is still running.

12. 
  
   
   

   
