# Ansible_study
Ansible の使い方を勉強していく過程です
<img src="https://github.com/78tch/Ansible_study/blob/master/images/atom.jpg"/>

# 第１段階・Vagrant でテスト環境準備編
１．Ubuntu マシンにVagrantとVirtualboxを導入  
`sudo apt-get install virtualbox vagrant`  
２．Vagrant 用のディレクトリを作って初期化  
`user00@HostMachine:~$ mkdir hoge`  
`user00@HostMachine:~$cd ./hoge`  
`user00@HostMachine:~/hoge$vagrant init`  
３．何も設定せず試す  
`user00@HostMachine:~/hoge$vagrant up`  
エラーメッセージを読む。  
４．boxを選定し、boxの設定のみして試す  
５．ボックスのリスト、ステータスをみる。デストロイ、リムーブを試す。  
５．ssh で接続してみる、キーはどこにある？ほかにどんな設定が可能なのか
６．hostname と ip を設定  
７．同一ディレクトリで２つのVMを立ててssh で接続  
８．別ディレクトリで３つめのVMを立ててssh で接続  
９．Vagrant ファイルのまとめ  

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
