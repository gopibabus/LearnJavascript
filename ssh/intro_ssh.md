# 🔥 SSH

* **SSH**, or **Secure Shell**, is a remote administration protocol that allows users to control and modify their remote servers over the Internet.
* The service was created as a secure replacement for the unencrypted **Telnet**.

### ✳Syntax

```bash
ssh {user}@{host}

Example: ssh root@162.523.85.567
```
### ✳Copy files between machines

```bash
rsync -av . root@162.523.85.567:~/DevTools
```

> In above command we are copying all files in current working directory to DevTools directory on remote server.
