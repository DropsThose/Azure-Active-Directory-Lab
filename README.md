# Azure-Active-Directory-Lab

This project will go over the steps to create an Active Directory lab environment within Microsoft Azure.

At the time of writing, You can create a free account with Microsoft Azure that will give you $200 worth of credits to use in your first 30 days.

![image](https://github.com/user-attachments/assets/77e0304f-4e70-45a4-bfe4-9363539a38db)

Once you create your free account and sign in, you will be greeted with a screen that looks something like this. 

![image](https://github.com/user-attachments/assets/2f2edf81-40df-4185-b7bd-dfe70255c745)

Click the 3 bars located at the top left of the page to open up the left side bar menu. 

![image](https://github.com/user-attachments/assets/40a0a88b-d6d8-4e18-b8d2-b1923a76bc14)

From here, click on Virtual Networks.

![image](https://github.com/user-attachments/assets/8179332a-e2f4-48c9-837e-c2a4a6c8805f)

This is where you will create a virtual network for your lab environment to use. 

![image](https://github.com/user-attachments/assets/2214f627-6a89-4142-bf9c-42a407730bf6)

Click create.

![image](https://github.com/user-attachments/assets/00f754db-e32f-4a7f-9087-7d131bb65c9f)

Create a new resource group where all your lab devices will reside. I called mine ADLab.

![image](https://github.com/user-attachments/assets/7f49ee25-e58f-418c-a46a-79fb9446c7cb)

Give your virtual network a name and select the region where you would like it to be located. 

![image](https://github.com/user-attachments/assets/5407b7ed-9cd2-4b47-be1e-e7815e3b3c4b)

Navigate to the IP addresses tab. This is where you will configure the subnet your virtual network will use. I left mine at the default 10.0.0.0/16.

![image](https://github.com/user-attachments/assets/22eec304-2f33-401c-bf1b-9f21725131b6)

Click on Review + create, and it will run a validation check to ensure everything is configured properly. If all is well, it will allow you to click the create button. Click create.

![image](https://github.com/user-attachments/assets/ec89814a-4a48-4b69-b170-4af19bab5eae)

It will take some time to deploy your newly created virtual network.

![image](https://github.com/user-attachments/assets/668a3f6a-c445-4b1f-8158-245784d86033)

Once your virtual network is deployed, you will see a screen like this.

![image](https://github.com/user-attachments/assets/b70b7ef9-5059-4e62-b36c-bab25d9fb7be)

Click the 3 bars, then Virtual machines.

![image](https://github.com/user-attachments/assets/6b99c749-7e5e-4f58-98a5-9bc631a0befe)

This is where we will create the virtual machines for our lab environment. 

![image](https://github.com/user-attachments/assets/8128697f-a6ac-48ff-b903-82d67d6cec36)

Click Create.

![image](https://github.com/user-attachments/assets/8d9da761-b0d1-4cda-993f-ed3c1c07c0a7)

We will start by creating our domain controller. Ensure that you select the correct resource group that we created earlier. Give your virtual machine a name.

![image](https://github.com/user-attachments/assets/6e32f62c-8c7e-4ace-a9e4-18794ebb239c)

Click on See all images.

![image](https://github.com/user-attachments/assets/e0c5d091-cae8-48ca-a5d9-037e6120e2af)

Find Windows Server and select which version you would like to use. I chose to use Windows Server 2022 Datacenter - x64 Gen 2 for this example. 

![image](https://github.com/user-attachments/assets/39ab7c91-4007-429e-82c6-192023d43cbd)

Once you choose your image, select B1ms for the size. Under Administrator account, create a username and password for your admin user to log in to this virtual machine. Leave everything else default and click on Next: Disks. 

![image](https://github.com/user-attachments/assets/1e37a452-4a2a-46f7-ac9e-06eff0afee00)

Change the OS disk type to Standard HDD. Click Next: Networking.

![image](https://github.com/user-attachments/assets/a17a52ec-11d9-493b-97d1-a9765eb6572b)

Under the networking tab, it tells you that a virual network interface card will be created for your virtual machine. This virtual NIC will hold the private IP and public IP that will be assigned to your virtual machine. One thing of note is that with the free subscription of Microsoft Azure you can only create a maximun of 3 public IP addresses so what we will do is create 1 public IP here with the domain controller and then transfer that public IP to all of the other virtual machines as we create them in order to configure them initially. At the end when our Kali Linux attack box is created the public IP will remain with the attack box where we will then be able to ssh to the public IP of the Kali box to use it as a jump box to then connect using the private IPs of the other virtual machines if need be. Leave the defaults here and click Review + create.

![image](https://github.com/user-attachments/assets/7c80a7fc-558d-4539-aba7-521b7729042f)

Once it finishes running a validation check, click on Create. 

![image](https://github.com/user-attachments/assets/4bc78f49-8657-47e8-9d34-3c5dbdea9137)

When deployment is complete, click on Go to resource.

![image](https://github.com/user-attachments/assets/43b42934-0e49-49dd-b35c-d34a3a2e5559)

Here you will see an overview of your newly created virtual machine. Click on Connect.

![image](https://github.com/user-attachments/assets/28fda01c-418e-4f97-a652-8b6286c24f8c)

Download and open the RDP file.

![image](https://github.com/user-attachments/assets/03ecd676-fd9e-4f94-9772-84b652f0367b)

You will be greeted with a login screen showing the Admin user you created earlier. Log in with the password you created.

![image](https://github.com/user-attachments/assets/5979b7aa-1f4b-49ef-893c-70bb4cbff9ce)

Once everything loads, you should see something like this. Click "Yes" in the blue banner on the right side. 

![image](https://github.com/user-attachments/assets/43c76bab-fa01-435a-af24-e97a3587ceb1)

Go to "Add roles and features". Click "Next" in the "Before You Begin" tab.

![image](https://github.com/user-attachments/assets/be33c31c-6e21-466f-ae7b-2ad60d3785bb)

Do the defaults for "Installing Type".

![image](https://github.com/user-attachments/assets/6430826e-96f9-42f7-b6c0-ac1ddeed5f47)

Ensure your DomainController machine is selected within the "Server Selection" tab.

![image](https://github.com/user-attachments/assets/e1a1ba53-3ed6-4651-af74-2e039f4d2e50)

Within the "Server Roles" tab, tick the box for "Active Directory Domain Services". This will open up another window, click "Add Features". Click "Next".

![image](https://github.com/user-attachments/assets/032327a3-0f77-4cda-b936-c3747dc8754f)

Defaults for "Features".

![image](https://github.com/user-attachments/assets/64e3b31b-1fa3-4122-89e4-04a5abc24d06)

Defaults for "AD DS".

![image](https://github.com/user-attachments/assets/43b5c0ab-78c3-48ce-bd41-5d4d57bbe0ec)

In "Confirmation", check the box to restart if needed. Click "Install".

![image](https://github.com/user-attachments/assets/c207b02c-adca-44ef-9eb8-26b534fe51d5)

Wait for the install to finish.

![image](https://github.com/user-attachments/assets/5ee97545-d4c3-425f-bc7d-37337893a715)

Once it finishes, click "Close".

![image](https://github.com/user-attachments/assets/110cbb88-998a-495c-aeaf-015b6d077a3f)

After the installation, you will see an alert stating a need for "Post-deployment Configuration". Click "Promote this server to a domain controller". A new window will open.

![image](https://github.com/user-attachments/assets/16e50fea-90a8-41f8-b4a0-1588e2e82e1d)

Select "Add a new forest". Give your domain a name followed by ".local". I chose "Alpha.local".

![image](https://github.com/user-attachments/assets/f8f25aa1-a9aa-4b82-9430-f72a74b6befb)

Create a password for DSRM.

![image](https://github.com/user-attachments/assets/46729317-54be-43ef-95a0-c54a908c8dee)

"Next" on "DNS Options".

![image](https://github.com/user-attachments/assets/22843888-9a6b-430e-a635-d4b433c28c36)

Under "Additional Options", you will see your domain name automatically populate. 

![image](https://github.com/user-attachments/assets/1fe0216f-4185-49d0-b770-c55f9098956d)

Defaults for "Paths".

![image](https://github.com/user-attachments/assets/891ea53a-897e-4d39-a5cb-8f64f935bb3d)

"Next" on "Review Options".

![image](https://github.com/user-attachments/assets/ff62a982-f034-45a5-abf5-71b336fb20ef)

Click "Install".

![image](https://github.com/user-attachments/assets/7b1204b4-10a0-4327-936c-476a8448697f)

After the installation, your VM will reboot, and you will be able to log in with your Domain username.

![image](https://github.com/user-attachments/assets/58053aff-3a6b-466a-a736-4f83e2802be5)

Now let's create some users for our domain. Go to "Tools" and then select "Active Directory Users and Computers".

![image](https://github.com/user-attachments/assets/23d92632-bafa-407d-b28b-79c2f71d9f68)

Expand your domain, then click on the "Users" folder.

![image](https://github.com/user-attachments/assets/be0c677f-551b-4cb4-8968-c6913e792a79)

Right-click within the "Users" folder, then go to "New" and "User".

![image](https://github.com/user-attachments/assets/3facc241-767f-4322-baac-344d415650b4)

Give your user a First and Last name, then create a logon name for them. 

![image](https://github.com/user-attachments/assets/c060afee-2b94-46b4-9fce-87dd029dfe1e)

Create a password and uncheck the box labeled "User must change password at next logon." Click "Next" then "Finish".

![image](https://github.com/user-attachments/assets/ba65f52e-707a-4aad-957d-068dbbbd81d3)

You will see a new user is added to the "Users" folder. Repeat the process to create another user.

![image](https://github.com/user-attachments/assets/1f3af4e0-1f0c-459c-bf1f-730cabb0c91f)

Here is my second user, Micheal Smith.

![image](https://github.com/user-attachments/assets/f447e905-27ea-4cc1-b201-46ac0ed41e0d)

Now it's time to create the Windows 10 VMs that will join our newly created domain. 

Within the Azure Portal, under Virtual machines, click on Create.

![image](https://github.com/user-attachments/assets/3a09c2d9-fa01-4003-aec2-dbceddd65bd0)

Ensure the VM is added to the correct Resource group. Give it a name and select which version of Windows 10 you would like to use. I chose Windows 10 Enterprise, version 22H2 x64 Gen2.

![image](https://github.com/user-attachments/assets/93e3d5c6-a04f-43d9-a8b4-5ea9fb420afe)

Select B1ms for the size. Create an Administrator account and check the box about licensing.

![image](https://github.com/user-attachments/assets/ffa4598d-e272-4088-a25a-934731a4895d)

Under Disks, change it to Standard HDD.

![image](https://github.com/user-attachments/assets/160e7d5f-cad5-47e1-9725-885d56cf1af4)

Under Networking, set Public IP to none. Remember, we will be transferring the public IP we created initially between the VMs as we go.

![image](https://github.com/user-attachments/assets/a3254a7b-e425-4e88-bdd8-e46fd3b92a6a)

Go to Review + create, then click Create.

![image](https://github.com/user-attachments/assets/afb648cf-af5e-4640-a759-17a51599b858)

Once the VM is deployed, go to All resources and click on the NIC that was created for the DomainController VM. We need to unassociate the public IP that was assigned to that VM in order to give it to our newly created Windows 10 VM. 

![image](https://github.com/user-attachments/assets/bb281ebf-eea9-4165-88b2-62a4c6c88d55)

Under Settings, go to IP configurations, then click on ipconfig1.

![image](https://github.com/user-attachments/assets/886db879-77b8-4512-bd08-201909c073f8)

Uncheck the box labeled "Associate public IP address." This will free up that public IP and allow it to be used with our other Windows 10 VM.

![image](https://github.com/user-attachments/assets/3bdbfa51-c5ca-45a7-ba8f-c9d6409dd286)

In all resources, navigate to the NIC that was created for our Windows 10 VM.

![image](https://github.com/user-attachments/assets/d1f0cec3-6d7d-454b-a414-70e4fd9348e9)

Repeat the steps we did to unassociate the public IP. This time, check the box labeled "Associate public IP address" and select the now available public IP from the dropdown menu.

![image](https://github.com/user-attachments/assets/c499d81d-055a-4b5d-b024-652bb5bd30db)

Download the RDP file for the Windows 10 VM and connect with the credentials you created.

![image](https://github.com/user-attachments/assets/585846bf-9da5-45d9-9cb1-ea779d0f3354)

Once you are logged in, click yes within the blue banner again and then right-click the ethernet icon in the lower right corner of the screen. Click "Open Network & Internet settings".

![image](https://github.com/user-attachments/assets/95344333-4185-4c60-a2b5-0fdea9bf819a)

Go to "Change adapter options".

![image](https://github.com/user-attachments/assets/1854e93f-464e-4b56-9a6f-4072f546c12b)

Right-click "Ethernet" then go to "Properties".

![image](https://github.com/user-attachments/assets/4106fbfa-62cf-4357-95a8-b6413f1b10da)

Find "Internet Protocol Version 4" then click "Properties".

![image](https://github.com/user-attachments/assets/ba4197ab-43c2-4273-827e-61e1df05e8f8)

Check "Use the following DNS server addresses:" and put the private IP of your DomainController VM in the first box. Press "OK". At this point you may lose your RDP connection and may need to reconnect or restart the Windows 10 VM from the Azure Portal.  

![image](https://github.com/user-attachments/assets/9b239152-d1d6-4e63-be78-2ddd8fa6f0c4)

Once you are logged back in, open up File Explorer and right-click on This PC, then click properties.

![image](https://github.com/user-attachments/assets/3a6893dc-9904-43ab-a9dc-7eb549e0eb40)

Click "Rename this PC (advanced)", then "Change", and finally change the "Member of" to Domain and input the name of your domain.

![image](https://github.com/user-attachments/assets/4bf2fb2a-5137-4b55-a30a-df4a8df30df9)

Input the credentials of the Administrator account you created for your DomainController VM.

![image](https://github.com/user-attachments/assets/818062ef-f9a9-4fe3-9aa9-ba31ab4977d3)

You will be greeted with this message welcoming you to the domain! You will then be prompted to restart your VM. Once you restart, you will be able to log in using any of the two users you created within your Domain Controller. 

![image](https://github.com/user-attachments/assets/b8549ad3-a5d4-4a5e-8630-843fdf42fd2f)




