# google-course---Use-Linux-commands-to-manage-file-permissions
Project Description
This project demonstrates how Linux commands are used to examine and manage file permissions to maintain security and appropriate access for a research team. Through this task, I ensured that sensitive data is only accessible to authorized users and that system vulnerabilities from improper permissions are mitigated. By using Linux tools like ls -la and chmod, I secured files and directories, including hidden files, according to organizational policies.

Step 1: Checking Current Permissions
To check existing permissions, I used the command:
bash
Copy code
ls -la
This command lists all files and directories, including hidden ones, along with their permissions. Hidden files in Linux start with a . (dot) and are typically used to store configuration or sensitive data.
Example Output:
sql
Copy code
-rwxrwxrwx  1 user group   1048576 Nov 19 10:00 file.txt  
-rw-r--r--  1 user group   2048    Nov 19 10:01 .project_x.txt  
drwxrwxr-x  2 user group   4096    Nov 19 10:02 drafts  
The 10-character string at the beginning of each line represents file permissions. For example:
•	-rw-r--r--
o	-: Regular file.
o	rw-: The owner has read and write permissions.
o	r--: The group has read permissions only.
o	r--: Others have read permissions only.
•	.project_x.txt is a hidden file because its name starts with a dot (.).

Step 2: Changing Permissions for a File
The organization prohibits "write" permissions for others. I updated the permissions of file.txt to remove unauthorized write access.
Command Used:
bash
Copy code
chmod 644 file.txt
Output:
bash
Copy code
-rw-r--r--  1 user group   1048576 Nov 19 10:00 file.txt  
Explanation:
•	The 644 permission ensures:
o	Owner can read and write (rw-).
o	Group and others can read (r--).

Step 3: Changing Permissions on a Hidden File
The .project_x.txt file is archived and should not have write permissions for anyone. Only the user and group should have read access.
Command Used:
bash
Copy code
chmod 440 .project_x.txt
Output:
bash
Copy code
-r--r-----  1 user group   2048    Nov 19 10:01 .project_x.txt  
Explanation:
•	Hidden files like .project_x.txt are identified by their leading dot (.). These files often contain sensitive or configuration data.
•	The 440 permission ensures:
o	Owner and group can read (r--).
o	Others have no access (---).

Step 4: Restricting Directory Access
The drafts directory contains sensitive data and must only be accessible to the researcher2 user.
Command Used:
bash
Copy code
chmod 700 drafts/
Output:
bash
Copy code
drwx------  2 researcher2 group   4096    Nov 19 10:02 drafts  
Explanation:
•	The 700 permission ensures:
o	Owner has full access (rwx).
o	Group and others have no access (---).

Details on Hidden Files and Directories
Hidden files and directories are a common feature in Linux, typically used for configuration data or sensitive information. These files are not displayed by default in directory listings unless the -a option is used with commands like ls. For example:
bash
Copy code
ls -la
This command reveals hidden files, such as .project_x.txt, ensuring they are included in permission audits. Properly securing hidden files is critical to prevent unauthorized access to sensitive information.

Summary
This project involved reviewing and modifying file and directory permissions to secure the organization's research files. Using ls -la, I identified current permissions and interpreted the 10-character string to ensure compliance with security policies, including for hidden files. By applying chmod commands, I removed unauthorized access and restricted sensitive data to appropriate users. This demonstrates the effective use of Linux commands to manage and secure file permissions in a professional setting.

