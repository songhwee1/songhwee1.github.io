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
+ 클라우드 방식으로 관이되는 버전 관리 시스템(VCS)
+ 자체 구축이 아닌 빌려쓰는 클라우드의 개념  

간단하게 말해서 **Git**은 로컬 버전 관리 시스템을 운영하는 방식이고, **GitHub**는 깃허브에서 제공해주는 클라우드 서버를 이용한다는 것의 차이입니다.

## Git 설치하기  
[여기](https://gitforwindows.org/)에 접속해서 Download버튼을 눌러 Git을 다운로드 해줍니다.  
이후 설치 옵션들은 next를 눌러주며 기본 옵션으로 설치해줍니다.  

설치가 되었다면, Cmd(명령 프롬프트)창을 열고, 다음 명령어를 입력하여 정상적으로 설치가 되었는지 확인해줍니다.
```
git version
```
정상적으로 설치가 되었다면, 아래와 같은 화면이 나옵니다.
![git 다운로드 확인](https://songhwee1.github.io/assets/img/envops/git_download_test.png "git 다운로드 확인")