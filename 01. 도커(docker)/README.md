# 도커(docker)

- 2013년 3월에 처음으로 세상에 알려졌으며 **컨테이너 기반의 오픈소스 가상화 플랫폼**
- 애플리케이션을 신속하게 구축, 테스트 및 배포할 수 있는 소프트웨어 플랫폼
- 소프트웨어를 **컨테이너라**는 표준화된 유닛으로 패키징하며, 이 컨테이너에는 라이브러리, 시스템
  도구, 코드, 런타임 등 소프트웨어를 실행하는 데 필요한 모든 것이 포함됨
- 환경에 제한받지 않고 애플리케이션을 신속하게 배포 및 확장
- 코드를 실행하는 표준 방식을 제공하며 컨테이너를 위한 운영 체제

![스크린샷 2024-12-15 오후 10 18 40](https://github.com/user-attachments/assets/baeca227-e47d-4e45-a1f9-0c0e735ff9f0)

> 도커란? (레드햇 기술문서 중)<br>
> Docker 기술은 Linux 커널과 Cgroups 및 네임스페이스 등 커널의 기능을 사용하여 프로세스를 분리함으로써 독립적으로 실행할 수 있도록 한다. 이러한 독립성은 컨테이너의 본래 목적으로서 여러 프로세스와 애플리케이션을 서로 개별적으로 실행하여 인프라를 더 효과적으로 활용하고 개별 시스템을 사용할 때와 동일한 보안을 유지할 수 있다.<br><출처> https://www.redhat.com/ko/topics/containers/what-is-docker

- 도커는 개발자가 컨테이너를 빌드, 배포, 실행, 업데이트, 관리할 수 있는 오픈 소스 플랫폼이다. <b>컨테이너란 표준화되고 실행 가능한 구성요소로 애플리케이션 소스 코드와 이 코드를 임의의 환경에서 실행하는 데 필요한 운영 체제(OS) 라이브러리와 종속 항목을 조합한 것</b>이다.
- 컨테이너를 활용하면 분산형 애플리케이션을 간편하게 개발하고 제공할 수 있다. 기업에서 **클라우드 네이티브 개발 및 하이브리드 멀티클라우드 환경**으로 전환함에 따라 컨테이너가 더욱 널리 사용되고있다. (클라우드 네이티브(Cloud Native)란 넓은 의미로 클라우드 컴퓨팅의 장점을 최대한 활용할
  수 있도록 애플리케이션을 개발하고 운영하는 방법론이다.)

## 가상화란?

![스크린샷 2024-12-15 오후 10 22 59](https://github.com/user-attachments/assets/1a81e052-f5b9-43ca-979f-78872f6cdd21)

## 가상 머신과 도커 컨테이너 비교

![스크린샷 2024-12-15 오후 10 23 52](https://github.com/user-attachments/assets/a0df0aee-5b10-4cc8-bd0c-9aa7b7f45c1c)

- **하이퍼바이저**는 호스트 컴퓨터에서 다수의 운영 체제를 동시에 실행하기 위한 논리적 플랫폼을 말한다. 가상화 머신 모니터 또는 가상화 머신 매니저라고도 부른다.

![스크린샷 2024-12-15 오후 10 25 55](https://github.com/user-attachments/assets/02269daf-91fc-411f-a345-5190e594dde0)

<br>

![스크린샷 2024-12-15 오후 10 26 12](https://github.com/user-attachments/assets/3cd0d0b8-84f4-4112-a48b-69497a606929)

## 가상머신(VM) 기반 가상화와 도커(컨테이너) 기반 가상화 비교

![스크린샷 2024-12-15 오후 10 29 02](https://github.com/user-attachments/assets/230b3db3-23fc-4278-8b1d-dc27825037eb)

![스크린샷 2024-12-15 오후 10 29 24](https://github.com/user-attachments/assets/ba2e368f-3c9e-46d3-9bc2-bf14da9a8f20)

## 도커의 주요 활용

- 팀원들에게 동일한 개발환경 제공
  - 함께 일하는 프로젝트 팀원들에게 개발환경을 동일하게 제공
  - 프로젝트별 컨테이너를 따로 사용할 수 있음
- 새로운 버전의 테스트
  - 새로운 운영체제나 라이브러리 버전을 개발환경에서 먼저 테스트 후 운영환경에 컨테이너로 적용
- 동일한 서버가 여러 대 필요한 경우
  - 1대의 물리 서버에 여러 개의 컨테이너를 이용할 수 있으므로 비용 절약
  - 명령어 한 줄로 원하는 만큼 서버 구동 가능 -> 배포시간 단축
  - 스케일링에 유리하므로 웹 서버나 API 서버로 많이 활용

## 이미지와 컨테이너

- **도커 이미지** : 특정 서버 또는 애플리케이션의 실행할 수 있는 상태를 저장한 압축파일
- **도커 컨테이너** : 도커 컨테이너 이미지를 실행한 인스턴스, 필요한 요소를 포함하는 SW 패키지

![스크린샷 2024-12-15 오후 10 33 28](https://github.com/user-attachments/assets/68fb03d3-2bf5-47e0-a370-8d97e36a0329)

## 도커 허브(https://hub.docker.com)

- <b>도커 레지스터리(이미지를 배포하는 사이트)</b>
- 공개된 컨테이너 이미지가 모여 있는 사이트

![스크린샷 2024-12-15 오후 10 36 04](https://github.com/user-attachments/assets/55f31396-10aa-433a-a921-9a274900c873)

## Docker Desktop 설치

- Docker Desktop은 Mac, Linux, Windows 환경에서 컨테이너 이미지 빌드, 실행, 공유 등을 도와주는 애플리케이션이다. 컨테이너, 애플리케이션, 이미지를 머신에서 직접 관리할 수 있는 간단한 GUI(그래픽 사용자 인터페이스)를 제공한다.
- https://docs.docker.com/get-started/get-docker/ 페이지에서도 각 운영체제별 설치 프로그램을 다운로드할 수 있다.
- 도커 설치가 완료 되면 cmd창을 재기동한 후에 다음 명령을 실행하여 도커의 버전을 확인한다.

![스크린샷 2024-12-15 오후 10 48 46](https://github.com/user-attachments/assets/0d1fce62-9c99-4d0b-a228-376a1977eb79)

![스크린샷 2024-12-15 오후 10 48 56](https://github.com/user-attachments/assets/86f1d177-e47c-4e4c-bd5c-18bf00c64ac1)

## 윈도우용/macOS용 도커 사용하기

- 리눅스 운영체제가 들어있는 패키지, ‘도커 데스크톱’ 이용

![스크린샷 2024-12-15 오후 10 49 04](https://github.com/user-attachments/assets/5e629fda-0aa3-4447-a4e5-f02dd2f39bbc)

- **도커는 리눅스 기반**의 컨테이너 기술이므로 Windows에서 Docker을 사용하려면 리눅스 커널에 접근할 수 있는 방법인 WSL2를 사용한다. WSL 이란 리눅스용 윈도우 하위 시스템 <b>(Windows Subsystem for Linux)</b>으로서 윈도우 10과 윈도우 11에서 네이티브로 리눅스 실행 파일을 실행하기 위한 호환성 계층이다. 또한 도커 데스크톱은 **Hyper-V**를 사용하여 가상화를 수행할 수도 있어서 리눅스용 윈도우 하위 시스템(WSL)을 별도로 사용하지 않고도 가상화를 처리할 수 있다.

## WSL 2 및 Hyper-V

![스크린샷 2024-12-15 오후 10 52 26](https://github.com/user-attachments/assets/02769a19-659f-4536-bbe5-d77b75055e70)
![스크린샷 2024-12-15 오후 10 53 47](https://github.com/user-attachments/assets/e78907ef-87ad-4567-b530-49d9a031ed97)
![스크린샷 2024-12-15 오후 10 54 08](https://github.com/user-attachments/assets/24a4caac-229a-4fa4-9ade-641d55292711)

## docker \[container\] run 옵션

- 도커 컨테이너 생성 및 실행 기능, 필요시 이미지 다운로드 기능도 수행
- docker pull + docker create + docker start

![스크린샷 2024-12-15 오후 10 56 13](https://github.com/user-attachments/assets/cbe772e6-45ca-46fc-97ce-2319c96ad1ef)
![스크린샷 2024-12-15 오후 10 56 22](https://github.com/user-attachments/assets/fbcfac56-a468-4ff7-8859-b35c512fc0fd)
![스크린샷 2024-12-15 오후 10 56 37](https://github.com/user-attachments/assets/a13823a5-adf6-49d5-b3f1-91e90e8f42a8)
![스크린샷 2024-12-15 오후 10 56 45](https://github.com/user-attachments/assets/a47c6914-4f51-4c8c-9e07-6f53b3a4297b)

- **chcp 65001** 명령을 수행시킨 다음에 type 명령을 실행하면 한글이 깨지지 않고 잘 보인다.

![스크린샷 2024-12-15 오후 10 59 48](https://github.com/user-attachments/assets/0b5f1e2f-0ed8-472f-bd86-b20a44c0a3aa)

```
docker cp index.html myhttpd2:/usr/local/apache2/htdocs/
```

- 브라우저 주소창에 http://localhost:8071 입력 후 변경된 화면을 확인합니다.

- docker cp 호스트경로 컨테이너이름:컨테이너경로

![스크린샷 2024-12-15 오후 11 02 17](https://github.com/user-attachments/assets/730c7a69-b78e-4253-853a-8406b4468427)

- docker cp 컨테이너이름:컨테이너경로 호스트경로

![스크린샷 2024-12-15 오후 11 02 22](https://github.com/user-attachments/assets/f2089f55-e7d9-4655-9fe5-035fadf1d740)

## docker run 의 주요 옵션

![스크린샷 2024-12-15 오후 11 04 09](https://github.com/user-attachments/assets/b274af25-3503-4c11-8fdf-3b9691d03b78)

- 동작 중인 컨테이너는 삭제 불가능 -> 컨테이너 정지 후 삭제

```
docker stop 컨테이너이름 & docker rm 컨테이너이름
```

## 컨테이너 안으로 들어가서 쉘 기반으로 명령어 실행해 보기

```
docker exec -it myhttpd2 bash
```

- -i(--interactive) - 컨테이너의 표준 입력(stdin)을 활성화. (주로 -it 함께 사용)
- -t(--tty) - tty(가상 터미널)을 할당. 리눅스에 키보드를 통해 표준 입력(stdin)이 전달할 수있게 한다. (주로 -it 함께 사용)

![스크린샷 2024-12-15 오후 11 06 16](https://github.com/user-attachments/assets/e78fc8e2-5d08-4205-a0e8-c434a08dc30d)

## 도커 허브 – 도커 이미지 레지스트리

![스크린샷 2024-12-15 오후 11 09 25](https://github.com/user-attachments/assets/1858e1ca-2b9a-4da2-b453-145788905a6b)
![스크린샷 2024-12-15 오후 11 09 37](https://github.com/user-attachments/assets/9dd4b637-730b-4fc5-b81a-591c7e1664a8)
![스크린샷 2024-12-15 오후 11 10 16](https://github.com/user-attachments/assets/8f513909-16f7-494a-a7ff-40261a6408d4)

## 이미지명 규칙

![스크린샷 2024-12-15 오후 11 12 07](https://github.com/user-attachments/assets/6641eb5a-c306-4b22-8d91-f99f338a229e)

- docker pull httpd 에서 이미지명 **httpd** 는 <b>docker.io/library/httpd:latest</b> 를 의미함.

![스크린샷 2024-12-15 오후 11 12 52](https://github.com/user-attachments/assets/ef191be0-bad3-4b68-9a9f-3421fab9f1d0)
![스크린샷 2024-12-15 오후 11 13 04](https://github.com/user-attachments/assets/ebbea8b4-7b56-4f8a-aa66-f7866c867899)
![스크린샷 2024-12-15 오후 11 13 13](https://github.com/user-attachments/assets/338c795a-c8c3-41aa-a172-0aaee03d6968)
![스크린샷 2024-12-15 오후 11 13 23](https://github.com/user-attachments/assets/68c88582-cde5-4238-b532-cdd536d0b23b)
![스크린샷 2024-12-15 오후 11 13 31](https://github.com/user-attachments/assets/0f9d898a-c812-4dc4-9a11-d17994e2fb83)

## 컨테이너 라이프사이클

![스크린샷 2024-12-15 오후 11 13 44](https://github.com/user-attachments/assets/3f54b1eb-bd2f-428e-ad2a-9839177eda4e)

![스크린샷 2024-12-15 오후 11 16 47](https://github.com/user-attachments/assets/5f138bc9-a195-4d42-bdba-12686db3af4e)

## 도커를 사용하면 좋은 점-예시

- 둘리는 서버 100대를 관리한다. 서비스를 하기 위해서 OS를 일일이 설치하고 그위에 Apache와 Node.js를 설치하고 소스 코드를 다운로드하고 구동시킨다.
  - 같은 일을 100번 해야 한다.
- 이번에 Apache를 NginX로 교체하기로 했다. 소스 코드는 Git 등을 통해서 원격으로 쉽게 다운로드가 가능하지만, Apache 나 Nginx 같은 환경에 대한 교체는 쉽지 않다. 일일이 100대의 머신에서 Apache를 제거하고 NginX를 설치해야 한다. 만약 OS를 CentOS에서 Ubuntu로 교체한다고 한다면 일일이 모두 포멧하고 모든 과정을 반복해야 한다.

- Docker를 사용할 경우, CentOS + Apache + Node.js + Source 형식의 이미지를 하나만 준비하고 원격으로 한 번에 모두 배포 및 구동한다. Apache가 Nginx로 교체된다면 CentOS + Nginx + Node.js + Source 의 형태로 이미지만 다시 제작하여 한 번에 배포한 후 컨테이너만 기동시키면 된다. OS의 경우도 마찬가지이다.
- 극단적으로 예를 들긴 한 것이지만 그 만큼 Docker를 활용하여 단순히 비즈니스 어플리케이션을 넘어서 환경 자체를 배포하기 용이하다.

## 도커 이미지의 구조

- Docker에서 이미지란 컨테이너를 구동시키는데 있어서 필요한 파일과 설정 값 등을 저장한 파일 시스템이다. <b>이미지는 변하지 않고(Immutable) 상태를 가지지 않는다(Stateless)</b>. <b>이미지는 단지 컨테이너를 구동할 때만 사용되며, 실행 중에 변경된 내용은 컨테이너 레이어에 저장</b>된다.

![스크린샷 2024-12-15 오후 11 21 30](https://github.com/user-attachments/assets/358b84f9-8f04-479f-ac19-59954cd9a667)

- Docker 이미지의 핵심은 레이어 형태로 되어있다는 것이다. 유니온 파일 시스템을 이용해 여러 개의 레이어를 하나의 파일시스템으로 사용할 수 있게 해준다. **이미지는 여러 개의 읽기 전용 레이어로 구성되고 파일이 추가되거나 수정될 때 새로운 레이어가 생성**된다.
- 여러 이미지를 가지고 있다고 하여도 중복된 부분은 하나만 가지고 있어서 공간이 효율적으로관리되고 확장성이 좋다. 이런 확장성을 바탕으로 Docker Hub에는 다양한 이미지들이 존재하고 80억이 넘는 다운로드가 이루어지고 있다.

![스크린샷 2024-12-15 오후 11 22 58](https://github.com/user-attachments/assets/802cdbfc-d949-4e64-bcc8-74f7db54001c)

- **ubuntu 이미지가 기존에 존재하는데 nginx 이미지를 다운 받을 경우 nginx 레이어만 다운받게 된다.** Docker 이미지는 위 그림처럼 여러 레이어로 구성되며, 각 레이어는 이전 레이어의 변경사항을 가지고 있다. 여러 개의 레이어에는 읽기 전용인 read only 레이어와, 새로 변경되거나 추가된
  내용을 담은 새로운 레이어로 구성된다.

![스크린샷 2024-12-15 오후 11 25 20](https://github.com/user-attachments/assets/c6b41eb6-2a18-41b5-8df2-b6981c9863b0)

- 이미지의 **레이어 구조는 재활용에 유리하며 효율적인 데이터 저장과 전송을 지원**한다. 이미지 레이어는 이전 레이어의 변경 사항을 저장한다. **컨테이너 실행 시 읽기, 쓰기가 가능한 새로운 레이어가 추가**된다.(**컨테이너 레이어**)

![스크린샷 2024-12-15 오후 11 27 27](https://github.com/user-attachments/assets/0a140d78-6e7a-4137-a449-adf21fda4d2e)
![스크린샷 2024-12-15 오후 11 27 35](https://github.com/user-attachments/assets/e34ffdfd-2d44-4e33-afe1-b3d9eb52d1ce)
![스크린샷 2024-12-15 오후 11 27 47](https://github.com/user-attachments/assets/aef5fe15-f67e-464c-941a-83f3b0d49a83)

## 이미지 삭제

- 컨테이너를 삭제해도 이미지는 남아있으므로 불필요한 이미지는 즉시 삭제하는 것이 좋다.
- 해당 이미지를 사용하는 컨테이너가 남아 있으면 이미지 삭제는 불가하다.
- 이미지 삭제 명령

```
docker image rm 이미지명 [이미지명 . . .]
```

- 이미지 조회 명령

```
docker image ls
```

![스크린샷 2024-12-15 오후 11 29 55](https://github.com/user-attachments/assets/e77db169-d048-41de-bb44-4ad1cfb05062)

## 도커로 mysql 이미지 다운로드 : docker pull mysql

- 다운로드된 이미지 확인 : docker images 또는 docker image ls

![스크린샷 2024-12-15 오후 11 31 44](https://github.com/user-attachments/assets/6e94497a-c26a-477a-bfaf-f13969f3b358)

## 컨테이너의 통신

### 웹 서버(httpd, nginx 등)

- 웹 서버 기능을 제공하는 소프트웨어
- 컨테이너는 기본적으로 외부에서 접근 불가능한(격리된) 상태로 실행
- 컨테이너 실행 시 네트워크 관련 설정이 필요하며 컨테이너가 실행된 후에는 변경 불가

- 컨테이너와의 통신 위해서는 포트포워딩을 해야 한다. **포트포워딩**이란 컨테이너 <b>내부 네트워크의 포트와 호스트 포트(인터넷 포트)를 연결시켜 서로 통신할 수 있도록 열어주는 것</b>을 말한다.

![스크린샷 2024-12-16 오전 6 59 39](https://github.com/user-attachments/assets/654d4ac8-db14-422b-a9ea-8f7580a277b3)

- 외부와의 접속을 위해 통신포트 설정

![스크린샷 2024-12-16 오전 7 01 24](https://github.com/user-attachments/assets/f232a7fc-6fa6-4e71-89b4-1ae50a0ff0bd)

- 여러 개의 웹 서버 컨테이너 구동 시 호스트\_포트번호는 다르게 구성

  - 컨테이너 A는 8080
  - 컨테이너 B는 8081
  - 컨테이너 C은 8082

  ![스크린샷 2024-12-16 오전 7 03 51](https://github.com/user-attachments/assets/278de486-2160-4ae8-8f57-1d5aea7982d0)

- 웹 브라우저를 이용한 접근
  - http://localhost:8081, http://localhost:8082 로 접근

### 공인 IP 와 사설 IP

![스크린샷 2024-12-16 오전 7 06 14](https://github.com/user-attachments/assets/ce4cd741-449e-4186-81f5-a6c39bd6a486)

### NAT 와 포트포워딩

- NAT(Network Address Translation)는 Network 계층의 주소(IP)를 변환시켜주는 기술이다.
- <b>컨테이너 기반 가상화에서의 포트 포워딩(Port Forwarding)은 호스트와 컨테이너 사이에서 네트워크 트래픽을 전달하는 기술</b>이다. 컨테이너는 가상화된 환경에서 실행되는 독립적인 프로세스로, 컨테이너 내부에서 실행되는 애플리케이션은 호스트와 같은 IP 주소나 포트에 직접적으로 접근할 수 없다. 이를 해결하기 위해 <b>컨테이너의 포트와 호스트의 포트를 매핑</b>해주는 것이 포트 포워딩이다.
- <b>포트 포워딩은 NAT를 지원하는 장치에서 설정 가능하며 특정 포트를 Open하고 해당 포트로 들어오는 모든 패킷을 내부의 사설 IP와 포트로 전달해주는 기능</b>이다.

![스크린샷 2024-12-16 오전 7 10 12](https://github.com/user-attachments/assets/159fd4c8-c510-4963-8f7f-e94505f5ac9a)
![스크린샷 2024-12-16 오전 7 10 25](https://github.com/user-attachments/assets/54a86ac1-6956-4e29-a7c8-89733ac7f3f3)

- <b>브릿지 네트워크(Bridge)</b> : 도커 브릿지를 활용해 건테이너간 통신, NAT 및 포트 포워딩 기술을 활용해 외부 통신 지원

![스크린샷 2024-12-16 오전 7 10 47](https://github.com/user-attachments/assets/f04243b8-4ddc-4f68-9c4b-1ebffd047ec4)

![스크린샷 2024-12-16 오전 7 12 44](https://github.com/user-attachments/assets/e074f525-0454-4a7d-af8d-d6ee55ac2fd4)
![스크린샷 2024-12-16 오전 7 13 30](https://github.com/user-attachments/assets/e18ad073-c5c6-49c5-b471-1a174ff1cd59)

![스크린샷 2024-12-16 오전 7 13 38](https://github.com/user-attachments/assets/85cdf37d-4202-4d8a-81fd-72362d0ea3eb)

### 도커 네트워크 생성/삭제

- 도커는 네트워크를 직접 생성하지 않아도 기본 네트워크가 자동으로 세 개 만들어짐
- 네트워크를 명시적으로 지정하지 않고 Docker 컨테이너를 시작하면 <b>기본값인 “bridge” 네트워크 로 Docker 컨테이너를 시작</b> 함

![스크린샷 2024-12-16 오전 7 17 17](https://github.com/user-attachments/assets/b57aa635-fc57-4d5b-851e-78b58b93436e)

- 컨테이너에 의해 기동된 일부 서버들 만의 통신망을 구축하기 위해서 가상의 네트워크를 정의하여 사용할 수 있음
- 네트워크 생성 명령

```
docker network create 네트워크이름
```

- 네트워크 삭제 명령

```
docker network rm 네트워크이름
```

- 기타 네트워크 관련 명령

![스크린샷 2024-12-16 오전 7 17 49](https://github.com/user-attachments/assets/0406c30d-5401-4d16-8903-7695adc236c5)

- MySQL 컨테이너 생성 및 실행

```
docker run --name 컨테이너이름 –dit --net=네트워크이름 ……… mysql
```

## 도커 컨테이너의 저장소

- <b>Docker 컨테이너(container)에 쓰여진 데이터는 컨테이너가 삭제될 때 함께 사라지게</b> 된다.
- Docker에서 돌아가는 많은 애플리케이션이 컨테이너의 생명 주기와 관계없이 <b>데이터를 영속적으로 저장을 해야 하는 경우, 그리고 여러 개의 Docker 컨테이너가 하나의 저장 공간을 공유해서 데이터를 읽거나 써야 하는 경우</b>가 있다.
- 이렇게 Docker 컨테이너의 생명 주기와 관계없이 데이터를 영속적으로 저장할 수 있도록 Docker는 두가지 옵션을 제공하며 <b>Docker 볼륨(volume)</b>과 <b>바인드 마운트(bind mount)</b>이다.


![스크린샷 2024-12-16 오전 7 22 55](https://github.com/user-attachments/assets/559fb667-0727-4824-b1f7-9aba3468a06c)

### Docker 볼륨

- <b>도커 엔진이 관리하는 영역 내</b>에 만들어진 <b>볼륨을 컨테이너에 디스크 형태로 마운트하여 사용</b>
- 직접 조작이 어려우므로 주로 ‘임시 목적’ 또는 ‘자주 쓰지는 않지만 지우면 안되는 파일을 저장’ 하는 목적으로 사용
- 도커 엔진에 의해 관리
  - 리눅스 경우 /var/lib/docker/volumns
  - <b>도커 데스크톱의 경우 도커 엔진의 관리영역</b>
- 운영체제와 무관하게 일관성 있는 방식으로 작업
- <b>도커 제작사에서 추천하는 방식</b>
- 도커 컨테이너를 이용하지 않고는 접근 불가능
- 백업 절차 복잡

![스크린샷 2024-12-16 오전 7 23 04](https://github.com/user-attachments/assets/667e83e9-caff-4ba1-b573-7a59222ab7b1)


![스크린샷 2024-12-16 오전 7 23 11](https://github.com/user-attachments/assets/8a645299-ed74-40c1-9616-afb685b9b031)

### Docker 볼륨 생성 방법

```
docker volumn create 볼륨이름
docker volumn rm 볼륨이름
```

![스크린샷 2024-12-16 오전 7 23 19](https://github.com/user-attachments/assets/c3eb517c-7c1f-47ee-9af4-53065100c8b6)


-  Docker 볼륨 설정 명령

```
docker run . . . –v 볼륨_이름:컨테이너_마운트_경로 . . .
```

## mysql 서버를 도커 컨테이너로 기동하기

- 기동되어 있는 MySQL 서버를 종료한다.


![스크린샷 2024-12-16 오전 7 31 15](https://github.com/user-attachments/assets/13facb7a-735d-497b-8a16-948c41d1a960)


- MySQL 에서 사용할 볼륨을 생성한다.


```
docker volume create vtest
```

![스크린샷 2024-12-16 오전 7 31 40](https://github.com/user-attachments/assets/b986e2d3-9890-4985-b47e-c8574ad4bbaf)


- 생성된 볼륨을 지정하여 mysql 도커 이미지를 가지고 도커 컨테이너를 기동한다.


```
docker run -d -p 3306:3306 -e MYSQL_ROOT_PASSWORD=1234 -v vtest:/var/lib/mysql --
name mysql_db -e TZ=Asia/Seoul mysql
```

![스크린샷 2024-12-16 오전 7 32 52](https://github.com/user-attachments/assets/e4b59120-e7d1-4f77-99af-69c9a8d67eb5)


