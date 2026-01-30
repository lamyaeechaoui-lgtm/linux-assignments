# Linux User Management and File System Access:
#### Task is to create users and use created users to test out file access permissions
### 1. Create the Tupu user using the adduser script:
Using the sudo adduser tupu scripting, it asked for my username's password and then to set a password,
set some information..


<img width="518" height="332" alt="sudo adduser tupu" src="https://github.com/user-attachments/assets/330e4582-0ddc-4023-b0da-6e47114aca7a" />


### 2. Create the Lupu user using the useradd command. Try to create a user profile, home directory, and user group similar to Tupu:

I began with creating the user's group using "sudo groupadd lupu"
then created the user using "sudo useradd -m -d /home/lupu -s /bin/bash -g lupu lupu"
After creating the user, a password was assigned separately.

<img width="701" height="159" alt="Screenshot 2026-01-30 024320" src="https://github.com/user-attachments/assets/20d3eebd-7d7d-4d65-9423-6307b6581a69" />

To verify that the user exists, i used "ls /home" command.

### 3. Create the Hupu system user with the login shell set to /bin/false:

I ran exactly "sudo useradd --system --shell /bin/false hupu"
The login shell was set to /bin/false to prevent the user from logging in to the system.

### 4. Add the users Tupu and Lupu to the sudo users:
To add users to the sudo group, i used these two commands:
sudo usermod -aG sudo tupu
sudo usermod -aG sudo lupu
<img width="867" height="49" alt="Screenshot 2026-01-30 030600" src="https://github.com/user-attachments/assets/bc375e97-0021-4acc-ade5-a7c4ee16c651" />
