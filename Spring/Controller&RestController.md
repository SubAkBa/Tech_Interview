## @RestController & @Controller
Spring에서 Controller를 지정해주기 위한 어노테이션이며, HTTP Response Body가 생성되는 방식에 차이가 있다.

<br />

#### @Controller (Spring MVC Controller)
주로 View를 반환하기 위해 사용하며, 아래와 같은 과정을 통해 Spring MVC Controller는 Client의 요청으로부터 View를 반환해준다.

<img src="../img/restcontroller&controller1.png" width="500">

> (1) Client는 URI 형식으로 웹 서비스에 요청을 보낸다.  
> (2) DispatcheServlet이 HandlerMapping을 통해 적절한 Controller를 매핑시킨다.  
> (3) Controller가 요청을 처리한 후에 응답을 DispatcherServlet으로 반환하고, DispatcherServlet은 View를 사용자에게 반환한다.

<br />

##### Data를 반환하는 경우
Spring MVC Controller가 데이터를 반환하는 경우, @ResponseBody 어노테이션을 활용하여 JSON형태로 데이터를 반환할 수 있다.

<img src="../img/restcontroller&controller2.png" width="500">

> (1) Client는 URI 형식으로 웹 서비스에 요청을 보낸다.  
> (2) DispatcheServlet이 HandlerMapping을 통해 적절한 Controller를 매핑시킨다.  
> (3) @ResponseBody를 사용하여 Client에게 Json 형태로 데이터를 반환한다.

<br />
<br />

#### @RestController (Spring RESTful Controller)
Spring MVC Controller에 @ResponseBody가 추가된 것으로, 주 목적은 JSON 형태로 데이터를 반환하는 것이다.

<img src="../img/restcontroller&controller3.png" width="500">

> (1) Client는 URI 형식으로 웹 서비스에 요청을 보낸다.  
> (2) DispatcheServlet이 HandlerMapping을 통해 적절한 Controller를 매핑시킨다.  
> (3) RestController는 해당 요청을 처리하고 데이터를 반환한다.
