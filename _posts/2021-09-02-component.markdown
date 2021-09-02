---
layout: post
title: 컴포넌트 패턴
date: 2021-09-02 23:18:34 +0900
category: DesignPattern
---
# 컴포넌트 패턴
> 기능을 잘게 나누어, 쉽게 읽히고 다른 스크립트와 엮이지 않도록 하는 것

<br/>
<br/>
예를 들어 position, rotation, scale을 동시에 조절하는 스크립트가 있다고 생각해 보자
<br/>
<br/>

<br/>
```c#
public class ComplexMove : MonoBehaviour
{
    private void Start()
    {
        StartCoroutine(StartCor());
    }

    IEnumerator StartCor()
    {
        while (true)
        {
            transform.Translate(Vector3.forward);

            transform.Rotate(Vector3.up * 20);

            transform.localScale *= 0.9f;

            yield return new WaitForSeconds(0.5f);
        }
    }
}
```
![](/assets/img/designpattern/2021-09-02-23-35-26.png)

<br/>
<!-- 움직임은 다음과 같다. -->
<br/>
이때 어느 한가지만 다른 주기로 움직이고 싶다거나 움직임의 정도를 바꾸고 싶을때 복잡해진다.
<br/>
<br/>

그렇기 때문에 컴포넌트 패턴을 활용하여 추가하는 식으로 다음과 같이 작성한다.


```c#
public class PositionMove : MonoBehaviour
{
    private void Start()
    {
        StartCoroutine(StartCor());
    }

    IEnumerator StartCor()
    {
        while (true)
        {
            transform.Translate(Vector3.forward);

            yield return new WaitForSeconds(0.5f);
        }
    }
}


public class RotationMove : MonoBehaviour
{
    private void Start()
    {
        StartCoroutine(StartCor());
    }
    
    IEnumerator StartCor()
    {
        while (true)
        {
            transform.Rotate(Vector3.up * 20);

            yield return new WaitForSeconds(0.5f);
        }
    }
}



public class ScaleMove : MonoBehaviour
{
    private void Start()
    {
        StartCoroutine(StartCor());
    }
    
    IEnumerator StartCor()
    {
        while (true)
        {
            transform.localScale *= 0.9f;

            yield return new WaitForSeconds(0.5f);
        }
    }
}
```

<br/>

![](/assets/img/designpattern/2021-09-02-23-38-36.png)


<br/>
기능별로 컴포넌트로 나누어 쉽게 이해할 수 있고 다른 컴포넌트와는 상관없이 각각 수정할 수 있다.