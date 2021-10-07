---
layout: post
title: 어댑터 패턴
date: 2021-10-07 23:14:23 +0900
category: DesignPattern
---
# 어댑터 패턴
<br/>

> 한 클래스의 인터페이스를 클라이언트에서 사용하고자 하는 다른 인터페이스로 변환함.
어댑터를 이용하면 인터페이스 호환성 문제로 같이 쓸 수 없는 클래스를 연결해서 쓸 수 있다.

**이미 제공되어있는것 과 필요한것 사이의 차이를 없애주는 디자인 패턴**

이미 만들어진 클래스를 새로운 인터페이스에 맞게 개조시키는 경우에 사용!

<br/>
<br/>


```c#
namespace CSharp_AdapterPattern
{
    class Target
    {
        public virtual void Request()
        {
            Console.WriteLine("Called Target Request()");
        }
    }
 
    class Adapter : Target
    {
        private Adaptee _adaptee = new Adaptee();
 
        public override void Request()
        {
            _adaptee.SpecificRequest();
        }
    }
 
    class Adaptee
    {
        public void SpecificRequest()
        {
            Console.WriteLine("Called SpecificRequest()");
        }
    }
 
    class Program
    {
        static void Main()
        {
            Target target = new Adapter();
            target.Request();
        }
    }
}

```
<br/>
<br/>

위의 예시는 어댑터 클래스를 활용하는 방법





```c#

// 우리 회사에서 PayY 인터페이스 구현
public class PayImpl : PayY, PayX {

    // for PayY
    private string customerCardNum;

	public string getCustomerCardNum() {
		Debug.Log ("PayY (Get)");
		return customerCardNum;
	}

	public void setCustomerCardNum (string customerCardNum) {
		Debug.Log ("PayY (Set)");
		this.customerCardNum = customerCardNum;
	}

	// ------------------------------------------------------

	// for PayX Method
    public string getCreditCardNum()
    {
        return getCustomerCardNum();
    }

    public void setCreditCardNum(string creditCardNum)
    {
        setCustomerCardNum(creditCardNum);
    }
}

```
<br/>
<br/>

위의 예시는 원래 인터페이스(payX)를 다른 인터페이스 (payY) 로 변환하는 클래스!





