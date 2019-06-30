- - -

## Docker 명령어

유용한 도커 명령어 사용법 정리
Update : 2019.06.22

버전 및 정보 조회
```
docker --version

docker info
```

이미지 관련 명령
```
docker search “images file name"
    docker search --filter "is-official=true” centos

docker pull

docker images “images file name"
```

컨테이너 생성 및 실행, 재구동
```
docker create “container”
    docker create --name centos01 -it centosdocker start

docker attach “container name or ID”

docker exec -it “container name or ID” /bin/bash

docker stop “container name or ID"

docker kill “container name or ID"

docker restart “container name or ID"

docker run “container name or ID”
    docker run --name centos02 -it centos
    docker run --name ngnix-test -p 8080:80 nginx
    docker run --name centos02 --hostname centos02 -it centos
```

컨테이너 상태 조회
```
docker ps
    docker ps -a
```

컨테이너 이미지 삭제
```
docker rm “container name or ID"

docker rmi “image name"
```

컨테이너 이미지 저장과 외부 Export
```
docker save
    docker save alpine -o alpine_edit.tar
    docker load -I alpine_edit.tar

docker export “container name or ID"
    docker export web_container -o  web_container.tar

docker import
    docker import web_container.tar
```

컨테이너 상태 조회
```
docker history “Image name or ID"

docker logs “Container name or ID”
    docker logs -f “Container name or ID"

docker stats
    docker stats —-no-stream

docker top “container name or ID”

docker inspect
    docker inspect -f "{{.NetworkSettings.IPAddress}}”
```

컨테이너 빌드
```
docker build -t
```

컨테이너 태깅
```
docker tag “source image:tag” “target image:tag”
```

컨테이너 네트워크 
```
docker network create “bridgename” --driver bridge -- subnet “subnet, 172.16.1.0/24” --ip-range "172.16.1.0/24" --gateway “gateway,172.16.1.1"

```

명령어 자동 완성

```
# Mac book 에서 구성 방법

#oh-my-zsh 사용 케이스에서 구성

vi ~/.zshrc

plugins=(
   docker
   docker-compose
   )

## plugin autoload
echo "autoload -Uz compinit; compinit" >> ~/.zshrc

# CentOS

yum update
yum -y install bash-completion
curl https://raw.githubusercontent.com/docker/docker-ce/master/components/cli/contrib/completion/bash/docker -o /etc/bash_completion.d/docker.sh

# Ubuntu

apt-get update
apt-get install bash-completion
curl https://raw.githubusercontent.com/docker/docker-ce/master/components/cli/contrib/completion/bash/docker -o /etc/bash_completion.d/docker.sh
```
