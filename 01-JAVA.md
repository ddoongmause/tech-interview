## 자바 기술면접 준비

<details>
    <summary>JVM에 대해 설명해 주시겠어요?</summary>
    </br>
    <p>Java Virtual Machine(자바 가상 머신) 약자의 줄임말</p>
    <p>자바 애플리케이션을 클래스로더를 통해 읽어 들여 자바 API와 함께 메모리, gc등을 실행합니다.</p>
</details>

<details>
    <summary>GC에 대해 설명해 주세요.</summary>
    </br>
    <p>가비지 컬렉션의 약자이며, JVM의 Heap영역에서 사용하지 않는 객체를 삭제하는 프로세스를 말합니다.</p>
</details>

<details>
   <summary>GC 루트가 될수있는 조건이 어떻게 될까요?</summary>
   </br>
   <p>1. Stack에 있는 지역변수나 파라미터들</p>
   <p>2. Method영역의 static 데이터들</p>
   <p>3. 자바 네이티브메서드 인터페이스(JNI)에 의해 생성된 객체들</p>
</details>

<details>
   <summary>GC 수거 대상이 어떻게 될까요?</summary>
   </br>
   <p>참조되지 않은객체 (UnReachable)이 수거 대상입니다.</p>
</details>

<details>
   <summary>GC 동작 순서</summary>
   </br>
   <p>한 사이클과정은 Mark and Sweep으로 돌아가며, 어쩔때는 compact상황까지 돌아갑니다.</p>
</details>

<details>
   <summary>GC는 언제 일어날까요?</summary>
   </br>
   <p>Heap 영역 : Young Generaion, Old Generation 으로 나뉩니다.</p>
   <p>Young Generaion (새로운 객체들이 할당되는 영역) -> 에덴 영역과 서바이벌 2개영역으로 총 3개의 영역이 존재합니다.</p>
   <p>Survivor가 다 쌓이면 다른 Survivor로 이동하고 하나는 빈상태로 변경합니다.</p>
   <p>이과정을 반복 후 살아있으면 Old영역으로 이동합니다.</p>
   <p>Old Generation이 꽉차면 Major GC가 일어납니다.</p>
</details>

<details>
   <summary>GC 과정에 대해 설명해주세요.</summary>
   </br>
   <p>1. 가비지 컬렉터가 스택의 모든변수를 스캔하면서 각각 어떤 객체를 참조하고 있는지 찾아서 마킹한다.</p>
   <p>Reachable Object가 참조하고 있는 객체도 찾아서 마킹한다.</p>
   <p>마킹되지 않은 객체를 Heap에서 제거한다.</p>
</details>

<details>
   <summary>GC를 직접 수행할 수 있을까요?</summary>
   </br>
   <p>GC는 System.gc() 메소드를 통해 개발자가 의도적으로 실행이 가능하다. 하지만 Stop-the-world 가 발생할 수 있어 시스템의 성능을 오히려 저하시킬 수 있다.</p>
</details>

<details>
   <summary>그러면 GC는 어떻게 삭제할 객체가 아닌 객체를 구분할 수있는 걸까요?</summary>
   </br>
   <p>GC루트로 부터 각각 참조하고 있는 객체들을 하나씩 하나씩 탐색해 나갑니다.</p>
   <p>참조된 객체들을 Reachable(리처블), 참조되지 않은객체는 UnReachable(언리처블)하다고 표현합니다.</p>
</details>

<details>
    <summary>객체가 JVM 메모리에 저장될 때 어디에 저장되는지</summary>
    </br>
    <p>메모리의 공간은 크게 'Static(스태틱) 영역', 'Stack(스택) 영역', 'Heap(힙) 영역'으로 구분되고 데이터타입(자료형)에 따라서 해당 공간에 할당 된다.</p>
    <p>클래스로드가 끝난 후 JVM은 main 메소드를 찾아 지역변수, 객체변수, 참조변수를 스택에 쌓음</p>
</details>

