# AI/SW 개발 워크스테이션 구축

![코디세이 로고](https://codyssey.kr/assets/logo-vertical-BAqw98XA.png)


# 프로젝트 개요(미션 목표 요약)
본 프로젝트는 개발의 기초가 되는 터미널 조작, Docker 컨테이너 환경 구축, Git/GitHub을 이용한 버전 관리 및 협업 환경 설정을 목표로 합니다. 재현 가능한 개발 환경을 구축하고, 문제를 해결하는 사고방식을 익힙니다.

## 1) 실행 환경
- OS: macOS 15.7.4
- Shell: zsh 5.9
- Docker: 28.5.2
- Git: 2.53

## 2) 수행 체크리스트
- [x] 터미널 기본 조작 및 폴더 구성
- [x] 권한 변경 실습
- [x] Docker 설치/점검
- [x] hello-world 실행
- [x] Dockerfile 빌드/실행
- [x] 포트 매핑 접속(2회)
- [ ] 바인드 마운트 반영
- [ ] 볼륨 영속성
- [ ] Git 설정 + VSCode GitHub 연동

 ## 3) 수행 로그(발췌)

### 01 터미널 기본 조작 및 폴더 구성

```bash
# 문서(Documents) 폴더 내에 프로젝트 폴더 생성
mkdir -p ~/Documents/codyssey/
cd ~/Documents/codyssey/
```


```bash
# 현재 위치를 확인하고 폴더를 생성합니다.
$ pwd
/Users/gdone90098008/Documents/codyssey

$ mkdir codyssey-e1-1
$ cd codyssey-e1-1

$ mkdir practice 
$ cd practice

$ pwd
/Users/gdone90098008/Documents/codyssey/codyssey-e1-1/practice

# 빈 텍스트 파일을 생성하고 내용을 확인해봅니다.
$ echo "Terminal Practice" > hello.txt
$ cat hello.txt
Terminal Practice
````

### 02 권한 변경 실습


```bash
$ ls -l
hello.txt
-rw-r--r--  1 gdone90098008  gdone90098008  18 Apr  3 12:39 hello.txt

$ chmod 644 hello.txt
$ ls -l
hello.txt
-rw-r--r--  1 gdone90098008  gdone90098008  18 Apr  3 12:39 hello.txt

$ chmod 755 hello.txt
$ ls -l 
hello.txt    
-rwxr-xr-x  1 gdone90098008  gdone90098008  18 Apr  3 12:39 hello.txt
```

### 03 Docker 설치/점검

```bash
$ docker --version
Docker version 28.5.2, build ecc6942

$ docker info
Client:
 Version:    28.5.2
 Context:    orbstack
 Debug Mode: false
 Plugins:
  buildx: Docker Buildx (Docker Inc.)
    Version:  v0.29.1
    Path:     /Users/gdone90098008/.docker/cli-plugins/docker-buildx
  compose: Docker Compose (Docker Inc.)
    Version:  v2.40.3
    Path:     /Users/gdone90098008/.docker/cli-plugins/docker-compose

Server:
 Containers: 0
  Running: 0
  Paused: 0
  Stopped: 0
 Images: 0
 Server Version: 28.5.2
 Storage Driver: overlay2
  Backing Filesystem: btrfs
  Supports d_type: true
  Using metacopy: false
  Native Overlay Diff: true
  userxattr: false
 Logging Driver: json-file
 Cgroup Driver: cgroupfs
 Cgroup Version: 2
 Plugins:
  Volume: local
  Network: bridge host ipvlan macvlan null overlay
  Log: awslogs fluentd gcplogs gelf journald json-file local splunk syslog
 CDI spec directories:
  /etc/cdi
  /var/run/cdi
 Swarm: inactive
 Runtimes: io.containerd.runc.v2 runc
 Default Runtime: runc
 Init Binary: docker-init
 containerd version: 1c4457e00facac03ce1d75f7b6777a7a851e5c41
 runc version: d842d7719497cc3b774fd71620278ac9e17710e0
 init version: de40ad0
 Security Options:
  seccomp
   Profile: builtin
  cgroupns
 Kernel Version: 6.17.8-orbstack-00308-g8f9c941121b1
 Operating System: OrbStack
 OSType: linux
 Architecture: x86_64
 CPUs: 6
 Total Memory: 15.67GiB
 Name: orbstack
 ID: 0331763c-ddd4-4207-9715-2232c2594c28
 Docker Root Dir: /var/lib/docker
 Debug Mode: false
 Experimental: false
 Insecure Registries:
  ::1/128
  127.0.0.0/8
 Live Restore Enabled: false
 Product License: Community Engine
 Default Address Pools:
   Base: 192.168.97.0/24, Size: 24
   Base: 192.168.107.0/24, Size: 24
   Base: 192.168.117.0/24, Size: 24
   Base: 192.168.147.0/24, Size: 24
   Base: 192.168.148.0/24, Size: 24
   Base: 192.168.155.0/24, Size: 24
   Base: 192.168.156.0/24, Size: 24
   Base: 192.168.158.0/24, Size: 24
   Base: 192.168.163.0/24, Size: 24
   Base: 192.168.164.0/24, Size: 24
   Base: 192.168.165.0/24, Size: 24
   Base: 192.168.166.0/24, Size: 24
   Base: 192.168.167.0/24, Size: 24
   Base: 192.168.171.0/24, Size: 24
   Base: 192.168.172.0/24, Size: 24
   Base: 192.168.181.0/24, Size: 24
   Base: 192.168.183.0/24, Size: 24
   Base: 192.168.186.0/24, Size: 24
   Base: 192.168.207.0/24, Size: 24
   Base: 192.168.214.0/24, Size: 24
   Base: 192.168.215.0/24, Size: 24
   Base: 192.168.216.0/24, Size: 24
   Base: 192.168.223.0/24, Size: 24
   Base: 192.168.227.0/24, Size: 24
   Base: 192.168.228.0/24, Size: 24
   Base: 192.168.229.0/24, Size: 24
   Base: 192.168.237.0/24, Size: 24
   Base: 192.168.239.0/24, Size: 24
   Base: 192.168.242.0/24, Size: 24
   Base: 192.168.247.0/24, Size: 24
   Base: fd07:b51a:cc66:d000::/56, Size: 64

WARNING: DOCKER_INSECURE_NO_IPTABLES_RAW is set
```
### hello-world 실행

```zsh
$ docker run hello-world
Unable to find image 'hello-world:latest' locally
latest: Pulling from library/hello-world
4f55086f7dd0: Pull complete 
Digest: sha256:452a468a4bf985040037cb6d5392410206e47db9bf5b7278d281f94d1c2d0931
Status: Downloaded newer image for hello-world:latest

Hello from Docker!
This message shows that your installation appears to be working correctly.

To generate this message, Docker took the following steps:
 1. The Docker client contacted the Docker daemon.
 2. The Docker daemon pulled the "hello-world" image from the Docker Hub.
    (amd64)
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


$ docker ps -a
CONTAINER ID   IMAGE         COMMAND    CREATED          STATUS                     PORTS     NAMES
b6372eb5bdc9   hello-world   "/hello"   10 seconds ago   Exited (0) 9 seconds ago             goofy_yonath


$ docker run -it --name my-ubuntu ubuntu bash
Unable to find image 'ubuntu:latest' locally
latest: Pulling from library/ubuntu
817807f3c64e: Pull complete 
Digest: sha256:186072bba1b2f436cbb91ef2567abca677337cfc786c86e107d25b7072feef0c
Status: Downloaded newer image for ubuntu:latest
root@24bfc4a49ce7:/# cat /etc/os-release
PRETTY_NAME="Ubuntu 24.04.4 LTS"
NAME="Ubuntu"
VERSION_ID="24.04"
VERSION="24.04.4 LTS (Noble Numbat)"
VERSION_CODENAME=noble
ID=ubuntu
ID_LIKE=debian
HOME_URL="https://www.ubuntu.com/"
SUPPORT_URL="https://help.ubuntu.com/"
BUG_REPORT_URL="https://bugs.launchpad.net/ubuntu/"
PRIVACY_POLICY_URL="https://www.ubuntu.com/legal/terms-and-policies/privacy-policy"
UBUNTU_CODENAME=noble
LOGO=ubuntu-logo

root@24bfc4a49ce7:/# echo "hello from container" > container_file.txt
root@24bfc4a49ce7:/# ls
bin   container_file.txt  etc   lib    media  opt   root  sbin  sys  usr
boot  dev                 home  lib64  mnt    proc  run   srv   tmp  var
root@24bfc4a49ce7:/# exit
exit

$ docker ps -a
CONTAINER ID   IMAGE         COMMAND    CREATED              STATUS                      PORTS     NAMES
24bfc4a49ce7   ubuntu        "bash"     About a minute ago   Exited (0) 31 seconds ago             my-ubuntu
b6372eb5bdc9   hello-world   "/hello"   2 minutes ago        Exited (0) 2 minutes ago              goofy_yonath

# 기존 실행되어있는도커를 모두 종료한다.
$ docker rm -f $(docker ps -aq)

```
### Dockerfile 빌드/실행

```zsh
$ echo "<h1>Welcome to GangdongOne's Web Server</h1>" > index.html

$ ls
hello.txt	index.html

$ cat <<EOF > Dockerfile
FROM nginx:alpine
COPY index.html /usr/share/nginx/html/index.html
EXPOSE 80
EOF

$ ls
Dockerfile	hello.txt	index.html

$ docker build -t my-web:1.0 .
[+] Building 7.6s (7/7) FINISHED                                docker:orbstack
 => [internal] load build definition from Dockerfile                       0.2s
 => => transferring dockerfile: 114B                                       0.0s
 => [internal] load metadata for docker.io/library/nginx:alpine            2.7s
 => [internal] load .dockerignore                                          0.2s
 => => transferring context: 2B                                            0.0s
 => [internal] load build context                                          0.3s
 => => transferring context: 82B                                           0.0s
 => [1/2] FROM docker.io/library/nginx:alpine@sha256:e7257f1ef28ba17cf7c2  3.7s
 => => resolve docker.io/library/nginx:alpine@sha256:e7257f1ef28ba17cf7c2  0.2s
 => => sha256:e7257f1ef28ba17cf7c248cb8ccf6f0c6e0228ab9 10.33kB / 10.33kB  0.0s
 => => sha256:7e89aa6cabfc80f566b1b77b981f4bb98413bd2d513 2.50kB / 2.50kB  0.0s
 => => sha256:d5030d429039a823bef4164df2fad7a0defb8d00c 12.32kB / 12.32kB  0.0s
 => => sha256:589002ba0eaed121a1dbf42f6648f29e5be55d5c8a6 3.86MB / 3.86MB  0.5s
 => => sha256:8892f80f46a05d59a4cde3bcbb1dd26ed2441d42148 1.87MB / 1.87MB  0.8s
 => => sha256:91d1c9c22f2c631288354fadb2decc448ce151d7a197c16 626B / 626B  0.9s
 => => extracting sha256:589002ba0eaed121a1dbf42f6648f29e5be55d5c8a6ee0f8  0.1s
 => => sha256:cf1159c696ee2a72b85634360dbada071db61bceaad253d 953B / 953B  1.0s
 => => extracting sha256:8892f80f46a05d59a4cde3bcbb1dd26ed2441d4214870a4a  0.1s
 => => sha256:3f4ad4352d4f91018e2b4910b9db24c08e70192c3b75d0d 402B / 402B  1.3s
 => => sha256:c2bd5ab177271dd59f19a46c214b1327f5c428cd075 1.21kB / 1.21kB  1.3s
 => => extracting sha256:91d1c9c22f2c631288354fadb2decc448ce151d7a197c167  0.0s
 => => extracting sha256:cf1159c696ee2a72b85634360dbada071db61bceaad253db  0.0s
 => => sha256:4d9d41f3822d171ccc5f2cdfd75ad846ac4c7ed1cd3 1.40kB / 1.40kB  1.5s
 => => extracting sha256:3f4ad4352d4f91018e2b4910b9db24c08e70192c3b75d0d6  0.0s
 => => sha256:3370263bc02adcf5c4f51831d2bf1d54dbf9a6a80 20.25MB / 20.25MB  2.0s
 => => extracting sha256:c2bd5ab177271dd59f19a46c214b1327f5c428cd075437ec  0.0s
 => => extracting sha256:4d9d41f3822d171ccc5f2cdfd75ad846ac4c7ed1cd36fb99  0.0s
 => => extracting sha256:3370263bc02adcf5c4f51831d2bf1d54dbf9a6a80b0bf32c  0.4s
 => [2/2] COPY index.html /usr/share/nginx/html/index.html                 0.2s
 => exporting to image                                                     0.2s
 => => exporting layers                                                    0.1s
 => => writing image sha256:4171d94cebffa7650fa9be313e5ec5d63d7adfd30c13a  0.0s
 => => naming to docker.io/library/my-web:1.0                              0.0s

$ docker images
REPOSITORY    TAG       IMAGE ID       CREATED         SIZE
my-web        1.0       4171d94cebff   5 seconds ago   62.2MB
hello-world   latest    e2ac70e7319a   10 days ago     10.1kB
ubuntu        latest    f794f40ddfff   5 weeks ago     78.1MB

$ docker run -d -p 8080:80 --name my-web-server my-web:1.0
72efead3e43c35aa8f586838395394fd5588991f107cfa5c5a75db9e55568004

$ docker ps
CONTAINER ID   IMAGE        COMMAND                  CREATED         STATUS         PORTS                                     NAMES
72efead3e43c   my-web:1.0   "/docker-entrypoint.…"   9 seconds ago   Up 8 seconds   0.0.0.0:8080->80/tcp, [::]:8080->80/tcp   my-web-server

```

### 포트 매핑 접속(2회)

images 폴더 안에 화면캡춰 이미지 삽입

<img src="images/Screenshot 2026-04-03 at 12.54.52 PM.png" alt="접속 결과" width="600">

### 바인드 마운트 반영


```zsh

# 1. 폴더와 파일 준비
mkdir -p ~/Documents/codyssey/codyssey-e1-1/practice/html
echo '<h1>Bind Mount Success!</h1>' > ~/Documents/codyssey/codyssey-e1-1/practice/html/index.html

# 2. 실행
docker run -d -p 8080:80 --name my-web-server \
-v ~/Documents/codyssey/codyssey-e1-1/practice/html:/usr/share/nginx/html \
nginx:alpine

# 에러시 기존 서버를 삭제
docker rm -f my-web-server

# 웹브라우저에서 접속 http://localhost:8080/

```

<img src="images/bindmountsuccess.png" alt="접속 결과" width="600">


### 볼륨 영속성
```zsh
docker volume create my-web-data
docker volume ls

DRIVER    VOLUME NAME
local     my-web-data

# 경로가 아닌 볼륭을 장착하여 컨테이너 실행
docker run -d -p 8082:80 --name my-web-v3 \
-v my-web-data:/usr/share/nginx/html \
nginx:alpine


# 1. 컨테이너 내부 파일 수정 (임시로 문구 변경)
docker exec -it my-web-v3 sh -c 'echo "<h1>Volume Persistence Success!</h1>" > /usr/share/nginx/html/index.html'

# 2. 브라우저 확인: http://localhost:8082

# 3. 서버 삭제 (컨테이너를 아예 없애버립니다)
docker rm -f my-web-v3

# 4. 똑같은 볼륨을 장착해서 다시 실행
docker run -d -p 8082:80 --name my-web-v3 -v my-web-data:/usr/share/nginx/html nginx:alpine

# 5. 다시 브라우저 확인: http://localhost:8082

```
<img src="images/volumesuccess.png" alt="접속 결과" width="600">


### Git 설정 + VSCode GitHub 연동

```zsh
# 1. 프로젝트 최상위 폴더로 이동합니다.
cd ~/Documents/codyssey/codyssey-e1-1

# 2. 새로 추가한 이미지 파일과 수정된 README.md가 상태에 뜨는지 확인합니다.
git status

# 3. 변경된 모든 파일(이미지 포함)을 스테이징 영역에 추가합니다.
git add .

# 4. 오늘 전체 과정을 마무리하는 커밋 메시지를 작성합니다.
git commit -m "Docs: Complete Mission E1-1 report with screenshots and troubleshooting logs"

# 5. GitHub 원격 저장소로 최종 전송합니다.
git push origin main
```



### 트러블슈핑
컨테이너가 이미 실행중일때, 1.기존 컨테이너를 삭제하거나, 이름을 바꾼다. 2.새로운 이름의 컨테이너를 새로운 포트매팅으로 만들다.

```zsh
$ docker run -d -p 8080:80 --name my-web-server my-web:1.0 
docker: Error response from daemon: Conflict. The container name "/my-web-server" is already in use by container "72efead3e43c35aa8f586838395394fd5588991f107cfa5c5a75db9e55568004". You have to remove (or rename) that container to be able to reuse that name.

Run 'docker run --help' for more information

$ docker rm -f my-web-server
my-web-server

$ docker run -d -p 8080:80 --name my-web-server my-web:1.0
8ceaf43ca338923a4a9eea6fa2c29d877340c5e3a2edb611793537c9ccae64ce

$ docker start my-web-server
my-web-server


$ docker ps
CONTAINER ID   IMAGE        COMMAND                  CREATED          STATUS          PORTS                                     NAMES
8ceaf43ca338   my-web:1.0   "/docker-entrypoint.…"   23 seconds ago   Up 23 seconds   0.0.0.0:8080->80/tcp, [::]:8080->80/tcp   my-web-server

$ docker run -d -p 8081:80 --name my-web-v2 my-web:1.0
4467bfccb544d17f73ace96ae2fa9f29942541f11319afd3ffcb054fd3f56187
$ docker ps
CONTAINER ID   IMAGE        COMMAND                  CREATED              STATUS              PORTS                                     NAMES
4467bfccb544   my-web:1.0   "/docker-entrypoint.…"   42 seconds ago       Up 41 seconds       0.0.0.0:8081->80/tcp, [::]:8081->80/tcp   my-web-v2
8ceaf43ca338   my-web:1.0   "/docker-entrypoint.…"   About a minute ago   Up About a minute   0.0.0.0:8080->80/tcp, [::]:8080->80/tcp   my-web-server

```

두번째 트러블슈팅
전체 명령어를 감싸는 따옴표를 홀따옴표(' ')로 바꾸어서 해결

```zsh

# 1. 컨테이너 내부 파일 수정 (임시로 문구 변경)
docker exec -it my-web-v3 sh -c "echo '<h1>Volume Persistence Success!</h1>' > /usr/share/nginx/html/index.html"


docker exec -it my-web-v3 sh -c 'echo "<h1>Volume Persistence Success!</h1>" > /usr/share/nginx/html/index.html'

```