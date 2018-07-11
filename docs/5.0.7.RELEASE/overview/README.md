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
* 필요한 경우 트랜잭션 조정을위한 JTA / JCA 설정을 제공합니다.

## 디자인 철학

## 피드백 및 참여

## 시작하기