<details>
    <summary>Java의 세 가지 변수에 대해 JVM 메모리와 연관지어 설명해주세요.</summary>
    </br>
    <p>자바 변수에는 지역 변수, 클래스 멤버 변수, 객체 멤버 변수가 존재합니다.</p>
    <p>지역 변수는 스택영역에서 일생을 보낸다. 스택 영역 안에서도 스택 프레임 안에 존재합니다. 따라서 프레임이 사라지면 함꼐 사라진다.</p>
    <p>클래스 멤버 변수는 스태틱 영역에 위치한다. JVM에 의해 클래스가 로딩될 때 함꼐 로딩되며 한 번 자리를 잡으면 JVM이 종료될 때까지 고정된 상태로 위치한다. 멤버 변수 앞에 static keyword가 붙게되면 클래스 멤버 속성이 된다.</p>
    <p>객체 멤버 변수는 힙에 위치한다. 객체 멤버 변수들은 GC에 의해 메모리 회수가 되기전까지 객체와 함꼐 존재한다. </p>
</details>

<details>
    <summary>Java의 객체 멤버 메서드는 어디에 위치할까요?</summary>
    </br>
    <p>객체 멤버 변수와 달리, 메서드는 한 번 로딩되면 인스턴스가 모두 공유하는 코드가 됩니다. static 영역에 로딩됩니다.</p>
</details>

<details>
   <summary>자바프로그램 실행과정에 대해 설명 해 주세요</summary>
   </br>
   <p>자바 컴파일러(javac)가 자바 소스코드(.java)를 자바 바이트코드(.class)로 변환하고 Class Loader를 통해 JVM으로 로딩하고 실행 엔진을 통해 해석하여 Runtime Data Areas에 배치되어 실질적인 수행</p>
</details>

<details>
   <summary>JVM 구성은 어떻게 되어 있나요?</summary>
   </br>
   <p>Class Loader(클래스 로더)</p>
   <p>Execution Engine(실행 엔진) : 자바 바이트 코드를 명령어 단위로 읽어서 실행한다.</p>
   <p>Interpreter(인터프리터) : 한줄 씩 수행하는 방식.</p>
   <p>JIT(Just In Time) : 인터프리터 방식의 단점을 보완하기 위해 도입된 JIT 컴파일러이다.</p>
   <p>자바</p>
</details>   

<details>
   <summary>JIT가 어떻게 이용되는지??</summary>
   </br>
   <p>전체바이트 코드를 네이티브 코드로 변경하여 실행 성능을 높이는 방식</p>
</details>

<details>
   <summary>JVM에서 메모리의 누수가 발생할까?</summary>
   </br>
   <p>JVM에서도 메모리 누수가 발생할 수 있다. GC는 참조하지 않는 Unreachable한 객체를 제거 대상으로 간주하기 때문에 사용은 하지 않지만 계속해서 참조를 하는 경우가 있다면 메모리 누수가 발생할 수 있다.</p>
</details>

<details>
   <summary>메모리 누수 원인</summary>
   </br>
   <p>Static 변수에 의한 객체 참조</p>
   <p>모든 현재 자바 쓰레드 stack내의 지역변수, 매개 변수에 의한 객체 참조</p>
   <p>JNI 프로그램에 의해 동적으로 만들어지고 제거되는 JNI global 객체 참조</p>
   <p>-> 이러한 경우에 사용할 수 있는 개체로 분류되어 GC에서 가져가지 안항 메모리가 누수될 수 있습니다.</p>
</details>

## 2. Collection (컬렉션)
<details>
   <summary>List, Set, Map에 설명해 주세요</summary>
   </br>
   <p>리스트(List) : 순서를 가지고 있으며, 데이터의 중복을 허용하는 보관 구조입니다.</p>
   <p>세트(Set) :  순서를 가지지 않고, 데이터의 중복을 허용하지 않는 구조입니다.</p>
   <p>맵(Map) : 키와 값을 가지며, 키를 가지고 원하는 데이터를 검색하는 구조</p>
</details>

<details>
   <summary>List, Set, Map은 어떤 인터페이스를 구현하나요?</summary>
   </br>
   <p>List, Set은 각각 Collection인터페이스를 구현한다. Map은 별도로 정의합니다.</p>
</details>

<details>
   <summary>forEach를 사용할 수 있는 자료구조는 어떠한 인터페이스를 상속받고 있나요?</summary>
   </br>
   <p>Iterable 인터페이스를 구현한다.</p>
</details>

<details>
   <summary>forEach를 사용하면 다음 데이터를 얻기위해서 내부적으로 호출되는 메서드가 있는데 무엇일까요?</summary>
   </br>
   <p>iterator() 메소드를 호출합니다.</p>
</details>

<details>
   <summary>forEach를 사용하면 다음 데이터를 얻기위해서 내부적으로 호출되는 메서드가 있는데 무엇일까요?</summary>
   </br>
   <p>iterator() 메소드를 호출합니다.</p>
