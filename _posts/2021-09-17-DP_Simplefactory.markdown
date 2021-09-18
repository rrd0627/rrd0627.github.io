---
layout: post
title: 심플 팩토리 패턴
date: 2021-09-16 22:49:17 +0900
category: DesignPattern
---
# 심플 팩토리 패턴
<br/>

> 객체 생성 패턴 중 기본!
주어진 입력을 기반으로 객체를 반환하는 패턴!

<br/>
<br/>

```c#
public enum UnitType
{
    SWORD,
    SPEAR,
    GUN,
}
public class UnitFactory
{
    public static Unit CreateUnit(UnitType unitType)
    {
        Unit unit = null;

        switch(unitType)
        {
            case UnitType.SWORD:
                unit = new SwordUnit();
            break;
            case UnitType.SPEAR:
                unit = new SpearUnit();
            break;
            case UnitType.GUN:
                unit = new GunUnit();
            break;
        }
        return unit;
    }    
}

```

CreateUnit 함수를 활용하여 어디서든 Unit생성 가능
