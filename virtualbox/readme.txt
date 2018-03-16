■仮想サーバセッティング
・vagrantをインストール
・virtualboxをインストール
vagrant box add centos7 https://github.com/CommanderK5/packer-centos-template/releases/download/0.7.2/vagrant-centos-7.2.box


■エラー対策
□フォルダー同期ができない

vagrant plugin install vagrant-vbguest

vagrant vbguest

vagrant ssh

エラーで出ているバージョンのkernel-develをインストール
$ sudo yum -y install http://ftp.riken.jp/Linux/cern/centos/7/updates/x86_64/Packages/kernel-devel-3.10.0-514.26.2.el7.x86_64.rpm

vagrant vbguest --status
[OK]なら完了]

参考
https://qiita.com/ak-ymst/items/bdc37aaf53f857d37fcc
https://qiita.com/iwsksky/items/1374b1f9ed311c1e8423
