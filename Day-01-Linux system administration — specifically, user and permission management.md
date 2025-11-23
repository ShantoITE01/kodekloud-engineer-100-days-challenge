English side (Step by step)

Day-01-Linux system administration — specifically, user and permission management

My first ticket was related to Linux system administration — specifically, user and permission management.

🧩 Task Summary:
Logged in to App Server 2 (stapp02)

Created a new Apache user named john

Assigned UID 1704

Set the home directory as /var/www/john

💡 Key Learnings:

How to SSH into different servers using proper credentials

Using useradd with custom options for security compliance

Understanding user-specific configurations in web environments

Answer-
---
SSH into the server:

ssh steve@stapp02

Remember:SSH command-এর ফরম্যাট হলো:

ssh username@server_ip (মানে তুমি যেই username হিসেবে ওই সার্ভারে ঢুকবে, সেটাই লিখতে হবে।)

তোমার username = steve

যেই server-এ ঢুকতে চাও তার IP = 192.168.1.10 but here @stapp02

When prompted, enter password: Am3ric@

Note: password input is hidden (no stars), so type carefully and press Enter.

Create the user john with specified UID and home:

sudo useradd -u 1704 -d /var/www/john -m john

---

Explanation:

-u 1704 sets the UID.

-d /var/www/john sets the home directory.

-m creates the home directory if it doesn’t exist.

Provide sudo password if prompted

If sudo asks for a password, enter the appropriate user password (here: Am3ric@).

Verify the user and directory:

id john

ls -ld /var/www/john


Expected output (example):

uid=1704(john) gid=1704(john) groups=1704(john)
drwx------ 2 john john 4096 Oct  6 11:35 /var/www/john


(Optional) Set a password for john

sudo passwd john


Finish: go back to the lab UI and press Check to validate the task.

![Image Alt](https://github.com/ShantoITE01/kodekloud-engineer-100-days-challenge/blob/2c6ea0fc6ebab7825cc8a33c45ea3eaffb002fb4/Screenshot%202025-10-06%20223722.png)
