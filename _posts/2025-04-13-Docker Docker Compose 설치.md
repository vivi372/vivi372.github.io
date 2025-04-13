---
title: Docker / Docker Compose 설치
date: 2025-04-13 20:40:00 +09:00
categories:
  - Server
tags:
  - Server
  - Ubuntu
  - Docker
---

# Docker

Docker는 가상 머신처럼 독립된 실행환경을 만들어주는 것으로, 운영체제를 설치하는 것과 유사한 효과를 낼 수 있지만, 실제 운영체제를 설치하지 않기 때문에 설치 용량이 적고 실행 속도 또한 빠르다. 원도우에 VM Ware와 같은 가상 머신을 설치하여 사용했으나 최근에는 리눅스 계열에서 Docker가 그 역할을 대신하고 있다.

도커 컨테이너는 일종의 소프트웨어를 소프트웨어의 실행에 필요한 모든 것을 포함하는 완전한 파일 시스템 안에 감싼다. 여기에는 코드, 런타임, 시스템 도구, 시스템 라이브러리 등 서버에 설치되는 무엇이든 아우른다. 이는 실행 중인 환경에 관계 없이 언제나 동일하게 실행될 것을 보증한다.

출처: 위키 백과

## Docker 설치

### 패키지 업데이트

```bash
sudo apt-get update
```

### Docker 패키지 추가

```bash
sudo apt-get install apt-transport-https ca-certificates curl gnupg-agent software-properties-common
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"
```

### 패키지 업데이트


```bash
sudo apt-get update
```

### Docker 설치

```bash
sudo apt-get install docker-ce docker-ce-cli containerd.io
```
### 실행 권한 부여

```bash
sudo chmod 666 /var/run/docker.sock
```

### Docker 설치 확인

```bash
sudo systemctl status docker
```

# Docker-compose

단일 서버에서 여러개의 컨테이너를 하나의 서비스로 정의해 컨테이너의 묶음으로 관리할 수 있는 작업 환경을 제공하는 관리 도구

## Docker-compose 설치

### 다운로드 및 설치

```bash
sudo curl -L "https://github.com/docker/compose/releases/download/v2.29.3/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
```

### 실행 권한 부여

```bash
sudo chmod +x /usr/local/bin/docker-compose
```

### Docker-compose 설치 확인

```bash
docker-compose --version
```