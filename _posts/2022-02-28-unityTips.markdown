---
layout: post
title: Jenkins
date: 2022-02-28 19:51:13 +0900
category: ETC
---
# Jenkins

Mac에서

1. brew install jenkins-lts   ( 다운로드 )
1. jenkins ( 실행 )
1. localhost:8080 접속
1. 비밀번호로 접속후 추천 플러그인 설치 ( 비밀번호는 터미널이나 JENKINS_HOME/secrets/initialAdminPassword 여기서 확인)
1. Unity3d/xcode intergration/ant/gradle/slack notification 플러그인 설치 
1. jenkins git 연동 ( 모든 유저 )
1. git webhook 연동 ( push 로 빌드하기... ip가 필요하므로 포트포워딩)
1. Unity 빌드 환경 세팅
### Docker Download

1. https://docs.docker.com/docker-for-mac/install/
1. https://github.com/docker/kitematic#installing-kitematic
1. Jenkins 검색 , 가장 많은 다운로드수를 가진 게시물 Create
1. Local Folder 설정
1. 세팅에 포트번호로 접속
1. 비밀번호로 접속후 추천 플러그인 설치
1. 어드민 설정
1. 