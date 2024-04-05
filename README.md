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

=> controller 
      - return 렌더링될 파일명
           => templates/hello.html (Thymeleaf 템플릿 엔진 처리)
      - model.addAttribute(키, 값)
           => templates/hello.html 에서 ${키} 이렇게 끌어와서 데이터 처리 가능

   * 컨트롤러에서 리턴 값으로 문자를 반환하면 ViewResolver 가 화면을 찾아 처리


=> spring-boot-devtools 라이브러리 추가시
     html 파일을 컴파일 해주면 서버 재시작 없이 View 파일 변경 가능



ㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡ

@ Build 하기 (터미널)

- ./gradlew.bat build
- cd build
- cd libs
- dir (linux 의 li 와 같음)
- java -jar hello-spring-0.0.1-SNAPSHOT.jar (build 한 파일 실행)
               ㄴ> 서버 배포할 때 이 파일만 복사해 가지고 서버에 PUSH
               ㄴ> java -jar 실행


- ./gradlew.bat clean (** build 폴더 없애기)
- ./gradlew.bat clean build (** build 폴더 없애고 다시 빌드)


ㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡ

@ 스프링 웹 개발 기초

- 정적 컨텐츠            : 서버에서 하는 거 없이 파일을 그대로 웹 브라우저에 그대로 보여주기

- MCV 와 템플릿 엔진 : JSP, PHP 템플릿 엔지니어 서버에서 HTML 을 프로그래밍 해서 
                              동적으로 보여주기 (템플릿 엔진)

                              컨트롤러, 모델, 템플릿 엔진(화면) 이 세가지를 
                              모델뷰 컨트롤러, MCV 라고 함

- API                      : VUE, REACT 등등이나 서버끼리 통신할 때 사용 
                 

ㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡ

@ 정적 컨텐츠

  => static/hello-static.html (컨트롤러 없이 생성)
        => url : localhost:8080/hello-static.html 
             => hello-static 의 controller 를 먼저 찾지만
                  없는 경우 바로 hello-static.html 렌더링



ㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡ

@ MCV 와 템플릿 엔진

- View 는 화면과 관련된 일만
- 비즈니스 로직과 서버 관련은 다 Controller 나 비즈니스 로직에서 처리
- Model 을 화면에서 필요한 것들을 다마 가지고 View 쪽에 넘겨주는 패턴

- param 을 추가하여 만든 Controller 와 Template 접속
          => localhost:8080/hello-mvc?name=spring!!!




ㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡ

@ API

  - @ ResponseBody
       - 응답 바디부에 이 내용을 직접 PUSH 의 의미
       - View 없이 html 없이 그대로 데이터 제공
       - 문자가 오면 그대로 반환
       - 객체가 오면 JSON 으로 반환
 
