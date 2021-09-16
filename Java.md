

<h1> Java </h1>

---

## 추상 클래스

---

* **추상 메소드**

  * 기능이 구현되지 않고 원형만 선언되어 있는 메소드.

  * 중괄호 "{}"가 생략외어있다.

    ```java
    abstract class DObject {
        public DObject next;
        
        public DObject() { next = null; }
        abstract public void draw();
    }
    ```

  * 추상 메소드는 서브 클래서에서 오버라이딩하여 구현한다.

  * 추상 클래스는 추상 메소드가 0개 이상 선언되어야 한다.

  * 추상 클래스는 **객체를 생성할 수 없다**.

  * 서브 클래스는 **`extends`**해서 추상클래스를 사용할 수 있다.

* **final** 

  * final 클래스는 **상속될 수 없다**.
  * final 메소드는 자식 클래스가 **Overriding 할 수 없습니다**.
  * 변수에 final을 쓰면 **상수**가 된다.

## Interface

---

* **Interface**

  * 상수와 추상 메소드로만 이루어져 있다.

  * 메소드의 내용읠 정의하는 중괄호"{}"가 없다.

  * 추상메소드에 abstract를 사용하지 않아도 된다.

  * 모든 추상 메소드의 접근지정자를 public으로 가정한다.

  * 추상 메소드의 사용 이유

    * 앞으로 추가되거나 구현되야하는 기능의 설계 역할, 실제 기능은 구현하지 않고 원형만 구현

    * 외부에 공개할 메소드를 등록하는 목적으로 사용.

    * 인터페이스를 구현하는 클래스는 인터페이스 상에 있는 모든 추상메소드를 구현해야한다.***(하나라도 구현하지 않으면 구현클래스는 추상클래스가 된다.)***

    * 인터페이스는 객체를 생성 할 수 없다.

    * **Interface**를 사용하고자 하는 클래스는 **implements** 해줘야한다.

      ```java
      interface A {}
      
      public class B implements A {}
      ```

      

## Package(Folder, Directory)

---

* 같거나 비슷한 처리를 하는 클래스를 그룹으로 묶어 지정하는 것을 패키지 지정이라고 한다.
* 폴더에서 파일을 분류하듯 클래스를 그룹별로 분리할 수 있게 해줌.
* 모든 클래스는 기본패키지인 java.lang을 자동으로 import 한다.*(따로 선언하지 않아도 됨)*
* 패키지 클래스는 반드시 javac -d . *.java로 컴파일 할것!
* 

## 박싱/언박싱

---

* 기본타입과 참조타입 클래스에서 발생한다.

* 박싱 : 기본타입 -> 참조타입

  ```java
  Integer gg = 3;
  ```

  

* 언박싱 : 참조타입 -> 기본타입

  ```java
  int ff = new Integer(4);
  ```

  

* 주로 기본타입과 랩퍼클래스에서 이루어 진다.



## Generics

* 객체를 저장하는 기술인 Collection Framework의 단점을 개선한 기능

* 클래스나 메소드에 자료형을 매개변수 형식으로 사용할 수 있는 기능.

* `Class ArrayList<E>`에서 E가 있는 곳에는 ArrayList를 선언하고 생성할 때 사용할 실제 데이터 타입을 기입.

* `new ArrayList<String>()`을 하게 되면 ArrayList에는 String 타입의 데이터만 넣을 수 있다.

  ```java
  ArrayList<Integer> list = new ArrayList<Integer>(10); 
  list.add(new Integer(10)); 
  ```

  

* Generic 클래스

  * 제네릭 클래스는 형 매개변수를 가지는 클래스이다.

  * 형매개변수는 객체 생성시 전달 받으며 속성이나 메소드의 자료형으로 사용한다.

  * 아래처럼 두가지 타입을 전달 받을 수 있다.

    ```java
    class Price<N, V> { 
    private N[] names; 
    private V[] values; 
    private int index; 
    Price(int size) { 
    names = (N[])new Object[size]; 
    values = (V[])new Object[size]; 
    index = 0; 
    } 
    public void insert(N n, V v) { 
    names[index] = n; 
    values[index] = v; 
    ++index; 
    } 
    public void print() { 
    for (int i = 0; i < index; i++) 
    System.out.println(names[i] + " : " + values[i]); 
    } 
    } 
     
    public class MultipleTypeParam { 
    public static void main(String[] args) { 
    Price<String, Integer> p1 = new Price<String, Integer>(10); 
    Price<String, Double> p2 = new Price<String, Double>(10); 
    p1.insert("Apple", 1200); 
    p1.insert("Banana", 2000); 
    p1.insert("Grape", 4500); 
    p2.insert("USD", 943.0); 
    p2.insert("JPY", 822.86); 
    p2.insert("EUR", 1273.05); 
    System.out.println("*** Fruit Price ***"); 
    p1.print(); 
    System.out.println("*** Exchange Rate ***"); 
    p2.print(); 
    } 
    } 
    ```

    