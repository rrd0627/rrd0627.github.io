---
layout: post
title: 팩토리 매서드 패턴
date: 2021-09-18 23:37:52 +0900
category: DesignPattern
---
# 팩토리 매서드 패턴
<br/>

> 객체를 생성하기 위한 인터페이스를 정의!
서브클래스에서 결정함으로써 객체 생성을 캡슐화!

<br/>
<br/>

코드 중복을 줄이고 생성을 한군데에서 관리 할 수 있다.
새로운 객체가 추가되어도 소스의 수정이 거의 없다.

유지관리에서 좋다!


<br/>
<br/>

```c#
public enum UnitType
{
    SWORD,
    SPEAR,
    GUN,
}
```

```c#
abstract class UnitFactory : Monobehaviour
{
    public abstract void CreateUnit(UnitType unitType);     
}
```

```c#
class UnitGenerator : UnitFactory
{
    public UnitType unitType;

    public override void CreateUnit()
    {
        switch(unitType)
        {
            case UnitType.SWORD:
                unit = Instantiate(SwordUnit);
            break;
            case UnitType.SPEAR:
                unit = Instantiate(SpearUnit);                
            break;
            case UnitType.GUN:
                unit = Instantiate(GunUnit);                
            break;
        }
    }   
}
```


```c#
class UnitGenerator : Monobehaviour
{
    UnitGenerator factory = null;

    void Start()
    {
        factory = GetComponent<UnitGenerator>();

        //어디선가 어떤 조건에 의해 바꾸어주고
        factory.unitType = UnitType.GUN;

        //나는 뭐만드는지 모름! 만들뿐!
        factory.CreateUnit();        
    }
}
```