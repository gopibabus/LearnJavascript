# 🔥Practice SSH

### ✳Generate and Use SSH Keys

> Below steps will allow user to auto login server without password 😃

```bash
ssh-keygen -C "username@email.com"
```

> 💭 Above command will generate 2 keys (public and private keys) and store them in **.ssh** folder in your home directory.

?> Login to your server with password and navidate to .**ssh** folder in your home directory.
There you can find 2 files: **authorized_keys** and **known_hosts**. Please paste public key from your machine into the **authorized_keys** and exit.

> Make sure about following file permissions on files in **.ssh** folder

```bash
chmod 700 ~/.ssh
chmod 644 ~/.ssh/authorized_keys
chmod 644 ~/.ssh/known_hosts
chmod 644 ~/.ssh/config
chmod 600 ~/.ssh/id_rsa
chmod 644 ~/.ssh/id_rsa.pub
```

> Following command will help us to add SSH identity (in case of multiple ssh keys)

```bash
ssh-add ~/.ssh/id_rsa
```

> Following command will help us to remove all SSH identities

```bash
ssh-add -D
```

> Now enter following command in your command line

```bash
ssh username@ip.address
```

?> 😃 That's it , you are now logged into Server.⚡

!> Make Sure ssh-agent(server for SSH) is running on teh Server using following command:

```bash
eval $(ssh-agent -s)
```

[Visual guide for establishing SSH connections - Github](https://github.com/antonykidis/Setup-ssh-for-github/blob/master/Setup-ssh-on-github.pdf)

### ✳Copy content Commandline(MAC)

```bash
pbcopy < ~/.ssh/id_rsa.pub
```