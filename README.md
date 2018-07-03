## How to securely ssh into your server <br />

1. Run ```ssh-keygen``` on the remote computer. <br />
    > Specify private and public key folder and file names. <br />
    > Provide __passphrase__ for the key <br />

2. Run ```mkdir .ssh``` on the server _(in user's __*home*__ directory)_ <br />
    > Create __authorized_keys__ file inside the __.ssh__ directory <br />
    > Copy the content of __*<keyname>.pub*__ file from remote computer to the __authorized_keys__ file.<br /> 
    > While in home directory run __chmod 700 .ssh__ <br />
    > Then Run ```chmod 644 .ssh/authorized_keys``` again in the home directory.<br />

3. Run ```sudo vim /etc/ssh/sshd_config``` on the server machine. <br />
    > Find __#PasswordAuthentication yes__ then uncomment it and change __yes__ to __no__ <br />
    > In order to allow password authentication for some users or a user type these: <br />
    > __*sshd_config*__ file type ```Match user``` <br /> ```PasswordAuthentication yes``` <br />

4. Finally Login using ```shh user@ipaddress -i /location/to/private/key``` 

___