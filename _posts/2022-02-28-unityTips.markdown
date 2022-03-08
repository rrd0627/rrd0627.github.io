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
1. https://api.slack.com/apps/ 접속 > Create An App > From Strech > workspace 결정 후 create
1. Basic Information > Incoming WebHook On
1. Basic Information > Permission > Bot Token Scope > 
![](/assets/img/Unity/2022-03-09-01-09-06.png)
1. Basic Information > Install To workspace
1. OAuth & Permissions 에서 OAuth Tokens for Your Workspace
확인
1. Jenkins 에서 Add Credentials > ![](/assets/img/Unity/2022-03-09-00-53-07.png)
Secret에 OAuth Token넣어주기
1. 젠킨스 아이템 구성에 빌드 후 조치에 해당 Credential 넣고 Workspace Channel 넣고 Test Connection
1. ![](/assets/img/Unity/2022-03-09-01-11-39.png) 
Custom slack app bot user 체크
1. Slack File Upload는 ![](/assets/img/Unity/2022-03-09-01-15-05.png)  (경로를 주의해서 설정!)
1. ![](/assets/img/Unity/2022-03-09-01-20-39.png) 
슬랙에서 앱 추가!