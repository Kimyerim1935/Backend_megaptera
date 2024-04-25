## ✔️ 키워드 정리

### Database 란

[Database](https://aws.amazon.com/ko/what-is/database/)는 전자적으로 저장되고 체계적인 데이터 모음이다. 단어, 숫자, 이미지, 비디오를 포함한 모든 유형의 데이터가 포함될 수 있다.

Database는 일반적으로 DBMS에 의해 제어된다. 연결된 애플리케이션과 함께 데이터와 DBMS를 하나로 묶어 데이터베이스 시스템이라고 하며, 단축하여 Database라고도 한다.

### DBMS(Database Management System)

[DBMS](https://ko.wikipedia.org/wiki/%EB%8D%B0%EC%9D%B4%ED%84%B0%EB%B2%A0%EC%9D%B4%EC%8A%A4_%EA%B4%80%EB%A6%AC_%EC%8B%9C%EC%8A%A4%ED%85%9C)는 다수의 사용자들이 데이터베이스 내의 데이터를 접근할 수 있도록 해주는 소프트웨어 도구의 집합이다. DBMS는 사용자 또는 응용 소프트웨어의 요구를 처리하고 적절히 응답하여 데이터를 사용할 수 있게 해준다.

DBMS는 계층형(Hierarchical), 망형(Network), 관계형(Relational), 객체지향형(Object-Oriented), 객체관계형(Object-Relational)으로 분류되며, 현재는 관계형 DBMS가 가장 많은 부분을 차지하고 있다.


계층형 DBMS는 처음으로 등장한 DBMS 개념으로 1960년대에 시작되었다. 각 계층은 트리 형태를 갖고 있으며 처음 구성을 완료한 뒤에 수정하기가 까다롭다는 단점이 있다. 지금은 거의 사용하지 않는다.

망형 DBMS는 계층형 DBMS의 문제점을 개선하기 위해 1970년대에 등장했다. 트리 최하위층에 있는 구성원들끼리도 연결되어 유연하다는 장점이 있지만 프로그래머가 모든 구조를 이해해야만 프로그램 작성이 가능하다는 단점이 있기 때문에 계층형 DBMS와 마찬가지로 지금은 거의 사용하지 않는다.

관계형 DBMS는 줄여서 RDBMS라고 불리며, 대부분의 DBMS가 RDBMS 형태로 사용된다. RDBMS의 데이터베이스는 테이블이라는 최소 단위로 구성되며, 이 테이블은 하나 이상의 열(column)과 행(row)으로 이루어져있다.<br/>
RDBMS에서는 모든 데이터가 테이블에 저장된다.

### RDBMS(Relational Database Management System)

관계형 모델은 각 행을 식별하는 고유 키를 사용하여 데이터를 열과 행으로 구성된 하나 이상의 테이블로 구성한다. 행은 레코드 또는 튜플이라고 하며, 열은 속성이라고도 한다.

테이블의 각 행에는 고유한 키가 있다. 연결 된 행의 고유 키에 대한 열(외래키)를 추가하여 테이블의 행을 다른 테이블의 행에 연결할 수 있다.

데이터베이스 내의 기본 키는 테이블 간의 관계를 정의하는 데 사용된다. 

### 데이터베이스 언어 (DDL, DML, DCL)

DDL(Data Definition Language)는 테이블과 같은 데이터 구조를 정의하는데 사용되는 명령어들로 데이터 구조와 관련된 명령어들을 말한다. 

- CREATE(생성)
- ALTER(객체 구조 수정(컬럼 추가/수정/삭제, 제약조건 추가/삭제, 테이블/컬럼/제약조건명 수정))
- DROP(객체 삭제)
- RENAME(테이블명 변경)
- TURNCATE(테이블의 열은 남겨두고 모든 행 제거)

DML(Data Manipulation Language)는 사용자 데이터 처리 도구로, 사용자와 DBMS간 인터페이스를 제공한다.

- SELECT
- INSERT
- UPDATE
- DELETE

DCL(Data Control Language)는 데이터 무결성, 보안, 권한 제어, 회복 등 수행하기 위한 DBMS 제어 수행 언어이다.

데이터베이스에 접근하고 객체들을 사용하도록 권한을 주고 회수하는 명령어들을 말한다.

- GRANT
- REVOKE

### SQL

[SQL](https://ko.wikipedia.org/wiki/SQL)은 관계형 데이터베이스 관리 시스템의 데이터를 관리하기 위해 설계한 특수 목적의 프로그래밍 언어이다. 관계형 데이터베이스 관리 시스템에서 자료의 검색과 관리, 데이터베이스 스키마 생성과 수정, 데이터베이스 객체 접근 조정 관리를 위해 고안되었다.

SQL을 통해 데이터베이스에서 원하는 정보를 추출하고, 데이터의 흐름이나 특정 조건에 따른 데이터 분석을 할 수 있기 때문에 SQL을 사용하는 기업들이 늘어나고 있다.

### 데이터 모델(Data Model)

[데이터모델](https://ko.wikipedia.org/wiki/%EB%8D%B0%EC%9D%B4%ED%84%B0_%EB%AA%A8%EB%8D%B8)은 데이터의 관계, 접근과 그 흐름에 필요한 처리 과정에 관한 추상화된 모형이다. 데이터 모델은 데이터 구조를 결정한다. 데이터 모델은 자주 그래픽 형태로 설명되는 데이터 모델링 개념에 정의되어 있다.

데이터 모델의 주요 목적은 데이터의 정의와 형식을 제공하여 정보 시스템 개발을 지원하는 것이다.

데이터 모델 인스턴스는 3가지 종류 중 하나일 수 있다.

1. 개념적 데이터 모델
: 모델의 범위인 도메인의 의미를 설명한다. 개념적 스키마는 모델을 사용하여 표현될 수 있는 사실이나 명제의 종류를 지정한다.

2. 논리적 데이터 모델
: 특정 데이터 조작 기술로 표현되는 의미론을 설명한다.

3. 물리적 데이터 모델
: 데이터가 저장되는 물리적 수단을 설명한다.

✨ Reference
https://blog.naver.com/PostView.naver?blogId=imjys1201&logNo=220878934126&parentCategoryNo=&categoryNo=34&viewDate=&isShowPopularPosts=true&from=search<br/>
https://en.wikipedia.org/wiki/Data_model<br/>
https://www.oracle.com/kr/database/what-is-database/<br/>
https://aws.amazon.com/ko/what-is/database/