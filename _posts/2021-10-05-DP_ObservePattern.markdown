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
