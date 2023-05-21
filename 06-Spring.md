## 스프링 기술면접 준비

<details>
    <summary>Spring에서 DI나 IOC 개념을 설명해주세요.</summary>
    </br>
    <p>IoC(제어의 역전)은 개발자가 프로그램의 제어 흐름을 직접 제어하는 것이 아니라 외부에서 관리하는것을 말합니다.</p>
    <p>DI(의존성 주입 or 의존관계 주입)은 객체를 직접 생성하는게 아니라 외부에서 생성한 후 주입하는 방식이다.</p>
</details>

<details>
    <summary>DI 종류는 어떤것이 있고, 이들의 차이는 무엇인가요?</summary>
    </br>
    <p>DI는 세가지 방법이 있습니다. 생성자 주입, Setter 주입, 필드 주입이 있습니다 .</p>
    <p>생성자 주입은 생성자 호출시점에 딱 1번만 호출되는 것을 보장하며 불변, 필수 의존관계에 사용합니다. (private final 클래스명)</p>
    <p>Setter주입은 선택, 변경 가능성이 있는 의존관계에 사용되며 스프링빈을 선택적으로 등록이 가능합니다.</p>
    <p>필드 주입은 `@Autowired` 를 사용하는데 외부에서 변경이 불가능하여 테스트 하기 힘듭니다. </p>
</details>

<details>
   <summary>스프링 프레임워크와 스프링 부트의 차이점</summary>
   </br>
   <p>톰캣과 같은 웹서버를 내장에서 별도의 웹서버를 설치하지 않아도 됨</p>
   <p>손쉬운 빌드 구성을 위한 starter 종속성 제공</p>
   <p>스프링부트가 스프링과 외부 라이브러리가 자동 구성함으로써 즉 버전에 맞게 최적화 해줍니다.</p>
   <p>기존 스프링프레임워크는 war로 말아서 톰캣을 구동했다면, 스프링부트느 jar로 배포하여 자바 옵션만으로 쉽게 배포 가능합니다.</p>
</details>

<details>
   <summary>Interceptor와 Filter 차이는 무엇일까요?</summary>
   </br>
   <p>Filter는 WAS단에 설정되어 Spring과 무관한 자원에 대해 동작하고, Interceptor는 Spring Context 내부에 설정되어 컨트롤러 접근 전, 후에 가로채서 기능 동작 합니다.</p>
   <p>Filter는 Web Application(Tomcat을 사용할 경우 web.xml)에 등록하며, Interceptor는 Spring의 Application Context에 등록합니다.</p>
   <p>Filter는 doFilter() 메소드만 있지만, Interceptor는 pre와 post로 명확하게 분리</p>
</details>

<details>
   <summary>Filter는 Servlet의 스펙이고, Interceptor는 Spring MVC의 스펙입니다. Spring Application에서 Filter와 Interceptor를 통해 예외를 처리할 경우 어떻게 해야 할까요?</summary>
   </br>
   <p>Filter는 DispatcherServlet 외부에 존재하기 때문에 예외가 발생했을 때 ErrorController에서 처리해야 합니다.</p>
   <p>하지만 Interceptor는 DispatcherServlet 내부에 존재하기 때문에 @ControllerAdvice를 적용해서 처리할 수 있습니다.</p>
</details>

<details>
   <summary>Spring Bean이란 무엇인가요?</summary>
   </br>
   <p>스프링 컨테이너에 등록된 객체를 말하며, @Bean 을 사용하거나 xml설정을 통해 일반 객체를 Bean으로 등록할 수 있습니다.</p>
</details>

<details>
   <summary>Spring Bean의 라이프 사이클은?</summary>
   </br>
   <p>스프링은 빈 을 관리하는 컨테이너이다. 따라서 빈 객체를 생성하고, 초기화및 소멸 등 일련의 과정들을 담당하게 된다.</p>
   <p>객체 생성 → 의존 설정 → 초기화 → 사용 → 소멸 과정의 생명주기를 가지고 있습니다. </p>
</details>

