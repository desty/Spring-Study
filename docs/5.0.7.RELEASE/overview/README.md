# Spring Framework Overview
Spring을 사용하면 Java 엔터프라이즈 애플리케이션을 쉽게 만들 수 있습니다. Groovy 및 Kotlin을 JVM에서 대체 언어로 지원하고 응용 프로그램의 필요에 따라 다양한 종류의 아키텍처를 생성할 수 있는 유연성을 통해 엔터프라이즈 환경에서 Java 언어를 수용하는 데 필요한 모든 것을 제공합니다. Spring Framework 5.0부터 Spring은 JDK 8+ (Java SE 8+)를 필요로하며 JDK 9에 대한 즉시 지원을 제공합니다.

Spring은 다양한 애플리케이션 시나리오를 지원합니다. 대규모 엔터프라이즈에서 애플리케이션은 오랫동안 존재하는 경우가 많으며 개발자의 제어 범위를 벗어나는 업그레이드주기를 가진 JDK 및 애플리케이션 서버에서 실행해야합니다. 다른 것은 클라우드 환경에 서버가 내장 된 단일 jar으로 실행될 수 있습니다. 또 다른 것들은 서버가 필요없는 독립 실행형 응용 프로그램 (배치 또는 통합 작업 부하와 같은) 일 수 있습니다.

Spring은 오픈 소스입니다. 다양한 범위의 실제 사용 사례를 기반으로 지속적인 피드백을 제공하는 크고 활동적인 커뮤니티가 있습니다. 이것은 Spring을 오랜 기간 성공적으로 진화하는 것을 도왔습니다.

## "Spring"이 뭐죠 ?
"Spring"이라는 용어는 다른 맥락에서 다른 것을 의미합니다. Spring Framework 프로젝트 자체를 지칭하는 데 사용할 수 있습니다. 시간이 지남에 따라 다른 Spring 프로젝트도 Spring Framework 위에 구축되었습니다. 사람들이 "Spring"이라고 말할 때, 대부분 프로젝트의 전체 제품군을 의미합니다. 이 레퍼런스 문서는 스프링 프레임 워크 자체에 대한 토대에 중점을 둡니다.

스프링 프레임워크는 여러 개의 모듈로 나뉩니다. 애플리케이션은 필요한 모듈을 선택할 수 있습니다. 코어 컨테이너의 핵심 모듈중 구성 모델과 종속성 주입 메커니즘이 포함되어있습니다. 그 외에도 Spring Framework는 메시징, 트랜잭션 데이터 및 지속성, 웹 등 다양한 애플리케이션 아키텍처에 대한 기본 지원을 제공합니다. 또한 Servlet 기반 Spring MVC 웹 프레임워크와 Spring WebFlux 대응 웹 프레임워크가 포함되어있습니다.

모듈에 대한 참고 사항 : Spring의 프레임워크 jar들은 JDK9의 모듈 경로 ("직소-Jigsaw")에 배포할 수 있습니다. Jigsaw 지원 애플리케이션에 사용하기 위해 Spring Framework 5 jar에는 jar artifact 이름 (jar는 "."대신 "-"로 동일한 명명 패턴을 따릅니다. 예 : "spring-core" 및 "spring-context")와는 별도로 안정된 언어 수준(stable language-level) 모듈 이름 ("spring.core", "spring.context" 등)을 정의하는 "자동 모듈 이름 (Automatic-Module-Name)"을 제공 합니다. 물론 Spring의 프레임워크 jar는 JDK 8과 9의 classpath에서 잘 작동합니다.

## Spring과 Spring Framework의 역사

