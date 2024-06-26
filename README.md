# What is PyserSSH

PyserSSH is a library for remote control your code with ssh client. The aim is to provide a scriptable SSH server which can be made to behave like any SSH-enabled device.

This project is part from [damp11113-library](https://github.com/damp11113/damp11113-library)

This Server use port **2222** for default port

> [!WARNING]  
> For use in product please **generate new private key**! If you still use this demo private key maybe your product getting **hacked**! up to 90%. Please don't use this demo private key for real product.

# Install
Install from pypi
```bash
pip install PyserSSH
```
Install from github
```bash
pip install git+https://github.com/damp11113/PyserSSH.git
```

# Quick Example
```py
import os

from PyserSSH import Server, Send, AccountManager

useraccount = AccountManager()
useraccount.add_account("admin", "") # create user without password

ssh = Server(useraccount)

@ssh.on_user("command")
def command(client, command: str):
    if command == "hello":
        Send(client, "world!")
        
ssh.run(os.path.join(os.path.dirname(os.path.realpath(__file__)), 'private_key.pem'))
```
This example you can connect with `ssh admin@localhost -p 2222` and press enter on login
If you input `hello` the response is `world`

# Demo
https://github.com/damp11113/PyserSSH/assets/64675096/49bef3e2-3b15-4b64-b88e-3ca84a955de7

For run this demo you can use this command
```
$ python -m PyserSSH
```
then
```
Do you want to run demo? (y/n): y
```
But if no [damp11113-library](https://github.com/damp11113/damp11113-library)
```
No 'damp11113-library'
This demo is require 'damp11113-library' for run
```
you need to install [damp11113-library](https://github.com/damp11113/damp11113-library) for run this demo by choose `y` or `yes` in lowercase or uppercase
```
Do you want to install 'damp11113-library'? (y/n): y
```
For exit demo you can use `ctrl+c` or use `shutdown now` in PyserSSH shell **(not in real terminal)**

I intend to leaked private key because that key i generated new. I recommend to generate new key if you want to use on your host because that key is for demo only.
why i talk about this? because when i push private key into this repo in next 5 min++ i getting new email from GitGuardian. in that email say "
GitGuardian has detected the following RSA Private Key exposed within your GitHub account" i dont knows what is GitGuardian and i not install this app into my account.