<details>
   <summary>@ControllerAdvice가 무엇인가요?</summary>
   </br>
   <p>@Controller나 @RestController에서 발생한 예외를 한 곳에서 관리하고 처리할 수 있게 도와주는 어노테이션이다.</p>
</details>

<details>
   <summary>Controller, RestController는 뭐가 다른가요? 응답이 어떻게 다른가요?</summary>
   </br>
   <p>컨트롤러는 Client가 URI 요청을 보내면 DispatcherServlet과 Handler Mapping이 요청을 Intercept</p>
   <p>Controller에 의해 요청을 처리 하고 DispatcherServlet이 Model과 View를 적절히 Client에 리턴</p>
   <p>기존 컨트롤러에서 @ResponseBody가 추가되었기 때문에 따로 Response를 해 줄 필요가 없습니다.</p>
</details>

<details>
   <summary>Spring에서 @Service, @Controller, @Repository annotation의 차이점</summary>
   </br>
   <p>@Component : Spring에서 관리되는 객체임을 표시하기 위해 사용하는 가장 기본적인 annotation이다. 즉, scan-auto-detection과 dependency injection을 사용하기 위해서 사용되는 가장 기본 어노테이션이다.</p>
   <p>@Service : 비지니스 로직의 stereotype</p>
   <p>@Controller : spring-mvc의 사용되는 stereotype</p>
   <p>@Repository : persistence layer(영속성을 가지는 [파일, db등]) stereotype</p>
</details>

<details>
   <summary>IoC Container 직접 만든다면 어떻게 구현하실 생각인가요?</summary>
   </br>
   <p>AppConfig 처럼 객체를 생성하고, 관리하면서 의존관계를 연결합니다.</p>
   <p>POJO의 생성, 초기화, 서비스, 소멸에 대한 권한을 가집니다.</p>
</details>

<details>
   <summary>Spring MVC 에서 요청이 들어왔을 때부터 응답이 나갈 때까지의 흐름을 설명해주세요.</summary>
   </br>
   <p>1.DispatcherServlet이 브라우저로부터 요청을 받는다.</p>
   <p>2.DispatcherServlet은 요청된 URL을 HandlerMapping 객체에 넘기고, 호출해야 할 Controller 메소드(핸들러) 정보를 얻는다.</p>
   <p>3.DispatcherServlet이 HandlerAdapter 객체를 가져온다.</p>
   <p>4.HandlerAdapter 객체의 메소드를 실행한다.</p>
   <p>5.Controller 객체는 비즈니스 로직을 처리하고, 그 결과를 바탕으로 뷰(ex. JSP)에 전달할 객체를 Model 객체에 저장한다. DispatcherServlet에게 view name을 리턴한다.</p>
   <p>6.DispatcherServlet은 view name을 View Resolver에게 전달하여 View 객체를 얻는다.</p>
   <p>7.DispatcherServlet은 View 객체에 화면 표시를 의뢰한다.</p>
   <p>8.View 객체는 해당하는 뷰(ex. JSP, Thymeleaf)를 호출하며, 뷰는 Model 객체에서 화면 표시에 필요한 객체를 가져와 화면 표시를 처리한다.</p>
</details>

<details>
   <summary>AOP에 대해 설명해주세요</summary>
   </br>
   <p>애플리케이션 전체에 걸쳐 사용되는 기능을 재사용하도록 지원하는 것이다.</p>
   <p>관점(관심) 지향 프로그래밍으로 바라보아 클래스별로 공통적인 기능을 모듈화하여 제공하는 것입니다.</p>
</details>

<details>
   <summary>프레임워크와 라이브러리의 차이점</summary>
   </br>
   <p>프레임워크는 내가 작성한 코드를 제어하고 대신 실행하면 프레임워크다. (예를들면 junit)</p>
   <p>라이브러리는 내가 작성한 코드가 직접 제어의 흐름을 담당하는 것이다.</p>
</details>

