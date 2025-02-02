1. 관계형 데이터베이스(RDBMS)와 비관계형 데이터베이스(NoSQL)의 장단점 비교

- 관게형 데이터베이스는 속성과 값을 가진 테이블들이 서로 관계를 맺으며 존재하는 DBMS, 비관계형 데이터베이스는 테이블들이 서로 관계를 맺지 않는 DBMS입니다.  
RDBMS는 데이터에 대한 접근(분류, 정렬, 탐색, 업데이트 등의 작업시)이 빠름, SQL을 이용하므로 질의가 구조화됨, 작업이 완전함을 보장 등을 장점으로 갖고 있습니다. NoSQL은 데이터 간 관계를 정의하지 않고 정해진 스키마(DB를 구성하는 것을 정의한 메타데이터의 집합)가 없으므로 자유로운 형식을 갖고, 낮은 복잡도로 인한 대용량 데이터의 저장 및 처리가 가능합니다.  
단점을 알아보자면, RDBMS는 정해진 스키마에 따라 데이터를 다뤄야하고 데이터 처리에 대한 부하가 발생했을 시 처리가 어렵습니다. NoSQL은  키값에 대해서만 입출력을 지원하며, 정해진 스키마가 없음으로 인해 규격화되지 않은 데이터, 데이터의 업데이트에 있어 느린다는 단점이 있습니다.  
이 둘은 서로 장단점을 가지지만 비교를 통해 어느 DBMS가 더 좋다고 판단할 것이 아닌, 필요한 곳에 적절한 DBMS를 선정해 사용하는 능력이 필요해 보입니다.

2. 트랜잭션(transaction)이란 무엇인가요?

- 트랜잭션이란 데이터베이스의 상태를 변경(CRUD)시키기 위해 수행하는 작업 단위입니다.  
트랜잭션에는 원자성, 일관성, 독립성, 지속성이라는 특징들이 존재합니다. 먼저 '원자성'은 트랜잭션이 모두 DB에 반영되거나, 반영되지 않아야한다는 것을 뜻합니다. 이러한 원자성이 깨지는 것을 방지하기 위해 트랜잭션에는 Rollback이라는 연산이 존재합니다. '일관성'은 트랜잭션의 작업 처리 결과가 일관되어야한다는 것을 뜻합니다. 하나의 트랜잭션이 성공적으로 끝났고 데이터베이스가 일관성있는 상태에 있을 때, 트랜잭션의 성공적 종료를 알려주기 위해 Commit이라는 연산을 사용해줍니다. 이를 통해 트랜잭션이 로그에 저장되며, 후에 Rollback을 할 일이 생겼을 때 트랜잭션 단위의 Rollback이 가능하게 됩니다. '독립성'은 하나의 트랜잭션은 다른 트랜잭션에 관여할 수(끼어들 수) 없다는 것을 뜻합니다. 마지막으로 '지속성'은 트랜잭션이 성공적으로 완료되면 영구적으로 결과에 반영되어야 한다는 것을 뜻합니다.  
트랜잭션은 5가지의 상태에 있을 수 있는데, Active, Failed, Aborted, Partially Commited, Commited가 그 5가지 입니다. 'Active'는 트랜잭션이 현재 실행 중인 상태이며, 이때 다른 트랜잭션은 해당 트랜잭션에 끼어들 수 없습니다. 'Failed'는 트래잭션이 실행되다 오류가 발생해 중단된 상태로, 해당 트랜잭션은 Rollback 연산의 대상이 되겠고, Rollback을 수행한 트랜잭션은 'Aborted' 상태가 됩니다. 'Partially Commited'는 트랜잭션의 연산이 마지막까지 실행되었지만 Commit은 되지 않은 상태이고, 이 상태에서 Commit이 되면 트랜잭션은 'Comiited' 상태가 됩니다.

3. MySQL에서 조인(join)의 역할은 무엇인가요? 다양한 join의 방식에 대해 설명해주세요.

- 조인이란 두 개 이상의 테이블에서 가져온 레코드를 조합, 하나의 테이블이나 결과 집합으로 만들어내는 쿼리입니다.  
MySQL에서 조인의 종류는 INNER JOIN, LEFT OUTER JOIN, RIGHT OUTER JOIN, CROSS JOIN, SELF JOIN이 있습니다. 'INNER JOIN'은 MySQL에서 JOIN으로 쓰이며 JOIN - [AS - ] ON - [WHERE - ] 과 같이 사용됩니다. 두 개 이상의 테이블 모두에서 포함하는 레코드를 합쳐서 표현해주는, 집합으로 치자면 교집합과 같은 JOIN입니다. 'LEFT OUTER JOIN', 'RIGHT OUTER JOIN'은 MySQL에서 LEFT, RIGHT로 쓰이며 [LEFT | RIGHT]( OUTER JOIN) - [AS - ] ON - [WHERE - ]과 같이 사용됩니다. 식으로 나타내면 A LEFT JOIN B, A RIGHT JOIN B와 같이 나타낼 수 있으며 이때 집합으로 이해하자면 LEFT JOIN은 (A와 B의 교집합)과 A의 합집합, RIGHT JOIN은 (A와 B의 교집합)과 B의 합집합으로 볼 수 있습니다. 'CROSS JOIN'은 카티전 조인이라고도 하며 집합에서는 집합 곱의 개념입니다. MySQL에서는 CROSS JOIN - [ AS - ]과 같이 사용됩니다. 이는 너무 많은 레코드를 생성할 위험이 있으므로 많이 사용되지는 않는다고 합니다. 마지막으로 'SELF JOIN'은 같은 테이블에서 두 번 참조를 해야하는 경우에 사용됩니다. MySQL에서의 사용법은 한 태이블 안에서 INNER JOIN을 하는 것입니다. 한 테이블에 내에서 FROM - INNER JOIN - ON - WHERE - 과 같이 사용할 수 있습니다. 예를 들어 요리사 A의 분야가 중식일 때, 중식을 요리하는 다른 요리사의 컬럼 값을 참조하고자 사용합니다. 이 때 요리사 A의 요리분야 컬럼(중식)을 이용, 요리분야 컬럼을 참조하여 분야가 중식인 다른 요리사를 SELECT 해주면 됩니다.

4. MySQL에서 인덱스(index)란 무엇인가요?

- 인덱스란 테이블의 조회 속도를 높여주는 자료구조입니다. 인덱스를 이용하지 않는다면 테이블을 전체 조회하여 성능 저하나 장애 발생 가능성이 있지만, 인덱스를 이용하면 데이터의 위치를 빠르게 찾을 수 있습니다. 이는 MySQL Index파일인 MYI에 저장됩니다.  
인덱스는 하나의 컬럼을 사용하는 단일 컬럼 인덱스, 여러개의 컬럼을 사용하는 다중 컬럼 인덱스로 설정할 수 있습니다. 이를 좋은 방향으로 설계하는 방법으로는 무조건 많은 인덱스 설정 지양, 여러 개의 단일 인덱스 보다는 다중 컬럼 인덱스로 설계, 조회에 자주 사용되는 컬럼 위주, JOIN에 자주 사용되는 컬럼, 고유하고 변하지 않는 값 위주, 중복도의 정도가 낮은 값 위주, key의 크기는 되도록 작게, 가변적이지 않은 정수형 자료로 생성 등이 있습니다.  
인덱스도 단점이 존재하는데 CRUD 중 C, U, D의 속도가 저하된다는 것입니다. 이는 테이블의 인덱스 정보를 갱신하는 추가적인 비용이 발생하기 때문입니다.
