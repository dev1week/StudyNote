# JVM



## JVM이란?

> Javv Virtual Machine의 약자로, Java로 작성된 프로그램이 실행될 수 있는 가상 머신을 의미합니다.&#x20;



<figure><img src="../../.gitbook/assets/image (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>





JVM의 주요 기능과 역할은 다음과 같습니다:

1. **바이트코드 실행(Bytecode Execution)**: Java 컴파일러가 작성한 Java 코드를 바이트코드(.class 파일)로 변환합니다. JVM은 이 바이트코드를 실행하여 프로그램을 실행합니다.
2. **플랫폼 독립성(Platform Independence)**: JVM은 특정 플랫폼에 종속되지 않고, 다양한 운영 체제와 하드웨어에서 Java 프로그램을 동일하게 실행할 수 있게 합니다. 이는 "한 번 작성하고, 어디서나 실행"할 수 있는 Java의 중요한 특징입니다.
3. **메모리 관리(Memory Management)**: JVM은 가비지 컬렉션(Garbage Collection) 메커니즘을 통해 자동으로 메모리를 관리합니다. 이는 개발자가 명시적으로 메모리를 해제할 필요가 없게 하여 메모리 누수와 같은 문제를 줄입니다.
4. **로딩, 링크 및 초기화(Loading, Linking, and Initialization)**: JVM은 Java 프로그램의 클래스 파일을 로드하고, 필요한 라이브러리와 링크하며, 프로그램 실행에 필요한 초기화를 수행합니다.
5. **보안(Security)**: JVM은 샌드박스 환경을 제공하여 Java 애플리케이션이 시스템의 다른 부분에 영향을 미치지 않도록 합니다. 이를 통해 악의적인 코드 실행을 방지하고 시스템의 보안을 강화합니다.
6. **스레드 관리(Thread Management)**: JVM은 멀티스레드 환경을 지원하여 Java 프로그램이 여러 스레드를 효율적으로 생성하고 관리할 수 있게 합니다.

JVM은 Java 런타임 환경(JRE, Java Runtime Environment)의 핵심 구성 요소이며, JRE는 JVM과 Java 표준 라이브러리를 포함하여 Java 애플리케이션을 실행하는 데 필요한 모든 것을 제공합니다. Java 개발 키트(JDK, Java Development Kit)는 JRE에 추가적으로 개발 도구를 포함한 패키지로, Java 애플리케이션을 개발하고 실행할 수 있게 합니다.
