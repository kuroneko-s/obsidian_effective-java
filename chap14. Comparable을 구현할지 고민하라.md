나보다 작으면 양수
같으면 0
나보다 크면 음수


compareTo => 동치성 비교 + 순서 + 제네릭

Comparable을 구현했으면 해당 객체는 순서가 있는 개체임을 알려줌.

다른 객체들의 sort같은 기능들을 사용해서 정렬할 수 있게 해줌.
만약에 구현체가 없으면 기본 구현체가 있는지 확인하고 그래도 없으면 Cast 실패 에러가 나옴.

기본적인 규약은 equals와 동일함. (의미가 같다는 뜻)

- a.compareTo(a) == 0 (같음)
- x.compareTo(y) 와 y.compareTo(x)는 상반된 값을 나타내야함. 같을때 빼고
- 추이성. x.compareTo(y) > 0 (x가 더 크고) y. compareTo(z) > 0 (y가 더 크면) x.compareTo(z) > 0 (x가 더 커야함.)
- x.compareTo(y) == 0 (서로가 같으면), x.equals(y) == true 이면 좋다~. 이건 권고 사항인데 만약 서로 다르면 주석으로 명시를 해줘야함. 
	- (BigDecimal에서 equals에 주석으로 명시되어있음 2.0과 2.00은 서로 같지 않다고. compareTo로 비교하면 서로 같은 값이라고 인식함.)

이 인터페이스를 구현하면 정렬 컬렉션이나 검색, 정렬 알고리즘 객체 (Collections, Array) 같은곳에서 쓰기 편해짐.

equals로 비교하는게 같냐는게 중요하긴 한게 순서를 보장해주는 Collection같은 곳에서 동치성 비교를 equals를 안쓰고 compareTo를 사용한다고 함.

> Treeset은 진짜로 compareTo로 동치성 비교하고 있음..


옛날에는 정수타입을 <> 이거로 비교하라고 추천했는데 자바 7부터는 박싱 파입들의 compare을 쓰라고 추천하고 있음.

필드가 여러개면 핵심적인 필드를 우선적으로 비교를 해야함. 

값을 계산해서 넘겨줄때 서로의 차이를 계산해서 넘겨주면 언더플로우 에러 날수도 있음.  부등호로 비교하거나 이미 정의되어있는 메서드를 사용하는게 안전함.