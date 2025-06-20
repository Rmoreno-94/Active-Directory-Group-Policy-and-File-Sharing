# Active-Directory-Group-Policy-and-File-Sharing (WIP)
AD GP and File Sharing

Summary
This project was an extension of my previous Active Directory Homelab. I was able to build upon the previous project by establishing roles and groups typically found within corporate environments to serve as a simulated enviroment. These roles included an HR department, IT department, and Sales department. I used user profiles that were created in the previous homelab project to fill those roles. Once these groups were established, I began to create group policies within the domain to establish the policies and preferences necessary for basic security. These policies include USB restriction, password management and lockout policies. 

<br/>![AD existing users added to groups](https://github.com/user-attachments/assets/f2f3051e-94fb-4c37-a072-fb3a22dfc1ed)
I began this project by adding previously created users to specific groups by using the active directory users and computers tool to create the groups within the domain. I then added each member individually to their corresponding group.<br/>


<br/>![AD GP Management](https://github.com/user-attachments/assets/6847c464-fcbc-40af-914c-e70f245b47c4)
Once the groups and users were created and properly sorted, I created group policies for the domain by using the Group Policy Management Tool within the server manager. I created policies such as USB Prevention, Password management, and Account lockout policies to establish basic security policies for the environment. These policies were linked to the appropriate users and enforced to ensure compliance.<br/>



<br/>![AD GP Password Lockout policy](https://github.com/user-attachments/assets/ba1a82ee-516b-4ecd-b805-82e676b3872b)
After the policies were created, I set out to test the account lockout policy in order to verify it was working as intended. For the purposes of the project, I set the lockout duration timer for 1 minute. For this test, I used the IT intern Bob's profile. I proceeded to log out of the profile and purposefully used the wrong password three times to meet the policy threshold. The results of this can be seen in the screenshot below.<br/>


<br/>![AD GP Password Lockout policy verified](https://github.com/user-attachments/assets/b0d22b6a-34c7-4e9c-878b-b8a522c49b5a)
The profile was accessible again with the correct password after the minute had passed. In a live environment, the lockout timer would either be increased significantly or require an administrator to restore access to that profile. 


<br/>![AD Adding Client10 to Comp OU in HQ OU](https://github.com/user-attachments/assets/6b7fc812-f763-4887-a133-276fabdc4b23)
I then moved on to adding the Windows 10 client to a computers OU I created under the HQ OU I also created. A users OU was also added to the HQ as well. This allows for the ability to add group policies directly to the proper OUs. 


<br/>![AD Drive Map GPO](https://github.com/user-attachments/assets/0d2e7d1a-d96b-4519-b3ac-851cdbfbd26c)
I continued by establishing a mapped drive GPO to a shared drive named CorpFiles. This would serve as the container for simulated corporate files for the different departments in the organization. 



<br/>![AD File Sharing through Network](https://github.com/user-attachments/assets/033b7f3d-ad42-4c4a-915f-f430d5c11f38)
I then established file sharing through the network of the domain. This was accomplished by enabling the proper sharing settings through the file explorer.


<br/>![AD File Storage Manager Service Install](https://github.com/user-attachments/assets/50fea440-a66b-4a5a-8c87-8151c0ecb736)