Spring은 초기 [J2EE](https://en.wikipedia.org/wiki/Java_Platform,_Enterprise_Edition) 스펙의 복잡성에 대한 응답으로 2003 년에 들어 왔습니다. 일부는 Java EE와 Spring을 경쟁 대상으로 간주하지만 실제로 Spring은 Java EE를 보완합니다. Spring 프로그래밍 모델은 Java EE 플랫폼 사양을 포함하지 않습니다. 오히려 EE 우산(umbrella)에서 엄선 된 개별 사양과 통합됩니다.

* Servlet API ([JSR 340](https://jcp.org/en/jsr/detail?id=340))
* WebSocket API ([JSR 356](https://www.jcp.org/en/jsr/detail?id=356))
* Concurrency Utilities ([JSR 236](https://www.jcp.org/en/jsr/detail?id=236))
* JSON Binding API ([JSR 367](https://jcp.org/en/jsr/detail?id=367))
* Bean Validation ([JSR 303](https://jcp.org/en/jsr/detail?id=303))
* JPA ([JSR 338](https://jcp.org/en/jsr/detail?id=338))
* JMS ([JSR 914](https://jcp.org/en/jsr/detail?id=914))
* 필요한 경우 트랜잭션 조정을 위한 JTA / JCA 설정을 제공합니다.

또한 Spring Framework는 Spring Framework에서 제공하는 Spring 특정 메커니즘 대신 애플리케이션 개발자가 사용할 수 있는 Dependency Injection ([JSR 330](https://www.jcp.org/en/jsr/detail?id=330)) 및 Common Annotations ([JSR 250](https://jcp.org/en/jsr/detail?id=250)) 사양을 지원합니다.

Spring Framework 5.0 부터 Spring은 최소한 Java EE 7 레벨 (예 : Servlet 3.1+, JPA 2.1+)을 필요로하는 동시에 Java EE 8 레벨의 최신 API와의 즉각적인 통합을 제공합니다 (예 : Servlet 4.0, JSON Binding API) 런타임시 발생합니다. 이로써 Spring은 예를 들어 Tomcat 8 및 9, WebSphere 9 및 JBoss EAP 7과 완벽하게 호환됩니다.

시간이 지남에 따라 애플리케이션 개발에 Java EE의 역할이 진화했습니다. Java EE 및 Spring 초기에는 애플리케이션 서버에 배포 할 애플리케이션을 만들었습니다. 오늘날, Spring Boot의 도움으로 애플리케이션이 devops 및 cloud 친화적인 방법으로 생성되며 Servlet 컨테이너가 임베드되어 사소하게 변경됩니다. Spring Framework 5에서 WebFlux 애플리케이션은 서블릿 API를 직접 사용하지 않으며 서블릿 컨테이너가 아닌 서버 (예 : Netty)에서 실행할 수 있습니다.

Spring은 혁신과 진화를 계속하고 있습니다. Spring Framework 외에도 Spring Boot, Spring Security, Spring Data, Spring Cloud, Spring Batch 등과 같은 다른 프로젝트가 있습니다. 각 프로젝트마다 자체 소스 코드 저장소, 이슈 트래커 및 릴리스 종지(candence)가 있음을 기억해야합니다. Spring 프로젝트의 전체 목록은 [spring.io/projects](https://spring.io/projects)를 참조하십시오.

## 디자인 철학

framework에 대해 배울 때, framework가하는 일뿐만 아니라 그 원리에 대해서도 아는 것이 중요합니다. Spring Framework의 기본 원칙은 다음과 같습니다.

* 모든 단계에서 선택권을 제공. Spring을 사용하면 가능한 한 늦게 설계 결정을 연기 할 수 있습니다. 예를 들어, 코드를 변경하지 않고 구성(configuration)을 통해 지속성 공급자를 전환 할 수 있습니다. 다른 많은 인프라 문제와 써드 파티 API와의 통합에서도 마찬가지입니다.

* 다양한 관점을 수용. Spring은 융통성을 포용하고 어떻게 해야하는지에 대해 강조하지 않습니다. 다양한 관점에서 다양한 애플리케이션 요구를 지원합니다.

* 강력한 이전 버전과의 호환성 유지. Spring의 진화는 신중하게 관리되어 버전간에 몇 가지 주요 변경 사항을 적용합니다. Spring은 JDK 버전과 타사 라이브러리를 신중하게 선택한 범위에서 지원하므로 Spring을 사용하는 애플리케이션 및 라이브러리의 유지 관리가 수월합니다.

* API 디자인에 대한 케어. Spring 팀은 직관적이며 많은 버전과 여러 해 동안 유지할 수있는 API를 만드는 데 많은 시간과 노력을 기울이고 있습니다.

* 코드 품질에 대한 높은 기준을 설정. Spring Framework는 의미 있고, 최신의 정확한 Javadoc에 중점을 둔다. 패키지간에 순환 의존성이 없는 깨끗한 코드 구조를 요구할 수 있는 프로젝트는 거의 없습니다.

## 피드백 및 참여

## 시작하기
