# chapter1
「AIロボット入門」第1章のプログラム

## Docker 
大阪電気通信大学　升谷教授の資料から抜粋  
- Dockerのインストール  
次のサイトを参照  
[Ubuntu20.04：Dockerのインストール](https://demura.net/misc/21830.html)   
- Dockerイメージの作成  
Ubuntuの端末を開き，次のコマンドを実行する．      
```
docker build --progress=plain -t masutaniy/ros2-desktop-vnc-ai-robot-book:ver1 .
```
- 実行  
Ubuntuの端末を開き，次のコマンドを実行する．      
```
docker run -e RESOLUTION=1920x1080 --name ai_robot_book -p 6080:80 --shm-size=512m masutaniy/ros2-desktop-vnc-ai-robot-book:ver1a
```
