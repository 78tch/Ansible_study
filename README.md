# Ansible_study
Ansible の使い方を勉強していく過程です。  
<img src="images/atom.jpg" alt="image">

# 進め方・概略
1. Ansible はSSH接続の環境が必要なので、Ubuntuマシン上でVirtualboxとVagrant でSSH接続環境を作る。  
2.  


## Ubuntu + Virtualbox + Vagrant でSSH接続環境準備編
1. Ubuntu マシンにapt-get で VagrantとVirtualboxを導入  
2. Vagrant 用のディレクトリを作って初期化（Vagrant init）  
3. 何も設定せず試す（Vagrant status/box list/up）  
4. Vagrantfile に box の設定のみして試す  
5. ホストマシンから VM に ssh で接続してみる。キーはどこにある？ほかにどんな設定が可能なのか（vagrant ssh）  
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

# 進め方・導入編

１．Ansible を導入  
２．  
３．  
