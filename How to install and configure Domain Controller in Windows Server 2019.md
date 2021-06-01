### Pre-requisites:

1. VM or Physical Server with Windows Server 2019 installed
2. Assign a static IP address to the server that we promote as Domain Controller.
3. As we'll configure Active Directory-integrated DNS, therefore change the DNS settings in the network interface and set the same server IP address as the primary DNS server.


### Assign static IP address to the server and set it also as the primary DNS(Domain Name System) server

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

5. In the Server Roles tab, put tick mark for **Active Directory Domain Services** (select the **DNS Server** role as well, as we will configure AD integrated DNS server. If not selected, during installation it will automatically select and install the DNS Role). 

    Then, it will prompt to show you the associated features for the role. Click on **Add Features** to add those. Then click **Next** to continue. 

 <img width="786" alt="image" src="https://user-images.githubusercontent.com/56558508/118217168-7deaa580-b4a7-11eb-9076-d5b1ae66411b.png">

6. In the **Features** tab, the basic features for this required role are already selected by default. Click **Next** to install continue.
7. In the next window, it gives brief information about **Active Directory Domain Services** service. Click **Next** to proceed.
8. In the **Confirmation** tab,  verify the selections and click on the **Install** button. You may or may not select the option **Restart the destination server automatically if required**. It is always a best practice to restart the server post installation.
9. Once done, it will start the installation process and you can check the same in the **Results** tab. Then click **Close**.

10. Restart VM.
11. Open again the **Server MAnager** and click the Notification flag icon to the upper right and click **Promote the server into a Domain Controller**

<img width="896" alt="image" src="https://user-images.githubusercontent.com/56558508/118217995-21888580-b4a9-11eb-9b4c-37bc2ade6139.png">

12. **Active Directory Configuration Wizard**. Now, from the Deployment Configuration tab, select **Add a new forest**. Provide a Root Domain name, here it is **adtest.fnxlabs.com**. Then, click on **Next** to continue.

<img width="759" alt="image" src="https://user-images.githubusercontent.com/56558508/118218632-71b41780-b4aa-11eb-82a2-6a04468a560c.png">

13. In the **Domain Controller Option** tab, select a **Forest functional level** and a **Domain functional level** as per your environment. 
Since this is the first domain controller in the forest, please select the **DNS Server (as we are configure AD integrated DNS)** and the **Global Catalog (GC)** check boxes. 
    Then, enter the **Active Directory Restore Mode (DSRM)** password, this is used to retrieve/restore Active Directory data. Then, click **Next** to continue
    
    <img width="762" alt="image" src="https://user-images.githubusercontent.com/56558508/118219469-1aaf4200-b4ac-11eb-96f9-73753e55f9cd.png">
    
    <img width="765" alt="image" src="https://user-images.githubusercontent.com/56558508/118219499-30246c00-b4ac-11eb-9508-6d85ac10cdc7.png">

14. Since we have configured AD integrated DNS Server, you can ignore the DNS Delegation warning as shown in the below screen. Then, click **Next** to continue.

<img width="763" alt="image" src="https://user-images.githubusercontent.com/56558508/118219573-5b0ec000-b4ac-11eb-9c08-b97600b8405c.png">

15. In the **Additional Options** tab, enter a NetBIOS name for your domain. It is suggested to keep the NetBIOS name same as the root domain name (by default, it will fetch the domain name only). Then, click **Next** to continue.

<img width="763" alt="image" src="https://user-images.githubusercontent.com/56558508/118219721-a32de280-b4ac-11eb-830d-70ba06dacea6.png">

16. In the **Path** tab, you have to mention the **Database (NTDS Database), LOG files and SYSVOL** folders path. You can change the default path as per your organization security policies. Now, click **Next** to continue.

<img width="762" alt="image" src="https://user-images.githubusercontent.com/56558508/118219804-ceb0cd00-b4ac-11eb-951f-183cfe24937c.png">

17. In the **Review Options** tab,  you will review the configuration. If everything is as per your need, you can click Next to proceed or otherwise you can go back and change the required setting as per your need and then proceed further.

<img width="761" alt="image" src="https://user-images.githubusercontent.com/56558508/118219850-e5efba80-b4ac-11eb-8690-b2ced4fe63ac.png">

