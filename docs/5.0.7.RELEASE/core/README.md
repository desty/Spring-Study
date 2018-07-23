# 핵심 기술

참고 문서의 이 부분은 Spring Framework에 절대적으로 필수적인 모든 기술을 다룹니다.

그 중 가장 중요한 것은 Spring Framework의 IoC (Inversion of Control) 컨테이너입니다. Spring Framework의 IoC 컨테이너를 철저히 처리한 다음 Spring의 AOP (Aspect-Oriented Programming) 기술을 포괄적으로 다루고 있습니다.
Spring Framework에는 개념적으로 이해하기 쉽고 Java 엔터프라이즈 프로그래밍에서 AOP 요구 사항의 80%를 충족시키는 자체 AOP Framework를 가지고 있습니다.

Spring과 AspectJ (현재는 기능면에서 가장 부유 한 - 그리고 Java 엔터프라이즈 영역에서 가장 성숙한 AOP 구현)와의 통합도 제공됩니다.

## IoC 컨테이너

### Spring IoC 컨테이너와 빈(beans)에 대한 소개

이 장에서는 IoC (Inversion of Control) 원리의 Spring Framework 구현에 대해 다룹니다. IoC는 종속성 주입(DI-dependency injection)이라고도합니다. 이것은 객체가 자신의 종속성, 즉 생성자 인수, factory method에 대한 인수 또는 factory method에서 구성되거나 반환된 후 객체 인스턴스에 설정된 속성을 통해서만 작업하는 다른 객체를 정의하는 프로세스입니다. 그런 다음 컨테이너는 Bean을 작성할 때 이러한 종속성을 주입합니다. 이 프로세스는 근본적으로 반비례하므로 클래스 직접 작성 또는 Service Locator 패턴과 같은 메커니즘을 사용하여 종속성의 인스턴스 또는 위치를 제어하는 Bean 자체의 Inversion of Control (IoC)입니다.

org.springframework.beans와 org.springframework.context 패키지는 Spring Framework의 IoC 컨테이너의 기초입니다. [BeanFactory](https://docs.spring.io/spring-framework/docs/5.0.7.RELEASE/javadoc-api/org/springframework/beans/factory/BeanFactory.html) 인터페이스는 모든 유형의 객체를 관리 할 수 있는 고급 구성(advanced configuration) 메커니즘을 제공합니다. [ApplicationContext](https://docs.spring.io/spring-framework/docs/5.0.7.RELEASE/javadoc-api/org/springframework/context/ApplicationContext.html)는 BeanFactory의 하위 인터페이스입니다. Spring의 AOP 기능;메시지 자원 처리 (국제화에 사용), 이벤트 발행;과 웹 애플리케이션에서 사용하기위한 WebApplicationContext와 같은 애플리케이션 계층 별 컨텍스트 등의 통합이 더 쉽습니다.

즉, BeanFactory는 구성 프레임워크와 기본 기능을 제공하고 ApplicationContext는 엔터프라이즈 특정 기능을 추가합니다. ApplicationContext는 BeanFactory의 완전한 수퍼 셋이며 Spring의 IoC 컨테이너에 대한 설명에서 이 장에서만 사용된다. ApplicationContext 대신 BeanFactory를 사용하는 것에 대한 자세한 정보는 [The BeanFactory]를 참조하십시오.

Spring에서는 애플리케이션의 뼈대(backbone)를 형성하고 Spring IoC 컨테이너에 의해 관리되는 객체를 Bean이라고 부른다. Bean은 Spring IoC 컨테이너에 의해 인스턴스화, 어셈블링 및 관리되는 객체이다. 그렇지 않으면 bean은 단순히 애플리케이션의 많은 객체 중 하나입니다. Bean들과 그 사이의 의존성은 컨테이너가 사용하는 컨피규레이션 메타 데이터(configuration metadata)에 반영됩니다.

### 컨테이너 개요

org.springframework.context.ApplicationContext 인터페이스는 Spring IoC 컨테이너를 나타내며 앞서 언급 한 bean을 인스턴스화, 구성 및 어셈블하는 역할을 합니다. 컨테이너는 구성 메타 데이터(configuration metadata)를 읽음으로써 인스턴스화, 구성 및 어셈블 할 객체에 대한 지침을 가져옵니다. 구성 메타 데이터는 XML, Java 어노테이션 또는 Java 코드로 표시됩니다. 애플리케이션을 구성하는 개체와 이러한 객체 간의 풍부한 상호 종속성을 표현할 수 있습니다.

ApplicationContext 인터페이스의 여러 구현은 Spring과 함께 즉시 제공됩니다. 독립 실행형 애플리케이션에서는 [ClassPathXmlApplicationContext](https://docs.spring.io/spring-framework/docs/5.0.7.RELEASE/javadoc-api/org/springframework/context/support/ClassPathXmlApplicationContext.html) 또는 [FileSystemXmlApplicationContext](https://docs.spring.io/spring-framework/docs/5.0.7.RELEASE/javadoc-api/org/springframework/context/support/FileSystemXmlApplicationContext.html)의 인스턴스를 만드는 것이 일반적입니다. XML은 구성 메타 데이터를 정의하기위한 전통적인 형식 이었지만 컨테이너에 Java 주석이나 코드를 메타 데이터 형식으로 사용하도록 지시 할 수 있습니다. 이러한 XML 형식은 적은 양의 XML 구성을 제공함으로써 선언적으로 추가 메타 데이터 형식을 지원합니다.

대부분의 애플리케이션 시나리오에서 Spring IoC 컨테이너의 하나 이상의 인스턴스를 인스턴스화 하려면 명시적 사용자 코드가 필요하지 않습니다. 예를 들어, 웹 애플리케이션 시나리오에서 일반적으로 애플리케이션의 web.xml 파일에있는 표준 웹 설명자 XML의 간단한 8줄(또는 그정도)이면 충분합니다 ([웹 애플리케이션의 편리한 ApplicationContext 인스턴스화] 참조). [Spring Tool Suite](https://spring.io/tools/sts) Eclipse 구동 개발 환경을 사용하는 경우 마우스 클릭이나 키 입력을 거의 사용하지 않고 표준 구성을 쉽게 작성할 수 있습니다.

다음 다이어그램은 Spring의 작동 원리를 개괄적으로 보여줍니다. 애플리케이션 클래스는 구성 메타 데이터와 결합되므로 `ApplicationContext`를 만들고 초기화 한 후에 완전히 구성되고 실행 가능한 시스템 또는 애플리케이션을 가질 수 있습니다.

.The Spring IoC container
image::images/container-magic.png[]

### Bean overview

### Dependencies

### Customizing the nature of a bean

### Bean definition inheritance

### Container Extension Points

### Annotation-based container configuration

### Classpath scanning and managed components

### Using JSR 330 Standard Annotations

### Java-based container configuration

### Environment abstraction

### Registering a LoadTimeWeaver

### Additional capabilities of the ApplicationContext

### The BeanFactory

## Resources

## Validation, Data Binding, and Type Conversion

## Spring Expression Language (SpEL)

## Aspect Oriented Programming with Spring

## Spring AOP APIs

## Null-safety

## Data Buffers and Codecs

## Appendix
