# 캐시(Cache)와 세션(Session)의 공통점과 차이점
+ 공통점
    : 둘 다 사용자의 데이터를 저장한다.
+ 차이점
    + 캐시
        : 캐시는 Client 컴퓨터에 저장했다 서버 요청시 네트워크를 타고 서버로 전달되기 때문에 보안에 취약하다.
    + 세션
        : 세션은 사용자 정보가 서버에 저장되고 브라우저 단위로 관리된다. 캐시에 비해 보안성이 좋다.

# Session과 Cookie
+ Session과 Cookie 사용 이유
    + 현재 우리가 인터넷에서 사용하고 있는 HTTP프로토콜은 연결 지향적인 성격을 버렸기 때문에 새로운 페이지를 요청할 때마다 새로운 접속이 이루어지며 **이전 페이지와 현재 페이지 간의 관계가 지속되지 않는다.** <br>
    이에 따라 HTTP프로토코을 이용하게 되는 웹사이트에서는 웹페이지에 특정 방문자가 머르고 있는 동안에 그 방문자의 상태를 지속시키기 위해 쿠키와 세션을 이용한다.
+ **Session** <br>
    + 특정 웹사이트에서 상용자가 머무르는 기간 또는 한 명의 사용자의 한번의 방문을 의미한다.
    + Session에 관련된 데이터는 **Server에 저장**된다.
    + 웹 브라우저의 캐시에 저장되어 브라우저가 닫히거나 서버에서 삭제시 사라진다.
    + Cookie에 비해 보안성이 좋다.
+ **Cookie** <br>
    + 사용자 정보를 유지할 수 없다는 HTTP의 한계를 극복할 수 있는 방법
    + 인터넷 웹 사이트의 방문 기록을 남겨 사용자와 웹 사이트 사이를 매개해 주는 정보
    + Cookie는 인터넷 사용자가 특정 웹서버에 접속할 때, 생성되는 개인 아이디와 비밀번호, 방문한 사이트의 정보를 담은 임시 파일로써,
    Server가 아닌 **Client에 텍스트 파일로 저장**되어 다음에 해당 웨서버를 찾을 경우 웹서버에서는 그가 누구인지 어떤 정보를 주로 찾았는지 등을 파악할 때 사용된다.
    + Cookie는 **Client PC에 저장**되는 정보이기 때문에, **다른 사용자에 의해서 임의로 변경이 가능**하다. (정보 유출 가능, Session보다 보안성이 낮은 이유)

    **Q. 보안성이 낮은 Cooke 대신 Session을 사용하면 되는데 안하는 이유?** <br>
    A. 모든 정보를 Session에 저장하며 Server의 메모리를 과도하게 사용하게 되어 Server에 무리가 감
# Request 전송 방식에는 어떤 것들이 있나?
+ Get 방식
    : URL의 쿼리문자열에 데이터를 같이 전달하는 방식으로 데이터 길이에 제한이 있고, 보안에 취약하다.
+ POST 방식
    : 헤더에 데이터를 넣어 보내기 때문에 보안에 좀더 유리하고 데이터 길이에 제한이 없다. 하지만, Get에 비해 다소 느리다.
+ DELETE 방식
    : RESTFULT 에서 삭제 기능을 할 때 주로 사용된다
+ PUT/PUSH 방식
    : RESTFUL에서 수정 작업을 할 때 주로 사용된다.

# RESTFUL 이란
: 해당 URL만 보더라도 바로 어떤 작업을 하는지를 알 수 있도록 하나의 데이터는 하나의 URL을 갖도록 하는 작업 방식

# 디자인 패턴
+ 싱클톤(SingleTone Pattern)
    : 대표적으로 Calendar 객체나 dataSource 객체처럼 객체가 하나만 생성되어야 하는 경우
    전체 코드에서 하나의 객체만 존재할 수 있도록 이미 생성된 객체가 있으면 그 객체를 사용하도록 하는 방식.
    그 객체(인스턴스)에 대한 전역 접근을 제공한다.
+ 팩토리 패턴(Factory Pattern)
    : 객체간 의존성을 줄이기 위해 객체의 생성과 데이터 주입만 담당하는 Factory Class를 저으이하고 개발 코드 부분에서는
    생성된 객체를 가져다 사용함으로써 의존성을 줄이는 방식입니다.
+ 옵저버 패턴(Observer Pattern)
    : 기후 정보처럼 RSS 수신 시 하나의 객체가 변하면 다른 객체에 객체가 변했다는 사항을 알려주어야 할 겨우에 주로 사용됩니다.

