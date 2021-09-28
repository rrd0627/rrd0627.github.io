---
layout: post
title: 빌더 패턴
date: 2021-09-27 23:18:30 +0900
category: DesignPattern
---
# 빌더 패턴
<br/>

> 복잡한 유형의 오브젝트를 조합하여 만드는데 사용

**객체를 구성하는 부분을 생성하고 조합함으로 객체를 생성**

<br/>
<br/>


```c#
interface IUnitBuilder
{
    Unit getUnit();
    
    void BuildFrame();
    void BuildWeapon();
    void BuildMove();    
}
```


```c#
class TankBuilder : IUnitBuilder
{
    private Unit _unit;

    public Unit getUnit()
    {
        return _unit;
    }

    public TankBuilder()
    {
        _unit = new Unit();
    }
    
    public void BuildFrame()
    {
        print("장갑차");
    }
    public void BuildWeapon()
    {
        print("대포");
    }
    public void BuildMove()
    {
        print("바퀴");
    }
}
```


```c#
class SwordBuilder : IUnitBuilder
{
    private Unit _unit;

    public Unit getUnit()
    {
        return _unit;
    }

    public SwordBuilder()
    {
        _unit = new Unit();
    }
    
    public void BuildFrame()
    {
        print("사람몸");
    }
    public void BuildWeapon()
    {
        print("검");
    }
    public void BuildMove()
    {
        print("다리");
    }
}
```

```c#
class UnitMaker
{
    public void Construct(IUnitBuilder unitBuilder)
    {
        unitBuilder.BuildFrame();
        unitBuilder.BuildWeapon();    
        unitBuilder.BuildMove();    
    }
}
```

```c#
class UnitManager : MonoBehaviour
{    
    void Start()
    {
        UnitMaker unitMaker = new UnitMaker();
        
        SwordBuilder swordBuilder = GetComponent<SwordBuilder>();
        TankBuilder tankBuilder = GetComponent<TankBuilder>();

        unitMaker.Construct(swordBuilder);
        unitMaker.Construct(tankBuilder);

        Unit swordUnit = swordBuilder.getUnit();
        Unit tankUnit = tankBuilder.getUnit();
    }
}
```

<br/>
<br/>