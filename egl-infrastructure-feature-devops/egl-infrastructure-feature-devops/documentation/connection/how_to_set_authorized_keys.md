# How to create a new user and authorized key
## creating an ssh key
### Linux System

 - in you localhost open the terminal, running the command below to create a new ssh key and press enter

    ```ssh-keygen```

    ![ssh-keygen](https://github.com/tmaior/elitegaming-devops-infra/blob/feature/docs/documentation/image/ssh-keygen.png)
- then, name the ssh key and press enter. the key by default will be created in the path /home/your_user/.ssh/ with the name id_rsa. If you want to change the name of the key, specify the path where you want to save the key, if not specified it will be created in your home

    ![ssh-keygen-name](https://github.com/tmaior/elitegaming-devops-infra/blob/feature/docs/documentation/image/ssh-keygen-name.png)
- then you will be asked for a long password, if you don't want a password, just hit enter and you will be asked to repeat the password again. two keys will be created, one public (underlined in red) and the other private (underlined in blue)

    ![ssh-keygen-created](https://github.com/tmaior/elitegaming-devops-infra/blob/feature/docs/documentation/image/ssh-keygen-created.png)
### Windows System
 - open cmd, running the command below to create a new ssh key and press enter
    
    ```ssh-keygen```

    - then, name the ssh key and press enter. the key by default will be created in the path C:\Users\you_user/.ssh/ with the name id_rsa. If you want to change the name of the key, specify the path where you want to save the key, if not specified it will be created in your home

    ![ssh-keygen-win](https://github.com/tmaior/elitegaming-devops-infra/blob/feature/docs/documentation/image/ssh-keygen-win.png)

    - then you will be asked for a long password, if you don't want a password, just hit enter and you will be asked to repeat the password again. two keys will be created, one public (underlined in red) and the other private (underlined in blue)

    ![ssh-keygen-created-win](https://github.com/tmaior/elitegaming-devops-infra/blob/feature/docs/documentation/image/ssh-keygen-created-win.png)
### MacOS System
  To create an SSH key on your mac just go to the link [MacOS](https://secure.vexxhost.com/billing/index.php/knowledgebase/171/How-can-I-generate-SSH-keys-on-Mac-OS-X.html)
## connect to bastion
 - send a copy of your public key to the bastion home using the scp command below
    
    `scp -i path/to/EGL-dev-key.pem <name_key>.pub <user_instance>@<PublicIP_instance>:~/`

 - connect to bastion using connection instructions via [ssh](cluster_by_ssh.md) or [ssm](cluster_by_ssm.md)  
 ## create your user in the bastion

 - to create a new user use the adduser command

    `sudo adduser your_user`

 - move your key to your user's home
    
    `mv <name_key>.pub /home/<your_user>/`
 
 - create the .ssh directory and the authorization file
    

    ```
    sudo su - <your_user>
    mkdir .ssh
    chmod 700 .ssh
    touch .ssh/authorized
    chmod 600 .ssh/authorized_keys
    cat <name_key>.pub >> .ssh/authorized
    ```
## connect to the bastion using your key

 - use the ssh command to connect to bastion
    
    `sudo ssh -i .ssh/<name_key> <your_user>@<PublicIP_instance>`