# MVC 패턴이란?
+ Model : data 처리와 접근을 담당
+ View : Client에 보여지는 화면을 담당
+ Controller : Model과 View를 제어
하는 3가지 부분으로 나눔으로써, 데이터와 화면간의 의존관계를 벗어날 수 있게 하는 개발 기법

# Servlet vs JSP
+ Servlet : 자바 어넝로 웹 개발을 위해 만들어진 것으로, Container가 이해할 수 있게 구성된 순수 자바코드로만 이루어진 것
+ JSP : html 기반에 JAVA 코드를 블록화하여 삽입한 것으로 Servlet을 좀 더 쉽게 접근할 수 있또록 만들어 진 것

# JDBC
Java Data Base Connection의 약자로 JAVA 언어를 통해 데이터 베이스에 접근 할 수 잇는 프로그래밍을 의미

# 소켓 통신(TCP/UDP)
+ **TCP(Transmisson Control Protocol)** <br>
    + 연결형 서비스 제공
    + 높은 신뢰성 보장
    + 연결의 설정(3-way handshaking)
    + 연결의 해제(4-way handshaking)
    + 데이터 흐름 제어, 혼잡 제어
    + 전이중, 점대점 서비스(양방향 송수신 서비스)
+ **UTP(User Datagram Protocol)** <br>
    + 비연결형 서비스 제공
    + 신뢰성이 낮음
    + 데이터의 전소 순서가 바뀔 수 있음
    + 데이터 수신 여부 확인 암함(3-way hadshaking과 같은 과정x)
    + TCP보다 전송속도가 빠름

# jQuery란?
![image](https://user-images.githubusercontent.com/41488792/47792999-98812700-dd60-11e8-94c2-34ce91fa44ac.png)
출처:http://mkil.tistory.com/166

# Ajax란?
![image](https://user-images.githubusercontent.com/41488792/47793408-88b61280-dd61-11e8-8f14-17cfca1ddbe0.png)
![image](https://user-images.githubusercontent.com/41488792/47793445-a08d9680-dd61-11e8-8dd4-faf7878733d9.png)
![image](https://user-images.githubusercontent.com/41488792/47793481-af744900-dd61-11e8-831c-c85129054dcf.png)
![image](https://user-images.githubusercontent.com/41488792/47793870-9ae48080-dd62-11e8-836d-56b067e8fe0c.png)
![image](https://user-images.githubusercontent.com/41488792/47793904-a9cb3300-dd62-11e8-9206-4cf33378c6ab.png)

출처 : https://coding-factory.tistory.com/143

# JSP를 공부한 이유
+ 자바 언어를 기반으로 하고 있기 때문에 플랫폼에 사관없이 사용할 수 있습니다.
(OS에 독립적)
+ 자바 언어에 대한 깊은 이해가 없더라도 빠르게 배울 수 있습니다.
+ 대규모 어플리케이션을 구현할 때 사용되는 스프링과 같은 프레임워크와 완벽하게 연동되며, 금융권에서 많이 사용되는 다른 엔터프라이즈 기술과도 완벽하게 연동됩니다.

# JSON
JavaScript Object Notation 자바스크립트 객체 표기법

JSON은 **"네트워크를 통해 데이터를 주고받는 데 자주 사용되는 경량의 데이터 형식"** <br>

# 어노테이션(Annotation) 이란?
이 어노테이션으로 인해 데이터의 유효성 검사 등을 쉽게 알 수 있고, 이와 관련한 코드가 깔끔해지게 됩니다.
일단 어노테이션의 용도는 다양한 목적이 있지만 **메타 데이터의 비중**이 가장 크다 할 수 있습니다.

<h3>메타-테이터(Meta-Data)</h3> : 데이터를 위한 데이터를 의미하며, 풀어 이야기하면 한 데이터에 대한 설명을 의미하는 데이터. (자신의 정보를 담고 있는 데이터)

![image](https://user-images.githubusercontent.com/41488792/47957663-b8814680-dffd-11e8-9d60-1a5342baaa10.png)
![image](https://user-images.githubusercontent.com/41488792/47957670-d9e23280-dffd-11e8-9f68-9ff7cc5004fe.png)
![image](https://user-images.githubusercontent.com/41488792/47957676-f1b9b680-dffd-11e8-953f-80b2dceacde9.png)

출처: https://elfinlas.github.io/2017/12/14/java-annotation/