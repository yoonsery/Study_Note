# Docker

어플리케이션을 패키징 할 수 있는 툴

컨테이너(작은 소프트웨어 유닛) 안에 어플리케이션, 시스템 툴(환경설정), 디펜더시를 하나로 묶어서 다른 서버나 pc에서도 쉽게 배포하고 안정적으로 구동할 수 있게 도와주는 툴

어플리케이션을 구동하기 위한 런타임 환경에 필요한 모든 것들을 어떤 환경에서도 구동할 수 있음

#### `Container` vs `VM`

- VM: 무거운 운영체제를 포함한다
- Container: 컨테이너 엔진이 Host OS에 접근해서 필요한 것들을 처리함

컨테이너 엔진 중에 가장 인기있는 게 Docker!

## 컨테이너를 만들기 위해 필요한 3가지

Dockerfile을 만들고 이를 이용해서 Image를 만들어서 컨테이너를 구동할 수 있다

1. Dockerfile
   : 컨테이너를 어떻게 만들어야 하는지 알려주는 설명서

- [x] Copy files
- [x] Install dependencies
- [x] Set environment variables
- [x] Run setup scripts

2. Image
   : 어플리케이션을 실행하는 데 필요한 코드, 런타임 환경, 시스템 툴, 시스템 라이브러리 등 모든 세팅들이 포함되어 있다. 실행되고 있는 어플의 상태를 스냅샷을 찍어 이미지로 만들어 두었다고 보면 된다. 이렇게 만들어진 이미지는 변경이 불가능

3. Container
   : 어플리케이션의 이미지를 고립된 환경(컨테이너 안)에서 실행한다

Image는 클래스와 비슷함 (템플릿 형태의 이미지를 만들어 두고) 이미지를 이용해서 어플이 동작하는 각각의 컨테이너를 만들 수 있다. 이미지는 불변의 상태이지만, 컨테이너에서 각각 동작하는 어플리케이션은 파일생성, 수정등 개별적으로 설정이 가능하다 (이미지는 클래스, 각각의 컨테이너는 인스턴스)

## Shipping Containers

이미지를 어떻게 공유할 수 있나? (어떻게 컨테이너를 배포할 수 있나)

로컬머신에서 이미지를 만들어서 `Container Registry`(like GitHub)에 이미지를 push한다  
필요한 서버나, 다른 개발자 pc에서 그 이미지를 가지고 와서 실행하면 된다  
실행하기 위해서는 `docker`와 같은 컨테이너 엔진을 설치해야 한다

Container Registry에는 public, private이 있다

- public: docker hub, GitHub Packages
- private: aws, Google Cloud, Microsoft Azure
