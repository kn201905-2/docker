https://qiita.com/hiyuzawa/items/81490020568417d85e86  
https://blog.web.nifty.com/engineer/2714

---
* Docker Hub からイメージを DL する。
```
イメージは、https://hub.docker.com/ から調べることができる。
# docker pull ubuntu:18.04

DL したイメージの確認
# docker images
```

---
* イメージの実行
```
https://docs.docker.jp/engine/reference/commandline/run.html
# docker run -it -d -v /home/docker_share:/home/host_share -p 8080:80 -w /home/dev/chatbot --name myubuntu ubuntu:18.04

オプション
-i : Keep STDIN open even if not attached
-t : Allocate a pseudo-tty
-d : コンテナをデタッチド・モードで起動（コンテナをデーモン化する）
-v : ボリュームマッピング。「ホスト側：コンテナ側」の順序で記述。-v は複数指定可能
-p : ポートマッピング。「ホスト側：コンテナ側」の順序で記述
--name : コンテナに名前を付ける（名前を付けなくても良いが、その後の操作が楽になる。コンテナIDで操作するより、コンテナ名での操作が簡単。）

コンテナ内に入るとき
# docker attach コンテナ名
```

---
* 現在実行中のコンテナの確認
```
# docker ps
```

---
* コンテナ内のコマンド実行
```
# docker exec -it my-ubuntu /bin/bash
```

---
* コンテナの停止＆起動＆再起動＆削除
```
# docker stop my-ubuntu
# docker start my-ubuntu
# docker restart my-ubuntu
# docker rm my-ubuntu

停止したことの確認
# docker ps -a

# docker rm コンテナID
```

---
* イメージの削除
```
# docker images

# docker rmi イメージID
```

---
* イメージ、コンテナの commit、save、load
```
# docker commit 既存のコンテナ名 保存するイメージ名
# docker commit mycentos mycentos_with_httpd

https://docs.docker.jp/engine/reference/commandline/save.html
https://docs.docker.jp/engine/reference/commandline/load.html
# docker save sample-image > sample-image.tar
# docker load < sample-image.tar

https://docs.docker.jp/engine/reference/commandline/export.html
https://docs.docker.jp/engine/reference/commandline/import.html
# docker export sample-container > sample-container.tar
# cat example-container.tar | docker import - new-image:latest
```
