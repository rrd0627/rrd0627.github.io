---
layout: post
title: Jenkins
date: 2022-03-09 01:58:52 +0900
category: ETC
---
# Jenkins IOS

Jenkins IOS 빌드

1. 새로운 pipeline 생성 후 Editor Command는 
( -quit -batchmode -buildTarget iOS -executeMethod AutoBuilder.PerformBuildIOS )
1. Developmnet Team -> ( 시스템 설정에서 추가 )

Configuration -> Release

Xcode Schema File -> Unity-iPhone

Generate Archive? -> Check

Pack application, build and sign .ipa? -> Check

Export method -> app-store

.ipa filename pattern -> Unity-iPhone

Upload Symbols? -> Check

Pack on demand resources? -> Check

Strip Swift Symobols? -> Check

< Code signing & OS X keychain options >

Automatic Signing -> Check

< Advanced Xcode build options >

Xcode Project Directory -> ./IOS