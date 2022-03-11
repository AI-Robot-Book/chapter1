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
docker build --progress=plain -t masutaniy/ros2-desktop-vnc-ai-robot-book:ver1 .
```

## コンテナの作成と起動（初回のみ） 
  - 次のコマンドを実行して，コンテナを作成して起動する．一度，コンテナを作成したら次回からは起動するだけで良い．
```
docker run -e RESOLUTION=1920x1080 --name ai_robot_book -p 6080:80 --shm-size=512m masutaniy/ros2-desktop-vnc-ai-robot-book:ver1a
```
## コンテナの起動（２回目から）
  - 既にコンテナは作成されているので起動するだけでよい．一度，コンテナを作成したら次回からは起動するだけで良い．
```
docker start -e RESOLUTION=1920x1080 --name ai_robot_book -p 6080:80 --shm-size=512m masutaniy/ros2-desktop-vnc-ai-robot-book:ver1a
```
## 使い方  
- コンテナを起動したら，ウェブブラウザを開き，以下にアクセスする．  
    - [http://127.0.0.1:6080](http://127.0.0.1:6080)
