# REFERENCE
https://www.youtube.com/watch?v=vpk_1gldOAE

# 1- ON THE REMOTE MACHINE
  ## Create .ssh folder for the user
  mkdir ~/.ssh


# 2- ON THE CLIENT MACHINE
  ## Create ssh key
  ssh-keygen -t rsa -b 4096 -C "YOUR@EMAIL.com" -f /home/[USER]/.ssh/sshkey_rsa

  ## Copy ssh public key the remote machine
  scp ~/.ssh/sshkey_rsa [REMOTE-USER]@[REMOTE-MACHINE-IP]:/home/[USER]/.ssh/authorized_keys


# 3- ON THE REMOTE MACHINE
  ## Make a backup of sshd_config file
  sudo cp /etc/ssh/sshd_config /etc/ssh/sshd_config.back

  ## Setup permissions on the REMOTE MACHINE
  chmod 700 ~/.ssh/
  chmod 600 ~/.ssh/*

  ## Disable password base authentication , IF YOU WANNA DISABLE PASSWORD-BASED AUTHENTICATION
  sudo vim /etc/ssh/sshd_config
    ## Chagne this line
    PasswordAuthentication no

  ## Restart ssh service
  sudo systemctl restart sshd
