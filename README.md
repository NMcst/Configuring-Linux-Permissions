# Configuring Linux Permissions

## Project description
In this project, I’ll be demonstrating Linux commands to configure the file permissions of an organization properly. In this scenario, the research team at my organization needs to update file permissions for certain files and directories within the _projects_ directory. The permissions do not currently reflect the level of authorization that should be given. This project is done through a Google-owned platform called Qwiklabs.

## Checking file and directory details
The following command shows the existing permissions set for a specific directory in the file system.

![image](https://github.com/user-attachments/assets/f99e4550-61a1-472c-8f0b-31143b505964)

The first command I used was **_ls_** to list all the directories that are available. Then, I used **_cd_** to change the directory to the projects directory. I used **_pwd_** to confirm the working directory that I’m in. In the projects directory, I used a **_ls_** command with the **_-la_** option to list all files and directories and include hidden files and directories under the _projects_ directory. In the list, we can see one hidden file named **_.project_x.txt_** with four other files that **is not hidden** and a **_draft_** directory.

## Describing the permissions strings
The permission string can be described by character. Each permissions string is a 10-character string to determine authorization of the file or directory.

•	1st character: This character is either represented by d if it’s a directory or – hyphen if it’s a file

•	2nd–4th characters (User): These characters are used for the permission of a user. These characters can be represented read (r), write (w), and execute (x) if the user can; otherwise, it will represent a hyphen (-) if the permission is not granted to the user.

•	5th-7th characters (Group): The explanation in the 2nd-4th character is the same for the 5th-7th character, but for the group instead of the user. 

•	8th-10th characters (Other): The explanation in the 2nd-4th character is the same for the 8th-10th character, but for the others instead of the group. 

For example, the directory permission for **_drafts_** is **drwx--x---**. The first character is **d**, which means it is a _directory_, and the **2nd-4th characters** are rwx, which means the user, the researcher, can **read, write, and execute** in that directory. For the **5th-7th characters** are --x which means the group research_team can only **execute**. While for the **8th-10th characters** are ---, which means others can't read, write, and execute for that directory.

## Changing file permissions
The organization requires others shouldn't have write access to any of their files. To comply with this, I referred to the file permissions that I previously returned. I determined that project_k.txt must have the write access removed for others.

![image](https://github.com/user-attachments/assets/9e1e22e5-1edc-46d9-bb44-9ca7ec470d63)

The first two lines of the screenshot display the commands I entered, and the other lines display the output of the second command. The _chmod_ command changes the permissions on the files and directories. This first argument indicates what permission should be changed, which is the _o-w_ to remove write permission. The second argument specifies the file or directory, which is _project_k.txt_. It is shown above that I removed the write permission from the other for the _project_k.txt_ file. I used the command _ls -la_ to review the updates I made.

## Changing file permissions on a hidden file
The research team recently archived _.project_x.txt_ hence the filename starting with a dot (.) which makes it a hidden or archived file. They do not want anyone to have write access to this project, but the **user and group** should have **read access**. Based on the default permission, the **user and the group have a write access** that needs to be removed and **add a read access for the group**.

![image](https://github.com/user-attachments/assets/f6ac3e55-7a74-4b5c-bbf0-6087ede8ef9b)

Similar to changing file permissions, I used the command _chmod u-w,g-w_ to **remove write access** from the user and group, and I **added read access** to the group using the command _chmod g+r_ for the _.project_x.txt_ hidden file. Again, I used the command _ls -la_ to review the updates I made.

## Changing directory permissions 
The organization requires the _researcher2_ **user** to be the only one that has execute access to the _drafts_ directory and its content. Based on the default permission, the _researcb_team_ group also has access, so I have remove the execute access for the group.

![image](https://github.com/user-attachments/assets/bd67dcfc-8a4c-4d18-8560-ca392cfc8a98)

Similar to the previous actions, I used the command chmod g-x drafts in order to remove the execute access of the _research_team_ group so that the _researcher2_ user has the only access to the drafts directory.

## Summary
In this project, I demonstrated how to change multiple permissions to match the level of authorization my organization requires for files and directories in the **_projects_** directory. In this project the most reoccurring command is _ls -la_ and _chmod_. The _ls -la_ command shows the list of permissions of hidden files and directories. The _chmod_ command is the command that changes the permission of the file or directory. Overall, the project showcased how to secure hidden files and directories in the system using chmod to have a proper authorization level to keep the organization's data safe. 
