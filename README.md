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

## Creating a Designated Save Location for the VMs and Files WORK ON IT WITH UPDATED PICTURES

1. Create a new folder called "**AD LAB**" in a location with the most space. Here I created it in my D: drive

![](https://github.com/marlopenaga/Active-Directory-Home-Lab-2024/blob/main/images/AD%20LAB%202.PNG?raw=true)

3. Inside of **AD LAB** create two folders: **AD Lab Files**, **Virtual Machines**

  - **HTH Lab Files** is the location where the VirtualBox, Windows Server 2022 ISO, and Windows 10 Enterprise installation files will be located
  - **Virtual Machines** is the location where we will install our VMs later using VirtualBox, which will be discussed later

![](https://github.com/marlopenaga/Active-Directory-Home-Lab-2024/blob/main/images/AD%20LAB%203.PNG?raw=true)

## Installing pfSense as a Virtual Machine

1. Click on the link to download the latest version of **pfSense**. It may ask you to create a free account.
  > *pfSense Download** https://www.pfsense.org/download/

![HTH PFS Setup 1](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/9c134a9c-2f75-494d-99bc-5cb948f94ced)

2. Make sure to download the file in your designated folder for ease of access and organization
3. Extract the zip file, I use **7-Zip** (free to download)

![HTH PFS Setup 2](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/8c85bb57-97fa-43df-8e1c-fb85cf772491)

![HTH PFS Setup 3](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/ce8faf32-69a2-4247-bd29-a4192ae57715)

![HTH PFS Setup 4](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/cbb7a510-b928-42b5-ae9a-4858189df811)

![HTH PFS Setup 5](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/705db5fe-b3c8-491d-b04c-b7fd295cd55c)

![HTH PFS Setup 6 5](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/8f99b59d-6b95-4844-867e-63d5005c3206)

![HTH PFS Setup 6](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/939529f2-f429-45db-b126-c35d7d61c12f)

![HTH PFS Setup 7](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/ceca3dbb-d4d9-4d61-ae3b-e1f5f3703580)

![HTH PFS Setup 8](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/d4fc119c-50c1-47c4-b478-354753b7c99c)

![HTH PFS Setup 9](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/cd893cc8-7806-4d1a-b0ae-c9f1525cfce5)

![HTH PFS Setup 10](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/5dd37fbd-f1b1-4c28-a855-c63de894a661)

![HTH PFS Setup 11](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/e322a623-78a7-4780-9466-973571a4ea10)

![HTH PFS Setup 12](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/28eb22c0-d782-41cd-b00e-804c1755a640)

![HTH PFS Setup 13](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/73b71fe2-8933-40bd-ad2b-aae4650bcd2f)

![HTH PFS Setup 14](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/eec749f5-efab-428d-90db-0874818d7896)

![HTH PFS Setup 15](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/4e541e02-39cc-4786-adb9-8c5ec9aab6db)

![HTH PFS Setup 16](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/07ccf3b4-4bf6-4d5c-a18c-6b59738ac26b)

![HTH PFS Setup 17](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/cee7cd6b-1618-4e25-8ef0-b0700d7a7508)

![HTH PFS Setup 18](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/93675a09-6fff-4955-ba94-b6f0dde15744)

![HTH PFS Setup 19](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/c41a8df1-eb27-4fce-90f5-0309796dce67)

![HTH PFS Setup 20](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/82d36b28-1273-4a1a-b57e-ff42837f40cd)

![HTH PFS Setup 21](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/99d5c8f4-364f-47bd-a3ec-14c98e7a39f7)

![HTH PFS Setup 22](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/b46daf9f-6643-4e65-8c71-e2d841adbef2)

![HTH PFS Setup 23](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/1681b7e2-d226-4a17-a44c-95b6922bf513)

![HTH PFS Setup 24](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/6c265583-951b-4617-8086-cebb69ae03ec)

![HTH PFS Setup 25](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/9fa06fab-f332-4326-9251-bb17f4e3def3)

![HTH PFS Setup 26](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/ff283fa6-3a4d-47ad-a295-74ef02fa524e)

![HTH PFS Setup 27](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/7a61ff46-43f6-4127-85db-cd701d8922e0)

## Installing Snort in pfSense

![HTH Snort Setup 1](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/c77f26d3-96e1-4668-9e6f-0aa236d895b7)

![HTH Snort Setup 2](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/4331c26d-288b-4d2c-ae58-95ff59bf7d05)

![HTH Snort Setup 3](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/b4a865a4-af1b-4502-a223-eac91038f75d)

![HTH Snort Setup 4](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/7ef4dc91-8496-46f4-90a8-b68c655bea87)

![HTH Snort Setup 5](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/ba57b12f-939b-4772-aefd-40f488a118f4)

![HTH Snort Setup 6](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/7d0942de-ea84-4a73-b7c4-e66e929868dc)

![HTH Snort Setup 7](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/619e3abc-5976-446b-ae25-301c5adc40c9)

![HTH Snort Setup 8](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/80df6990-8b5d-4173-be9b-b815a94d24c1)

![HTH Snort Setup 9](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/1cd72d30-a193-4c54-9dee-3c15ce240123)

![HTH Snort Setup 10](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/e8fabba5-6bd0-417a-be35-8ddcb6751976)

![HTH Snort Setup 11](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/2c07917a-74f7-4c1d-bf3f-c1c4c28b22d2)

![HTH Snort Setup 12](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/303fdb93-240c-4bc6-a5d6-96cd7604300f)

![HTH Snort Setup 13](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/ac06b957-7044-4dc2-b514-2c837c97791e)

## Installing Splunk VM

![HTH Splunk Setup 1](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/ced93c08-8e75-45bf-bce9-575eb1386480)

![HTH Splunk Setup 2](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/5d7729b0-7afc-44e3-b98e-9b2722591a71)

![HTH Splunk Setup 3](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/0d9b3998-12a4-4321-8ebe-f3179667cc5d)

![HTH Splunk Setup 4](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/6da2030c-c323-43f4-a089-dba592b1022b)

![HTH Splunk Setup 5 5](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/3e43a9d1-7a91-4cd2-9d96-451ac08c8d4d)

![HTH Splunk Setup 5](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/629b2f67-348c-4720-82ff-dce78d69ebde)

![HTH Splunk Setup 6](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/afd832b8-0f6b-4b48-8044-238d02fee6dd)

![HTH Splunk Setup 7](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/8355449e-fe4e-49eb-b16a-64fada537bf7)

![HTH Splunk Setup 8](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/b014feae-9a0c-4c70-af9c-c1b8dfca4ef9)

![HTH Splunk Setup 9](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/21eaa9fd-5df3-4518-9e4d-4c4a134f54e0)

![HTH Splunk Setup 10](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/43e8fa20-4d12-4883-bf5e-da5bcbaf1cbf)

![HTH Splunk Setup 11](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/8d1dffef-ad83-4abb-ac80-00fd6ae33359)

![HTH Splunk Setup 12](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/9b705635-7c15-4bfa-b672-fcabfb1f8ab8)

![HTH Splunk Setup 13](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/32b54e97-6dd4-4b20-8ae7-4336d92c1a2d)

![HTH Splunk Setup 14](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/c681a7b6-8a84-4f21-9cf8-d459070c82dd)

![HTH Splunk Setup 15](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/3b610dc7-cf4d-49db-9f3e-be687b15e325)

![HTH Splunk Setup 16](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/6aa4bfed-3e64-4965-97c4-63854ab68ab2)

![HTH Splunk Setup 17](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/3e50e4a8-21bf-4a9d-976b-16f27501e361)

![HTH Splunk Setup 18](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/ea38b65e-9ae7-42ec-be43-c45b37a7a5c5)

![HTH Splunk Setup 19](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/15eb44d1-520f-452e-bae2-e201e65b1f68)

![HTH Splunk Setup 20](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/12efcf72-1058-47a1-8afd-be9c17ac9640)

![HTH Splunk Setup 21](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/8af60e6d-09cb-489f-a31e-223f97df8084)

![HTH Splunk Setup 22](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/c1baaad5-596e-4dd1-bb25-e0a58c902db7)

![HTH Splunk Setup 23](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/4eee41a0-72b9-4437-ad06-5520bf40d06e)

![HTH Splunk Setup 24](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/9898740b-e2a1-4840-bc51-d8c0bf95dd5f)

![HTH Splunk Setup 25](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/098f0172-7e88-4ae3-ab39-ad3741a4122e)

![HTH Splunk Setup 26](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/07c23077-3337-449c-8cf7-bc918474a83c)

![HTH Splunk Setup 27](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/411c6bb4-894a-42ce-bd47-41849b391150)

![HTH Splunk Setup 28](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/12c614ab-2398-4cef-9398-b9c2648b6e98)

![HTH Splunk Setup 29](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/5fcc32c4-b5bb-4975-bb4d-7a75fb4828fb)

![HTH Splunk Setup 30](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/43611e86-680c-461f-a1a0-4d6a6a52d326)

![HTH Splunk Setup 31](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/46229452-be9e-4b61-afe6-c7b592558351)

![HTH Splunk Setup 32](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/88e19c1d-ce28-44be-8ca4-d902e4392f21)

![HTH Splunk Setup 33](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/9a94153e-0382-4c3e-9355-c2457830e1f4)

![HTH Splunk Setup 34](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/914c0386-628d-49e2-8c63-f4a9b5adfc33)

## Install and Configuring Splunk Fowarder

![HTH Forwarder 1](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/a4150ccd-cbc4-47fc-8f9a-f6012ce42254)

![HTH Forwarder 2](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/6fc1fef4-db63-4d0e-aee5-f18c57d6c199)

![HTH Forwarder 3](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/c9605d4e-b8e0-4e61-88d5-a349abae6073)

![HTH Forwarder 4](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/8704ecbd-4a4c-4ff5-8634-716c2a8226d8)

![HTH Forwarder 5](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/673de4bf-2e26-47db-9287-a44446cd0fbd)

![HTH Forwarder 6](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/b5714b98-f4e7-4b01-ad5c-52c7fb249402)

![HTH Forwarder 7](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/0b2d2c19-14de-4985-b750-8cc4dc10274f)

![HTH Forwarder 8 25](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/3688f597-2b29-4d83-a311-d526f5912899)

![HTH Forwarder 8 35](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/e2641dce-99a6-4bbc-bd0d-c7a46960bf9a)

![HTH Forwarder 8 5](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/713c93d3-1c49-4717-9486-30f9ffcf9f17)

![HTH Forwarder 8](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/9c115a7a-f2d2-44ca-bef8-a5778b3dda05)

![HTH Forwarder 9](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/4acf5a22-cb60-4401-9582-a62caadcc958)

![HTH Forwarder 10](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/a6c3dc3c-6aef-4c84-a6d4-e1e0a08d07ca)

![HTH Forwarder 11](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/98758aef-12a5-4fa3-bb23-909a8f6cf94e)

![HTH Forwarder 12](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/6ee01b6f-a30d-4b5f-b238-14e0eaabfdc3)

![HTH Forwarder 13](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/2d7f5cfc-9cf1-4719-977b-f380f88cdd5b)

![HTH Forwarder 14](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/368286b0-d1dc-4502-abe7-5d94e626a624)

![HTH Forwarder 15](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/c84e1d38-2561-428f-a0b4-98c80c108bc9)

![HTH Forwarder 16](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/cab2c062-e519-4010-92b8-64946bb0ec91)

![HTH Forwarder 17](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/9cc6c5e7-4acd-450c-baff-97a14df49773)

![HTH Forwarder 18](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/86348786-499c-4853-9b5e-0fd461ea4e27)

![HTH Forwarder 19](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/be8186e6-9a99-4d63-906f-5cd89c8c9d5e)

![HTH Forwarder 20](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/0f1e2431-62b2-450d-af38-edc66bdd8a78)

![HTH Forwarder 21](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/7ea5adbc-c489-43c3-a209-c818d2bdb409)

![HTH Forwarder 22](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/62891a07-8695-4bce-9275-b24414d1f3dc)

![HTH Forwarder 23](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/448052b1-a05b-4460-ab12-988f76fca4db)

![HTH Forwarder 24](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/bce4bd8f-b17c-4cf9-b5ea-cf38d194bd37)

![HTH Forwarder 25](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/12c9ee69-721a-4fc8-9273-7cf9afdad1cb)

![HTH Forwarder 26](https://github.com/marlopenaga/Network-Security-Home-Lab-Implementation-PfSense-Snort-Splunk/assets/165770329/6f3a8bc8-b270-4b1d-9fda-e41bfed2bc3b)

