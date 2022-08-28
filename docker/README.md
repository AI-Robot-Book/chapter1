# Dockerイメージの使い方

ROS2とPythonで作って学ぶAIロボット入門（出村・萩原・升谷・タン著，講談社，以下では「この本」と書きます）のためのDockerイメージの使い方を説明します．

## 概要

- Dockerを使ってこの本の教材をすぐに試すことのできるデスクトップ環境を提供します．Ubuntu Linuxでは，ハードウェアの利用も可能です．Windowsでは，ハードウェアの利用はできませんが，シミュレーションの実行が可能です．MacOSでも利用できると思われますが，確認していません．
- 提供するDockerのイメージには以下の内容が含まれており，個別のインストールは不要です．
  - Ubuntu 20.04 デスクトップ環境（日本語化済み）
  - テキストエディタ VSCodium
  - ROS Foxy
  - この本の教材に必要なパッケージ・ライブラリ
  - この本のサンプルプログラム
- Dockerイメージの作り方については，この文書では説明しません．[こちらのリポジトリ](https://github.com/AI-Robot-Book/docker-ros2-desktop-ai-robot-book)を見てください．

## Ubuntu Linuxの場合

### Dockerのインストール
```
sudo apt install docker
sudo adduser ＄USER docker
```

### コンテナの起動

- 利用するコンピュータをインターネットに接続します．
- 起動コマンドが長いので，[ここからシェルスクリプトrun.bash](https://raw.githubusercontent.com/AI-Robot-Book/docker-ros2-desktop-ai-robot-book/ai-robot-book/run.bash)をダウンロードします．
- ダウンロードしたファイルを適当なディレクトリに置きます．
- 端末ウィンドウを開き，以下を入力して実行します．
  ```
  cd run.bashを置いたディレクトリ
  chmod +x run.bash
  ./run.bash
  ```
- 初めて起動する場合は，DockerHubからイメージ（約10GB）をダウンロードするので，かなり時間がかかります．
- 以下のような内容が表示されたら，コンテナの準備完了です．
  ```
  2022-08-28 16:06:25,549 INFO success: lxpanel entered RUNNING state, process has stayed up for > than 1 seconds (startsecs)
  2022-08-28 16:06:25,549 INFO success: pcmanfm entered RUNNING state, process has stayed up for > than 1 seconds (startsecs)
  2022-08-28 16:06:25,549 INFO success: x11vnc entered RUNNING state, process has stayed up for > than 1 seconds (startsecs)
  2022-08-28 16:06:25,549 INFO success: novnc entered RUNNING state, process has stayed up for > than 1 seconds (startsecs)
  ```

### コンテナによるデスクトップ環境の利用

コンテナが的供するデスクトップ環境の利用には複数の方法があります．

- ウェブブラウザを使う場合

  - ウェブブラウザを起動する．
  - アドレス欄に「`http://127.0.0.1:6080`」と入力しEnterキーを押します．
  - ブラウザ内に以下のような内容が表示されればOKです．  
    <img src="images/ubuntu-firefox-1.png" width="70%">

  - この本のDockerイメージで利用しているデスクトップ環境LXDEでは，画面の下辺にアイコンなどが表示されますので，このままでは操作できません．画面の左辺のタブをクリックしてnoVNCのメニューアイコンを表示します．  
    <img src="images/ubuntu-firefox-2.png" width="70%">

  - Fullscreenのアイコンをクリックして，全画面表示にします．  
    <img src="images/ubuntu-firefox-3.png" width="70%">

  - デスクトップ環境での操作は他と共通ですので，後述します．

  - 終わりたい場合は，ログアウトやサインアウトは要りません．noVNCのメニューを出し，Dosconnectのアイコンをクリックします．ウェブブラウザ（のタブ）も閉じて構いません．

- Remminaを使う場合

  - Remmina（Ubuntu標準のリモートデスクトップクライアント）を起動します．  
    <img src="images/ubuntu-remmina-1.png" width="50%">

  - アドレス欄の左側をクリックしてプロトコルとして「VNC」を選び，アドレス欄に「127.0.0.1:15900」を入力しEnterキーを押します．  
    <img src="images/ubuntu-remmina-2.png" width="50%">

  - 別のウィンドウが現れ，以下のような内容が表示されればOKです．  
    <img src="images/ubuntu-remmina-3.png" width="70%">

  - ウィンドウ左辺のアイコンの並びの中から「全画面モードのオン/オフ」をクリックして，全画面表示にします．  
    <img src="images/ubuntu-remmina-4.png" width="70%">

  - デスクトップ環境での操作は他と共通ですので，後述します．

  - 終わりたい場合は，ログアウトやサインアウトは要りません．画面の上辺にマウスカーソルを移動させて，RemminaのNCのメニューを出し，「切断」のアイコンをクリックします．最初のRemminaのウィンドウも閉じて構いません．  
    <img src="images/ubuntu-remmina-5.png" width="70%">

### コンテナの中断

デスクトップ環境を切断しただけでは，まだコンテナはメモリ上に存在しています．これを停止するには，別の端末ウィンドウを開いて，以下のように入力しEnterキーを押します．
```
docker stop ai_robot_book
```
`ai_robot_book`はコンテナを起動したときにコンテナに付けた名前です．

### コンテナの再開

停止したコンテナを再び使えるようにするには，端末ウィンドウで以下のように入力しEnterキーを押します．
```
docker start ai_robot_book
```
### コンテナの削除

コンテナ上での作業内容を全て破棄して，コンテナを削除するには，端末ウィンドウで以下のように入力しEnterキーを押します．
```
docker rm ai_robot_book
```

## Windowsの場合

### Dockerのインストール

### コンテナの起動

- 利用するコンピュータをインターネットに接続します．
- 起動コマンドが長いので，[ここからバッチファイルrun.bat](https://raw.githubusercontent.com/AI-Robot-Book/docker-ros2-desktop-ai-robot-book/ai-robot-book/run.bat)をダウンロードします．
- ダウンロードしたファイルを適当なディレクトリに置きます．
- エクスプローラでディレクトリを開き，アドレス欄に「cmd」と入力しEnterキーを押します．すると，そこをカレントディレクトリとしてコマンドプロンプトが起動します．

- コマンドプロンプトのウィンドウ内で以下を入力して実行します．
  ```
  run.bat
  ```
- 初めて起動する場合は，DockerHubからイメージ（約10GB）をダウンロードするので，かなり時間がかかります．
- 以下のような内容が表示されたら，コンテナの準備完了です．
  ```
  2022-08-28 16:06:25,549 INFO success: lxpanel entered RUNNING state, process has stayed up for > than 1 seconds (startsecs)
  2022-08-28 16:06:25,549 INFO success: pcmanfm entered RUNNING state, process has stayed up for > than 1 seconds (startsecs)
  2022-08-28 16:06:25,549 INFO success: x11vnc entered RUNNING state, process has stayed up for > than 1 seconds (startsecs)
  2022-08-28 16:06:25,549 INFO success: novnc entered RUNNING state, process has stayed up for > than 1 seconds (startsecs)
  ```

### コンテナによるデスクトップ環境の利用

コンテナが的供するデスクトップ環境の利用には複数の方法があります．

- ウェブブラウザを使う場合

  - ウェブブラウザを起動する．
  - アドレス欄に「`http://127.0.0.1:6080`」と入力しEnterキーを押します．
  - ブラウザ内に以下のような内容が表示されればOKです．  

  - この本のDockerイメージで利用しているデスクトップ環境LXDEでは，画面の下辺にアイコンなどが表示されますので，このままでは操作できません．画面の左辺のタブをクリックしてnoVNCのメニューアイコンを表示します．  

  - Fullscreenのアイコンをクリックして，全画面表示にします．  

  - デスクトップ環境での操作は他と共通ですので，後述します．

  - 終わりたい場合は，ログアウトやサインアウトは要りません．noVNCのメニューを出し，Dosconnectのアイコンをクリックします．ウェブブラウザ（のタブ）も閉じて構いません．

- VNCビューアを使う場合

### コンテナの中断


### コンテナの再開


### コンテナの削除



## デスクトップ環境の使い方（共通事項）

## ハードウェアの使い方

### 音声入出力

### USB接続機器

## ヘルプ

Q&Aなどを追加する予定です．

## Windows リモートデスクトップ接続の利用（未完成）

## 著者

升谷 保博

## 履歴

- 2022-08-28: ドキュメントの整備

## 参考文献
