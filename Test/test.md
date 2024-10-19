## 테스트

개발된 응용 애플리케이션이나 시스템의 사용자가 요구하는 기능과 성능, 사용성, 안전성 등을 확인하고 노출되지 않은 숨어있는 결함을 찾아내는 활동이다.

과정 속 필요한 **역할** : 소프트웨어 아키텍트, 테스트 매니저

*소프트웨어 아키텍쳐 : 소프트웨어의 골격이 되는 구조

소프트웨어 생명주기 V모델에서 두 역할은 서로 보완 관계에 있다.

**소프트웨어 아키텍트**는 **요구사항 → 분석 → 디자인 → 구현or개발** 순으로 진행한다.

**테스트**는 **단위 테스트 → 통합 테스트 → 시스템 테스트 → 인수 테스트** 순으로 진행한다.

**V모델**
![테스트](https://github.com/jeongyeon0000/TIL/assets/153992648/578c8dcc-996c-47d2-b01d-df0f01ae1945)

### 테스트의 7가지 원칙

1. **계획단계부터 한다.** : 테스트 활동은 소프투웨어 개발 주기에서 가능한 초기부터 시작해야 한다.
2. **결함을 밝히는 활동이다.** :결함의 제거x 결함의 발견o, 결함이 없다는 것은 증명할 수 없다.
3. **완전한 테스트는 불가능하다.**:모든 것(입력 값, 경로, 타이밍)에 대한 테스팅은 자원의 한계
4. **테스트는 상황에 따라 다르다.**:동일한 테스트에 대한 비정상적인 결함 검수가 이루어질 수 있다.
5. **결함 집중을 고려한다.**:대부분 결함은 소수의 특정 모듈에 집중되어 발생하는 경향

*결함이 높은 곳에 자원이 집중되어 있다.(파레토 법칙)

6. **살충제 패러독스를 고려한다.**:동일한 테스트 케이스에 의한 반복적 테스트로 새로운 버그를 찾지 못하는 내성 현상
7. **오류 부재의 궤변을 고려한다.**:개발 제품이 사용자의 필요와 기대에 부응하지 못하고 쓸모가 없을 때

### 단위 테스트

**컴포넌트or모듈를 테스트**하는 것으로, 일반적으로 개발자에 의해 진행된다.

 과거에는 시간 부족의 이유로 생략되었으나, 최근에는 개발 도구의 발전으로 자동으로 진행되며,

개발 도구에서 지원하지 않더라도, **반드시 수행**해야한다.

구조적 /기능성/리소스 관련/강건성 테스트 등, **비기능성 테스트** 등이 포함되어 수행된다.

**컴포넌트 명세, 소프트웨어 상세 설계, 데이터 모델 명세 등을 이용**하여 테스트한다.

- **구조 기반** : 업무 단위별 **제어 흐름**과 **조건 결정**이 목적이다.
- **명세 기반** : 동등 분할과 경계값 분석이 목적으로, 사용자의 입출력과 내부 이벤트 등을 확인한다.

**화이트박스 테스트** : 개발자 관점, 구조 기반의 테스트이다.(**종류**:기초 경로/제어 흐름/조건/루프/데이터 흐름/분기 테스트)

**블랙박스 테스트** : 사용자 관점, 명세 기반의 테스트이다.(**종류** : 균등 분할/한계값/원인 효과 그래프/비교 테스트)

### 통합 테스트

모듈 사이의 인터페이스, 통합된 컴포넌트 간의 상호작용을 테스트하는 것으로, 하나의 프로세스를 완성 후 부분적으로 수행하는 경우가 있다.

일반적으로 빅뱅 방식보다는 순차적 형태와 아키택처에 대한 이해를 바탕으로 진행한다.

**종류**
|구분|빅뱅|상향식|하향식|
|--|---|---|---|
|수행 방법|모든 모듈을 동시에 통합 후 수행|최하위 모듈부터 점진적으로 상위 모듈과 함께 수행|최상위 모듈부터 하위 모듈들을 통합하며 수행|
|더미 모듈|x|드라이버|스텁|
|장점|단시간 테스트 가능, 작은 시스템에 유리|장애 위치 파악 쉬움, 모듈 개발 시간 낭비 없음|장애 위치 파악 쉬움, 이른 프로토타입 가능, 중요 모듈의 선 테스트 기능, 결함 조기 발견 가능|
|단점|장애 위치 파악 어려움, 모든 모듈 개발|이른 프로토타입 어려움, 중요 모듈이 마지막으로 테스트될 가능성이 높음|많은 스텁이 필요, 하위 모듈들의 불충분한 테스트 수행|


드라이버 : 상향식 테스트 방식의 존재하지 않는 상위 모듈 간의 인터페이스 역할

스텁 : 하향식 테스트 방식의 작성이 쉬운 시험용 모듈
### 시스템 테스트

통합된 단위 **시스템의 기능이 정상적으로 수행**되는지 테스트하는 것으로, 성능 및 장애 테스트가 이에 포함된다.

**환경 제한적 장애 관련 리스크 최소화를 위해** 실제 사용자 환경과 유사한 시스템 성능, 관련된 고객의 **기능/비기능적인 요구사항 등이 수행되었는지 체크**한다.

**요구사항 명세서, 비즈니스 절차, 유스케이스, 리스크 분석 결과 등을 이용**한다.

*유스케이스 : 시스템의 동작을 사용자의 입장에서 표현한 시나리오와 관련 요구사항을 알아내는 과정

**기능적 요구사항** : 명세서 기반의 블랙박스 테스트(비즈니스 절차, 유스케이스 등)

**바기능적 요구사항** : 구조적 요소에 대한 화이트 박스 테스트(성능 테스트, 회복 테스트 등)
### 인수 테스트

최종 사용자와 업무에 따른 이해관계자 등이 테스트를 수행하며 **개발된 제품에 대해 운영 여부를 결정**하는 테스트로, **실제 업무에 적용하기 전** 수행한다.

**종류**
- **사용자 인수 테스트** : 비즈니스 사용자가 시스템 사용의 적절성 여부 확인
- **운영상의 인수 테스트** : 시스템 관리자가 시스템 인수 시 수행하는 테스트 활동, 백업/복원
- **계약 인수 테스트** : 계약상의 인수/검수 조건을 준수하는지 확인
- **규정 인수 테스트** : 정부 지침, 범규, 규정 등 규정에 맞게 개발하였는지 확인
- **알파 테스트** : 개발하는 조직 내 잠재 고객에 의해 테스트 수행
- **베타 테스트** : 실제 환경에서 고객에 의해 테스트 수행
---
## 테스트 케이스
### 명세 기반 테스트의 설계 산출물이다.
- 특정 프로그램의 일부분 또는 경로에 따라 수행하거나, 특정 요구사항을 준수하는지 확인하기 위해 설계된 입력값, 실행 조건, 기대 결과로 구성된 테스트 항목의 명세서를 말한다.
- 미리 설계하여 오류를 방지할 수 있고 테스트 수행에 필요한 인력, 시간 등의 낭비를 축소할 수 있다.

**테스트 케이스 작성 절차**

계획 검토 및 참조 문서 수집 → 내부 검토 및 우선순위 결정 → 요구사항 정의 → 테스트 설계와 방법 결정 → 테스트 케이스 정의 → 테스트 케이스 타당성 확인 및 유지보수 → 테스트 수행
## 테스트 오라클
테스트의 결과가 참인지 거짓인지를 판단하기 위해 사전에 정의된 값을 입력해 비교하는 기법 및 활동을 말한다.
### 테스트 오라클 유형
- **참 오라클** : 모든 입력값의 기대 결과를 생서하여 발생된 오류를 모두 검출한다.
- **샘플링 오라클** : 특정한 입력값들에 대해서만 기대하는 결과를 제공한다.
- **휴라스틱(추정) 오라클** : 샘플링 오라클을 개선한 것으로 특정 입력값에 대해 올바른 결과를 제공하고 나머지 값들에 대해서는 휴라스틱(추정)으로 처리한다. 
- **일관성 검사 오라클** : 애플리케이션 변경이 있을 때, 수행 전과 후의 결과값이 동일한지 확인한다. 
---
## 테스트 자동화
### 사람이 하던 반복적 테스트 절차를 자동화 도구를 활용하여 하는 것이다.
- 준비, 구현, 수행, 분석 등을 스크립트 형태로 구현함으로써 테스트 시간과 인력 투입의 부담을 최소화할 수 있고, 휴먼에러를 줄일 수 있다.
- 운영 중인 시스템의 모니터링 또는 UI가 없는 서비스의 경우에도 정밀한 테스트가 가능하다.
### 테스트 도구의 장점
1. 테스트 데이터의 재입력과 재구성 같은 **반복 작업의 자동화를 통해 인력과 시간을 최소화** 한다.
2. 향상된 요구사항 정의, 성능 및 스트레스 테스트, 품질 측정을 최적화 한다.
3. 빌드 확인, 회귀, 다중 플랫폼 호환성, 소프트웨어 구성, 기본 테스트 등의 향상된 테스트 품질을 보장한다.
### 테스트 도구의 단점
1. 도입 후 테스트 도구 전문가 양성 또는 고용이 필요하다.
2. 초기에 프로세스 적용에 대한 시간, 비용, 노력에 대한 추가 투자가 필요하다.
3. 비공개 상용 소프트웨어의 경우, 고가이며 인력과 교육에 대한 유지관리 비용이 높다.
### 테스트 자동화 수행 시 고려사항
- 테스트 절차를고려해 재사용 및 측정 불가한 테스트 프로그램은 제외한다.
- 설계 기준을 고려해 반복적 빌드에서 스크립트 재사용성이 가능해야 한다.
- 도구의 한계성으로 모든 수동 테스트 과정을 자동화 할 수 있는 도구는 없기에, 용도에 적절한 도구를 사용해야 한다.
- 도구 환경 설정과 도구 습득 기간을 고려해 프로젝트 지연을 방지해야 한다.
- 테스트 엔지니어의 늦은 투입은 프로젝트의 이해 부족으로 불완전한 테스트를 방지하기 위해 프로젝트 초기에 적절한 투입 시기와 계획을 수립해야 한다.
### 테스트 도구의 평가 방법 및 요소
|테스트 활동|테스트 도구|내용|
|------|---|---|
|테스트 계획|요구사항 관리|고객의 요구사항 정의 및 변경 사항 관리|
|테스트 분석/설계|테스트 케이스 생성|테스트 기법에 따른 테스트 데이터 및 케이스 작성|
||커버리지 분석|대상 시스템에 대한 테스트 완료 범위의 척도|
|테스트 수행|테스트 자동화|기능 테스트등 테스트도구를 활용하여 자동화를통한 테스트의 효율성 제고|
||정적 분석|코딩 표준, 런타임 오류 등을 검증|
||동적 분석|대상 시스템 시뮬레이션을 통한 오류 검출|
||성능 테스트|가상 사용자를 인위적으로 생성하여 시스템 처리 능력 측정|
||모니터링|시스템 자원의 상태 확인 및 분석 지원 도구|
|테스트 통제|형상 관리|테스트 수행에 필요한 다양한도구 및 데이터 관리|
||테스트 관리|전반적인 테스트 계획 및 활동에 대한 관리|
||결함 추적/관리|테스트에서 발생한 결함 관리 및 협업 지원|