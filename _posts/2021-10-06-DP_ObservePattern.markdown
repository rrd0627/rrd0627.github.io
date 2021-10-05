---
layout: post
title: 옵저버 패턴
date: 2021-10-05 00:14:10 +0900
category: DesignPattern
---
# 옵저버 패턴
<br/>

> 한 객체가 그 객체를 의존하는 다른 객체들에게 자동으로 내용을 갱신시켜주는 패턴

**옵저들에게 내용의 변경을 알려줌**

<br/>
<br/>


```c#
using System;

// 먼저 이벤트 발생에 사용할 델리게이트 형식을 선언한다.
// 이것은 System.EventHandler 형식과 같은 델리게이트이다.
// 이 델리게이트는 추상 옵저버로서의 기능을 제공한다.
// 어떠한 구현도 제공하지 않으며, 단지 규약만 제공한다.
public delegate void EventHandler(object sender, EventArgs e);

// 다음으로, 공개된 이벤트를 선언한다. 이것은 구체적인 서브젝트로서의 기능을 제공한다.
public class Button
{
    // 공개된 이벤트를 선언한다.
    public event EventHandler Clicked;

    // 관습적으로, .NET 이벤트 발생은 가상 메서드로 구현된다.
    // 이는 하위 클래스가 해당 이벤트를 재정의를 통해 사용할 수 있게 하고, 발생 여부도 조정할 수 있게 한다.
    protected virtual void OnClicked(EventArgs e)
    {
        // Clicked 이벤트에 등록된 모든 EventHandler 델리게이트를 호출한다.
        if (Clicked != null)
            Clicked(this, e);
    }
}

// 이제 옵서버 클래스에서 이벤트에 델리게이트를 등록하거나 등록 해제할 수 있다:
public class Window
{
    private Button okButton;

    public Window()
    {
        okButton = new Button();

        // Clicked 이벤트에 델리게이트를 등록하는 부분이다. 등록 해제는 -= 연산자를 사용한다.
        // 다수의 옵서버가 Clicked 이벤트에 델리게이트를 등록하는 것이 가능하다.
        okButton.Clicked += new EventHandler(okButton_Clicked);
    }

    private void okButton_Clicked(object sender, EventArgs e)
    {
        // 이 메서드는 Button 클래스에서 Clicked(this, e) 를 호출할 때마다 실행된다.
    }
}
```
<br/>
<br/>

옵저버 클래스에서 자신이 보고있는 서브젝트만 보고있다가 서브젝트가 이벤트를 발생하는 순간 실행되도록 하는 패턴!
