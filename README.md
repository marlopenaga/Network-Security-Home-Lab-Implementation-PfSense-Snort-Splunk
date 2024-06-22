# Network-Security-Home-Lab-Implementation-pfSense-Snort-Splunk
This project demonstrates the setup and configuration of a comprehensive network security solution in VirtualBox. The lab features an Active Directory (AD) domain with 100 users. The primary focus is on implementing and integrating pfSense (Firewall), Snort (IDS/IPS), and Splunk (SIEM) to secure and monitor the network.

### Key Components:

- **pfSense Firewall**: Configured to protect the network perimeter, manage NAT, establish firewall rules, and enable secure VPN connections.
- **Snort IDS/IPS**: Deployed and tuned to monitor network traffic, providing real-time threat detection and automated response to intrusions. Integrated inside pfSense as a package interface with community rules uploaded and enforced. 
- **Splunk SIEM**: Installed and integrated as a Security Information and Event Management (SIEM) solution for centralized log collection, analysis, and correlation, enhancing visibility and improving incident response.
- **Oracle VirtualBox**: The lab is completed and configured inside VirtualBox. Created separate Virtual Machines (VMs) for pfSense & Snort, Splunk (Ubuntu), the Windows Server 2022 Domain Controller (DC), and Windows 10 Enterprise Clent User.

### Active Directory Setup:

- **Domain**: virtualdomain.com
  - **Users**: 100 users simulated to provide realistic network activity and testing scenarios.

### Features:

- **Network Security Policies**: Development and enforcement of comprehensive security policies including access control, traffic filtering, and logging standards.
- **Continuous Monitoring**: Regular analysis of security logs from pfSense, Snort, and Splunk to identify and investigate potential threats.

### Important to Read:

- This will focus on the setup, implementation, and configuration of the security controls on my previous Active Directory HomeLab.
  - Github link: https://github.com/marlopenaga/Active-Directory-Home-Lab-2024
  - My Github link will guide you to the setup and installation of my previous project of setting up an Active Directory in VirtualBox.

### Links:

- **Splunk Download**: https://www.splunk.com/en_us/download.html
- **Ubuntu Linux Download**: https://ubuntu.com/desktop
- **pfSense Download** https://www.pfsense.org/download/

## Network Diagram
- This is an overview of the network diagram we are going to set up and configure.
> As mentioned, for the Active Directory setup please go to my Github and follow the Active Directory Home Lab 2024

![HTH Network Diagram](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/cdfafb7d-a009-4f98-a722-91f77b9a16ad)

## Create a Designated Save Location for the VMs and Files WORK ON IT WITH UPDATED PICTURES

1. Create a new folder called "**AD LAB**" in a location with the most space. Here I created it in my D: drive