</details>

<details>
   <summary>Iterator와 Iterable의 차이는 무엇인가요?</summary>
   </br>
   <p>iterator은 순회할 수 있는 컬렉션을 의미한다. iterable 인터페이스를 implement하면 객체는 foreach문을 사용할 수 있습니다.</p>
</details>

<details>
   <summary>List의 장점을 Array와 비교하여 설명해주세요.</summary>
   </br>
   <p>list 장점 : 가변적이기 때문에, 메모리를 효율적으로 사용할수 있다.</p>
   <p>list 단점 : 엑세스가 느리다.</p>
   <p>배열 장점  : 인덱스 번호를 통해 엑세스가 빠르다. </p>
   <p>배열 단점  : 정적 자료구조이기 때문에 메모리를 차지하고 있다.</p>
</details>

<details>
   <summary>Map(맵)의 장단점에 대해 설명해 주세요</summary>
   </br>
   <p>장점 : 엑세스가 빠르면서(배열), 늘어나거나 줄어들수 있다(리스트)</p>
   <p>단점 : 메모리를 많이 쓴다. o(1)</p>
</details>

<details>
   <summary>알고있는 MAP의 종류는?</summary>
   </br>
   <p>HashMap, TreeMap, LinkedHashMap 이 대표적입니다.</p>
</details>

<details>
   <summary>ArrayList 와 LinkedList의 차이점</summary>
   </br>
   <p>어레이리스트의 경우 원소가 배열인 반면에 링크드리스트의 원소는 노드이다.</p>
   <p>get method에서 linkedList의 시간복잡도는 O(n)이며 삽입과 삭제의 경우 O(1)이다.</p>
</details>

<details>
   <summary>LinkedList에 대해 설명해 주세요</summary>
   </br>
   <p>떨어져있는 리스트를 연결노드해서 쉽게 찾을수 있습니다.</p>
   <p>링크드 리스트를 양쪽 방향 연결한것이 double LinkedList 입니다.</p>
</details>

<details>
   <summary>size가 100인 배열을 만들습니다. 그 배열에 20개를 넣거나 5개로 줄이려면 어떻게 해야 하나요?</summary>
   </br>
   <p>배열은 새로운 배열을 만들어서 복사 해놓고 기존 배열은 지워야 합니다.</p>
   <p>배열 자체가 늘리거나 줄일순 없기 때문에, 갯수가 가변적이면 ArrayList를 사용하는것이 좋을 것 같습니다.</p>
</details>

<details>
   <summary>자바로 동적배열을 생성하고싶다면 어떡해야 할까요?</summary>
   </br>
   <p>자바의 배열은 동적 할당되지 않으므로 동적할당이 필요할 때 연결리스트 사용합니다.</p>
</details>

## 3. 스택 & 트리

<details>
   <summary>stack, heap 영역별로 무엇이 저장되는지 설명해 주세요.</summary>
   </br>
   <p>Heap은 프로그램을 실행 하면서 생성한 모든 객체 인스턴스를 heap에 저장</p>
   <p>stack은 스레드별로 1개만 존재하고, 스택 프레임은 메서드가 호출될 때마다 생성된다. 메서드 실행이 끝나면 스택 프레임은 pop 되어 스택에서 제거된다.</p>
   <p>(참고 영상: [10분 테코톡] 🎅무민의 JVM Stack & Heap) 영역별로 설명</p>
</details>

<details>
   <summary>Queue를 이용해 선입선출하는 메시지발송을 만들고 있는데, 만약에 긴급발송건이나 예약발송건이 있으면 먼저 보내주려면 어떤 자료구조를 이용하는 것이 좋을까요?</summary>
   </br>
   <p>PriorityQueue(우선순위큐) Comparator 방식으로 구현 합니다.</p>
</details>

<details>
   <summary>tree는 어떤 경우에 사용을 하나요? 다른 자료구조랑 어떤 차이가 있나요? 어떤경우에 사용하는 것이 좋나요?</summary>
   </br>
   <p>트리는 부모는 여러 자식을 가질 수 있지만 자식은 하나의 부모를 갖는 구조 입니다.</p>
   <p>또한 큐와 스택같은 선형구조는 자료를 저장하고 꺼내는것에 초점이 맞춰져 있다면, 비선형구조인 트리는 계층적인 구조 표현에 초점이 맞춰져 있습니다.</p>
