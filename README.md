# Docker Basic

---

## Usage

```
git clone git@bitbucket.org:ykcbit/learn-docker.git
```

## Setup

- 公式 HP から install[Docker-Desktop](https://www.docker.com/products/docker-desktop)
  > > ※PC の OS にあったものを install する

![docker-desktop](./images/docker.png)

## Role

- Docker コンテナ内で開発することで OS が違っても、動作環境が統一され、アプリケーションが問題なく動作可能になる

## Practices

1. DockerCommand
2. Dockerfile
3. docker-compose

## note

- Kubernetes を使用する場合は 1,2 が重要 (3 は使わない?)

- docker image の取得

```
docker search <imageName>
```

- docker container から抜けるショートカットコマンド

```
exit -> ctrl + d
detach -> ctrl + p + q
```

> detach で抜けると container のプロセスを切らずに出られる（動かしたまま）

- detach 後に再度 container に入る

```
docker attach <ContainerName>
```

- docker system prune(一括削除)

  - all stopped containers
  - all networks not used by at least one container
  - all dangling images
  - all dangling build cache(これめっちゃ溜まる)

```
docker system prune
```

- container image volume network 一括削除

```
docker-compose down --rmi all --volumes --remove-orphans
```

## Command collection

- docker

  - docker ps -a
  - docker images
  - docker volume ls
  - docker exec -it `<ContainerName>` bash
  - docker rm `<ContainerName>`
  - docker rmi `<ImageName>`
  - docker volume rm `<VolumeName>`
  - docker container prune
  - dokcer image prune
  - docker volume prune

- docker-compose

  - docker-compose up
  - docker-compose up -d
  - docker-compose up -d --build
  - docker-compose exec `<ServiceName>` bash
  - docker-compose stop
  - docker-compose down
