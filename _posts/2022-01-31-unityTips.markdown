---
layout: post
title: Unity URP Shader
date: 2022-01-31 23:54:42 +0900
category: ETC
---
# URP Shader

```c#
#ifndef CUSTOM_LIGHTINIG_INCLUDED
#define CUSTOM_LIGHTINIG_INCLUDED

void CalcaulateMainLight_float(float3 WorldPos,out float3 Direction, out float3 Color){
    #if defined(SHADERGRAPH_PREVIEW)
        Direction = float3(0.5,0.5,0);
        Color = 1;
    #else
        Light mainLight = GetMainLight(0);
        Direction = mainLight.direction;
        Color = mainLight.color;
    #endif    
}
#endif
```

CalcaulateMainLight_float 에서 CalcaulateMainLight가 함수 이름이고 float은 어떤 type을 사용할지 알려줌

float3 WorldPos,out float3 Direction, out float3 Color
에서 WorldPos는 인풋 나머지둘은 아웃풋

defined(SHADERGRAPH_PREVIEW) 는 쉐이더 그래프내에서 프리뷰로 보이는 아웃풋

GetMainLight는 유니티에서 가장 밝은 디렉셔널 라이트



해당 코드를 메인 라이트르 구하는데에 사용하여 쉐이더 그래프의 커스텀 Func으로 사용

![](/assets/img/Unity/2022-02-01-16-50-59.png)

인풋으로 월드포지션을 넣어 커스텀 func에서 나온 메인라이트 dir과 normal을 dot하여 -1 부터 1까지 메인라이트와의 방향성을 구함

거기서 1더해주고 2로 나누어 0에서 1로 바꿈

메인라이트의 컬러와 곱해주고 아웃풋을 컬러에 넣어주면 짜잔

보통 평범한 빛을 받는 쉐이더 완성


### Toon Ramp

![](/assets/img/Unity/2022-02-01-17-10-43.png)

빛을 받는 쉐이더에서 아웃풋 diffuse를 빼와서 x값으로 넣어주어 uv로 바꾸어주어 텍스처에 맞게 표현하면

텍스처 x값의 변화에 따라 빛의 명암이 변한다

### Texture

![](/assets/img/Unity/2022-02-01-17-26-49.png)

텍스처 넣어주기