</details>

<details>
   <summary>이진검색트리(Binary Search Tree)에 대해 설명해 주세요</summary>
   </br>
   <p>이진탐색(O(LogN) + 연결리스트(O(1))의 장점을 가진것이 이진탐색트리입니다.</p>
   <p>각 노드의 자식이 2개 이하인 트리이며 왼쪽 자식은 부모보다 작고, 오른쪽 자식은 부모보다 큽니다.</p>
</details>

<details>
   <summary>B-Tree와 이진검색트리는 내부적으로 어떤 차이가 있나요? 데이터가 어떻게 저장되나요?</summary>
   </br>
   <p>B-tree는 비 종단 노드가 가질 수 있는 자식 노드의 최대 수는 M입니다. 여기서 M은 B- 트리의 순서입니다.</p>
   <p>반면 이진트리는 최대 두 개의 하위 트리 또는 하위 노드를 가질 수 있습니다.</p>
</details>

<details>
   <summary>완전 이진 트리(Complete Binary Tree)에 대해 설명할 수 있나요?</summary>
   </br>
   <p>이진 트리의 노드를 생성할 때 트리의 왼쪽부터 차곡차곡 채워 나가는 트리를 의미한다.</p>
   <p>이때 완전 이진 트리의 한 레벨이 꽉 차기 전에는 다음 레벨에 노드를 생성할 수 없다. 즉, 마지막 레벨을 제외한 모든 레벨에는 노드가 꽉 차 있어야 한다는 뜻이다.</p>
</details>

<details>
   <summary>Queue와 Stack을 사용하는 예를 들어주세요.</summary>
   </br>
   <p>스택은 다음과 같이 방금 닦은 접시를 항상 접시 더미 맨 위에 올려놓게 되고, 접시가 필요하면 맨 위에 있는 접시를 꺼내게 되는 스택과 같은 구조를 가지고 있습니다.</p>
   <p>큐는 편의점 알바를 해보신 분들은 아시겠지만, 물품을 진열할 때 앞에서부터 채워 넣기 때문에 편의점 알바 경험이 있으신 분들은 선입선출에 대해 익숙할 것입니다.</p>
</details>

<details>
   <summary>만약에 인스턴스 메시지를 등록된 순서대로 발송한다고 하면 어떤 자료구조를 이용하는 것이 좋을까요?</summary>
   </br>
   <p>java.util.Queue 인터페이스는 java.util.Deque 하위 인터페이스에 의해 확장됩니다.</p> 
   <p>Deque는 양방향 대기열을 만듭니다.</p> 
   <p>일반 대기열에서는 뒤쪽에 삽입하고 앞쪽에 제거 만 허용하는 반면, 데크를 사용하면 앞뒤 모두에서 삽입 또는 제거가 가능합니다.</p> 
</details>

## 4. Generic (제네릭)
   <details>
      <summary>Generic 타입의 자료구조의 장점은 무엇인가요?</summary>
      </br>
      <p>프로그래머가 원하는 객체의 타입을 명시해서 의도하지 않은 객체는 저장될 수 없도록 컴파일시에 오류를 확인할 수 있게 된다.</p>
   </details>

   <details>
      <summary>Generic(제네릭) 타입의 자료구조와 None Generic(비제네릭)타입의 자료구조의 차이를 설명할 수 있나요?</summary>
      </br>
      <p>제네릭은 정의된 유형의 데이터만 보유할수 있고 안전하지만, 비제네릭은 모든데이터를 보유할 수 있지만, 안전하지 않습니다.</p>
      <p>제네릭은 타입 캐스팅이 필요 없고, 비제네릭은 검색할때마다 개별 유형 캐스팅을 수행해야 합니다.</p>      
      <p>비제네릭은 런타임시 안정성 확인, 제네릭은 컴파일타임에 형식 안정성을 확인할 수 있습니다.</p>
   </details>

   <details>
      <summary>None Generic 타입의 자료구조는 종류는 무엇이 있나요?</summary>
      </br>
      <p>기본형 자료형 타입</p>
   </details>

   <details>
      <summary>Generic 타입의 자료구조는 무엇이 있나요?</summary>
      </br>
      <p>컬렉션으로 구조이기 때문에 최상위객체인 Object형태로 저장되고 있습니다.</p>
   </details>

## 5. 자바 8
   <details>
      <summary>자바 8의 아는대로 설명하세요.</summary>
      </br>
      <p>람다식 표현식</p>
      <p>stram을 통해 쉽게 출력 컬렉션으로 매핑하거나 변경할때 유용하다. (map, filter, reduce, collect)/p>
      <p>Optional 사용가능</p>
      <p>날짜 관련 클래스들 추가</p>
      <p>함수형 인터페이스</p>
   </details>

   <details>
      <summary>Optional 특징에 대해 말씀해주세요.</summary>
      </br>
      <p>NullPointException를 유발할수 있는 null을 직접 다루지 않아도 된다. </p>
      <p>null 체크를 직접하지 않아도 된다.</p>
   </details>

   <details>
      <summary>Optional instance는 어떻게 만들까?</summary>
      </br>
      <p>optional 클래스 내부에 static method 3방법으로 생성할 수 있다. 종류는 다음과 같다.</p>
      <p>empty()를 통해 null을 담고있는 비어있는 Optional객체를 얻어온다.</p>
      <p>of(T value)를 통해 value가 null이면 NullPointerException 을 던진다.</p>
      <p>ofNullable(T value)는 empty() 메소드와 of(value) 메소드가 합쳐진 형태라고 생각하면 된다.</p>
   </details> 

   <details>
      <summary>Java 8 에서 나온 Date, Time API에 대해 아는대로 말씀해주세요.</summary>
      </br>
      <p>LocalDate와 LocalTime 클래스를 통해 타임존을 사용하지 않고 구현 가능합니다.</p>
   </details> 

## 6. 오버로딩과 오버라이딩

   <details>
      <summary>오버로딩과 오버라이딩 차이점</summary>
      </br>
      <p>오버로딩은 메서드 이름들이 같아도 매개변수가 다르게 만들 수있습니다.</p>
      <p>오버라이딩은 상속받은 클래스나 인터페이스의 메소드를 재정의 할수있습니다.</p>
   </details>  

   <details>
      <summary>동적 바인딩과 정적 바인딩에 대해 설명해 주세요</summary>
      </br>
      <p>동적바인딩이란 다형성을 사용하여 메소드를 호출할 때 발생하는 현상이다. 런타임에 성격이 결정되며 실제 참조하는 객체는 서브 클래스이니 서브 클래스의 메소드를 호출하게 된다.</p>
      <p>정적바인딩이란 컴파일 시간에 성격이 결정되는 것을 말한다.</p>
   </details>  

## 7. Wrapper class
   <details>
      <summary>Wrapper class에 대해 설명해주세요.</summary>
      </br>
      <p>기본 자료형에 대한 클래스 표현을 래퍼 클래스라고 합니다. Integer, Float, Boolen등이 래퍼클래스의 예이다.</p>
      <p>객체지향적인 프로그램을 위한 프로그래밍이기 때문에 기본자료형이었으면, == 으로 바로 비교해줄 수있지만, 래퍼클래스 경우에는 .intValue() 메소드를 통해 해당 래퍼 클래스의 값을 가져와 비교해줘야 한다.</p>
   </details>

   <details>
      <summary>boxing, unboxing 무엇인지, 자동으로 언제 일어나는지</summary>
      </br>
      <p>wrapper class에서 기본형 객체를 wrapper로 바꿔주는 것을 박싱이라고하고, 반대로 primitive로 바꾸는것을 언박싱이라고 한다.</p>
   </details> 

   <details>
      <summary>동적 바인딩과 정적 바인딩에 대해 설명해 주세요</summary>
      </br>
      <p>동적바인딩이란 다형성을 사용하여 메소드를 호출할 때 발생하는 현상이다. 런타임에 성격이 결정되며 실제 참조하는 객체는 서브 클래스이니 서브 클래스의 메소드를 호출하게 된다.</p>
      <p>정적바인딩이란 컴파일 시간에 성격이 결정되는 것을 말한다.</p>
   </details> 

## 8. Multi-Thread 환경에서의 개발
   <details>
      <summary>동기화 synchronized {}에 붙을때와 메소드에 붙을때 차이 (동기화 메소드와 동기화 블록 차이점)</summary>
      </br>
      <p>메서드하나 모두가 실행되고 다음 메서드 대기하고 있다가 실행됩니다. (1,2,3 메서드가 있으면 1번이 끝날때까지 기다리고, 3번은 맨 마지막으로 기다리게됩니다)</p>
      <p>필요한 부분만 동기화를 시키고 싶다면??? synchronized (this){}를 사용하면 됩니다.</p>
   </details>

## 9. Hash
   <details>
      <summary>HashTable과 HashMap의 차이는 무엇인가요?</summary>
      </br>
      <p>Hashtable은 JDK1.0 번전에서에서 처음 등장합니다. 하지만, JDK1.2 버전이 되면서부터 속도 문제 때문에 HashMap이라는 것으로 대체되었습니다.</p>
      <p>Hashtable은 키나 null값 저장이 불가하고, HashMap은 가능합니다. 단, 쓰레드 안전여부는 떨어집니다.</p>
   </details>

   <details>
      <summary>Hashing이란 무엇인가요</summary>
      </br>
      <p>해시함수를 이용해서 데이터를 해시 테이블에 저장하고 검색하는 기법을 말합니다.</p>
   </details>

   <details>
      <summary>hash에 대해 설명 해 주세요</summary>
      </br>
      <p>내부적으로 배열을 사용하여 데이터를 저장하여 검색 속도가 빠릅니다</p>
      <p>데이터의 삽입/삭제 시 해시 알고리즘을 이용하여 데이터와 연관된 고유한 숫자를 만들어 인덱스로 사용합니다.</p>
   </details>

   <details>
      <summary>해시 메서드에 대해 설명 해 주세요</summary>
      </br>
      <p>내부적으로 배열을 사용하여 데이터를 저장하여 검색 속도가 빠릅니다</p>
      <p>데이터의 삽입/삭제 시 해시 알고리즘을 이용하여 데이터와 연관된 고유한 숫자를 만들어 인덱스로 사용합니다.</p>
   </details>

   <details>
      <summary>hash에 대해 설명 해 주세요</summary>
      </br>
      <p>해시는 해시테이블을 사용하여 데이터를 저장한다.</p>
      <p>이때 인덱스를 구하기 위해 해시 메서드를 사용하여 고유의 숫자 값인 해시코드를 얻는다.</p>
   </details>

   <details>
      <summary>serialVersionUID를 선언해야 하는 이유</summary>
      </br>
      <p>JVM은 직렬화와 역직렬화를 하는 시점의 클래스에 대한 버전 번호를 부여합니다.</p>
      <p>SerialVersionUID값을 저장할 때 클래스 버전이 맞는지 확인하기 위한 용도입니다.</p>
   </details>

   <details>
      <summary>직렬화와 역직렬화 차이점</summary>
      </br>
      <p>직렬화 : 객체의 내용을 Byte 단위로 변환하여 파일 또는 네트워크를 통해 Stream(송/수신)이 가능하게 하는 것</p>
      <p>역직렬화 : Byte로 변환된 Data를 원래대로 Object나 Data로 변환하는 기술</p>
   </details>

## 10. static(정적)
   <details>
      <summary>non-static멤버와 static 멤버의 차이</summary>
      </br>
      <p>non-static멤버는 인스턴스 멤버이며 공유되지 않는다.</p>
      <p>static멤버는 클래스 멤버이며 동일한 클래스의 모든 객체들에 의해 공유된다.</p>
   </details>

## 11. 기타 질문
   <details>
      <summary>자바의 원시타입들은 무엇이 있으며 각각 몇 바이트를 차지하나요?</summary>
      </br>
      <p>실제 면접에서 들었던 질문입니다. 들었을 때 굉장히 당황했던 기억이 나네요.</p>
      <p>boolean(1), char(unsigned 2), byte(1), short(2), int(4), long(8), float(4), double(8)</p>
   </details>

   <details>
      <summary>동일성(identity)와 동등성(equality)에 대해 설명해주세요. (equals(), ==)</summary>
      </br>
      <p>동일성은 객체의 주소를 비교하는 것이고, 동등성은 객체의 같음을 비교하는 것입니다.</p>
      <p>기본적으로 자바에서는 Object 클래스에 정의된 equals() 메소드가 동일성 비교를 합니다. 따라서, 개발자는 원한다면 equals() 메소드를 오버라이딩해서 동등성의 판단 기준을 정의해주면 됩니다.</p>
   </details>

   <details>
      <summary>원시타입과 참조타입의 차이에 대해 설명해주세요.</summary>
      </br>
      <p>원시타입은 Java에서 단 8개 밖에 존재하지 않는 타입입니다. 나머지는 모두 참조타입이라고 볼 수 있고, Object 클래스이거나 이를 상속하는 클래스들로 이루어져 있습니다.</p>
      <p>원시타입은 항상 값이 존재해야 합니다. 반면, Object 타입은 null 포인터를 가질 수 있습니다. 그리고 멤버변수가 초기화될 때, 원시타입은 기본값을 가지지만, 참조타입은 null 포인터를 가지는 차이도 있습니다.</p>
   </details>

   <details>
      <summary>String, StringBuilder, StringBuffer 각각의 차이에 대해 설명해주세요.</summary>
      </br>
      <p>String은 불변입니다. StringBuilder와 StringBuffer는 이런 String의 특징때문에 사용하는 가변타입이라고 볼 수 있습니다.</p>
      <p>StringBuilder와 StringBuffer는 Thread-safe 여부의 차이가 있습니다. StringBuilder는 Thread-safe하지 않습니다. 따라서 Multi-Thread 환경에서 사용할 때는 StringBuffer를 사용합니다.</p>
   </details>

   <details>
      <summary>String을 ==로 비교하면 안되는 이유를 설명해주세요.</summary>
      </br>
      <p>참조하는 값이 다르기때문에 equals로 비교해야 합니다.</p>
   </details> 

   <details>
      <summary>Java에서 동일한 String을 새로 만들 때마다 객체가 생성되는지? </summary>
      </br>
      <p>새로운 객체를 계속 만들면 메모리 관리 측면에서 비효율적이다.</p>
   </details>

   <details>
      <summary>예를 들어 String a = Apple; 해놓고, String b = Apple;하면 String b를 위한 공간이 새로 할당 되는지? </summary>
      </br>
      <p>할당이 되지 않습니다. 리터럴로 사용하여 생성한 객체는 동일한 객체를 바라봅니다.</p>
      <p>하지만 new 연산자를 사용해서 생성했다면 서로 다른 객체를 만들고 바라봅니다.</p>
   </details> 

   <details>
      <summary>equals and hashcode 재구현한 이유</summary>
      </br>
      <p>동일한 객체는 동일한 메모리 주소를 갖는다는 것을 의미하므로, 동일한 객체는 동일한 해시코드를 가져야 한다.</p>
      <p>그렇기 때문에 만약 우리가 equals() 메소드를 오버라이드 한다면, hashCode() 메소드도 오버라이드 되어야 한다.</p>
   </details>

   <details>
      <summary>Stream이 무엇인가요?</summary>
      </br>
      <p>컬렉션 이터를 처리하는 임시 구현 코드 대신 질의로 표현할 수 있다</p>
      <p>fiter, sorted, map, collect 같은 여러 빌딩 블록 연산을 연결해서 복잡한 데이터 처리 파이프라인을 만들수 있다.</p>
   </details>

   <details>
      <summary>롬복이 생성하는 메서드가 어느 시점에서 생성되는 지 아는지?</summary>
      </br>
      <p>자바 컴파일 시점에서 특정 어노테이션으로 해당 코드를 추가할 수 있는 라이브러리입니디. </p>
   </details>

   <details>
      <summary>메서드를 분리하는 자신만의 기준이 있는지?</summary>
      </br>
      <p>많은 책임을 가진 객체로부터 책임을 분리합니다. OCP를 사용해 필요한 역할만 나눕니다.</p>
   </details>

   <details>
      <summary>Spring REST Docs 왜 썼는지?</summary>
      </br>
      <p>깔끔 명료한 문서를 만들수 있고, 문서제공용으로 좋습니다.</p>
      <p>반면 스웨거는 API동작을 테스트하는 용도에 더 특화되어 있습니다.</p>
   </details>

   <details>
      <summary>HashMap의 시간 복잡도 말해주세요.</summary>
      </br>
      <p>시간복잡도가 O(1)인 이유는 key값을 (hashing & n - 1)으로 직접 index를 가져오기 때문입니다.</p>
   </details>

   <details>
      <summary>Enum, 추상 클래스 어떤 식으로 사용했는지 설명해주세요.</summary>
      </br>
      <p>Enum은 주로 기존에 code테이블을 관리하기 위한 테이블에서 enum 클래스 변경을 통해 객체간 책임을 확실히 분리 하였습니다.</p>
      <p>추상 클래스는 공통적인 기능을 미리 구현해두고 싶을 떄 사용한다.</p>
   </details>

   <details>
      <summary>domain package에 repository, entity 들어있는데 그렇게 한 이유?</summary>
      </br>
      <p>관련된 코드들이 응집해 있고, 디렉토리 구조를 통해 도메인을 이해할 수 있습니다.</p>
   </details>

   <details>
      <summary>그러면 domain은 무엇인가요?</summary>
      </br>
      <p>네트워크상에서 컴퓨터를 식별하는 호스트명을 가리키며 '웹 주소'라고 불립니다.</p>
   </details>

   <details>
      <summary>Integer 하나만 있는 Vo 객체를 만든 이유는 무엇인가요?</summary>
      </br>
      <p>불변 클래스이기 때문에 readOnly 특징을 가진다. 예를 들자면 String,Integer,Color 클래스등이 있다.</p>
      <p>중간에 값을 바꿀수 없기떄문에 새로 만들어야 합니다.</p>
   </details>

   <details>
      <summary>Checked Exception은 언제 사용하나요?</summary>
      </br>
      <p>발생가능성이 충분히 예측가능하고, 런타임에 복구가 가능한 경우</p>
   </details> 

   <details>
      <summary>Unchecked, Checked Exception 차이가 뭔가요?</summary>
      </br>
      <p>Checked Exception은 반드시 예외를 처리해야되지만, Unchecked는 명시적인 처리를 강제하지 않음</p>
      <p>Checked Exception은 확인시점이 컴파일 단계라면, Unchecked는 실행단계</p>
      <p>Checked Exception은 롤백을 하지 않고, Unchecked는 롤백을 합니다.</p>
   </details> 

   <details>
      <summary>Custom Exception은 다 RuntimeException 상속 했는데, 특별한 이유가 있는지?</summary>
      </br>
      <p>RuntimeException은 Checked Exception과 Unchecked Exception을 구분하기 위한 Exception입니다.</p>
   </details> 

   <details>
      <summary>**Integer.MIN_VALUE에는 어떤 값이 들어가있나요? 어떤 컴퓨터에서 찍어도 동일한 값인가요?</summary>
      </br>
      <p>약 21억정도 되며, ??? </p>
   </details> 

   <details>
      <summary>** 해당 사전에서 단어의 일부분으로 검색할 수 있는 일종의 자동완성 기능을 추가하려고 한다. 예를 들어 a를 찾으면 a로 시작하는 단어 5개, ap로 찾으면 ap로 시작하는 단어 상위 5개, 이걸 어떤 식으로 구현할 것인지?</summary>
      </br>
      <p></p>
   </details>

   <details>
      <summary>Java에서 람다가 무엇인지 말씀해주세요.</summary>
      </br>
      <p>익명함수라고 불리며, 람다를 사용하면 코드가 간결해지고, 지연연산을 수행함으로써 불필요한 연산을 최소화 할 수 있습니다.</p>
      <p>단점이라면 stream사용시 단순 for문 또는 while문 사용 시 성능이 떨어집니다.</p>
   </details>

   <details>
      <summary>JUnit의 생명주기에 대해 아는지?</summary>
      </br>
      <p>만약 모든 테스트 메서드를 동일한 환경에서 동작시키고 싶다면, 단순히 @TestInstance 어노테이션을 사용하면 된다.</p>
      <p>만약 해당 클래스가 인스턴스 속성을 가진다면 @BeforeEach 나 @AfterEach 에서드를 사용하여 이를 초기화 해야 할 필요가 발생할 수 있다.</p>
   </details>

   <details>
      <summary>JUnit 4 와 JUnit 5의 차이를 설명해주세요.</summary>
      </br>
      <p>선언 어노테이션이 변경되었습니다. 예를들어 @Before -> @BeforeEach 변경으로 명확하게 네이밍이 변경됨.</p>
      <p>4에서는 접근제어자 public로 사용했다면 5는 접근제어자 Default로 사용</p>
   </details>

   <details>
      <summary>JVM 기반 언어의 특징을 설명해주세요.</summary>
      </br>
      <p>런타임으로 사용할 경우 몇 가지 이점과 혜택을 누릴 수 있다.</p>
      <p>다양한 언어로 구현한 애플리케이션들은 서로 라이브러리를 공유할 수 있고, 동일한 데이터 구조에서 작동한다.</p>
      <p>다양한 언어라면 코틀린, 스칼라, 파이썬등 자바를 보완할 수 있는 언어입니다.</p>
   </details>