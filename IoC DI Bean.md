**IoC**컨테이너란 **Inversion Of Control**의 약자로 이것을 알기 위해서는 컨테이너에 대해서 알아야한다.

컨테이너란 기존의 자바 애플리케이션에서의 객체의 생성주기, 결합 등을 자바 애플리케이션을 만든 코드가 결정했다면 이제는 컨테이너가 자바 애플리케이션을 이루는 객체들의 인스턴스의 생명주기를 관리하고, 생성된 인스턴스들에게 추가적인 기능을 제공해준다.

IoC라는 이름이 붙은 이유는 **제어의 역전 즉 외부에서 제어를 한다는 것이다.** 즉 객체의 인스턴스 생성, 생명주기 인스턴스화 등 모든 객체에 대한 제어권을 컨테이너가 갖고 있다는 뜻이다.

**DI**는 **Dependency Injection**으로 말그대로 의존성 있는 객체끼리 연결해주는 행위이다.
하지만 기존의 애플리케이션을 만들때는 
```java
class A{
	B b = new B();
}

class B{
	//some method
}
```
이렇게 객체 속에 직접 주입했다면 스프링에서는
```java
class A{
	Binterface B;
	public void setB(Binterface B){
		this.B = B;
	}
}

class B implement Binterface{
	//some method implementation
}
```
이렇게 setter 메서드를 만들어서 의존성 있는 객체끼리 연결해주는 setter, constructor 메서드 등을 만들어주고 따로 xml 또는 java annotation 등을 이용해서 의존성이 있는 객체끼리 연결해준다.

굳이 인터페이스로 기능을 정의하는 이유는 이렇게 하지 않으면 
```java
class A{
	B b;
	public void setB(B b){
		this.b = b;
	}
}

class B{
	//some code
}
```
클래스 B의 기능을 바꾸고 클래스 C로 바꿔야 된다고 했을때 바꿔야되는 코드가 생긴다. 코드를 직접 바꾸는 것은 유지보수에 힘들다. 우리는 이것을 연결성이 높아진다고 표현한다.

인터페이스를 만들어서 미리 기능을 정의하고 객체를 기능 구현으로만 만들면 객체를 바꾸기가 편하고 setter, constructor 같은 것을 설정하면 사용자가 아닌 컨테이너 객체를 대신해서 관리해 줄 수 있다. 이것을 연결성이 낮고 느슨한 결합이라고 한다. 우리는 항상 느슨한 결합을 해야 유지보수하기 쉬운 코드가 만들어진다.

그리고 이렇게 IoC 컨테이터에 의해 관리당하는 객체들을 **Bean**이라고 한다.

