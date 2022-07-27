# Python



## 수학연산자

---

| 연산자 |          설명           |
| :----: | :---------------------: |
|   +    |          덧셈           |
|   -    |          뺄셈           |
|   *    |          곱셈           |
|   /    |         나눗셈          |
|   //   |       나눗셈의 몫       |
|   %    | 모듈로(나눗셈의 나머지) |
|   **   |       지수 연산자       |
|  +var  |       단항 연산자       |
|  -var  |        단항 뺄셈        |



## 수학내장 함수

---

| 기능              | 설명                                                        |
| ----------------- | ----------------------------------------------------------- |
| abs(var)          | 절대값                                                      |
| pow(x, y)         | ** 연산자 대신에 사용 가능                                  |
| pow(x, y, modulo) | 삼항 지수-나머지(x**y)%modulo                               |
| round(var[,n])    | 10-n 또는 (10**-n)의 반올림한 근사치를 반환. n의 기본값은 0 |
| divmod(x, y)      | 나눗셈의 몫과 나머지로 이루어진 튜플을 반환                 |



## 시퀀스

---

* 시퀸스 자료형
  * 어떤 객체가 순서를 가지고 나열되어 있는 것을 말한다.
  * 문자열, 리스트, 튜플이 있다.
  * 문자열은 문자나 기호들이 순서대로 나열되어 있는 시퀀스 자료형이다.
  * 리스트는 임의의 객체가 순서대로 나열되어 있는 스퀀스 자료형이다.
  * 튜플은 리스트와 마찬가지로 값을 변경할 수 없는 임의의 객체가 나열되어 있는 시퀀스 자료형이다.
* 스퀀스 슬라이싱
  * 스퀀스 자료형에서 일정범위에 해당하는 부분을 취하는 방법
  * [시작인덱싱 : 끝인덱싱 : 스텝(간격)]
  * [m : n] m 이상 n 미만
  * [ : n] 처음부터  n 미만
  * [m : ] m부터 끝까지
  * [: -n] 처음부터 끝에서 n 번째 미만인 요소까지
  * [-m : ]자료의 끝에서  m번째 요소부터 시퀀스 자료의 끝까지
* 시퀀스 자료 연결 (+)
  * 자교형이 **동일한** 두개의 시퀀스 자료를 "+" 연산자로 순서있게 연결하여 새로운 시퀀스 자료로 만들 수 있다.
* 시퀀스 자료의 반복(*) 및 자료의 크기, 멤버체크 in
  * 동일한 시퀀스 자료를 반복하여 새로운 자료를 만들고자 하면 * 연산자 사용
  * len() 함수를 이용하면 시퀀스 자료의 크기를 알 수 있다.
  * in 은 자료에 어떤 값이 있는지 없는지 확인할 수 있다.



## 데이터 구조

---

**데이터 타입의 가변형 vs 불변형**

* 가변형은 변경이 가능한 데이터의 성질을 의미하고, 불변형은 변경이 불가능한 데이터 성질을 의미한다.
* **list, dict, set**은 가변형이고, **str과 tuple**은 불변형이다.
* 변혀은 데이터 추가, 삭제, 수정이 가능한 메서드를 가지고 있다.

**데이터 구조 list, tuple, set, Dictionary**

* 데이터 구조란?
  데이터를 활용 방식에 따라 조금 더 효율적으로 이용할 수 있도록 컴퓨터에 저장하는 여러 방법들
* Python의 데이터 구조는 list, tuple, set, Dictionary

   (1) list

* 파이썬 프로그래밍 언어 내에서 가장 많이 쓰이는 구조
* 목록은 어떠한 파이썬 자료형이라도 저장할 수 있다.
  * append : 목록에 값을 추가
  * extend : 다른 목록을 기존 목록에 추가 
    ex) new_list.extend(new_list2)
  * insert : 특정 위치에 값을 삽입
    ex) new_list.insert(2,'c')
  * pop(index) : index에 있는 값을 제거하고 return 해줌
  * remove(index) : index에 있는 값을 제거하고 return 하지 않음.

   (2) tuple

* 변경할 수 없는 list 형
* 서로 다른 종류의 데이터형으로 이루어진 항목들을 바로 풀었는 언패킹 또는 색인을 매기는 용도로 사용
* ()기호로 감싸거나 아예 감싸지 않는 방법으로 선언한다.
  ex) t2 = [1,2,3], [4,5,6]
  언패킹 ex) movie='슈퍼맨',1234,'배트맨',4321
  a,b,c,d = movide

   (3) set

* 색인에 대한 순서가 없고 중복이 허용되지 않는 데이터들의 조합
* set() 함수로만 set 생성이 가능하다.
  ex) myset = set([1,2,3,4,5])

   (4) Dictionary

* 전체항목이 정렬되지 않은 키와 값의 쌍으로 구성된 집합
* 순서가 없는 집합이다.
* key와 value값으로 저장된다. **{}**를 이용하여 생성한다.
* 요소를 참조할때는 **[]**를 사용한다.
