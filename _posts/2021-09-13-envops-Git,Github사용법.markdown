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



## Git Bash에 사용자 등록하기
내가 만든 Repo에 작성한 코드를 다운로드하거나, 업로드 하기 위해서 **Git Bash**를 사용해줍니다.
![git bash](https://songhwee1.github.io/assets/img/envops/git_bash.png "git bash")  
  
콘솔에 접속하였다면, 먼저 다음 명령어로 사용자를 등록해줍니다.
```
git config --global user.name ""유저 이름""
git config --global user.email ""가입할때 사용한 이메일""
```
![git user](https://songhwee1.github.io/assets/img/envops/git_bash_user.png "git user")  

## GitHub에 있는 Repository가져오기
먼저, 저장소를 둘 위치로 이동을 합니다.
저는 C드라이브 밑에 둘것이기 때문에 다음 명령어를 입력해줬습니다.
```
cd C:
```
그리고, 다음 명령어를 통해 저장소를 로컬로 clone해줍니다.
```
git clone https://github.com/사용자명/저장소명.git
```
그리고 **ls** 명령어를 통하여 디렉토리에 정상적으로 clone이 이루어졌는지 확인해줍니다.

## Git 자주 사용하는 명령어  
+ **git init** : 현재 디렉터리를 Git 저장소로 변환해줍니다.  
+ **git add** : 파일을 원격 저장소에 추가합니다. ( 예시로 test1.py를 추가하려면 git add test1.py  실제 추가가 아니라 깃의 저장소의 스냅샷에 포함된다고 생각하면 될듯 합니다.)  
+ **git commit** : 디렉토리의 변경과 추가를 저장소에 기록합니다. ( git commit -m "New File" : 커밋 시 남길 메시지)  
+ **git push** : 로컬 저장소의 변경사항을 github에 반영합니다. ( git push origin master )  
+ **git checkout** : 현재 위치하고 있지 않은 저장소를 체크아웃합니다. (예를 들어 master 브랜치를 보고 싶으면, git checkout master를 사용할 수 있습니다.)  
+ **git merge** : 브랜치에서 하던 작업을 끝내고, 동료가 볼 수 있는 master브랜치로 합치는 과정입니다.  
+ **git pull** : 로컬 저장소 작업할 때, 작업하고 있는 저장소의 최신 버전을 받아옵니다.  

## GitHub에 코드 업로드하기

먼저, 업로드 하려는 파일을 원격 저장소에 추가해줍니다.
```
git add 파일명 (모든 파일을 추가하려면 git add *)
```
이후, **commit**을 해줍니다.
```
git commit -m "어떤 내용을 commit하였는지"
```
그리고, GitHub로 **push**를 해줍니다.
```
git push origin main
```
이후 GitHub에 접속해보면, Repository가 최신화 된 것을 확인할 수 있습니다.

-----
Git과 GitHub의 사용은 개발자에게 매우 중요합니다.  
사용법을 잘 익혀둔다면 두고두고 큰 도움이 될거라고 생각합니다. 화이팅!