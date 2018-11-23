# Ansible_study
Ansible の使い方を勉強していく過程です
<img src="images/atom.jpg">

## Ubuntu + Virtualbox + Vagrant の仮想マシンでAnsible を使ってみる
いよいよ、Ansible を使ってみましょう。  

1. まず、新たにvagrant フォルダを作り、仮想マシンを１台立ち上げます。  
```sh
me@my_pc:~/$ cd ~  
me@my_pc:~/$ mkdir My_playbooks  
me@my_pc:~/$ cd My_playbooks  
me@my_pc:~/$ vagrant init ubuntu/cosmic64  
me@my_pc:~/$ vagrant ssh  
vagrant@default:~/$ sudo apt-get update  
vagrant@default:~/$ sudo apt-get install python  
```

公式HP  
https://docs.vagrantup.com  
boxを探す  
https://vagrantcloud.com/search  
コマンドラインのマニュアル  
https://www.vagrantup.com/docs/cli/  
Vagrantfileのマニュアル  
https://www.vagrantup.com/docs/vagrantfile/  

 設定可能な項目 | 内容
----|----
 config.vm | 仮想マシンの設定
 config.ssh | TD4
 config.winrm | TD4
 config.winssh | TD4
 config.vagrant | TD4

記法  
https://www.vagrantup.com/docs/vagrantfile/tips.html  
