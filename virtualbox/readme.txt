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


■nginx導入 参考(https://qiita.com/MuuKojima/items/afc0ad8309ba9c5ed5ee)
sudo sh -c "echo '[nginx]
name=nginx repo
baseurl=http://nginx.org/packages/mainline/centos/7/$basearch/
gpgcheck=0
enabled=1' > /etc/yum.repos.d/nginx.repo"

sudo yum install nginx
nginx -v
sudo systemctl enable nginx
sudo systemctl start nginx

nginxアクセス確認
http://192.168.33.10/


■vim導入 参考(https://www.server-world.info/query?os=CentOS_7&p=initial_conf&f=7 https://qiita.com/SOJO/items/9d6a65f3da941c49da36)
sudo yum list installed | grep -e mercurial -e ncurses-devel -e make -e gcc
無いものをinstall
sudo yum -y install mercurial
sudo yum -y install ncurses-devel
sudo yum -y install make
sudo yum -y install gcc
sudo yum -y install vim-enhanced 
sudo vim /etc/profile
  最後に追記
  alias vi='vim'
source /etc/profile

■nginxのconf設定
vi /etc/nginx/conf.d/default.conf
    location / {
        root   /sync_folder;
        #root   /usr/share/nginx/html;
vim /sync_folder/index.html
	適当に編集

■ruby導入 ver2.4.0 参考(https://www.server-world.info/query?os=CentOS_7&p=ruby24 https://www.server-world.info/query?os=CentOS_7&p=initial_conf&f=6の[3])
sudo yum -y install centos-release-scl-rh centos-release-scl
sudo yum --enablerepo=centos-sclo-rh -y install rh-ruby24
scl enable rh-ruby24 bash
ruby -v

■rails導入 参考(https://www.rubylife.jp/railsinstall/rails/index3.html)
gem -v
gem update --system







