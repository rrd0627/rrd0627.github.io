---
layout: post
title: 스트레티지 패턴
date: 2021-09-16 22:49:17 +0900
category: DesignPattern
---
# 스트레티지 패턴
<br/>

> 동일 목적의 기능을 서로 교환할 수 있도록 하는 패턴
예시 : 게임 케릭터 무기 변경 후 사용


<br/>
<br/>

```c#
public class GameManager : MonoBehaviour
{
    MyWeapon myWeapon;

    Start()
    {
        myWeapon = new MyWeapon();        
    }

    public void ChangeSword()
    {
        myWeapon.SetWeapon(new Sword());
    }
    public void ChangeSpear()
    {
        myWeapon.SetWeapon(new Spear());
    }
    public void ChangeGun()
    {
        myWeapon.SetWeapon(new Gun());
    }
    public void Fire()
    {
        myWeapon.Fire();
    }    
}
```

```c#
//스테틱 함수로 선언
public class MyWeapon
{
    // 인터페이스
    private IWeapon weapon;

    public void SetWeapon(IWeapon _weapon)
    {
        weapon = _weapon;
    }

    public void Fire()
    {
        weapon.Fire();
    }
}
```

```c#
//인터페이스
public interface IWeapon
{
    void Fire();
}
```


```c#
//인터페이스를 받음
public class Sword : IWeapon
{
    public void Fire()
    {
        Debug.Log("Sword Slash!");
    }
}
```

```c#
//인터페이스를 받음
public class Gun : IWeapon
{
    public void Fire()
    {
        Debug.Log("Gun Fire!");
    }
}
```