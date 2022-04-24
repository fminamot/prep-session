# prep-session

## はじめに

ターミナル上でのLinuxコマンドの操作に慣れるための練習です。
最初に演習を実施するためのRHEL8の環境を準備してください。
環境が準備できない方は、RHEL Open Labを使用することができます。

https://developers.redhat.com/courses/red-hat-enterprise-linux/open-lab

RHEL Open Labを起動するとターミナルが表示されます。
ターミナルではスーパーユーザーのプロンプト # が表示されていることが確認できます。
su コマンドを実行して一般ユーザーの rhel にユーザーを切り替えてください。
```
# su - rhel
$
```
シェルプロンプトが # から $ に変わったことを確認してから以下の演習を始めてください。

## 練習問題1: ディレクトリの移動
cdコマンドを使ってカレントディレクトリを移動させましょう。
```
$ cd
$ pwd
/home/rhel
$ cd /
$ ls
bin  boot  dev  etc  home  lib  lib64  media  mnt  opt  proc  root  run  sbin  srv  sys  tmp  usr  var
$ cd home
$ pwd
/home
$ ls
packer  rhel
$ cd rhel
$ ls
$ cd ..
$ pwd
/home
$ cd ..
$ pwd
/
```
## 練習問題2: ファイルの作成と削除
mkdirコマンドを使ったディレクトリを作成し、そのディレクトリの中にtouchコマンドを使ったファイルを作ります。
後処理としてrmコマンドをファイルを削除し、最後にrmdirコマンドでディレクトリを削除します。
```
$ cd
$ pwd
/home/rhel
$ ls
$ mkdir DO400
$ cd DO400
$ ls
file01
$ touch file02
$ touch file03
$ ls
file01  file02  file03
$ rm file01
$ ls
file02  file03
$ rm file02
$ ls
file03
$ rm file03
$ ls
$ cd ..
rmdir DO400
$ ls
$
```
## 練習問題3: ヒストリ機能
練習問題2と同様の処理をヒストリ機能を使って実施します。
ヒストリ機能は、上向き矢印↑とCtrl-rのどちらを使ってもOKです。
```
$ cd
$ mkdir DO400
$ cd DO400
$ pwd
/home/rhel/DO400
$ touch file01
上向き矢印↑で前の行を表示してファイル名を編集しfile02に変更
$ touch file02
上向き矢印↑で前の行を表示してファイル名を編集しfile03に変更
$ touch file03
$ ls
file01  file02  file03
$ cd ..
$ rm -r DO400
```

## 練習問題4: タブ補完
コマンドやファイルパスの入力のときにはできるだけタブ補完を使いましょう。
この演習ではgit cloneコマンドを使ってDO400-appsディレクトリをダウンロードしています。
```
$ cd
$ mkdir DO400
$ ls
DO400
$ cd DO  →Tabキーで補完
$ cd DO400
$ pwd
/home/rhel/DO400
$ git clone https://github.com/RedHatTraining/DO400-apps
Cloning into 'DO400-apps'...
remote: Enumerating objects: 1228, done.
remote: Counting objects: 100% (260/260), done.
remote: Compressing objects: 100% (114/114), done.
remote: Total 1228 (delta 184), reused 146 (delta 146), pack-reused 968
Receiving objects: 100% (1228/1228), 465.38 KiB | 448.00 KiB/s, done.
Resolving deltas: 100% (385/385), done.
$ ls
DO400-apps
$ cd  →Tabキーで補完
$ cd DO400-apps/
$ pwd
/home/rhel/DO400/DO400-apps
$ ls
calculator-microservices  greeting-devsecops       jenkins-agents  shipping-calculator  story-count
calculator-monolith       greeting-service         LICENSE         shopping-cart        tools
exchange-cli              hello                    README.md       shopping-cart-v2
greeting-cd-pipeline      home-automation          school-library  simple-calculator
greeting-console          home-automation-service  scoreboard      simple-webapp
$ cd hello
$ pwd
/home/rhel/DO400/DO400-apps/hello
$ ls
helloworld.py
$ cat hello  →Tabキーで補完
$ cat helloworld.py
print("Hello world!")
$ cd /
$ cd /h →Tabキーで補完
$ cd /home/r →Tabキーで補完
$ cd /home/rhel/DO →Tabキーで補完
$ cd /home/rhel/DO400/D →Tabキーで補完
$ cd /home/rhel/DO400/DO400-apps/ →Tabキーで補完
$ cd /home/rhel/DO400/DO400-apps/hello/
$ cat →Tabキーで補完
$ cat helloworld.py 
print("Hello world!")
```

## 練習問題5: ディレクトリのコピー
練習問題4のDO400-apps/helloディレクトリを親ディレクトリにmyhelloという名前でコピーしてみましょう。
```
$ cd /home/rhel/DO400
$ ls
DO400-apps
$ cp -r DO400-apps/hello ../myhello
$ cd ..
$ pwd
/home/rhel
$ ls
DO400 myhello
$ ls myhello
helloworld.py
$ rm -r myhello
```