![](https://github.com/marlopenaga/Active-Directory-Home-Lab-2024/blob/main/images/AD%20LAB%202.PNG?raw=true)

3. Inside of **AD LAB** create two folders: **AD Lab Files**, **Virtual Machines**

  - **HTH Lab Files** is the location where the VirtualBox, Windows Server 2022 ISO, and Windows 10 Enterprise installation files will be located
  - **Virtual Machines** is the location where we will install our VMs later using VirtualBox, which will be discussed later

![](https://github.com/marlopenaga/Active-Directory-Home-Lab-2024/blob/main/images/AD%20LAB%203.PNG?raw=true)

## Installing pfSense as a Virtual Machine

The current home lab has no security infrastructure at the moment therefore we will implement a firewall first. PfSense is the firewall of choice and will filter out incoming and outgoing data packets from the internet and between devices inside of our internal network in VirtualBox, intranet. The pfSense will also serve as a DHCP server as previously the Domain Controller served as the DHCP server. 

1. Click on the link to download the latest version of **pfSense**. It may ask you to create a free account.
  > *pfSense Download** https://www.pfsense.org/download/

![HTH PFS Setup 1](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/9c134a9c-2f75-494d-99bc-5cb948f94ced)

2. Make sure to download the file in your designated folder for ease of access and organization
3. Extract the zip file, I use **7-Zip** (free to download)

![HTH PFS Setup 2](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/8c85bb57-97fa-43df-8e1c-fb85cf772491)

### Create the pfSense Virtual Machine in VirtualBox

4. Open **Oracle Virtual Machine**, **Select New**

- Name: **pfSense**
- Folder: **Select a folder that has the most space, here I chose my designated Virtual Machines folder**
- ISO Image:  **Select the ISO file in the location we downloaded and extracted from**
  > ""pfSense-plus-installer..."
- Type: **BSD**
- Ver.: **FreeBSD (64-bit)** 

![HTH PFS Setup 3](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/ce8faf32-69a2-4247-bd29-a4192ae57715)

5. For hardware

- Base Memory: **2GB or 2048 MB**
- Processors: **1 CPU**
- Virtual Hard Disk Space: **minimum 10GB but I used 20GB** 

![HTH PFS Setup 4](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/cbb7a510-b928-42b5-ae9a-4858189df811)

6. Now that we have added the VM, go to **Settings** -> **Network**

- Adapter 1: **Bridged Adapter** and select your NIC card 

![HTH PFS Setup 5](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/705db5fe-b3c8-491d-b04c-b7fd295cd55c)

- Adapter 2: **Internal Network** and here I chose my pre-existing internal network: **intranet**

![HTH PFS Setup 6](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/939529f2-f429-45db-b126-c35d7d61c12f)

8. Go to **System Settings**

- **Deselect Floopy**
- **Reorganize** the boot order to **Hard Disk** -> **Optical**
- That is all for the pfSense settings  

![HTH PFS Setup 6 5](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/8f99b59d-6b95-4844-867e-63d5005c3206)

### Boot up and Setup pfSense VM

9. Now boot up the **pfSense VM**

![HTH PFS Setup 7](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/ceca3dbb-d4d9-4d61-ae3b-e1f5f3703580)

10. Click **Accept**

![HTH PFS Setup 8](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/d4fc119c-50c1-47c4-b478-354753b7c99c)

11. **Install pfSense** is highlighted and hit **OK**

![HTH PFS Setup 9](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/cd893cc8-7806-4d1a-b0ae-c9f1525cfce5)

12. Select our **WAN Interface, em0**

- **em0** is our WAN interface, using the bridged adapter to reach the internet
- **em1** is our LAN interface, which will encompass our internal network NIC intranet
- Select OK

![HTH PFS Setup 10](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/5dd37fbd-f1b1-4c28-a855-c63de894a661)

13. Here in the **LAN em1 Network Mode Setup**, and edit the settings to the following

  - IP Address: **172.16.0.2/24**
  - DHCP Range Start: **172.16.0.100**
  - DHCP Range End: **172.16.0.200** 

- This will ensure the pfSense firewall will monitor the client users connected to the network from their IP addresses we set.

![HTH PFS Setup 11](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/e322a623-78a7-4780-9466-973571a4ea10)

14. **Install CE** to start the installation of pfSense

![HTH PFS Setup 12](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/28eb22c0-d782-41cd-b00e-804c1755a640)

15. Select **OK**

![HTH PFS Setup 13](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/73b71fe2-8933-40bd-ad2b-aae4650bcd2f)

16. Select **Yes**

![HTH PFS Setup 14](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/eec749f5-efab-428d-90db-0874818d7896)

17. Select **OK** to get the current Stable release and let it install

![HTH PFS Setup 15](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/4e541e02-39cc-4786-adb9-8c5ec9aab6db)

18. Once you get to the home screen of pfSense, check to see if the **WAN** and **LAN** interfaces are configured correctly. Here the **LAN em1** is not our desired address range

- The pfSense home screen will provide options we can go into to adjust, here press **2** on your keyboard and hit **enter**

![HTH PFS Setup 16](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/07ccf3b4-4bf6-4d5c-a18c-6b59738ac26b)

19. Type in our address for the pfSense: **172.16.0.2**

20. Then we want the subnet mask to be **255.255.255.0** which is equal to **24**. To do so, enter **24** and hit **enter**

21. Next hit **Enter for none:** for the "enter the new LAN IPv$ upstream gateway address."

22. Press **n**, to not configure "the IPv6 address"

23. Again, hit **Enter for none:** to not enter a "new LAN IPv6 address"

24. Press **y** to **enable DCHP server on LAN**

25. Now enter our desired "IPv4 client address ranges": **172.16.0.100 & 172.16.0.200**

26. Last, press **n** to not "revert to HTTP as the webConfigurator protocol"

![HTH PFS Setup 17](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/cee7cd6b-1618-4e25-8ef0-b0700d7a7508)

27. pfSense will now apply the new settings and we have our new **IPv4 LAN address set to 172.16.0.2/24** to access the pfSense web interface to make further changes later on; the new URL is: **https://172.16.0.2/**

![HTH PFS Setup 18](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/93675a09-6fff-4955-ba94-b6f0dde15744)

28. Great, now when we hit **continue** the pfSense is set to our configurations and matches the network diagram.
  > Note that later on we will deactivate **IPv6 for WAN** as this homelab will use IPv4 addresses

![HTH PFS Setup 19](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/c41a8df1-eb27-4fce-90f5-0309796dce67)

### Setting Up and Configuring the pfSense Web Interface from our Domain Controller VM 

29. Next, we can boot up the Domain Controller (DC) VM, here I am logging into my **admin account** connected to my previously created domain: **virtualdomain.com**

![HTH PFS Setup 20](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/82d36b28-1273-4a1a-b57e-ff42837f40cd)

30. Open an internet browser (**Microsoft Edge**) and type in the pfSense WebConfigurator interface: **172.16.0.2** in the URL search bar

31. To sign in for the first time into pfSense web interface the credentials are
 
 - Username: **admin**
 - Password: **pfsense**

 - Here we are going to follow the pfSense wizard setup

![HTH PFS Setup 21](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/99d5c8f4-364f-47bd-a3ec-14c98e7a39f7)

32. Under General Information:

- Hostname: **pfSense**
- Domain: **virtualdomain.com**
- Primary DNS Server: **172.16.0.1** (This is our DC VM which will provide the DNS resolution protocol to other client user devices

![HTH PFS Setup 22](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/b46daf9f-6643-4e65-8c71-e2d841adbef2)

33. Under Time Server Information

- Use the default given hostname: **2.pfsense.pool.ntp.org**
- Timezone: select your appropriate timezone here I used **US/Central**

![HTH PFS Setup 23](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/1681b7e2-d226-4a17-a44c-95b6922bf513)

34. Under Configure WAN Interface, select **DHCP**

![HTH PFS Setup 24](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/6c265583-951b-4617-8086-cebb69ae03ec)

35. Under Configure LAN Interface, type in **172.16.0.2** this is our assigned IP address for pfSense

36. Continue to hit **Next** to complete the wizard setup 

![HTH PFS Setup 25](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/9fa06fab-f332-4326-9251-bb17f4e3def3)

37. We have finished the setup for pfSense to our network diagram and successfully connected the firewall to our domain

![HTH PFS Setup 26](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/ff283fa6-3a4d-47ad-a295-74ef02fa524e)

38. We can check to see the current status of the pfSense by going to **Status -> Dashboard** on the top menu of the web interface

- Here the green arrow for the interfaces tells us that pfSense is up and monitoring the WAN and LAN interfaces and devices connected to it
- And scrolling down you will see more information and statuses of other components and features

![HTH PFS Setup 27](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/7a61ff46-43f6-4127-85db-cd701d8922e0)

### Congratulations on setting up our firewall and adding the first layer of defense for our Active Directory home lab!

## Installing Snort in pfSense

In this section, we will be installing Snort an intrusion Detection System/Intrusion Prevention System (IDS/IPS). Snort is an available feature in pfSense. Snort will provide real-time network traffic analysis and data packet logging while conforming to set rules. Having a firewall with an IDS/IPS will increase the security infrastructure of the home lab.

1. While still in the pfSense web interface using the DC VM, navigate to **System -> Package Manager -> Available Packages**

2. Search **snort** and click install to start the download of the Snort package

![HTH Snort Setup 1](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/c77f26d3-96e1-4668-9e6f-0aa236d895b7)

3. Once it is done installing, navigate to **Services -> Snort**

![HTH Snort Setup 2](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/4331c26d-288b-4d2c-ae58-95ff59bf7d05)

4. Here we are going to enable the **Snort GPLv2 Community Rules** and download them to be enforced onto the interface

  - Feel free to go over the options in **Global Settings** and add any to your preference

![HTH Snort Setup 3](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/b4a865a4-af1b-4502-a223-eac91038f75d)

5. Go to **Updates** and you should see that **Snort GPLv2 Community Rules** have not been downloaded yet.

6. Select **Update Rules** to start the download of the rules

![HTH Snort Setup 4](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/7ef4dc91-8496-46f4-90a8-b68c655bea87)

7. Now the rules have been downloaded onto Snort

![HTH Snort Setup 5](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/ba57b12f-939b-4772-aefd-40f488a118f4)

8. Go to the **Snort Interfaces** tab and select **LAN Categories**. Make sure the **Snort GPLv2 Community Rules enable checkbox is checked and save

![HTH Snort Setup 6](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/7d0942de-ea84-4a73-b7c4-e66e929868dc)

7. Now navigate to **LAN Rules**, and select **GPLv2_community_rules from the dropdown of **Category Selection**

- Here you will be able to view all the enabled and disabled rules. Feel free to enable more rules from the community rules; make sure to apply and save

![HTH Snort Setup 7](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/619e3abc-5976-446b-ae25-301c5adc40c9)

8. Now we are going to enable the **Snort interface** to do this navigate to the **Snort Interface** tab and click the **blue play button icon**.

![HTH Snort Setup 8](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/80df6990-8b5d-4173-be9b-b815a94d24c1)

- A **green checkmark icon** will appear indicating that snort is up and running. Now click the **pencil icon** under the **Actions** title to view the settings

![HTH Snort Setup 9](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/1cd72d30-a193-4c54-9dee-3c15ce240123)

-Copy the following settings pictures below and customize the options to your liking
  - **Interface** is designated for **LAN(em1)** only
  - **Enable Send Alerts to System log** setting. This will send the alerts to pfSense's **Syslogs** where later on will forward these alerts (syslogs) to **Splunk** the SIEM

![HTH Snort Setup 10](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/e8fabba5-6bd0-417a-be35-8ddcb6751976)

![HTH Snort Setup 11](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/2c07917a-74f7-4c1d-bf3f-c1c4c28b22d2)

- Make sure to click **Save**

![HTH Snort Setup 12](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/303fdb93-240c-4bc6-a5d6-96cd7604300f)

9. **Snort is all set up and configured inside pfSense and you can check the status of the service and other services you would want to add by customizing the dashboard of pfSense

![HTH Snort Setup 13](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/ac06b957-7044-4dc2-b514-2c837c97791e)

### Congratulations on Installing and Configuring Snort, the IDS/IPS
  > We will revisit **pfSense** and **Snort** to make the **Splunk** SIEM be able to receive data and alerts.

## Installing Splunk VM, the Security Information and Event Management (SIEM)

Now we will be installing the SIEM, Splunk. Splunk will centralize, collect, and analyze the alerts from the pfSense firewall and the Snort IDS/IPS. Splunk will be installed in a separate VM using the Ubuntu Linux.

1. First install **Ubuntu Desktop** and save it into your designated download files for ease of access

  > Link:  https://ubuntu.com/desktop

![HTH Splunk Setup 1](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/ced93c08-8e75-45bf-bce9-575eb1386480)

2. After the download is finished, go to **VirtualBox** and create a new virtual machine

- Name: **Splunk**
- Folder: **Select a folder that has the most space, here I chose my designated Virtual Machines folder**
- ISO Image:  **Select the ISO file in the location we downloaded and extracted from**
  > The ISO File is: ubunutu-24.04-desktop-amd64.iso
- **Check the Skip Unattended Installation**

![HTH Splunk Setup 2](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/5d7729b0-7afc-44e3-b98e-9b2722591a71)

3. Hardware Settings

 - Base Memory: **4096 MB or 4GB**
 - Processors: **1 CPU or 2 CPU**
  > Splunk will require more computing capabilities so pick what is best for you

![HTH Splunk Setup 3](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/0d9b3998-12a4-4321-8ebe-f3179667cc5d)

4. Virtual Hard Disk

- Create the Virtual Hard Disk option: **20GB - 40GB**
- Select **Next

![HTH Splunk Setup 4](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/6da2030c-c323-43f4-a089-dba592b1022b)

5. Splunk Settings

- In **General -> Advanced Turn on bidirectional for Shared Clipboard and Drag'n'Drop**

![HTH Splunk Setup 5 5](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/3e43a9d1-7a91-4cd2-9d96-451ac08c8d4d)

- In **Network**, we only need 1 adapter activated: **Internal Network - intranet**
- Now we can **boot up the Splunk VM**

![HTH Splunk Setup 5](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/629b2f67-348c-4720-82ff-dce78d69ebde)

6. Let Ubuntu install and you will be directed to the wizard setup of Ubuntu

![HTH Splunk Setup 6](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/afd832b8-0f6b-4b48-8044-238d02fee6dd)

7. Continue through and select **Do not connect to the internet** as we will assign the IP address of Splunk manually later

![HTH Splunk Setup 7](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/8355449e-fe4e-49eb-b16a-64fada537bf7)

8. Select **Default selection**

![HTH Splunk Setup 8](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/b014feae-9a0c-4c70-af9c-c1b8dfca4ef9)

9. Check **Install third-party software for graphics and Wi-Fi hardware**

![HTH Splunk Setup 9](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/21eaa9fd-5df3-4518-9e4d-4c4a134f54e0)

10. Select **Erase disk and install Ubuntu**

![HTH Splunk Setup 10](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/43e8fa20-4d12-4883-bf5e-da5bcbaf1cbf)

11. Here create your Ubuntu desktop account, I tailored it to Splunk and make sure to keep track of all logins in a separate note or text file.

![HTH Splunk Setup 11](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/8d1dffef-ad83-4abb-ac80-00fd6ae33359)

- Make sure in the review screen that every setting is okay and matches and click **Install**.

![HTH Splunk Setup 12](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/9b705635-7c15-4bfa-b672-fcabfb1f8ab8)

12. Now restart Ubuntu by clicking **Restart now**. This may take a few minutes.

![HTH Splunk Setup 13](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/32b54e97-6dd4-4b20-8ae7-4336d92c1a2d)

13. Our Ubuntu Splunk account has been created and use the password we created to log into Ubuntu

![HTH Splunk Setup 14](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/c681a7b6-8a84-4f21-9cf8-d459070c82dd)

14. Select the **Ubuntu logo bottom left** and select **Settings -> Network** to open the network settings

- Here we are going to manually set the IPv4 address to match the network diagram and this will become Splunk's address as well

![HTH Splunk Setup 15](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/3b610dc7-cf4d-49db-9f3e-be687b15e325)

15. Select **Manual** and type in the following

- Address: **172.16.0.4**
- Netmask: **255.255.255.0**
- Gateway: **172.16.0.2** (pfSense Firewall)
- DNS: **172.16.0.1** (DC)
- Hit **Apply**

![HTH Splunk Setup 16](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/6aa4bfed-3e64-4965-97c4-63854ab68ab2)

16. Here we are going to test the connectivity of the Ubuntu VM to our firewall and DC by using the **ping command in Ubuntu's terminal**

- Type **ping -c 5 172.16.0.2**
  - This will ping the **pfSense** firewall
  - the **-c 5** input will send 5 data packets to the destination address, without **-c** it will continue to send data packets until manually stopped
- Repeat the same procedure and ping the DC VM **172.16.0.1**
  - Note you will need to have both the **pfSense** and **DC** VM opened to do so

![HTH Splunk Setup 17](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/3e50e4a8-21bf-4a9d-976b-16f27501e361)

17. Now that the Ubuntu VM is connected successfully, we are going to download **Splunk Enterprise** for free. You will be prompted to create a free account and have access for 14 days.

- Link: **https://www.splunk.com/en_us/download.html**
  - Or go open **Mozilla Firefox** and enter **www.splunk.com** and click **Free Splunk**

![HTH Splunk Setup 18](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/ea38b65e-9ae7-42ec-be43-c45b37a7a5c5)

- Scroll all down and you should see under **Products** -> **Free Trials * Downloads**

![HTH Splunk Setup 19](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/15eb44d1-520f-452e-bae2-e201e65b1f68)

- Click **Get My Free Trial** under **Splunk Enterprise**

![HTH Splunk Setup 20](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/12efcf72-1058-47a1-8afd-be9c17ac9640)

- Make sure to select **Linux** and get the **.deb** file and click **Copy wget link**
- Open **Ubuntu Terminal** and paste the **Splunk wget link** into the terminal

![HTH Splunk Setup 21](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/8af60e6d-09cb-489f-a31e-223f97df8084)

![HTH Splunk Setup 22](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/c1baaad5-596e-4dd1-bb25-e0a58c902db7)

18. Once the **Splunk** download is finished inside the terminal, type in the following to start the installation

- **sudo dpkg -i (copy and paste the **Splunk file name that ends with .deb**)
- Then you will be prompted to **enter the password for your Ubuntu account** to start the installation

![HTH Splunk Setup 23](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/4eee41a0-72b9-4437-ad06-5520bf40d06e)

![HTH Splunk Setup 24](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/9898740b-e2a1-4840-bc51-d8c0bf95dd5f)

19. Create the **Splunk Admin Account** that will grant you access to the Splunk Web Interface later on

![HTH Splunk Setup 25](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/098f0172-7e88-4ae3-ab39-ad3741a4122e)

20. Once you are down it will create the web interface that can be accessed through the internet; however here the web interface did not make it to match my Ubuntu's (Splunk) IP Address: **172.16.0.4**. But I will show you how to change that.

![HTH Splunk Setup 26](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/07c23077-3337-449c-8cf7-bc918474a83c)

21. Type in the following:

- "**sudo nano /opt/splunk/etc/system/local/web.conf**"
  - This will bring up the GUI to configure the web interface to match what we want

![HTH Splunk Setup 27](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/411c6bb4-894a-42ce-bd47-41849b391150)

- Once inside the GUI, type in **8000** for the http-port and make the **server.socket_host to 172.16.0.4**
  - Apply the changes and exit the GUI

![HTH Splunk Setup 28](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/12c614ab-2398-4cef-9398-b9c2648b6e98)

22. Restart **Splunk**

- Type in the line: "**sudo /opt/splunk/bin/splunk restart**" and let it restart

![HTH Splunk Setup 29](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/5fcc32c4-b5bb-4975-bb4d-7a75fb4828fb)

- Now the web server should be ""**http://172.16.0.4:8000**" and we can now access **Splunk Enterprise Web Interface** properly

![HTH Splunk Setup 30](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/43611e86-680c-461f-a1a0-4d6a6a52d326)

23. Open **Mozilla Firefox** and type in our new web address "**172.16.0.4:8000**" into the URL bar

- Here we type in the **Admin Account credentials** we set previously inside the terminal and sign in

![HTH Splunk Setup 31](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/46229452-be9e-4b61-afe6-c7b592558351)

24. This is the **Splunk Administrator Dashboard**, feel free to explore the option but we will come back to this as the next step is to install the **Splunk Forwarder** into our **DC** and configure p**fSense to send the firewall and Snort alerts to Splunk**

![HTH Splunk Setup 32](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/88e19c1d-ce28-44be-8ca4-d902e4392f21)

### Congratulations, we have installed and set up our SIEM, Splunk
  > Another security safeguard that centralizes and collects security alerts and data from the firewall and IDS/IPS for management. This is the last layer of defense for this home lab network diagram. The next step is configuring the DC, Firewall, and IDS/IPS to work and send data to Splunk so that we can organize and view Splunk's web interface.

## Install and Configuration of Splunk Forwarder

This is the last step for the setup of our network security for the home lab. We are going to configure the settings in pfSense to ensure alerts and data are sent to Splunk. Then we will install **Splunk Forwarder** an external software that will allow the Windows DC and other Windows Client VMs alerts sent to Splunk interface

1. Go back to the **DC VM** and open the **pfSense Web Interface**: **172.16.0.2** is the web address to type in

2. Navigate to **Status -> System Logs**

![HTH Forwarder 1](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/a4150ccd-cbc4-47fc-8f9a-f6012ce42254)

3. **Check Enable Remote Logging**, this will allow log messages to be remotely sent to an address, Splunk

- For **Remote log servers** enter: **172.16.0.4:514**
  - This will direct the sent logs to the Splunk address through the UDP port (514)
- Next have **System Events and Firewall Events** checked. This includes **Snort** alerts as previously done the alerts are sent as **Syslogs**.
- Hit **Save**

- This is all that needs to be done for the firewall and IDS/IPS settings and now we will go to the **Splunk VM** and configure the settings there

![HTH Forwarder 2](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/6fc1fef4-db63-4d0e-aee5-f18c57d6c199)

4. This part is to ensure **Splunk** runs on boot up of the VM

- Open **Ubuntu terminal**
- Type: "**sudo /opt/splunk/bin/splunk start --accept-license && sudo /opt/splunk/bin/splunk enable boot-start**"
- Then type the password for the **Ubuntu Desktop login**

![HTH Forwarder 3](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/c9605d4e-b8e0-4e61-88d5-a349abae6073)

5. Open up the **Splunk Enterprise Interface** (172.16.0.4:8000) in your web browser

6. Navigate to **Settings -> Data Inputs**

![HTH Forwarder 4](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/8704ecbd-4a4c-4ff5-8634-716c2a8226d8)

7. Locate **UDP** and **+Add New**, this will open up data input through UDP so that Splunk can receive **Syslogs** from pfSense

![HTH Forwarder 5](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/673de4bf-2e26-47db-9287-a44446cd0fbd)

8. Make sure to select **UDP** tab and for **Port** type: **514**

- Hit **Next**

![HTH Forwarder 6](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/b5714b98-f4e7-4b01-ad5c-52c7fb249402)

- Source type: Click the dropdown and select **syslog**
- Index: **main** (this is where the syslogs will be collected)
- Click **Next** all the way through to complete the process

![HTH Forwarder 7](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/0b2d2c19-14de-4985-b750-8cc4dc10274f)

9. This step is needed for **Splunk Forwarder** to have alerts forwarded or sent to Splunk

- Navigate to **Settings -> Forwarding and receiving**

![HTH Forwarder 8 25](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/3688f597-2b29-4d83-a311-d526f5912899)

- Under **Receive data**, click **+ Add new**

![HTH Forwarder 8 35](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/e2641dce-99a6-4bbc-bd0d-c7a46960bf9a)

- Type: **9997** for the port to listen, this is also the default
- Click **Save**

![HTH Forwarder 8 5](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/713c93d3-1c49-4717-9486-30f9ffcf9f17)

- Before we go and install **Splunk Universal Forwarder**, we can go check if pfSense and Snort have sent logs to Splunk

- Navigate to **Settings -> Searches, reports, and alerts**
- Here we can search and refine the search to output specific results
  - Type: "**source="udp:514" index="main" sourcetype="syslog"**"
- Elements will be highlighted from the search results, but here we can confirm the pfSense firewall and Snort IDS/IPS are connected and send alerts to Splunk

![HTH Forwarder 8](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/9c115a7a-f2d2-44ca-bef8-a5778b3dda05)

### Installing Splunk Universal Forwarder in the DC VM

This is the last step needed for Splunk configurations. This will allow the Windows DC and other Client Users connected to the domain; events and alerts to be sent to Splunk.

1. Still on the DC VM open up the Splunk website, navigate to the downloads and free trial page we have done before. Select **Get My Free Download** under **Universal Forwarder**
  - Link: https://www.splunk.com/en_us/download.html

![HTH Forwarder 9](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/4acf5a22-cb60-4401-9582-a62caadcc958)

2. Select **Windows** and Select **Download Now** for the **64-bit edition**
  - Let the download complete and click file to start the Wizard Setup

![HTH Forwarder 10](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/a6c3dc3c-6aef-4c84-a6d4-e1e0a08d07ca)

4. Setting up the **Splunk Universal Forwarder**

- **Check** the box to agree to the License Agreement
- **Select An on-premises Splunk Enterprise instance**
- **Select Customize Options**

![HTH Forwarder 11](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/98758aef-12a5-4fa3-bb23-909a8f6cf94e)

- Select **Local System**

![HTH Forwarder 12](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/6ee01b6f-a30d-4b5f-b238-14e0eaabfdc3)

- Select the type of event logs and what you want Splunk to forward from Windows, the following is what I checked
  - **Application Logs**
  - **Security Log**
  - **System Log**
  - **Forwarded Events Log**
  - **Setup Log**
  - **Enable AD Monitoring**

![HTH Forwarder 13](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/2d7f5cfc-9cf1-4719-977b-f380f88cdd5b)

- Here create an admin account for Splunk Universal Forwarder, I just did the same credentials for the Splunk Enterprise Installation process

![HTH Forwarder 14](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/368286b0-d1dc-4502-abe7-5d94e626a624)

- Before this page, the **deployment server** is optional and I skipped it but the **Receiving Indexer** is needed to forward directly to our Splunk Interface
  - Hostname: **172.16.0.4**
  - Port: **9997**, this is the port that we previously added in the Splunk Interface: Forwarding and Receiving Settings

![HTH Forwarder 15](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/c84e1d38-2561-428f-a0b4-98c80c108bc9)

- Select **Finish** and now the **Splunk Universal Forwarder** is installed and configured to send directly to Splunk

![HTH Forwarder 16](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/cab2c062-e519-4010-92b8-64946bb0ec91)

5. Here I went into **Windows Terminal** to restart **SplunkForwarder**
  - Type: "**Restart-Service SplunkForwarder**"

![HTH Forwarder 17](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/9cc6c5e7-4acd-450c-baff-97a14df49773)

### Checking Everything is Connected and Sent to Splunk

1. Go back to the **Splunk VM** and open the **Splunk Web Interface**

- Click **Search your data**

![HTH Forwarder 19](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/be8186e6-9a99-4d63-906f-5cd89c8c9d5e)

- Select **Data Summary**

![HTH Forwarder 20](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/0f1e2431-62b2-450d-af38-edc66bdd8a78)

- Inside **Data Summary**, we should now see two Hosts connected to our Splunk SIEM
  - **172.16.0.2** is our firewall and IDS/IPS (pfSense and Snort)
  - **DC** is the domain controller (DC) of our domain: virtualdomain.com
  - Under **Count** is the number of logs sent to Splunk dependent on what we checked during the Splunk Forwarder setup

![HTH Forwarder 21](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/7ea5adbc-c489-43c3-a209-c818d2bdb409)

- If we go to **Sources** and **Sourcetypes**, the list shows the type of sources and the count as well for each
- Confirmation that pfSense, Snort, and Splunk Forwarder are configured correctly and send traffic events/alerts to one central interface Splunk our SIEM

![HTH Forwarder 22](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/62891a07-8695-4bce-9275-b24414d1f3dc)

![HTH Forwarder 23](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/448052b1-a05b-4460-ab12-988f76fca4db)
