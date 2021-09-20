---
layout: post
title: 추상 팩토리 패턴
date: 2021-09-21 02:02:25 +0900
category: DesignPattern
---
# 추상 팩토리 패턴
<br/>

> 팩토리 매서드와 비슷!
관련성이 있는 여러 종류의 객체를 생성 할 때 사용!

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
public abstract class UnitFactory : Monobehaviour
{
    public abstract void CreateUnit();    
    public abstract void CreateWeapon(); 
}
```

```c#
class GunUnitFactory : UnitFactory
{    
    public GameObject gunUnit;
    public GameObject gun;
    public override void CreateUnit()
    {
        return Instantiate(gunUnit);
    }
    public override void CreateWeapon()
    {
        return Instantiate(gun);
    }
}
```


```c#
class FactoryMethod : Monobehaviour
{
    public UnitType type = UnitType.GUN;
    
    public UnitFactory getFactory()
    {
        UnitFactory factory = null;

        switch(type)
        {
            case UnitType.GUN:
                factory = GetComponent<GunUnitFactory>();
            break;
        }
        return factory;
    }
}
```

```c#
class FactoryMethodUse : Monobehaviour
{
    UnitFactory factory = null;    
    
    void Start()
    {
        factory = GetComponent<FactoryMethod>().getFactory();
        
        //뭔진 모르겟고! 만들뿐!
        GameObject unit = factory.CreateUnit();
        GameObject weapon = factory.CreateWeapon();
    }
}
```