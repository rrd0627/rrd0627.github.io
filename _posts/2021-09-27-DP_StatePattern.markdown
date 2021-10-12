---
layout: post
title: 상태 패턴
date: 2021-09-27 23:18:30 +0900
category: DesignPattern
---
# 상태 패턴
<br/>

> 내부 상태에 따라 스스로 행동을 변경 하는것을 허가하는 패턴

<br/>
<br/>


```c#
public interface PowerState {
    public void powerPush();
}


public class On : PowerState{
    public void powerPush(){
        System.out.println("전원 off");
    }
}
public class Off : PowerState {
    public void powerPush(){
        System.out.println("절전 모드");
    }
}
public class Saving : PowerState {
    public void powerPush(){
        System.out.println("전원 on");
    }
}


public class Laptop {
    private PowerState powerState;

    public Laptop(){
        this.powerState = new Off();
    }

    public void setPowerState(PowerState powerState){
        this.powerState = powerState;
    }

    public void powerPush(){
        powerState.powerPush();
    }
}


public class Client {
    public static void main(String args[]){
        Laptop laptop = new Laptop();
        On on = new On();
        Off off = new Off();
        Saving saving = new Saving();

        laptop.powerPush();
        laptop.setPowerState(on);
        laptop.powerPush();
        laptop.setPowerState(saving);
        laptop.powerPush();
        laptop.setPowerState(off);
        laptop.powerPush();
        laptop.setPowerState(on);
        laptop.powerPush();
    }
}

```

<br/>
<br/>

같은 버튼을 누르지만 상태에 따라 다르게 바뀜!
분기문을 처리하는데 사용됨!