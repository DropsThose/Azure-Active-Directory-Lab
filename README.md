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

