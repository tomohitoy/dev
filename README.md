# 開発用ツール

## 開発用環境
* CentOS 6.7
* Ruby 2.3.1 with rbenv
* PostgreSQL 9.5.2
* Nginx
* vim

## `vagrant up` するまでの手順
### 1. Mac OSXの場合
1. 必要となるものをインストールする
  * これらの手順は`sh mac_init.sh`だけで完了する。
  * インストールされるパッケージは下記の通り
    * `git`
    * `ansible`
    * `VirtualBox`(brew-cask)
    * `Vagrant`(brew-cask)

2. CentOS 6.7をVagrantboxに追加する
  * 利用しているBoxは`centos67`と命名しVagrantfileに設定済み。
  * centos67として設定するには、下記のコマンド。
  * `vagrant box add centos67 https://github.com/CommanderK5/packer-centos-template/releases/download/0.6.7/vagrant-centos-6.7.box`
  * vagrantboxは[http://www.vagrantbox.es/](こちら)から参照
  * CentOS6.7では動作確認。

## これからやりたいこと
1. Railsユーザを作ってそちらでデプロイできるようにする。
2. vmを二つ作って、片方を公開用、もう片方を開発ようにする。

## 開発時の注意点

### 1. PostgreSQLのPeer認証がうまく行かない。(現在この手順が必要かわかりません。)
* その場合には、`/var/lib/pgsql/9.4/data/pg_hba.conf`上にある、下記の値を修正します

```/var/lib/pgsql/9.4/data/pg_hba.conf
# local all all peer
local all all trust
```

その後PostgreSQLをrestartして再起動します。
