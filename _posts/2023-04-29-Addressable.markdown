---
layout: post
title: Addressable0
date: 2023-04-29 01:00:24 +0900
category: Addressable
---
# Addressable 막무가내 정리하기

Resources 와 Addressable 의 차이

앱사이즈가 증가하기 떄문에 좋지 않다

AssetBundle로 다운로드를 하도록 함

그런데 의존성 때문에 문제가 생김

의존성이란 같은 텍스쳐를 다른 번들에 둘다 넣은경우 

에디터에서 공통 참조되는것은 두개 로드 됨 ( 중복 로드가 되면서 런타임 메모리가 두배로 들어감)

시작 로딩이 길어짐

의존성을 어느정도 해결해줌

로컬에서 사용할지 다운받아서 설정할지 고를 수 있음

레퍼런스 카운트를 관리하며 번들에 포함된 에셋이 레퍼런스가 있을경우 번들은 메모리에 로드 됨

번들에 있는 모든 에셋레퍼런스가 0이면 언로드 됨


에셋번들을 어떻게 식별하는지

에셋번들은 ID가 있음

번들 아이디가 이미 메모리에 있으면 다시 같은 번들 아이디를 로드 할 수 없게 되어있음

러닝중에 번들을 다시 로드해야되면 에셋 번들 시스템 상 불가능

어드레서블은 번들 빌드시 고유한 아이디를 생성함 ( 같은 번들도 이전 버전과는 다른 아이디가 생김 )




yield return Addressables.InitalizeAsnyc() 로 초기화함

로드 먼저 하거나 하면 내부적으로 어차피 실행 됨

Addressables.LoadAssetAsnyc 로 메모리에 올림 ( 레퍼런스 카운트 +1)

Addressables.InstantiateAsync 로 인스턴스 생성( 레퍼런스 카운트 +1)

Addressables.ReleaseInstance 로 인스턴스 삭제 (레퍼 -1)

Addressables.Release 메모리 언로드 (레퍼 -1)


빌드 하고나면 Library   com.unity.addessables   aa   android   여기에 빌드된 번들 파일과 세팅파일 존재



세팅에서 Build를 Do not build로 해주어 수동으로 빌드하도록 함



# Addressable 핵심

어드레서블은 이니셜때 세팅을 읽어서 카탈로그를 읽음
로컬 카탈로그를 세팅에서 찾음

settings.json - 정보 리스트를 찾기위한 데이터가 들어가 있음 
(ex : 카탈로그 로케이션 )

catalog.json - 번들의 목록


InistalizeAsync 호출 후레 Catalog를 읽음

리소스 로케이터를 통해 리소스 로케이션으로 변환한다

카탈로그에 있는 데이터를 토대로 키 값들을 로케이터로 로케이션형태로 변환

로케이션은 에셋을 로드하기 위한 의존성 관계나 키 값 어떤 프로바이더르 사용해서 로드할지 정보가 있음




Resource Location

Resource Locator

Resource Provider



remote catalog 해쉬값은 카탈로그 json데이터를 토대로 해쉬값을 만듦

카탈로그가 바뀌면 해쉬값도 당연히 바뀌고 안바뀌면 그대로



카탈로그 다운로드 -> 사이즈 다운로드 -> 번들 다운로드


카탈로그는 리모트와 로컬의 카탈로그 해쉬값이 서로 다른경우 다운로드 받음

사이즈 다운로드는 유저에게 동의를 구할때와 새로 받을 번들이 있는지 알아야할 때 다운로드받을게 없으면 사이즈가 0

번들 다운받기 = 라벨 기준으로 다운