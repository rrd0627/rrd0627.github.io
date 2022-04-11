---
layout: post
title: Jenkins
date: 2022-03-09 01:58:52 +0900
category: ETC
---
# Jenkins IOS

Jenkins IOS 빌드

1. 새로운 파이프라인 생성
1. Definition > Pipeline sciprt from SCM ![](/assets/img/Unity/2022-03-23-23-00-15.png) 
1. Script Path 설정 > Assets/Plugins/Editor/Jenkisfile ( 파일 들어있는 위치 )
![](/assets/img/Unity/2022-03-23-23-02-57.png)
1. exportOptionsPlist 파일을 미리 생성하여 옵션에서 지정한 위치에 -  '../../ios-conf/exportOptions.plist'  두어야 함
1. https://appleid.apple.com/account/manage 여기서 앱암호 설정하여 jenkinsfile 에 비밀번호 입력