<details>
   <summary>스프링 Bean의 Scope에 대해서 설명해주세요.</summary>
   </br>
   <p>빈 스코프는 빈이 존재할 수 있는 범위를 뜻하며 싱글톤, 프로토타입, request, session, application 등이 있습니다.</p>
   <p>싱글톤은 기본 스코프로 스프링 컨테이너의 시작과 종료까지 유지되는 가장 넓은 범위의 스코프입니다.</p>
   <p>프로토타입은 빈의 생성과 의존관계 주입까지만 관여하고 더는 관리하지 않는 매우 짧은 범위의 스코프입니다.</p>
   <p>request는 웹 요청이 들어오고 나갈때까지 유지하는 스코프, session은 웹 세션이 생성, 종료할때까지, application은 웹 서블릿 컨텍스트와 같은 범위로 유지하는 스코프입니다.</p>
</details>

<details>
   <summary>Spring 서비스 추상화란?</summary>
   </br>
   <p>추상화란 하위 시스템의 공통점을 뽑아내서 분리시키는 것을 말합니다. 그렇게 하면 하위 시스템이 어떤 것인지 알지 못해도, 또는 하위 시스템이 바뀌더라도 일관된 방법으로 접근할 수가 있습니다.</p>
   <p>추상화를 하려면, IoC/DI를 이용해 서비스 추상화를 용이하게 할 수 있습니다. applicationContext.xml을 통해 서비스 추상화를 구현합니다.</p>
   <p>이때 중요한 것은 높은 응집도와 낮은 결합도를 준수하는 것입니다.</p>
</details>

<details>
   <summary>스프링은 트랜잭션이 어떻게 발생하나요?</summary>
   </br>
   <p>트랜잭션은 AOP Proxy를 통해 처리됩니다.</p>
   <p>트랜잭션은 여러 CRUD 작업을 하나의 동작으로 하기 위함이고, 비즈니스 로직을 처리하는 Service단에서 트랜잭션을 수행하는 것이 권장됩니다.</p>
</details>

<details>
   <summary>POJO란 무엇인가요? Spring Framework에서 POJO는 무엇이 될 수 있을까요?</summary>
   </br>
   <p>스프링에서 POJO를 'java Beans'라고 부름</p>
   <p>Beans는 Spring IoC 컨테이너에 의해 인스턴스화, 관리, 생성됨</p>
</details>

<details>
   <summary>Put과 Post 구현시 차이점?</summary>
   </br>
   <p>POST는 request message로 포함된 엔티티를 이용해 새로운 자원을 생성해 내는것이고,</p>
   <p>PUT은 request message와 함께 넘어온 식별자의 자원을 만드는 것입니다.</p>
   <p>예를들어 POST 게시판에 글쓰기 요청을 2번날리면 2개의 게시물이 등록되지만 PUT은 식별자와 함께 요청해야 합니다.</p>
</details>

<details>
   <summary>Spring에서 CORS 에러를 해결하기 위한 방법을 설명해주세요.</summary>
   </br>
   <p>Server side에서 CORS 요청이 허용되도록 허용합니다.</p>
   <p>예를들면 controller파일에서 @CrossOrigin을 통해 모든 주소에 대해 접근을 헝용하며, 허용시간 3600초를 적용 시킵니다.</p>
   <p>사용자가 직접 웹 브라우저 실행 옵션을 변경하거나 플러그인 설치하는 방법도 있지만 책임을 전가하는건 좋지 않습니다.</p>
</details>

<details>
   <summary>Bean/Component 애노테이션에 대해서 설명해주시고, 둘의 차이점에 대해 설명해주세요.</summary>
   </br>
   <p>@Bean의 경우 개발자가 컨트롤이 불가능한 외부 라이브러리들을 Bean으로 등록하고 싶은 경우에 사용된다. (@Target이 METHOD로 지정되어 있지만, TYPE은 없다)</p>
   <p>@Component는 직접 컨트롤이 가능한 Class들의 경우 사용합니다. (@Target이 TYPE로 지정되어 Class위에서만 선언될수 있음을 알수 있다.)</p>
   <p>@Bean과 @Component는 각자 선언할 수 있는 타입이 정해져있어 해당 용도외에는 컴파일 에러를 발생시킨다.</p>
