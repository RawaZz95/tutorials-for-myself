## How to securely ssh into your server <br />
___

1. Run ```ssh-keygen``` on the remote computer. <br />
    __1.1__ Specify private and public key folder and file names. <br />
    __1.2.__ Provide __passphrase__ for the key <br />

___

2. Run ```mkdir .ssh``` on the server _(in user's __*home*__ directory)_
    __2.1.__ Create __authorized_keys__ file inside the __.ssh__ directory
    __2.2.__ Copy the content of __*<keyname>.pub*__ file from remote computer to the __authorized_keys__ file.<br /> 
    __2.3.__ While in home directory run __chmod 700 .ssh__ <br />
    __2.4.__ Then Run ```chmod 644 .ssh/authorized_keys``` again in the home directory.<br />

___

3. Run ```sudo vim /etc/ssh/sshd_config``` on the server machine. <br />
    __3.1__ Find __#PasswordAuthentication yes__ then uncomment it and change __yes__ to __no__ <br />
    __3.2__ In order to allow password authentication for some users or a user type these:<br />
            __*sshd_config*__ file type ```Match user```<br />
                                            ```PasswordAuthentication yes``` <br />

___

4. Finally Login using ```shh user@ipaddress -i /location/to/private/key``` 