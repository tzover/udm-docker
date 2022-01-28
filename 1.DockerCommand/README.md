# Docker command (CLI)

---

## Learning points

- Docker Hub 上にある docker image を pull する

```
docker pull <imageName>:<tag>

(ex.)
docker pull node:14.15.4-slim
```

- local に所有している docker image から docker container を作成する

> 存在しない場合は Docker Hub から pull されて run される

```
docker run node:14.15.4-slim
```

- 所持している docker image の確認方法

```
docker images
```

- 所持している docker container の確認方法

```
docker ps
docker ps -a
```

> option ( -a ) を付けることで全て表示できる

- exited 状態の docker container を running させる

```
docker restart <ContainerID>
```

- running 状態の docker container に入る

```
docker exec -it <ContainerID> bash
```

- 編集した docker container から新しい image を local に作成する

```
docker commit <ContainerID> <NewImageName>:<tag>
```

> tag を付けられる。Default は latest になる

- docker image の複製時に tag を指定する

```
docker tag <imageName>:<tag> <NewImageName>:<tag>
```

- docker image を docker hub に push する

```
docker push <userName>/<ImageName>:<tag>
```

- docker hub から original image を pull する

```
docker pull <username>/<imageName>:<tag>
```

- docker container の削除

```
docker rm <containerName>
```

- docker image の削除

```
docker rmi <imageName>
```

## Practices

### HelloWorld image の pull と run

```
docker pull hello-world
docker run hello-world
```

処理結果

```
docker ( 🍇 ) :$ docker run -it hello-world

Hello from Docker!
This message shows that your installation appears to be working correctly.

To generate this message, Docker took the following steps:
 1. The Docker client contacted the Docker daemon.
 2. The Docker daemon pulled the "hello-world" image from the Docker Hub.
    (arm64v8)
 3. The Docker daemon created a new container from that image which runs the
    executable that produces the output you are currently reading.
 4. The Docker daemon streamed that output to the Docker client, which sent it
    to your terminal.

To try something more ambitious, you can run an Ubuntu container with:
 $ docker run -it ubuntu bash

Share images, automate workflows, and more with a free Docker ID:
 https://hub.docker.com/

For more examples and ideas, visit:
 https://docs.docker.com/get-started/
```

### ubuntu image を使う

```
docker run -it ubuntu bash
```

- container に名前を付ける

```
docker run -it --name tests ubuntu  bash
```

- container が running -> exited になったら削除する

```
docker run --rm -it --name tests ubuntu  bash
```

- container を detached で run させる

```
docker run -d -it --name tests ubuntu  bash
```

### ubuntu image を Docker Hub へ Push, Pull

- docker image を run

```
docker run -it --name sample ubuntu bash
```

- test ファイルを作成

```
pwd
touch test
```

- container から image を作成

```
docker commit <ContainerID> ubuntu:v1
```

- image から image を名前を変えて複製

```
docker tag ubuntu:v1 <NewImageName>:<tag>

(ex.)
docker tag ubuntu:v1 yt0323/my-practice:v2
```

> <NewImageName>は Docker Hub Repository Name と合わせる

- image を Docker Hub に Push

```
docker push yt0323/my-practice:v2
```

- Docker Hub から image を pull

```
docker pull yt0323/my-practice:v2
docker run yt0323/my-practice:v2
```

---

## note

- local に volume された docker volume の確認方法

```
docker volume ls
```

> たまに確認するとめちゃくちゃゴミが溜まってる

- local に構築された docker network の確認方法

```
docker network ls
```
