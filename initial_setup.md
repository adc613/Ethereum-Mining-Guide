# Initial Setup (Optional)
There are few things I like to do just to get setup and situated.
1) IMPORTANT: install vim also I install tmux and openssh-server
```
sudo apt-get install vim git tmux openssh-server -y
```
2) Setup .vimrc I have a simple dotfile that I have in order to get quickly
situated
```
git clone https://github.com/adc82/Dotfiles.git
ln -s Dotfiles/vanilla_settings/.vimrc ~/.vimrc
ln -s Dotfiles/vanilla_settings/.tmux.conf ~/.tmux.conf
```
3) Setup ssh server
From mining rig:
```
mkdir ~/.ssh
```
From local machine:
```
scp ~/.ssh/id_rsa.pub username@ipaddress:~/.ssh/authorized_keys
```
4) Test by trying to ssh into the machine, if you're prompted for a password
there was mistake
5) Assuming you passed the test Edit /etc/ssh/sshd_config and change the line:
```
# PasswordAuthentication yes
```
to 
```
PasswordAuthentication no
```
6) Finally restart your ssh server and we should be good to go
```
sudo service ssh restart
```

***Also don't forget to install updates and everything***
```
sudo apt-get update
sudo apt-get upgrade
```
