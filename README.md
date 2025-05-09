# Active Directory Users And Computers

<p align="center">
<img src="https://github.com/user-attachments/assets/6dd2e501-535b-4c4c-9244-dd088bb76696" alt="Microsoft Active Directory Logo"/>
</p>

Overview

1. We will create two organizational units, `_EMPLOYEES` and `_ADMINS`
2. We will create an admin user.

---
<br />

<h2>Create Organizational Units</h2>

- In Active Directory, Organizational Units (OUs) are containers that hold objects like users, computers, and other OUs, allowing you to organize and manage them logically.
- They serve as a structure for applying Group Policy, delegating administrative control, and managing resources more effectively.

- To create an Organizational Unit in Active Directory, follow the steps outlined below.


---
<br />

<h3>Log Into Windows 2022 Server with your Domain Controller domain</h3>


- Because our Windows 2022 Server is now a Domain Controller, we have to specify the context to which we want to log into from the Remote Desktop client.
- The user accounts exist in a domain.
- So now we have to specify the domain name that we added as the domain controller above.
- In this example, my domain is `IanBates.com` and my administrator username is `Admin-DC`.
- So in my Remote Desktop client, I will enter `IanBates.com\Admin-DC` into the User name field as shown below.

  <img src="https://github.com/user-attachments/assets/002ed335-7a7c-4337-b9ef-6477fe9b8280" height="40%" width="40%" />



---
<br />

<h3>Open `Active Directory Users and Computers`</h3>


- Click your Windows 2022 Server Start Charm
- Under `Windows Administrative Tools`, select `Active Directory Users and Computers` as shown below.

  <img src="https://github.com/user-attachments/assets/d265e36f-16c3-490b-b9ec-65827b98c70e" height="60%" width="60%" />


---
<br />

<h3>Create A New Organizational Unit</h3>

1. Right-click your domain
2. Select `New`
3. Select `Organizational Unit` as shown below.

  <img src="https://github.com/user-attachments/assets/90e839f6-34f6-4397-aba9-4de025ff1d39" height="50%" width="50%" />


---
<br />

<h3>Create An Organizational Unit Named `_EMPLOYEES`</h3>

1. Add a name for the new organizational unit. In this example, we'll name it `_EMPLOYEES`.
2. Click `OK` to save and create our new organizational unit as shown below.

  <img src="https://github.com/user-attachments/assets/bbc95c0b-a0ed-4992-afe1-9b87b68a4982" height="40%" width="40%" />


---
<br />

<h3>Create An Organizational Unit Named `_ADMINS`</h3>

- Right-click your domain > Select `New` > Select `Organizational Unit`.

1. Add a name for the new organizational unit. In this example, we'll name it `_EMPLOYEES`.
2. Click `OK` to save and create our new organizational unit as shown below.

  <img src="https://github.com/user-attachments/assets/f7bdc73a-d004-4ed2-8796-40cdcc9d827a" height="40%" width="40%" />



---
<br />

<h4>View Your Two New OU's, `_EMPLOYEES` and `_ADMINS`</h4>

- In the left-hand panel, you can view and manage our two new Organizational Units, `_EMPLOYEES` and `_ADMINS` as shown below.

  <img src="https://github.com/user-attachments/assets/c67e8525-ea07-4fdd-9134-b2a8fac94f6e" height="40%" width="40%" />


---
---
<br />
<br />

<h2>Create A New User in Active Directory</h2>

- To add a new user in the `_ADMINS` organizational unit, follow the steps outlined below.
- NOTE: Simply adding the user to the `_ADMINS` organizational unit does not make this user an administrator.
- We will need to add this user to the built-in **DOMAIN ADMINS** Security Group after the user is created.
- This section will simply create a normal user.


---
<br />

<h3>Step 1: Create A New User in the `_ADMINS` OU</h3>

1. Right-click the `_ADMINS` organizational unit.
2. Select `New`.
3. Select `User` as shown below.

  <img src="https://github.com/user-attachments/assets/2e541bb4-a481-4fa5-96d9-073c28e66ed6" height="50%" width="50%" />


---
<br />

<h3>Step 2: Add The New User Name and Username</h3>

1. Enter the user's first and last name. In this example, I used first name `Jane` and last name `Doe`
2. Create a username. In ths example, I used `jdoe` as the username.
3. Click `Next` to continue as shown below.


  <img src="https://github.com/user-attachments/assets/55d6ec56-bee0-461a-a169-734a101c0789" height="50%" width="50%" />



---
<br />

<h3>Step 3: Add The New User Password</h3>

1. Enter a password for the new user.
2. For <b>lab purposes only</b> I unchecked the option to make the new user change their password at next logon and I checked `Password never expires`.
   - <b>NOTE: In a production environment you would not likely have the password never expire. Instead you would leave the default `User must change password at next logon` as the only option checked here.</b>
3. Click `Next`.

  <img src="https://github.com/user-attachments/assets/e4bb9d99-6a66-478e-bd8c-bc2bbb749ea0" height="50%" width="50%" />



---
<br />

<h3>Step 4: Confirm and Create the New User Object</h3>

- Review the new user details. If acceptable, select `Finish` to add the new user object.

  <img src="https://github.com/user-attachments/assets/26536bac-8598-4dd1-994d-464a4e8d7bbe" height="50%" width="50%" />




---
---
<br />
<br />


<h2>Add New User to Domain Admins Security Group</h2>

- <b>NOTE: Simply adding the new user above to the `_ADMINS` organizational unit does not make this user an administrator.</b>
- We will need to add this user to the built-in **DOMAIN ADMINS** Security Group after the user is created.
- To add a normal user to the Domain Admins Security Group, follow the steps outlined below.


---
<br />

<h3>Step 1: Open the New User Properties</h3>

1. Click the `_ADMINS` Organizational Unit.
2. Right click on the new user. In this example, that would be `Jane Doe`.
3. Select `Properties` as shown below.


  <img src="https://github.com/user-attachments/assets/199b7303-abdd-4477-8c79-fcf94669407f" height="50%" width="50%" />


---
<br />

<h3>Step 2: Add User As A Member Of Domain Admins</h3>

1. Click on the `Member Of` tab.
2. Click on the `Add` button.
3. Type the name `Domain Admins` in the text box entitled `Enter the object names to select`.
4. Click the `Check Names` button.
5. Select the `OK` button as shown below.

  <img src="https://github.com/user-attachments/assets/e6c3a070-4f47-4dd8-8922-5a3242efa1da" height="70%" width="70%" />

6. Click the `Apply` button to complete this process as shown below.


  <img src="https://github.com/user-attachments/assets/0f4e4b36-d016-4f03-aa27-0a457b42def9" height="50%" width="50%" />


---
<br />

<h3>View Domain Admins To Confirm</h3>

- You can confirm that our new user `jane doe` is a member of the Domain Admins Security Group by viewing Jane Doe's `Member Of` tab.
- You can also click on the Domain Admins Security Group and view its members as shown below.
- In this example, new user jane doe (`jdoe`) is a member of the Domain Admins Security Group:


  <img src="https://github.com/user-attachments/assets/f2398081-a6cc-4882-b2fe-7013f0dbb056" height="80%" width="80%" />











