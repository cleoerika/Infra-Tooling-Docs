### Pre-requisites:

1. VM or Physical Server with Windows Server 2019 installed
2. Assign a static IP address to the server that we promote as Domain Controller.
3. As we'll configure Active Directory-integrated DNS, therefore change the DNS settings in the network interface and set the same server IP address as the primary DNS server.


### Assign static IP address to the server and set it also as the primary DNS server

1. Open command prompt and run this command
```ipconfig /all```
2. Take note of the IP Address

<img width="645" alt="image" src="https://user-images.githubusercontent.com/56558508/118185138-c2a61a80-b46e-11eb-88b0-ecfef9ed2974.png">

3. Go to **Control Panel** in the Windows start menu. Under Control Panel, click **Network and Internet** and then click on **Network and Sharing Center**.

    Under **Network and Sharing Center** click on **Change Adapter Settings** on left side pane. It will open the list of attached network adapters on your   system.

    On **Ethernet**, make a right click and click on **Properties** to open settings for that particular adapter.
  
  <img width="362" alt="image" src="https://user-images.githubusercontent.com/56558508/118185786-832bfe00-b46f-11eb-9b56-3a3acd0f5ff2.png">

4. Select **Internet Protocol Version 4 (TCP/IPv4)** and click on **Properties**
5. Select the radio button **Use the following IP address** and put the IP address we noted down in Step #2
   Also select the radio button **Use the following DNS server addresses** and put the address of the DNS resolver servers we obtained from Step #3.
  
  <img width="402" alt="image" src="https://user-images.githubusercontent.com/56558508/118215853-f734c900-b4a4-11eb-973f-4a6c83f97d04.png">
  
6. Click **OK** button to save the configuration.



### Install Active Directory Domain Services (ADDS)
1. Log into Windows Server 2019. Open **Server Manager** → click on **Dashboard** → click on **Add roles and features**

<img width="1322" alt="Server Manager" src="https://user-images.githubusercontent.com/56558508/118134334-632b1900-b434-11eb-9be2-ecceb942b07f.png">

2. **Before you begin** tab contains some important informations. Please go through it  and click **Next**.
3. **Installation Type** tab choose **Role-based or Feature-based installation** and click on **Next** button.
4. In the **Server Selection** tab, select the destination server on which the role will be install. Please verify the hostname and the IP address points of the selected server. Click **Next** to continue.

<img width="784" alt="re Add Roles and Features Wizard" src="https://user-images.githubusercontent.com/56558508/118136190-6cb58080-b436-11eb-94ed-89bf349102d4.png">


6. 
