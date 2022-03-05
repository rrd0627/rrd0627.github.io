---
layout: post
title: Jenkins
date: 2022-02-28 19:51:13 +0900
category: ETC
---
# Jenkins

Mac에서

1. brew install jenkins-lts   ( 다운로드 )
1. jenkins 또는 jenkins-lts ( 실행 )
1. localhost:8080 접속
1. 비밀번호로 접속후 추천 플러그인 설치 ( 비밀번호는 터미널이나 JENKINS_HOME/secrets/initialAdminPassword 여기서 확인)
1. Unity3d/xcode intergration/ant/gradle/slack notification 플러그인 설치 
1. 다른 컴퓨터에서 내부 망을 통해 접속 할 수 있도록 URL 변경 ![](/assets/img/Unity/2022-03-03-22-20-40.png)  
1. 회원가입이 가능하도록 Jenkins관리 > Configure Global Security > 사용자 가입 허용
1. jenkins git 연동 ( 필수 - 각자 유저가 ) ( Jenkins관리 > 시스템설정 > GitHub > GitHub Server) ![](/assets/img/Unity/2022-03-03-23-01-43.png)  Secret에는 깃에서 받은 Personal access tokens 넣기  (GitHub > Setting > Developer Setting > Personal access tokens > Generate new tokken )  ![](/assets/img/Unity/2022-03-03-23-01-14.png)
1. git webhook 연동하여 push 로 빌드하기 ( 옵션 - 각자 유저가 )
1. Unity 빌드 환경 세팅 ( jenkins 관리 > Global tool Configuration) ![](/assets/img/Unity/2022-03-03-22-53-02.png)
1. ( -quit -batchmode -buildTarget Android -executeMethod AutoBuilder.PerformBuildAOS )