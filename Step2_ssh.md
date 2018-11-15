# Ansible_study
Ansible の使い方を勉強していく過程です
<img src="images/atom.jpg">

## Ubuntu + Virtualbox + Vagrant でSSH接続環境の前準備編
前回、２台の仮想マシンを用意しましたので、ここでは１台の仮想マシンからもう１台の仮想マシンにSSHで接続できるようにしていきます。  
1. まず、仮想マシンを２台とも立ち上げ、<kbd>ping</kbd> コマンドで疎通を確認します。  
```sh
me@my_pc:~/My_test$ vagrant ssh web  
vagrant@web:$ ping 192.168.33.12  
vagrant@web:$ ssh 192.168.33.12  
```
そうすると、次のようなエラーメッセージが出ると思います。  
```sh
vagrant@web:~$ ssh 192.168.33.12  
"The authenticity of host '192.168.33.12 (192.168.33.12)' can't be established.   
ECDSA key fingerprint is SHA256:40FdK9XWaizUpGmj0SR3NqResNdYEuY2Da+i43+AXVM.  
Are you sure you want to continue connecting (yes/no)?" y  
"Please type 'yes' or 'no':" yes
"Warning: Permanently added '192.168.33.12' (ECDSA) to the list of known hosts. "
"vagrant@192.168.33.12: Permission denied (publickey)."  
vagrant@web:~$
```  
2. ssh-keygen  
3. SSHで必要なファイルとその格納場所のまとめ（/etc/ssh/ ~/.ssh/）  
`~/.ssh/authorized_keys`  
`~/.ssh/known_hosts`  
`/etc/ssh/ssh_host_hoge_key`  
`/etc/ssh/ssh_host_hoge_key.pub`  
4. 別ディレクトリにもvagrant 環境をつくり、３つめのVMを立てて ssh 接続してみる。  
5. Vagrantfile のまとめ  

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