</details>

<details>
   <summary>Spring Web MVC에서 요청 마다 Thread가 생성되어 Controller를 통해 요청을 수행할텐데, 어떻게 1개의 Controller만 생성될 수 있을까요?</summary>
   </br>
   <p>싱글톤 Scope</p>
</details>

<details>
   <summary>Spring Application을 구동할 때 메서드를 실행시키는 방법에 대해 설명해주세요.</summary>
   </br>
   <p>CommandLineRunner, ApplicationRunner를 구현한 클래스를 만들어서 실행시키는 2가지 방법이 있습니다.</p>
   <p>또한 Spring의 ApplicationEvent를 사용한 방법, @Postconstruct를 사용한 방법, InitializingBean 인터페이스를 구현하는 방법, @Bean의 initMethod를 사용한 방법이 있습니다.</p> 
</details>

<details>
   <summary>의존성과 설정값을 생성자 인자로 주입해야 하는 이유에 대해 설명해주세요.</summary>
   </br>
   <p>모든 의존성을 생성자를 통해 주입하면, 인스턴스 생성 시 즉시 어떠한 동작을 실행할 수 있습니다. </p>
   <p>생성자의 경우 클래스 로더에의해 단 한번만 수행되는 것을 보장하여 final로 선언할 경우 명확한 싱글톤 객체임을 보장할 수 있습니다.</p>
</details>

<details>
   <summary>SOLID 원칙에 대해 설명해주세요.</summary>
   </br>
   <p>SRP (단일 책임 원칙) : '한 클래스는 하나의 책임만 가져야 한다.' 중요한 기준은 변경이며, 파급 효과가 적으면 단일 책임 원칙을 잘 따른것</p>
   <p>OCP (개방 폐쇄 원칙) : 소프트웨어 요소는 확장에는 열려 있으나 변경에는 닫혀 있어야 한다. 이를 해결하기 위해 다형성을 활용해야 합니다.</p>
   <p>(예를 들어 자동차 모델들이 여러개 있어도 변경이 된다한들 운전자는 아무 영향이 없다.)</p>
   <p>LSP (리스코프 치환 원칙) : 프로그램의 객체는 프로그램의 정확성을 깨뜨리지 않으면서 하위 타입의 인스턴스로 바꿀 수 있어야한다.</p>
   <p>(자동차 엑셀 기능 예시 : 자동차 인터페이스의 엑셀은 앞으로 가라는 기능, 뒤로 가게 구현하면 LSP 위반, 느리더라도 앞으로 가야함)</p>
   <p>ISP (인터페이스 분리 원칙): 특정 클라이언트를 위한 여러 개가 범용 인터페이스 하나보다 낫다</p>
   <p>(자동차 인터페이스 예시 : 운전 인터페이스, 정비 인터페이스로 분리)</p>
   <p>DIP (의존관계 역전 원칙) : 구현 클래스에 의존하지 말고, 인터페이스에 의존하라는 뜻</p>
   <p>(예를들어 운전자가 자동차 역할만 알면되고, 차에 대한 디테일 기능을 알필요가 없다)</p>
</details>

<details>
   <summary>EJB와 스프링의 차이점</summary>
   </br>
   <p>서버 어플리케이션의 생산성의 향상과 이동성을 실현하기 위해서 생겨난 것이 ejb입니다. bean에 의존하지만 객체지향적이지 않고, 컨테이너에서 안에서만 동작할 수 있는 객체구조입니다.</p>
   <p>이러한 문제점들을 개선한것이 스프링입니다. 스프링은 EJB의 기능을 유지하면서 복잡성을 제거해 코드가 가벼워 졌고, 여러 객체들을 DI 및 IOC하며 객체들의 라이프 사이클을 관리해 줍니다.</p>
</details>

