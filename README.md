## How to securely ssh into your server
___

1. Run ```shell ssh-keygen``` on the remote computer
    __1.1__ Specify private and public key folder and file names.
    __1.2.__ Provide __passphrase__ for the key

___

2. Run ```shell mkdir .ssh``` on the server _(in user's __*home*__ directory)_
    __2.1.__ Create __authorized_keys__ file inside the __.ssh__ directory
    __2.2.__ Copy the content of __*<keyname>.pub*__ file from remote computer to the __authorized_keys__ file. 
    __2.3.__ While in home directory run __chmod 700 .ssh__
    __2.4.__ Then Run ```shell chmod 644 .ssh/authorized_keys``` again in the home directory.

___

3. Run ```shell sudo vim /etc/ssh/sshd_config```
    __3.1__ Find __#PasswordAuthentication yes__ then uncomment it and change __yes__ to __no__
    __3.2__ In order to allow password authentication for some users or a user type these:
            __*sshd_config*__ file type ```shell Match user```
                                            ```shell PasswordAuthentication yes```

___

4. Finally Login using ```shell shh user@ipaddress -i /location/to/private/key``` 