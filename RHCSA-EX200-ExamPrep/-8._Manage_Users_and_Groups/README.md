Manage users and groups
========================

**QUESTION (1)**
--------------
**Create the user named eric and deny to interactive login.**

**ANSWER (1)**
```
useradd -m eric                   <-- Create eric user
passwd eric                       <-- type password
```

```
vi /etc/nologin      <-- The primary function of /etc/nologin file is to display a message (stored in the file) to users 
                         attempting to log on to a system during the process of shutdown. Once the message has been displayed
                         to the user, the login procedure terminates, preventing the user from logging onto the system.
```

**you can type something, or leave it empty**

```
vi /etc/passwd                              <-- go to the desired user and change it's login shell from /bin/bash to either
                                                sbin/nologin or /bin/nologin. if /bin/nologin doesn't exit just create it
                                                usingtouch command, and leave it empty, the system will look for this file and                                                 excute it, then close the session, resulting of closing the session each time                                                   somebody trys to access this user through the shell                
```

![image](https://user-images.githubusercontent.com/80536675/198735214-41988edd-a983-4c73-af14-60e6fe294c43.png)

**The /etc/passwd file has as the last item on a user's line the program to be run upon login. For normal users this is typically
set to /bin/sh or other shell (e.g. bash, zsh).**

**We just need to edit the /etc/passwd file, go to user eric and change the interactive shell from /bin/bash to /sbin/nologin, this 
prevent both interactive and non-interactive shell**

**Note please don't create /etc/nologin because it prevent all users from access the system, if you are using Oracle VM and tried to login as any user the /etc/nologin that you've created will prevent all users from access except the root user
if you are use ssh through MobaXterm or Putty to access VM as root you'll be able to access other users during the ssh session
so in the exam, please use /sbin/nologin to prevent both interactive and non-interactive shell access**

