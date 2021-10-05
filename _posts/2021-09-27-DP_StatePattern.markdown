---
layout: post
title: 상태 패턴
date: 2021-09-27 23:18:30 +0900
category: DesignPattern
---
# 상태 패턴
<br/>

> 내부 상태에 따라 스스로 행동을 변경 하는것을 허가하는 패턴

**객체를 구성하는 부분을 생성하고 조합함으로 객체를 생성**

<br/>
<br/>


```c#
//Implementation in C#.
class Pizza
{
    string dough;
    string sauce;
    string topping;
    public Pizza() {}
    public void SetDough( string d){ dough = d;}
    public void SetSauce( string s){ sauce = s;}
    public void SetTopping( string t){ topping = t;}
}

//Abstract Builder
abstract class PizzaBuilder
{
    protected Pizza pizza;
    public PizzaBuilder(){}
    public Pizza GetPizza(){ return pizza; }
    public void CreateNewPizza() { pizza = new Pizza(); }

    public abstract void BuildDough();
    public abstract void BuildSauce();
    public abstract void BuildTopping();
}

//Concrete Builder
class HawaiianPizzaBuilder : PizzaBuilder
{
    public override void BuildDough()   { pizza.SetDough("cross"); }
    public override void BuildSauce()   { pizza.SetSauce("mild"); }
    public override void BuildTopping() { pizza.SetTopping("ham+pineapple"); }
}

//Concrete Builder
class SpicyPizzaBuilder : PizzaBuilder
{
    public override void BuildDough()   { pizza.SetDough("pan baked"); }
    public override void BuildSauce()   { pizza.SetSauce("hot"); }
    public override void BuildTopping() { pizza.SetTopping("pepparoni+salami"); }
}

/** "Director" */
class Waiter {
    private PizzaBuilder pizzaBuilder;

    public void SetPizzaBuilder (PizzaBuilder pb) { pizzaBuilder = pb; }
    public Pizza GetPizza() { return pizzaBuilder.GetPizza(); }

    public void ConstructPizza() {
        pizzaBuilder.CreateNewPizza();
        pizzaBuilder.BuildDough();
        pizzaBuilder.BuildSauce();
        pizzaBuilder.BuildTopping();
    }
}

/** A customer ordering a pizza. */
class BuilderExample
{
    public static void Main(string[] args) {
        Waiter waiter = new Waiter();
        PizzaBuilder hawaiianPizzaBuilder = new HawaiianPizzaBuilder();
        PizzaBuilder spicyPizzaBuilder = new SpicyPizzaBuilder();

        waiter.SetPizzaBuilder ( hawaiianPizzaBuilder );
        waiter.ConstructPizza();

        Pizza pizza = waiter.GetPizza();
    }
}
```
>출처 : 나무위키

<br/>
<br/>

웨이터가 레시피와 피자를 가지고 있고 주문을 받은것대로 **세팅후** 돌려준다
여기서 중요한것은 레시피 *(PizzaBuilder)* 대로 조합하여 세팅하는것!
