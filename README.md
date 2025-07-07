# Active-Directory-Group-Policy-and-File-Sharing 
AD GP and File Sharing

Summary
<br/>This project was an extension of my previous Active Directory Homelab. I was able to build upon the previous project by establishing roles and groups typically found within corporate environments to serve as a simulated enviroment. These roles included an HR department, IT department, and Sales department. I used user profiles that were created in the previous homelab project to fill those roles. Once these groups were established, I began to create group policies within the domain to establish the policies and preferences necessary for basic security. These policies include USB restriction, password management and lockout policies. I will also be creating file sharing options through a mapped drive over the domain as well as file permissions separated by simulated departments within an organization. Finally, I will complete this homelab by modifying the delegation options of GPOs to specific users and departments.

<br/>![AD existing users added to groups](https://github.com/user-attachments/assets/f2f3051e-94fb-4c37-a072-fb3a22dfc1ed)
I began this project by adding previously created users to specific groups by using the active directory users and computers tool to create the groups within the domain. I then added each member individually to their corresponding group.<br/>


<br/>![AD GP Management](https://github.com/user-attachments/assets/6847c464-fcbc-40af-914c-e70f245b47c4)
Once the groups and users were created and properly sorted, I created group policies for the domain by using the Group Policy Management Tool within the server manager. I created policies such as USB Prevention, Password management, and Account lockout policies to establish basic security policies for the environment. These policies were linked to the appropriate users and enforced to ensure compliance.<br/>


<br/>![AD GP Password Lockout policy](https://github.com/user-attachments/assets/ba1a82ee-516b-4ecd-b805-82e676b3872b)
After the policies were created, I set out to test the account lockout policy in order to verify it was working as intended. For the purposes of the project, I set the lockout duration timer for 1 minute. For this test, I used the IT intern Bob's profile. I proceeded to log out of the profile and purposefully used the wrong password three times to meet the policy threshold. The results of this can be seen in the screenshot below.<br/>


<br/>![AD GP Password Lockout policy verified](https://github.com/user-attachments/assets/b0d22b6a-34c7-4e9c-878b-b8a522c49b5a)
The profile was accessible again with the correct password after the minute had passed. In a live environment, the lockout timer would either be increased significantly or require an administrator to restore access to that profile.<br/>


<br/>![AD Adding Client10 to Comp OU in HQ OU](https://github.com/user-attachments/assets/6b7fc812-f763-4887-a133-276fabdc4b23)
I then moved on to adding the Windows 10 client to a computers OU I created under the HQ OU I also created. A users OU was also added to the HQ as well. This allows for the ability to add group policies directly to the proper OUs.<br/>


<br/>![AD Drive Map GPO](https://github.com/user-attachments/assets/0d2e7d1a-d96b-4519-b3ac-851cdbfbd26c)
I continued by establishing a mapped drive GPO to a shared drive named CorpFiles. This would serve as the container for simulated corporate files for the different departments in the organization. I then used the gpupdate /force command in the command prompt to force this change.<br/>

<br/>![AD Sharing over network to domain users](https://github.com/user-attachments/assets/b8795d16-6f70-48c7-ab16-11e387719a91)
I then established file sharing through the network of the domain. This was accomplished by enabling the proper sharing settings through the CorpFiles folder in the file explorer. I added the domain users group to the sharing settings and modified the permissions to read/write which allowed domain users to have access to this folder after authenticating.<br/>

<br/>![AD Results of sharing mapped drive across domain](https://github.com/user-attachments/assets/6b2dd379-5c61-40ec-a3a5-4a20f2f449b5)
Once the proper sharing settings were established, I was able to create a Testfile1.txt file on the DC and modify it in the Windows 10 client.<br/> 

<br/>![IT HR Folder Permissions segregated](https://github.com/user-attachments/assets/c2f4d297-4841-48c4-a27f-eb26e1aa95a4)
I expanded on this by creating IT and HR Dept folders within the CorpFiles folder. Both of these folders had inherited permissions disabled within the properties of each and respective groups (IT and HR) were created to allow for a simulated environment in which a member of the IT Dept would not be able to access the HR folders and vice versa. This can be a useful security feature to ensure the privacy of critical documents and preventing unathorized access to sensitive information. 

<br/>![GPO Delegation to IT ](https://github.com/user-attachments/assets/0710cb7b-72f1-4373-80bb-668d6cf98494)
After completing the GPOs I set out to create, I finished by delegating "Edit Settings" access of these GPOs to the IT Dept through the delegation tab of each GPO within Group Policy Management. This allows the IT Dept to review GPO settings and modify them as required by any changes in policy. I left the delete settings to the admins in order to prevent low level IT members from accidentally being able to delete a GPO such as a mapped drive. This can result in significant disruptions if overlooked.<br/>



<br/>Final Thoughts<br/>
I found this project to be very informative and rewarding. Being able to create policies that would impact a simulated organization is a strong tool that reinforces security for that organization and maintains an order required by the organization. Establishing file permissions also allowed me to implement basic security options for files and folders which would enhance overall security and make it more difficult for unathorized breaches of data to occur.






