﻿**RESTful API**에서 오는 각각의 요청은 무상태(Stateless) 메시지다.
- 리소스 요청
- 리소스 업데이트
- 리소스 생성
- 리소스 삭제
보통 정보 요청(request) 및 응답(response)를 JSON 형식으로 한다.

스피링에서는 웹 애플리케이션의 요청을 **컨트롤러**가 처리한다. 컨트롤러는 클라이언트의 요청을 처리하고 응답을 보내는 역할을 하는 특수 컴포넌트이다.

컨트롤러는 다양한 **통신 프로토콜**이 있지만 그중 **REST Controller**는 RESTful API와 같이 요청을 처리하고 본문(body)에 Json을 담아서 응답한다.
