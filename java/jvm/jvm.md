# JVM의 메모리





## 구성요소&#x20;

<figure><img src="../../.gitbook/assets/image (1) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

### Stack Area&#x20;

> JVM에서 스레드를 생성하면 stack 영역이 기본적으로 생성됩니다. \
> 해당 스레드 안에서만 사용할 수 있는 Stack 자료 구조입니다.&#x20;

<table><thead><tr><th width="205"></th><th></th></tr></thead><tbody><tr><td>Local Variable Array</td><td> 해당 스레드를 실행하면서 필요한 지역변수를 array로 저장한다.</td></tr><tr><td>Operand Stack</td><td>계산의 중간 결과물을 저장한다.</td></tr><tr><td>Frame Data</td><td>상수 풀과 exception table을 가지고 있다.</td></tr></tbody></table>



### PC Register&#x20;

> 현재 수행할 JVM machine instruction을 올려놓는 PC Register 공간입니다. 실제 운영 체제의 PC Register와 같은 역할을 수행합니다.&#x20;



### Shared Memory&#x20;

> 모든 스레드에서 공유하는 자원입니다 JVM Heap 이라고도 부릅니다.&#x20;

<table><thead><tr><th width="161">영역 이름 </th><th>설명 </th></tr></thead><tbody><tr><td>메소드 영역</td><td><ul><li>class, method, static variables 등을 저장합니다.</li><li>불변합니다.</li></ul></td></tr><tr><td>Heap 영역</td><td><ul><li>java object들의 저장소입니다. </li><li>GC 대상이 됩니다. </li></ul></td></tr></tbody></table>

