# Web 개발 - Spring Boot 튜토리얼

[Spring Tutorial]

링크 : https://start.spring.io/ 

Gradle / Java 선택

Group / Artifact 작성

Add Dependencies => Spring Web / Thymeleaf 추가

Generate 클릭

ㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡ

Intellij 에 java SDK 버전을 위에 생성한 프로젝트와 맞춰서 실행

= > 아무것도 없이 Main Class 실행 시 Error page 렌더링

ㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡ

@ library (기본)

- 스프링 부트 라이브러리

   - spring-boot-starter-web
     - spring-boot-starter-tomcat : 톰캣 (웹서버)
     - spring-webmvc : 스프링 웹 MCV

   - spring-boot-starter-thymeleaf : 타임리프 템플릿 엔진 (View)

   - spring-boot-starter(공통) : 스프링 부트 + 스프링 코어 + 로깅
     - spring-boot
       - spring-core
     - spring-boot-starter-logging
       - logback, slf4j


- 테스트 라이브러리

   - spring-boot-starter-test
     - junit : 테스트 프레임워크
     - mockito : 목 라이브러리
     - assertj : 테스트 코드를 좀 더 편하게 작성하게 도와주는 라이브러리
     - spring-test : 스프링 통합 테스트 지원

ㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡ

src/main/resources/static/index.html
= > Main Class 실행 시 해당 index.html 렌더링


@ tymeleaf 사용 (템플릿 엔진)

- @GetMapping은 요청 url에 대한 GET 요청을 메소드와 mapping시키는 것

```
=> controller 
      - return 렌더링될 파일명
           => templates/hello.html (Thymeleaf 템플릿 엔진 처리)
      - model.addAttribute(키, 값)
           => templates/hello.html 에서 ${키} 이렇게 끌어와서 데이터 처리 가능

   * 컨트롤러에서 리턴 값으로 문자를 반환하면 ViewResolver 가 화면을 찾아 처리
```

```
=> spring-boot-devtools 라이브러리 추가시
     html 파일을 컴파일 해주면 서버 재시작 없이 View 파일 변경 가능
```


ㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡ

@ Build 하기 (터미널)


- ./gradlew.bat build
- cd build
- cd libs
- dir (linux 의 li 와 같음)
- java -jar hello-spring-0.0.1-SNAPSHOT.jar (build 한 파일 실행)
    - 서버 배포할 때 이 파일만 복사해 가지고 서버에 PUSH
    - java -jar 실행


- ./gradlew.bat clean (** build 폴더 없애기)
- ./gradlew.bat clean build (** build 폴더 없애고 다시 빌드)


ㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡ

@ 스프링 웹 개발 기초

```
- 정적 컨텐츠            : 서버에서 하는 거 없이 파일을 그대로 웹 브라우저에 그대로 보여주기

- MCV 와 템플릿 엔진 : JSP, PHP 템플릿 엔지니어 서버에서 HTML 을 프로그래밍 해서 
                              동적으로 보여주기 (템플릿 엔진)

                              컨트롤러, 모델, 템플릿 엔진(화면) 이 세가지를 
                              모델뷰 컨트롤러, MCV 라고 함

- API                      : VUE, REACT 등등이나 서버끼리 통신할 때 사용 
```              

ㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡ

@ 정적 컨텐츠

```              
  => static/hello-static.html (컨트롤러 없이 생성)
        => url : localhost:8080/hello-static.html 
             => hello-static 의 controller 를 먼저 찾지만
                  없는 경우 바로 hello-static.html 렌더링
```              



ㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡ

@ MCV 와 템플릿 엔진

- View 는 화면과 관련된 일만
- 비즈니스 로직과 서버 관련은 다 Controller 나 비즈니스 로직에서 처리
- Model 을 화면에서 필요한 것들을 다마 가지고 View 쪽에 넘겨주는 패턴

- param 을 추가하여 만든 Controller 와 Template 접속
    - localhost:8080/hello-mvc?name=spring!!!




ㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡ

