# chapter1
「AIロボット入門」第1章のサポート情報．現在，テスト中．．．

## Docker 
大阪電気通信大学　升谷教授の資料から抜粋  
- **Dockerのインストール**  
次のサイトを参照  
[Ubuntu20.04：Dockerのインストール](https://demura.net/misc/21830.html)   
- **Dockerイメージの作成**  
Ubuntuの端末を開き，次のコマンドを1行ごとコピペして端末に張り付けEnterキーを押して実行する．      
```
cd
git clone https://github.com/AI-Robot-Book/docker-ros2-desktop-vnc-ai-robot-book.git
cd docker-ros2-desktop-vnc-ai-robot-book
docker build --progress=plain -t masutaniy/ros2-desktop-vnc-ai-robot-book:ver1 .
```
- **実 行**  
次のコマンドを実行する．多くのファイルをダウンロードするので時間がかかる．      
```
docker run -e RESOLUTION=1920x1080 --name ai_robot_book -p 6080:80 --shm-size=512m masutaniy/ros2-desktop-vnc-ai-robot-book:ver1a
```
