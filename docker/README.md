# Docker （テスト中．．．）
大阪電気通信大学　升谷教授が作成された「ROS2 + VNC で CRANE+を試すDockerイメージ」の資料を改変している．現在，テスト中．．．

## 概要
VNCというリモートデスクトップアプリを使い，ウェブブラウザでROS2を使うことができるDockerfileとDockerイメージ．
Tiryohさんの以下のgithubをベースに作成されている．
- [tiryoh/ros2-desktop-vnc:foxy](https://github.com/Tiryoh/docker-ros2-desktop-vnc) 
それに，教育用ロボットアームCRANE+のアプリケーションと升谷先生が作られたサンプルプログラムを追加している．
- [crane_plus](https://github.com/rt-net/crane_plus)
- [crane_plus_commander](https://github.com/y-masutani/crane_plus_commander)
- [simple_arm](https://github.com/y-masutani/simple_arm)
- Visual Studio Code (1.57)
- 日本語環境


## Dockerのインストールと設定
  - 次のサイトでうまくいかない場合は，"Install Engine on Ubuntu"で検索してください．  
[Ubuntu20.04：Dockerのインストール](https://demura.net/misc/21830.html)

## Dockerのインストール


**Dockerイメージの作成**  
  - Ubuntuの端末を開き，次のコマンドを1行ごとコピペして端末に張り付けEnterキーを押して実行する．      
```
cd
git clone https://github.com/AI-Robot-Book/docker-ros2-desktop-vnc-ai-robot-book.git
cd docker-ros2-desktop-vnc-ai-robot-book
chmod +x ai-robot-book.sh
docker build --progress=plain -t masutaniy/ros2-desktop-vnc-ai-robot-book:ver1 .
```

## コンテナの作成と起動（初回だけ）
  - 次のdocker runコマンドを実行して，コンテナを作成して起動する．
```
docker run -e RESOLUTION=1920x1080 --name ai_robot_book -p 6080:80 --shm-size=512m masutaniy/ros2-desktop-vnc-ai-robot-book:ver1
```

## コンテナの起動（２回目以降）
  - 上のコマンドだとコンテナを毎回作成してしまい，無駄なコンテナがたくさんできてしまうので，docker startコマンドを実行してコンテナを起動だけにする．なお，startの後は，コンテナ名かコンテナIDを入れる．ここでは，上で作成したコンテナ名ai_robot_bookとしているので適宜変更する．
```
docker start ai_robot_book  
```

## 使い方  
- コンテナを起動したら，ウェブブラウザを開き，以下にアクセスする．  
    - [http://127.0.0.1:6080](http://127.0.0.1:6080)

## コンテナの停止
 - 次のコマンドでコンテナを停止する．
```
docker stop ai_robot_book  
```