<details>
   <summary>생성자 인젝션과 세터 인젝션의 차이점은?</summary>
   </br>
   <p>세터 인젝션 : 선택적인 의존성을 사용할 때 유용(상황에 따라 의존성 주입이 가능)</p>
   <p>생성자 인젝션 : 필수적인 의존성 주입에 유용하고 final 선언으로 객체가 불변하게 할 수 있음</p>
</details>

<details>
   <summary>직렬화와 역직렬화에 대해서 설명해주세요.<</summary>
   </br>
   <p>직렬화란 객체를 바이트 스트림으로 변경하는 것입니다.</p>
   <p>반대로 스트림을 통해 받은 직렬화된 객체를 원래 모양으로 만드는 과정을 역직렬화라고 합니다.</p>
</details>

<details>
   <summary>DAO와 DTO 무엇인가?</summary>
   </br>
   <p>DAO는 디비에 접근하는 트랜잭션 객체이고 DTO는 컨트롤러나 뷰와 같은 계층 간의 이동에 사용하는 전송 객체입니다.	</p>
</details>

<details>
   <summary>인터페이스를 사용하는 이유?</summary>
   </br>
   <p>OCP에 따르면 객체지향 프로그래밍에서는 확장에는 열려 있어야하고 수정에 있어서는 닫혀있어야 한다고 말합니다. 이에 따라 확장에 열려있는 설계를 위해 인터페이스를 사용합니다.</p>
</details>

<details>
   <summary>OOP란</summary>
   </br>
   <p>캡슐화, 다형성, 상속 을 이용하여 코드 재사용을 증가시키고, 유지보수를 감소시키는 장점을 얻기 위해서 객체들을 연결 시켜 프로그래밍 하는 것 입니다</p>
</details>

<details>
   <summary>field injection 대신 constructor injection을 사용해야하는 이유</summary>
   </br>
   <p>단일 책임 원칙 관점</p>
   <p>필드에 final 키워드 사용</p>
   <p>순환 참조 방지</p>
   <p>DI 컨테이너와 결합도가 낮기 때문에 테스트하기 좋다.</p>
   <p>NullPointerException 방지</p>
</details>

## JPA
<details>
  <summary>JPA 영속성 컨텍스트의 이점(5가지)을 설명해주세요.</summary>
  </br>
  <p>영속성 컨텍스트는 엔티티를 영구 저장하는 환경을 의미합니다.</p>
  <p>영속성 컨텍스트를 쓰는 이유는 1차 캐시, 동일성 보장, 쓰기 지연, 변경감지(Dirty checking), 지연로딩이 있습니다.</p>
  <ul>
    <li>1차 캐시: 조회가 가능하며 1차 캐시에 없으면 DB에서 조회하여 1차 캐시에 올려 놓습니다.</li>
    <li>동일성 보장: 동일성 비교가 가능합니다.(==)</li>
    <li>쓰기 지연: 트랜잭션을 지원하는 쓰기 지연이 가능하며 트랜잭션 커밋하기 전까지 SQL을 바로 보내지 않고 모아서 보낼 수 있습니다.</li>
    <li>변경 감지(Dirty checking): 스냅샷을 1차 캐시에 들어온 데이터를 찍습니다. commit 되는 시점에 Entity와 스냅샷과 비교하여 update SQL을 생성합니다.</li>
    <li>지연 로딩: 엔티티에서 해당 엔티티를 불러올 때 그 때 SQL을 날려 해당 데이터를 가져옵니다.</li>
  </ul>
</details>

<details>
  <summary>JPA Propagation 전파단계를 설명해주세요.</summary>
  </br>
  <p>대기업면접에서 나왔던 질문으로 트랜잭션 고립단계와 같이 질문할 가능성이 있습니다.</p>
  <p>JPA Propagation은 트랜잭션 동작 도중 다른 트랜잭션을 호출(실행)하는 상황에 선택할 수 있는 옵션입니다.</p>
  <p>@Transactional의 propagation 속성을 통해 피호출 트랜잭션의 입장에서는 호출한 쪽의 트랜잭션을 그대로 사용할 수도 있고, 새롭게 트랜잭션을 생성할 수도 있습니다.</p>
  <p>REQUIRED(디폴트): 부모 트랜잭션 내에서 실행하며 부모 트랜잭션이 없을 경우 새로운 트랜잭션을 생성합니다.</p>
  <p>이 외에도 종류가 REQUIRES_NEW, SUPPORTS, MANDATORY, NOT_SUPPORT, NEVER, NESTED 가 있지만 신입이 실제로 다뤄본 경험이 적기 때문에 REQUIRED(디폴트)값만 답변했습니다.</p>
