# Ansible_study
Ansible の使い方を勉強していく過程です
<img src="images/atom.jpg">

## Ubuntu + Virtualbox + Vagrant でSSH接続環境準備編
1. Ubuntu マシンにapt-get で VagrantとVirtualboxを導入  
```
$ sudo apt-get install virtualbox vagrant
```
2. Vagrant 用のディレクトリを作って初期化（Vagrant init）  
```
$ mkdir MyLesson
$ cd ./MyLesson
$ ls
$ vagrant status
$ vagrant box list
$ vagrant up
$ vagrant init
$ ls
```
3. 何も設定せず試す（Vagrant status/box list/up）  
```
$ vagrant up
```
4. Vagrantfile に box の設定のみして試す  
```
$ vi Vagrantfile
```  
`config.vm.box = "base"`  
となっている行を見つけて、以下のように修正。  
`config.vm.box = "ubuntu/cosmic64"`  
と直す。  
これは、ユーザー"ubuntu"さんの"cosmic64"という仮想マシンの雛形（box）を、公式サイトからダウンロードしてきて使います、という意味になる。  
box は自分で作ることもでき、  
`$ vagrant package --base "VM名" --output "box名"`  
とすることでboxファイルが生成される。
```
$ vagrant up
```  
２０〜３０分かかると思うので、しばらく放置。  
5. ホストマシンから VM に ssh で接続してみる。キーはどこにある？ほかにどんな設定が可能なのか（vagrant ssh）  
```
$ vagrant status
$ vagrant box list  
$ vagrant halt
$ vagrant status
$ vagrant up
$ vagrant status
```  
この状態で、vm にssh 接続してみる。  
```
$ vagrant ssh  
```  

6. Vagrantfile で hostname と ip を設定してみる。  
7. ひとつのVagrantfile で２つのVMを設定してみる。  
8. VM 間でSSH接続する。（ssh-keygen）  
9. SSHで必要なファイルとその格納場所のまとめ（/etc/ssh/ ~/.ssh/）  
10. 別ディレクトリにもvagrant 環境をつくり、３つめのVMを立てて ssh 接続してみる。  
11. Vagrantfile のまとめ  

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

# 第１段階・Vagrant でテスト環境準備編
１．Ubuntu マシンにVagrantとVirtualboxを導入  
```sh
$ sudo apt-get install virtualbox vagrant
```

a  
`user `


udo apt-get install virtualbox vagrant ''  
２．Vagrant 用のディレクトリを作って初期化  
`user00@HostMachine:~$ mkdir hoge`  
`user00@HostMachine:~$cd ./hoge`  
`user00@HostMachine:~/hoge$vagrant init`  
３．何も設定せず試す  
`user00@HostMachine:~/hoge$vagrant up`  
エラーメッセージを読む。  
４．boxを選定し、boxの設定のみして試す  
５．ボックスのリスト、ステータスをみる。デストロイ、リムーブを試す。  
６．ssh で接続してみる、キーはどこにある？ほかにどんな設定が可能なのか  
　~/.ssh/authorized_keys  
 ~/.ssh/known_hosts  
 /etc/ssh/ssh_host_hoge_key  
 /etc/ssh/ssh_host_hoge_key.pub  