@ API

  - @ ResponseBody
       - 응답 바디부에 이 내용을 직접 PUSH 의 의미
       - View 없이 html 없이 그대로 데이터 제공
       - 문자가 오면 그대로 반환
       - 객체가 오면 JSON 으로 반환



ㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡ


@ 회원 관리 예제 (백엔드)

- 비즈니스 요구사항 정리
- 회원 도메인과 리포지토리 만들기
- 회원 리포지토리 테스트 케이스 작성
- 회원 서비스 개발
- 회원 서비스 테스트




ㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡ


@ 비즈니스 요구사항 정리

- 데이터 
    - 회원 ID, 이름

- 기능 
    - 회원 등록, 조회

- 아직 DB 선정 X


- 일반적인 웹 애플리케이션 계층 구조
    - 컨트롤러 : 웹 MVC 컨트롤러 역할
    - 서비스 : 핵심 비즈니스 로직 구현
    - 리포지토리 : DB 에 접근, 도메인 객체를 DB 에 저장하고 관리
    - 도메인 : 비즈니스 도메인 객체 (예) 회원, 주문, 쿠폰 등 주로 DB 에 저장하고 관리


- interface 를 class 에 implements 시킬 때 alt + enter 하면  
  해당 메서드 선택해서 가져올 수 있음

- null 이 나올 가능성이 있으면 Optional.ofNullable( store.get(id) ) 사용
  ㄴ> 클라이언트 측에서 반환된 결과로 조절 가능


ㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡ


@ 테스트 코드

- 테스트의 순서는 랜덤

```
Assertions.assertEquals(값1, 값2)
  ㄴ> 같으면 초록불
  ㄴ> 다르면 빨간불 (Error)
```

```
AfterEach
테스트 끝날 때마다 한번씩 실행
```

- TEST 하려는 파일의 위에 포커스 주고
   CTRL + SHIFT + T 하면 테스트 코드 형식 그대로 생성 가능

- 이름 한글로 작성 가능

- given / when / then

- 예외 확인도 엄청 중요

- 이전 실행 다시 실행 shift + f10

- class 메서드, 필요 구조 기본 값 생성 alt + insert

```
BeforeEach
테스트 시작 전마다 한번씩 실행 
```

ㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡ

@ 서비스 코드

- 비즈니스 로직을 처리

함수 추출
ctrl + alt + shift + t


ㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡ


@ 컨트롤러 (서비스와 의존 관계)

멤버 서비스를 통해 회원가입
멤버 서비스를 통해 데이터를 조회


```
생성자에 Autowired 를 사용하면
컨트롤러가 생성이 될 때 스프링 빈에 등록되어 있는 
서비스를 객체에 가져다가 Push 해줌 (Dependency Injection : DI : 의존관계 주입)
ㄴ> 컨트롤러를 사용하려면 해당 서비스가 필요하니 주입해주고
      서비스를 사용하려면 해당 레포지토리가 필요하니 주입해주고

ㄴ> 생성자가 하나이면 자동으로 설정하지만 2개 이상이 되면 필수로 Autowired 설정해야함
ㄴ> Bean 직접 등록하면 작성안해도 됨
```

- 스프링 빈을 등록하는 2 가지 방법
   - @Component : 애노테이션이 있으면 스프링 빈으로 자동 등록
   - @Controller : 컨트롤러가 스프링 빈으로 자동 등록된 이유도 컴포넌트 스캔 때문

   - @Component 를 포함하는 다음 애노테이션도 스프링 빈으로 자동 등록
      - @Controller
      - @Service
      - @Repository


- 스프링은 스프링 컨테이너에 스프링 빈을 등록할 때 "기본으로 싱글톤으로 등록"
   - 헬로 컨트롤러는 헬로 컨트롤러 하나만
   - 멤버 서비스는 멤버 서비스 하나만
   - 멤버 리포지토리는 멤버 리포지토리 하나만
   - 공유 (와이어로 연결해서 똑같은 인스턴스 설정하여 사용)





 
