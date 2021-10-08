---
layout: post
title: 커맨드 패턴
date: 2021-10-09 01:22:05 +0900
category: DesignPattern
---
# 커맨드 패턴
<br/>

> 매서드 호출을 실체화 ,  즉 객체로 감싼 것

함수 호출을 객체화 하여 디커플링 되어 코드가 유연함

<br>

*게임 프로그래밍에서 사용예시*

- 입력키 변경
- 실행 취소, 재실행

<br/>
<br/>


```c#

interface Command
{
    public void excute();
}

class Button
{
    private Command command;
    public Button(Command command) { this.command = command; }
    public void setCommand(Command command) { this.command = command; }
    public void pressed() { command.excute(); }
}

class LampOnCommand : Command
{
    private Lamp lamp;
    public LampOnCommand(Lamp lamp)
    {
        this.lamp = lamp;
    }
    public override void excute()
    {
        lamp.turnOn();
    }
}
class AlarmStartCommand : Command
{
    private Alarm alarm;
    private Lamp lamp;
    private Window window;
    public AlarmStartCommand(Alarm alarm, Lamp lamp, Window window)
    {
        this.alarm = alarm;
        this.lamp = lamp;
        this.window = window;
    }
    public override void excute()
    {
        alarm.start();
        lamp.turnOn();
        window.open();
    }
}
class Lamp
{
    public void turnOn() { print("turn on lamp"); }
}
class Alarm
{
    public void start() { print("start alarm"); }
}
class Window
{
    public void open() { print("open window"); }
    public void close() { print("close window"); }
}


```
<br/>
<br/>

인터페이스를 설정하고 해당 객체에 알맞는 스크립트를 넣어서 구현된것을 활용


