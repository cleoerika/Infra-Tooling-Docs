### Pre-requisites:

1. VM or Physical Server with Windows Server 2019 installed
2. Assign a static IP address to the server that we promote as Domain Controller.
3. As we'll configure Active Directory-integrated DNS, therefore change the DNS settings in the network interface and set the same server IP address as the primary DNS server.


### Install Active Directory Domain Services (ADDS)
1. Log into Windows Server 2019. Open **Server Manager** → click on **Dashboard** → click on **Add roles and features**

<img width="1322" alt="Server Manager" src="https://user-images.githubusercontent.com/56558508/118134334-632b1900-b434-11eb-9be2-ecceb942b07f.png">

2. **Before you begin** tab contains some important informations. Please go through it  and click **Next**.
3. **Installation Type** tab choose **Role-based or Feature-based installation** and click on **Next** button.
4. In the **Server Selection** tab, select the destination server on which the role will be install. Please verify the hostname and the IP address points of the selected server. Click **Next** to continue.

<img width="784" alt="re Add Roles and Features Wizard" src="https://user-images.githubusercontent.com/56558508/118136190-6cb58080-b436-11eb-94ed-89bf349102d4.png">


6. 
