---
layout: post
title: 싱글톤 패턴
date: 2021-09-16 00:39:52 +0900
category: DesignPattern
---
# 싱글톤 패턴
<br/>

> 한 개의 클래스 인스턴스만 가지고, 전역적인 접근이 가능하도록 하는 패턴


<br/>
<br/>

>장점
접근이 쉽다!

>단점
여러 클래스와 커플링됨! 복잡함!

<br/>
<br/>

```c#
public class GameManager : MonoBehaviour
{
    public static GameManager instance;

    private void Awake()
    {
        instance = this;        
    }
}
```