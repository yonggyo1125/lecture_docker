## Docker 이미지를 빌드하는 2가지 방법

- 커밋 - 컨테이너의 현재 상태를 이미지로 저장
- 빌드 - Dockerfile(도커 이미지 생성관련 스크립트 파일)을 통해 이미지를 생성하여 저장

![스크린샷 2024-12-16 오후 10 21 54](https://github.com/user-attachments/assets/7a5d1c1f-7a97-4f6d-938e-1765620fa87b)

## commit 명령으로 컨테이너를 이미지로 변환하기

![스크린샷 2024-12-16 오후 10 22 17](https://github.com/user-attachments/assets/6b8f56bf-efd9-4e84-a3a9-7634b5f2bd76)

- 로컬에 있는 도커 이미지를 도커 허브에 푸쉬한다.

## Dockerfile 스크립트로 이미지 생성하기

- Dockerfile에 컨테이너에 넣을 이미지나 실행할 명령 등 기술

![스크린샷 2024-12-16 오후 10 25 51](https://github.com/user-attachments/assets/46142f0e-1273-4761-9d66-9c23270a2d09)
![스크린샷 2024-12-16 오후 10 26 34](https://github.com/user-attachments/assets/3e67c0e8-bafd-4d11-9384-e3a93fe1ff4c)
![스크린샷 2024-12-16 오후 10 26 44](https://github.com/user-attachments/assets/95c99216-3a8f-4d24-902f-00e51d3f932d)

## Dockerfile 기본 지시어

![스크린샷 2024-12-16 오후 10 28 42](https://github.com/user-attachments/assets/ba7d63ce-cba6-49fe-b999-d4fb35ce4590)
![스크린샷 2024-12-16 오후 10 29 23](https://github.com/user-attachments/assets/809db551-3db5-4c81-8eda-e4641be2f0d6)
![스크린샷 2024-12-16 오후 10 29 32](https://github.com/user-attachments/assets/e3487c2e-0e4c-4f3d-bf95-e4cbd2a9469d)

![스크린샷 2024-12-16 오후 10 31 40](https://github.com/user-attachments/assets/5f173574-2c58-4cd3-9b55-49d9cb6dc7c7)

## Dockerfile 스크립트에 사용되는 주요 명령

![스크린샷 2024-12-16 오후 10 32 46](https://github.com/user-attachments/assets/58914c7c-5fb8-4b68-bd29-402cc28ed731)

## Dockerfile 의 작성 방법

- <b>Docker가 대중화되면서 많은 프로젝트들이 개발 환경을 컨테이너화(containerization)</b>시키고 있다.
  이러한 프로젝트의 최상위 디렉터리에서는 Dockerfile이 위치하게 되며, Dockerfile의 작성 방법을 이해하는 것은 그 프로젝트의 개발 환경이 어떻게 구성되는지 이해하는 첫걸음이다.

- Dockerfile은 <b>Docker 이미지(image)가 어떤 단계를 거쳐 빌드(build)되어야 하는지</b>를 담고 있는 스크립트 파일이다. <b>Docker는 Dockerfile에 나열된 명령문을 차례대로 수행해서 이미지를 생성</b>한다.
- 다음은 자주 쓰이는 명령어 위주로 Dockerfile을 작성하는 방법에 대해서 정리한 내용이다.

### 명령어(INSTRUCTION) 인자(arguments)

- 각 명령문은 명령어로 시작하고 여러 개의 인자가 정의될 수 있으며, 해당 명령문에 대한 주석(#)도 정의할 수 있다. 인자와 구분이 쉽도록 명령어는 모두 영문 **대문자**로 작성하는 것이 관례이다.

#### FROM 명령문

```
FROM <이미지>
FROM <이미지>:<태그>
```

- 하나의 Docker 이미지는 base 이미지부터 시작해서 기존 이미지 위에 새로운 이미지를 중첩해서 여러 단계의 이미지 층(layer)을 쌓아가며 만들어진다.
- FROM 명령문은 이 base 이미지를 지정하기 위해서 사용되는데, 보통 Dockerfile 내에서 최상단에 위치한다. base 이미지는 일반적으로 Docker Hub와 같은 Docker repository에 올려놓은 잘 알려진 공개 이미지인 경우가 많다.

- Ubuntu 최신 버전을 base 이미지로 사용

```
FROM ubuntu:latest
```

- NodeJS 12를 base 이미지로 사용

```
FROM node:12
```

- Python 3.8 (alpine 리눅스 기반)을 base 이미지로 사용

```
FROM python:3.8-alpine
```

- 아파치 웹 서버를 base 이미지로 사용

```
FROM httpd
```

- 최신 버전의 MySQL 을 base 이미지로 사용

```
FROM mysql:latest
```

- openjdk 17 버전을 base 이미지로 사용

```
FROM openjdk:17-jdk
```

#### WORKDIR 명령문

- WORKDIR 명령문은 쉘(shell)의 cd 명령문처럼 컨테이너 상에서 **작업 디텍토리로 전환**을 위해서 사용된다. WORKDIR 명령문으로 작업 디렉터리를 전환하면 그 이후에 등장하는 모든 RUN, CMD, ENTRYPOINT, COPY, ADD 명령문은 해당 디렉터리를 기준으로 실행된다. 즉, WORKDIR은 도커 이미지의 어디에서 작업을 할지를 의미한다.

```
WORKDIR <이동할 경로>
```

- /usr/app으로 작업 디렉터리 전환

```
WORKDIR /usr/app
```

#### RUN 명령문

```
RUN ["<커맨드>", "<파라미터1>", "<파라미터2>"]
RUN <전체 커맨드>
```

- RUN 명령문은 마치 쉘(shell)에서 커맨드를 실행하는 것처럼 **이미지 빌드 과정에서 필요한 커맨드를 실행하기 위해서 사용**된다. 쉘(shell)을 통해 거의 못하는 작업이 없는 것처럼 RUN 명령문으로 할수 있는 작업은 제한 없지만 보통 이미지 안에 **특정 소트프웨어를 설치하기 위해**서 많이 사용된다.

- curl 도구 설치

```
RUN apk add curl
```

- npm 패키지 설치

```
RUN npm install --silent
```

- pip 패키지 설치

```
RUN pip install -r requirements.txt
```

#### ENTRYPOINT 명령문

```
ENTRYPOINT ["<커맨드>", "<파라미터1>", "<파라미터2>"]
ENTRYPOINT <전체 커맨드>
```

- **ENTRYPOINT 명령문은 이미지를 컨테이너로 띄울 때 항상 실행되어야 하는 커맨드를 지정**할 때 사용한다. ENTRYPOINT 명령문은 Docker 이미지를 마치 하나의 실행 파일처럼 사용할 때 유용하다. **컨테이너가 기동 될때 ENTRYPOINT 명령문으로 지정된 커맨드가 실행되고, 이 커맨드로 실행된 프로세스가 죽을 때, 컨테이너도 따라서 종료**되기 때문이다.

- npm start 스크립트 실행

```
ENTRYPOINT ["npm", "start"]
```

- nginx 서버 기동

```
ENTRYPOINT ["nginx", "-g", "daemon off;"]
```

#### CMD 명령문

```
CMD ["<커맨드>","<파라미터1>","<파라미터2>"]
CMD ["<파라미터1>","<파라미터2>"]
CMD <전체 커맨드>
```

- CMD 명령문은 해당 이미지를 컨테이너로 띄울 때 디폴트로 실행할 커맨드나, <b>ENTRYPOINT 명령문으로 지정된 커맨드에 디폴트로 넘길 파라미터를 지정할 때</b> 사용한다.
- CMD 명령문은 많은 경우, ENTRYPOINT 명령문과 함께 사용하게 되는데, <b>ENTRYPOINT 명령문으로는 커맨드를 지정하고, CMD 명령문으로 디폴트 파리미터를 지정</b>해주면 매우 유연하게 이미지를 실행할 수 있게 된다.
- 예를 들어, node 커맨드로 디폴트로는 index.js를 실행하되, docker run 커맨드에 인자가 있는 경우, 해당 인자를 실행하고 싶은 경우, 다음과 같이 Dockerfile을 작성한다.

```
ENTRYPOINT ["node"]
CMD ["index.js"]
```

- 그러면 다음과 같이 docker run 커맨드의 인자 유무에 따라 node 커맨드로 다른 파일이 실행되게 할 수 있다.

- node index.js 실행

```
$ docker run test
```

- node main.js 실행

```
$ docker run test main.js
```

- CMD 명령문과 RUN 명령문이 기능이 비슷해 보이는데 **RUN 명령문은 이미지 빌드시 항상 실행되며, 하나의 Dockerfile에 여러 개의 RUN 명령문을 선언**할 수 있다. 반면에, **CMD 명령문은 이미지를 컨테이너로 기동시킬 때 한 번의 실행 기회**를 가지게 된다.

## EXPOSE 명령문

```
EXPOSE <포트>
EXPOSE <포트>/<프로토콜>
```

- EXPOSE 명령문은 네트워크 상에서 컨테이너로 들어오는 트래픽(traffic)을 <b>리스닝(listening)하는 포트와 프로토콜</b>를 지정하기 위해서 사용된다. 프로토콜은 TCP와 UDP 중 선택할 수 있는데 지정하지 않으면 TCP가 기본값으로 사용된다.
- 여기서 주의할 점은 **EXPOSE 명령문으로 지정된 포트는 해당 컨테이너의 내부에서만 유효**하며, 호스트(host) 컴퓨터에서는 이 포트를 바로 접근을 할 수 없다. 호스트 컴퓨터로부터 해당 포트로의 접근을 허용하려면, <b>docker run 커맨드에서 -p 옵션을 통해 호스트 컴퓨터의 특정 포트를 포워딩(forwarding)</b>시켜주어야 한다.

- 80/TCP 포트로 리스닝

```
EXPOSE 80
```

- 9999/UDP 포트로 리스닝

```
EXPOSE 9999/udp
```

#### COPY/ADD 명령문

```
COPY <src>... <dest>
COPY ["<src>" ... "<dest>"]
```

- **COPY 명령문은 호스트 컴퓨터에 있는 디렉터리나 파일을 Docker 이미지의 파일 시스템으로 복사**하기 위해서 사용된다. 절대 경로와 상대 경로를 모두 지원하며, 상대 경로를 사용할 때는 이전에 등장하는 WORKDIR 명령문으로 작업 디렉터리를 어디로 변경했는지 고려해야 한다.

- package.json 파일만 복사

```
COPY package.json package.json
```

<b>이미지 빌드를 수행한 디렉터리의 모든 파일을 컨테이너의 app/ 디렉터리로 복사</b>

```
WORKDIR app/
COPY . .
```

- **ADD 명령문은 좀 더 파워풀한 COPY 명령문**이라고 할 수 있다. ADD 명령문은 일반 파일뿐만 아니라 압축 파일이나 네트워크 상의 파일도 사용할 수 있다. 이렇게 특수한 파일을 다루는 게 아니라면 **COPY 명령문**을 사용하는 것이 권장된다.

#### ENV 명령문

```
ENV <키> <값>
ENV <키>=<값>
```

- ENV 명령문은 환경 변수를 설정하기 위해서 사용한다. <b>ENV 명령문으로 설정된 환경 변수는 이미지 빌드 시에도 사용되고, 해당 컨테이너 안에서 실행되는 애플리케이션에서도 접근할 수 있다.</b>

- NODE_ENV 환경 변수를 production으로 설정

```
ENV NODE_ENV production
```

- 자바 버전을 11로 설정

```
ENV JAVA_VERSION 11
```

#### ARG 명령문

```
ARG <이름>
ARG <이름>=<기본값>
```

- ARG 명령문은 docker build 커맨드로 이미지 빌드 시, <b>--build-arg</b> 옵션을 통해 넘길 수 있는 인자를 정의하기 위해 사용한다.
- 예를 들어, Dockerfile에 다음과 같이 ARG 명령문으로 port를 인자로 선언해주면,

```
ARG port
```

- 다음과 같이 docker build 커맨드에 --build-arg 옵션에 port 값을 넘길 수가 있다.

```
$ docker build --build-arg port=8080 .
```

- 인자의 디폴트값을 지정해주면, --build-arg 옵션으로 해당 인자가 넘어오지 않았을 때 사용된다.

```
ARG port=8080
```

- 설정된 인자 값은 다음과 같이 ${인자명} 형태로 읽어서 사용할 수 있다.

```
CMD start.sh -h 127.0.0.1 -p ${port}
```

- **ENV와 달리 ARG로 설정한 값은 이미지가 빌드되는 동안에만 유효**하다.

#### .dockerignore 파일

- 명령문은 아니지만 .dockerignore 파일도 알아두면 Dockerfile을 작성할 때 유용한다. <b>Docker 이미지를 빌드할 때 제외 시키고 싶은 파일이 있다면, .dockerignore 파일에 추가한다.</b>
- 예를 들어, .git 디렉터리와 마크다운(markdown) 파일을 모두 제외 시키고 싶다면 다음과 같이 .dockerignore 파일을 작성해주면 된다.

```
.dockerignore 파일
.git
*.md
```

- 이렇게 설정을 해주면 Docker는 프로젝트 최상위 디렉터리에 위치하고 있는 markdown 파일들을 무시하게 되므로, RUN과 CMD, COPY와 같은 명령문이 해당 파일을 사용할 수 없게 된다.

![스크린샷 2024-12-16 오후 11 25 38](https://github.com/user-attachments/assets/e1ced8c5-22ab-48fc-86a3-9f22cd68a93a)

### (\*) Docker 파일 작성시 참고할 사이트

- https://docs.docker.com/reference/
- https://github.com/komljen/dockerfile-examples
- https://github.com/topics/dockerfile-examples?o=desc&s=updated

![스크린샷 2024-12-16 오후 11 27 44](https://github.com/user-attachments/assets/23e3730e-ceb9-4b67-8117-6d38f00903ec)

### 커밋과 빌드

![스크린샷 2024-12-16 오후 11 28 01](https://github.com/user-attachments/assets/74d6a5a8-3d04-4eaf-8d16-1f91733fdf9b)

![스크린샷 2024-12-16 오후 11 28 15](https://github.com/user-attachments/assets/63c9bb15-4fbb-436e-82ab-000818ce2c1b)

## 레지스트리와 리포지터리

- 레지스터리 : 이미지를 배포하는 장소 (도커허브에 회원 가입하면서 생성되는 계정명의 이름공간)
- 리포지터리 : 레지스트리를 구성하는 단위

![스크린샷 2024-12-17 오전 7 07 04](https://github.com/user-attachments/assets/dba8df10-7511-49ee-b716-d422f15be667)

![스크린샷 2024-12-17 오전 7 07 18](https://github.com/user-attachments/assets/fd8d348a-7e9c-451e-83dc-2c62f2313362)

## 이미지를 파일로 저장하기와 읽어 들이기

- 이미지를 호스트 컴퓨터의 파일시스템에 tar 형식으로 저장하는 것이 가능하다.

```
docker save -o 파일_이름.tar 이미지_이름
docker save 이미지_이름 > 파일_이름.tar
```

- tar 파일로 저장된 이미지를 도커 엔진으로 가져올 때는 load 명령 이용

```
docker load -i 파일_이름.tar
docker load < 파일_이름.tar
```

![스크린샷 2024-12-17 오전 7 11 53](https://github.com/user-attachments/assets/28c57815-0e9a-415b-bce0-433e5f6e7aee)

## 컨테이너를 파일로 저장하기와 읽어들이기

- 컨테이너를 파일로 저장

```
docker export [컨테이너명 or 컨테이너ID] > 파일_이름.tar
```

- 저장한 컨테이너를 도커 이미지로 읽어 들임

```
docker import [파일_이름.tar or URL] - [image name[:tag name]]
```

![스크린샷 2024-12-17 오전 7 15 39](https://github.com/user-attachments/assets/6028a329-ca15-4ee6-940d-d41d53eea231)

## 컨테이너 개조 방법(두 가지 방법 혼용)

- 파일 복사와 마운트
- 컨테이너에서 리눅스 명령 이용

![스크린샷 2024-12-17 오전 7 17 43](https://github.com/user-attachments/assets/9ba127b0-ba67-4f84-8b64-49fbae832302)

## 컨테이너에서 리눅스 명령 실행

- 리눅스 명령 실행을 위해 bash 쉘 필요 (/bin/bash)
- docker run 또는 **docker exec** 명령을 이용하여 실행
  - 컨테이너 속에서 명령을 실행하는 명령 실행 중인 컨테이너에 사용
- bash를 이용하여 변경이 완료되면 docker start 명령으로 재시작 필요

![스크린샷 2024-12-17 오전 7 18 23](https://github.com/user-attachments/assets/13628900-6f49-40dd-ad18-405127da55bb)

- docker exec 명령

```
docker exec [옵션] 컨테이너_이름 /bin/bash
```

- docker run 명령

```
docker run [옵션] 이미지_이름 /bin/bash
```

- docker exec 명령 예)

```
docker exec -it apa000ex23 /bin/bash
```

- docker run 명령 예)

```
docker run --name apa000ex23 -it -p 8089:80 httpd /bin/bash
```

- bash를 통해 컨테이너를 조작하는 동안에는 도커 명령을 사용할 수 없다.
- 컨테이너 조작이 끝나면 ‘exit’ 명령으로 컨테이너를 빠져나와야 한다.

- 도커 엔진 명령과 컨테이너 내부에서 실행하는 명령