</details>

<details>
  <summary>JPA를 쓴다면 그 이유에 대해서 설명해주세요.</summary>
  </br>
  <p>그동안 SQL중심의 무한 반복 CURD 작업을 하기때문에 SQL 의존적이었기 때문에 불편했습니다.</p>
  <p>ORM 기술이고, 자바를 객체지향으로 짜면, JPA가 뒷단에서 DB를 다뤄주는 것이다.</p>
  <P>필드만 추가하면 SQL은 JPA가 처리해줌으로써 성능과 생산성이 향상되고, 유지보수에 용이하며, 패러다임의 불일치를 해결할수 있습니다.</P>
</details>

<details>
  <summary>JPA에서 PK는 어떻게 설정하는지?</summary>
  </br>
  <p>@GeneratedValue 어노테이션을 통해 IDENTITY로 설정해주면 MySQL로 작업하면 알아서 AUTO_INCREMENT 처리 해줍니다.</p>
</details>

<details>
  <summary>LAZY와 EAGER 각각 어떤 기준으로 사용하시는지?</summary>
  </br>
  <p>보통 EAGER방식은 참조가 적고 간단한 쿼리에는 사용하지만, 되도록이면 지연로딩을 권장합니다.</p>
</details>

<details>
  <summary>@transactional에서 readOnly 붙인 이유?</summary>
  </br>
  <p>하이버네이트 세션 플러시 모드가 MANUAL로 설정되어 트랜잭션 커밋시 자동으로 flush가 호출되지 않는다.</p>
  <p>flush가 호출되지 않으니 스냅샷 비교등 무거운로직을 수행하지 않는다</p>
</details>

<details>
  <summary>OSIV(Open Session In View)</summary>
  </br>
  <p>true일 경우 사용자에게 응답 또는 view가 렌더링 될 때까지 영속성컨텍스트를 유지한다. 그래서 지연로딩이 가능했다.</p>
  <p>하지만 이전략은 너무 오랫동안 DB커넥션 리소스를 사용하기 떄문에 실시간 트래픽이 중요한 애플리케이션에서는 커넥션이 모자랄수 있다. 결국 장애로 이어짐</p>
  <p>false일 경우 트랜잭션을 종료할 때 영속성 컨텍스트 또한 닫힌다.</p>
</details>

<details>
  <summary>ManyToOne 쓴 이유는? 반대쪽에서 OneToMany 쓸수도 있지 않나요?</summary>
  </br>
  <p>기본적으로 ManyToOne는 FetchType이 EAGER로 되어있고, OneToMany는 lazy로 되어있습니다.</p>
  <p>따라서 추가쿼리가 실행될때마다 N+1 현상이 발생할 수 있습니다.</p>
</details>

<details>
  <summary>N + 1 문제가 발생하는 이유와 이를 해결하는 방법을 설명해주세요.</summary>
  </br>
  <p>N + 1 쿼리는 JPA의 프록시로 인한 지연 로딩 때문에 발생합니다. 정확한 의미는 1개의 쿼리를 실행했을 때, 내부에 존재하는 컬렉션들을 조회해오면서 생기는 문제입니다.</p>
  <p>만약 그런 객체를 가져와야 하는 경우 Fetch Join이라고 하는 JPQL의 join fetch를 사용합니다. 쿼리 한 번으로 해결할 수 있고, 또 다른 방법으로는 EntityGraph를 사용하는 방법이 있습니다.</p>
</details>