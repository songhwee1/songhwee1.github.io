---  
layout: post  
title: "Git, GitHub사용법 알아보기"  
subtitle: "Git, GitHub사용법"  
categories: envops
tags: 코드관리 협업 깃 깃허브 Git GitHub
comments: true  
---  

> Git, GitHub란 무엇인가?  
> Git, GitHub사용법

---
# Git은 뭐고 GitHub는 뭔가요?  
### Git  
+ 로컬에서 관리되는 버전 관리 시스템(VCS: Version Control System)
+ 소스코드 수정에 따른 버전을 관리해주는 시스템  

### GitHub
+ 클라우드 방식으로 관리되는 버전 관리 시스템(VCS)
+ 자체 구축이 아닌 빌려쓰는 클라우드의 개념  

간단하게 말해서 **Git**은 로컬 버전 관리 시스템을 운영하는 방식이고, **GitHub**는 깃허브에서 제공해주는 클라우드 서버를 이용한다는 것의 차이입니다.

## Git 설치하기  
[여기](https://gitforwindows.org/)에 접속해서 **Download**버튼을 눌러 **Git**을 다운로드 해줍니다.  
이후 설치 옵션들은 next를 눌러주며 기본 옵션으로 설치해줍니다.  

설치가 되었다면, Cmd(명령 프롬프트)창을 열고, 다음 명령어를 입력하여 정상적으로 설치가 되었는지 확인해줍니다.
```
git version
```
정상적으로 설치가 되었다면, 아래와 같이 **Git version**이 표시됩니다.
![git 다운로드 확인](https://songhwee1.github.io/assets/img/envops/git_download_test.png "git 다운로드 확인")

## GitHub 가입하기
[여기](https://github.com/)에 접속해서 우측 상단에 있는 **Sign Up**버튼을 눌러 가입을 진행합니다.  

메일 인증까지 완료하면, 가입이 완료됩니다.  

## Repository 생성하기
가입한 계정으로 로그인을 해줍니다.
![github 첫화면](https://songhwee1.github.io/assets/img/envops/git_login.png "github 첫화면")
처음 로그인을 하게 되면 위와 같은 창이 나올텐데, 좌측의 **Create repository**버튼을 눌러 첫 레포지토리를 만들어봅시다.

![github 레포생성](https://songhwee1.github.io/assets/img/envops/git_create_repo.png "github 레포생성")
버튼을 눌러 이동한 화면에서 **Repository name**을 입력해줍시다.(저는 Test라고 정하겠습니다.)  
**Description**에는 **Repo에 대한 간단한 설명**을 입력해줍니다.  
**Public**과 **Private**를 선택할 수 있는데, **Public**을 선택하면 외부에서 내 코드를 볼 수 있고, **Private**를 선택하면 비공개 Repo가 생성됩니다.  
설정을 완료했다면 하단의 **Create repository**버튼을 눌러 생성을 완료해줍니다.

![github 레포생성완료](https://songhwee1.github.io/assets/img/envops/git_create_repo_1.png "github 레포생성완료")
정상적으로 생성이 완료되면 위와 같은 화면을 볼 수 있습니다.

## 내가 작성한 코드 업로드해보기
내가 만든 Repo를 다운로드하거나, 업로드 하기 위해서 Git Bash를 사용해줍니다.