---
layout: post
title: 프로토타입 패턴
date: 2021-09-21 19:13:45 +0900
category: DesignPattern
---
# 프로토타입 패턴
<br/>

> 모든 객체 생성을 new 로 하지 않고 본래 object로부터 새로운 object를 만들어냄

<br/>
<br/>

```c#
public interface IUnit
{
    IUnit Clone();
}
```

```c#
public class SwordUnit : IUnit
{
    public int Hp {get;set;}
    public int AttackPower {get;set;}

    public IUnit Clone()
    {
        //얕은 복사    
        return this.MemberwiseClone() as IUnit;
    }
}
```

```c#
class UnitManager : MonoBehaviour
{    
    void Start()
    {
        SwordUnit swordUnit = new SwordUnit();
        swordUnit.Hp = 10;
        swordUnit.AttackPower = 5;

        //원래의 오브젝트로 부터 새로운 Clone생성! 
        //다른 객체임!
        SwordUnit swordUnitClone = (SwordUnit)swordUnit.Clone();

        swordUnitClone.Hp = 20;
        swordUnitClone.AttackPower = 2;
    }
}
```