18. In the Prerequisites Check tab,  it will do prerequisite check. 
    Once prerequisite checks completed successfully, it will enable/highlight the **Install** option. Then, click on Install button to start the installation process. 
    
<img width="763" alt="image" src="https://user-images.githubusercontent.com/56558508/118220068-5565aa00-b4ad-11eb-9dcb-6b2ae8b010dc.png">

19. Once installation completed successfully, you will get the below confirmation message. Close this window and restart the Server. 

<img width="761" alt="image" src="https://user-images.githubusercontent.com/56558508/118220235-c60cc680-b4ad-11eb-8958-50812c260505.png">

20. Login and verify the health of the Domain controller. You can also verify the settings/configurations from the **Active Directory tools like Active Directory Users and Computers** or **Active Directory Domains and Trusts**, etc. You will get all the Active Directory tools in the folder named **Administrative Tools** on the Start menu.

<img width="744" alt="image" src="https://user-images.githubusercontent.com/56558508/118717382-94eb1800-b858-11eb-8207-35e698f9768f.png">


### To test if you were able to connect to that AD server ###
- To search LDAP using the admin account
```ldapsearch -x -h <ldap_host> -b <search_base> -D <bind_dn> -w <password>```
```
ldapsearch -x -h adtest.fnxlabs.com -b "dc=adtest,dc=fnxlabs,dc=com" -D "CN=Jane Doe,CN=Users,DC=adtest,DC=fnxlabs,DC=com" -w Password~1
```
<img width="1334" alt="image" src="https://user-images.githubusercontent.com/56558508/118719643-4d19c000-b85b-11eb-9bd4-94770ab0ab26.png">
<img width="142" alt="image" src="https://user-images.githubusercontent.com/56558508/118719073-961d4480-b85a-11eb-8d7f-8774a002c9ee.png">

- To search LDAP using the admin account with objectclass for a narrowed result
```ldapsearch -x -h <ldap_host> -b <search_base> -D <bind_dn> -w <password> "(object_type)=(object_value) <optional_attributes>"```

```
ldapsearch -x -h adtest.fnxlabs.com -b "dc=adtest,dc=fnxlabs,dc=com" -D "CN=Jane Doe,CN=Users,DC=adtest,DC=fnxlabs,DC=com" -w Password~1 "(&(objectClass=user)(objectCategory=Person))" cn
```

<img width="1660" alt="image" src="https://user-images.githubusercontent.com/56558508/118718259-9bc65a80-b859-11eb-90f8-0434f5465211.png">

- To search LDAP using the admin account with conditions
```ldapsearch -x -h <ldap_host> -b <search_base> -D <bind_dn> -w <password> "(object_type)=(object_value) <optional_attributes>"```

```
ldapsearch -x -h adtest.fnxlabs.com -b "dc=adtest,dc=fnxlabs,dc=com" -D "CN=Jane Doe,CN=Users,DC=adtest,DC=fnxlabs,DC=com" -w Password~1 "(&(objectClass=user)(objectCategory=Person)(!(userAccountControl:1.2.840.113556.1.4.803:=2))(sAMAccountName=jdoe)(primaryGroupID=513))" cn
```

<img width="1687" alt="image" src="https://user-images.githubusercontent.com/56558508/118720182-e1842280-b85b-11eb-900c-dc07ad5c0db7.png">


```
ldapsearch -x -h adtest.fnxlabs.com -b "dc=adtest,dc=fnxlabs,dc=com" -D "CN=Jane Doe,CN=Users,DC=adtest,DC=fnxlabs,DC=com" -w Password~1 "(&(objectClass=user)(objectCategory=Person)(!(userAccountControl:1.2.840.113556.1.4.803:=2))(primaryGroupID=513))" cn
```

<img width="1769" alt="image" src="https://user-images.githubusercontent.com/56558508/118720271-011b4b00-b85c-11eb-96b2-fbea52f2cd5e.png">



### Important Notes ###
Issues might occur along the way and these links was a great help.
- https://docs.microsoft.com/en-us/answers/questions/180365/0x2407-can39t-connect-to-ad-domain-computer-rdp.html
- https://www.wintips.org/fix-specified-domain-either-does-not-exist-or-could-not-be-contacted/#

### cheatsheets
- https://devconnected.com/how-to-search-ldap-using-ldapsearch-examples/






