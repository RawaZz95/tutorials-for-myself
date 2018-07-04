## Add a user to sudoers list <br />

1. Redirect to __sudeoers.d__ using ``` cd /etc/sudoers.d/ ``` <br />
    1. Run ``` touch username ``` in order to create a file for the username. <br />
    2. Add ``` username ALL=(ALL) NOPASSWD:ALL ``` to the file using a texte eitor. <br />

___

## How to securely ssh into your server <br />

1. Run ``` ssh-keygen ``` on the remote computer. <br />
    1. Specify private and public key folder and file names. <br />
    2. Provide __passphrase__ for the key <br />

2. Run ``` mkdir .ssh ``` on the server _(in user's __*home*__ directory)_ <br />
    1. Create __authorized_keys__ file inside the __.ssh__ directory <br />
    2. Copy the content of __*<keyname>.pub*__ file from remote computer to the __authorized_keys__ file.<br /> 
    3. While in home directory run ``` chmod 700 .ssh ``` <br />
    4. Then Run ``` chmod 644 .ssh/authorized_keys ``` again in the home directory.<br />

3. Run ``` sudo vim /etc/ssh/sshd_config ``` on the server machine. <br />
    1. Find __PermitRootLogin yes__ and change it to __no__ if you want to deny ssh to root user. <br />
    2. Then find __#PasswordAuthentication yes__ then change it to __no__ <br />
    3. In order to allow password authentication for some users or a user type these: <br />
    4. __*sshd_config*__ file type ``` Match user ``` <br />
    ``` PasswordAuthentication yes ``` <br /> to allow ssh login for that user.
    5. Finally run ``` systemctl restart ssh ```

4. Finally Login using ``` shh user@ipaddress -i /location/to/private/key ``` 

___

## How to setup the Linux Firewall <br />

1. Install the Uncomplicated Firewall ufw via ``` apt-get install ufw ``` <br />
2. Make ufw deny everything by default using ``` ufw default deny incoming ``` <br />
3. Allowing default outgoing ``` ufw default allow outgoing ``` <br />
4. To allow a port, type ``` ufw allow portNumber/tcp ```<br />