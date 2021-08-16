# 실습을 위한 개발 환경 세팅
* https://github.com/slipp/web-application-server 프로젝트를 자신의 계정으로 Fork한다. Github 우측 상단의 Fork 버튼을 클릭하면 자신의 계정으로 Fork된다.
* Fork한 프로젝트를 eclipse 또는 터미널에서 clone 한다.
* Fork한 프로젝트를 eclipse로 import한 후에 Maven 빌드 도구를 활용해 eclipse 프로젝트로 변환한다.(mvn eclipse:clean eclipse:eclipse)
* 빌드가 성공하면 반드시 refresh(fn + f5)를 실행해야 한다.

# 웹 서버 시작 및 테스트
* webserver.WebServer 는 사용자의 요청을 받아 RequestHandler에 작업을 위임하는 클래스이다.
* 사용자 요청에 대한 모든 처리는 RequestHandler 클래스의 run() 메서드가 담당한다.
* WebServer를 실행한 후 브라우저에서 http://localhost:8080으로 접속해 "Hello World" 메시지가 출력되는지 확인한다.

# 각 요구사항별 학습 내용 정리
* 구현 단계에서는 각 요구사항을 구현하는데 집중한다. 
* 구현을 완료한 후 구현 과정에서 새롭게 알게된 내용, 궁금한 내용을 기록한다.
* 각 요구사항을 구현하는 것이 중요한 것이 아니라 구현 과정을 통해 학습한 내용을 인식하는 것이 배움에 중요하다. 

### 요구사항 1 - http://localhost:8080/index.html로 접속시 응답
* Socket을 통해 Server, Client를 연결해주는 connection을 생성한다.
* InputStream을 통해 클라이언트가 전송하는 데이터를 서버에서 읽을 수 있다.
* OutputStream을 통해 서버가 클라이언트한테 전송해야 하는 데이터를 전송할 수 있다.
* InputStream은 BufferedReader(new InputStreamReader)을 통해 라인별로 읽을 수 있다.

### 요구사항 2 - get 방식으로 회원가입
* GET 요청 URL에 접근경로와 데이터가 포함되어 있다.
* ? 이전에는 접근 경로가 있다.
* ? 이후에는 "이름=값" 데이터가 있다.
* 데이터는 "이름=값&이름=값" 형태로 '&' 문자로 데이터가 이어져 있다.

### 요구사항 3 - post 방식으로 회원가입
* POST 요청은 GET과 다르게 URL에 데이터가 포함되어 있지 않다.
* 데이터는 HTTP 본문에 담겨져 있다.
* HTTP 본문은 HTTP 헤더 이후 빈 공백을 가지는 한 줄(line) 다음부터 시작한다.
* HTTP 본문에 전달되는 데이터 형식은 GET과 동일하다.
* 본문의 길이는 "Content-Length" 값으로 확인할 수 있다.

```java
char[] body = new char[contentLength];
BufferedReader.read(body, 0, contentLength);
```

### 요구사항 4 - redirect 방식으로 이동
* 하이퍼텍스트 전송 프로토콜(HTTP)의 302 Found 리다이렉트 상태 응답 코드는 클라이언트가 요청한 리소스가 Location 헤더에 주어진 URL에 일시적으로 이동되었음을 가리킨다.

### 요구사항 5 - cookie
* 응답 헤더에 Set-Cookie를 추가해주면 재요청시에도 쿠기 값이 계속 포함되어 있다.

### 요구사항 6 - stylesheet 적용
* 

### heroku 서버에 배포 후
* 