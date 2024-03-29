# Ansible_study
Ansible の使い方を勉強していく過程です
<img src="images/atom.jpg">

## 学習環境として Ubuntu + Visual Studio Code + Github で学習環境の構築
学習を進めるにあたり、学習メモをVSCode でMarkdown 形式で書き残し、Github にアップしていきます。  
  
1. Ubuntu マシンにapt-get で git を導入  
```sh  
$ sudo apt-get install git  
$ git config --global user.name "My_Name"  
$ git config --global user.email "My_email"  
$ git config --global credential.helper store
```  
2. Visual Studio Code を公式HP からインストールし、必要な機能拡張（Extensions）を導入する。  
3.Github で学習用のレポジトリを作り、VSCode でローカルにpull する。  
4. Vagrantfile に box の設定のみして試す  
```sh
$ vi Vagrantfile
```  
`config.vm.box = "base"`  
となっている行を見つけて、以下のように修正。  
`config.vm.box = "ubuntu/cosmic64"`  
と直す。  
これは、ユーザー"ubuntu"さんが作った"cosmic64"という仮想マシンの雛形（box）を、vagrant の公式サイトからダウンロードしてきて使います、という意味になる。  
box は自分で作ることもでき、  
`$ vagrant package --base "VM名" --output "box名"`  
とすることでboxファイルが生成される。
```sh
$ vagrant up
```  
２０〜３０分かかると思うので、しばらく放置。  
またこのときに、  
`~/.vagrant.d`  
や  
`~/VirtualBox VMs`  
というディレクトリも作成される。  
box ファイルは　`~/.vagrant.d`　配下に保存され、仮想マシンの雛形として利用される。実際の仮想マシンは、これを　`~/VirtualBox VMs`　配下にコピーして格納される。  
待っている間に、ホームディレクトリを「隠しファイルを表示する」で表示しておくとこれらのディレクトリが作成されるのが見られたり、またVirtualbox マネージャー 画面を表示しておくと、vagrant コマンドによって仮想マシンが登録されて起動・シャットダウンされるのが確認できる。  
通信環境がない（貧弱な）場合、boxのアップデートチェックをしないようにもできる。（非推奨だが学習時にはありうる。）  

` config.vm.box_check_update = false `

ファイル|置き場所|役割  
--|--|--  
Vagrantfile|初期化したフォルダ直下|仮想マシンの設定  
boxファイル|~/.vagrant.d|仮想マシンの雛形  
仮想マシンファイル|~/VirtualBox VMs|実際の仮想マシンのファイル  
ログインユーザーの公開鍵|リモートSSHサーバーの~/.ssh/authorized_keys|id_rsa.pubの内容を追記したもの。
ログインユーザーの秘密鍵| .vagrant/machines/default/virtualbox/private_key|id_rsaをリネームしたもの。$ vagrant ssh-config で場所を確認できる。

![vagrant_init](images/vagrant_init.png)

5. ホストマシンから VM に ssh で接続してみる。キーはどこにある？ほかにどんな設定が可能なのか（vagrant ssh）  

```sh
$ vagrant status
$ vagrant box list  
$ vagrant halt
$ vagrant status
$ vagrant up
$ vagrant status
```  

この状態で、vm にssh 接続してみる。  

```sh  
$ vagrant ssh-config  
```  
これにより、SSHに関する情報が表示される。  
秘密鍵の場所は「IdentityFile」の項でパスが書いてある。

```sh  
$ vagrant ssh  
vagrant@default :$ hostname  
vagrant@default :$ ifconfig
```  

6. Vagrantfile で hostname と ip を設定してみる。  
`config.vm.hostname = "web"`  
`config.vm.network :private_network, ip:"192.168.33.11"`  
これで<kbd>vagrant up</kbd>して、改めて<kbd>vagrant ssh</kbd>してみると  
```sh
$ hostname  
$ ifconfig  
```  
7. いちど仮想マシンを削除しする。て作り直してみる。  
```sh  
$ vagrant destroy  
$ vagrant up  
```  
8. define で複数の項目を設定してみる  
`config.vm.define :web do |web|`  
`web.vm.hostname = "web"`  
`web.vm.network :private_network, ip:"192.168.33.11"`  
`end`  
先にVagrantfile を書き換えてしまうと、古い仮想マシンが残ってしまう。  
一時的にVagrantfile を元に戻して、<kbd>vagrant destroy</kbd>すれば消せる。  
改めて<kbd>vagrant up</kbd>してから<kbd>hostname</kbd>と<kbd>ifconfig</kbd>してみる。  
9. ひとつのVagrantfile で２つのVMを設定してみる。  
`config.vm.define :web do |web|`  
`web.vm.hostname = "web"`  
`web.vm.network :private_network, ip:"192.168.33.11"`  
`end`  
`config.vm.define :db do |db|`  
`db.vm.hostname = "db"`  
`db.vm.network :private_network, ip:"192.168.33.12"`  
`end`  
こうすると、<kbd>vagrant up</kbd>すれば仮想マシン「web」と「db」が立ち上がる。  
複数の仮想マシンが定義されたVagrant 環境では、コマンドの引数に仮想マシン名を指定して、対象を区別する。  
```sh  
$ vagrant ssh  
$ vagrant ssh web  
$ vagrant halt db  
$ vagrant status  
$ vagrant up db  
$ vagrant status  
$ vagrant destory web  
$ vagrant status  
$ vagrant halt db  
$ vagrant status  
$ vagrant up web  
$ vagrant status  
```  
など、いろいろ試してみる。  
10. VM 間でSSH接続する。（ssh-keygen）  
Virtualbox のネットワークの割当の種類  
* NAT:()デフォルトのため、設定をしない場合これになる。外部からVMには接続できない
* ブリッジアダプター:(public_network)ホストと同一のネットワークになり、ホストからだけでなく、外部マシンからも接続できる。
* 内部ネットワーク:（private_network,virtualbox_intnet）VM同士は接続できるが、ホストや外部マシンからVMへは接続できない。
* ホストオンリーアダプター:（private_network）ホストやVM同士は接続できるが、外部マシンからVMへは接続できない。
* 汎用ドライバー:
* NATネットワーク:

11. SSHで必要なファイルとその格納場所のまとめ（/etc/ssh/ ~/.ssh/）  
12.  別ディレクトリにもvagrant 環境をつくり、３つめのVMを立てて ssh 接続してみる。  
13. Vagrantfile のまとめ  

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

　~/.ssh/authorized_keys  
 ~/.ssh/known_hosts  
 /etc/ssh/ssh_host_hoge_key  
 /etc/ssh/ssh_host_hoge_key.pub  
