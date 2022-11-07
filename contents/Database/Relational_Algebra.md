# 관계 대수
릴레이션을 처리하기 위해 연산자와 연산규칙을 제공하는 언어
- 순수 관계 연산자: SELECT, PROJECT, JOIN, DIVISION
- 일반 집합 연산자: UNION(합집합), INTERSECTION(교집합), DIFFERENCE(차집합), CARTESIAN PRODUCT(교차곱)

## 순수 관계 연산자
- Select: 릴레이션에 존재하는 튜플 중에서 선택 조건을 만족하는 튜플의 부분집합을 구하여 새로운 릴레이션을 만듦.
- Project: 릴레이션에서 속성 List에서 제시된 속성만 추출
- Join: 공통 속성을 중심으로 두 개 의 릴레이션을 하나로 합쳐서 새로운 릴레이션으로 만듦
  - 세타조인<br/> 
   : 세타(θ)는 비교연산자{=,≠,≥,≤,>,<} 중의 하나로 세타 조인은 비교 연산자를 이용해 다양한 조건을 표현<br/>
     두 릴레이션의 기본키와 외래키 관계에 해당되는 속성들이 세타 조인 조건을 만족하는 투플들을 골라낸다.
  - 동등조인<br/>
   : 세타 연산자가 비교 연산자(=)인 세타 조인을 말한다.
  - 자연조인<br/> 
   : 동등 조인의 결과 두 릴레이션에서 공통으로 사용되는 중복되는 키 속성 중 하나를 제외한 것이다.
  - 세미조인<br/>
   : 자연조인을 한 후 두 릴레이션 중 한쪽 릴레이션의 결과만 반환한다.
- Division: X⊃Y 인 릴레이션 R(X)와 S(Y)가 있을 때, R의 속성이 S의 속성값을 모두 가진 튜플에서 S가 가진 속성을을 제외한 속성만 구함
<div>
<img src="https://user-images.githubusercontent.com/76613385/200225410-46e5cb73-a9a1-407d-a18d-d160b7eac6ac.png" width="150" heigth="400">
<img src="https://user-images.githubusercontent.com/76613385/200228168-0cd345a7-512e-4a4c-bc82-4116921d862b.png" width="80%" >
</div>

![image](https://user-images.githubusercontent.com/76613385/200217265-13bfde0b-df5b-4e5a-92a9-715239fa1db0.png)
  
  ## 일반 집합 연산자
  수학적 집합 이론에서 사용하는 연산자, 일반 집합 연산자 중 합집합, 교집합, 차집합은 합병 조건이 가능해야 한다.
  - 합병 조건<br/>
   : 합병하려는 두 릴레이션 간에 애트리뷰트의 수가 같고, 각 애트리뷰트가 취할 수 있는 도메인의 범위가 같아야 한다.<br/>

#### 연산의 특징
- 합집합(UNION, ∪): 두 릴레이션에 존재하는 튜플의 합집합을 구하고 중복되는 튜플은 제거<br/>
```
                         R∪S ={t | t ∈ R ∨ t ∈ S} |R∪S| ≤ |R|+|S|   *t는 R또는 S에 존재하는 튜플
```
  - 교집합(INTERSECION, ∩): 두 릴레이션에 존재하는 튜플의 교집합을 구함<br/>
```
                         R ∩ S ={t | t ∈ R ∧ t ∈ S} |R ∩ S| ≤ min(|R|,|S|)  *t는 R과 S에 동시에 존재하는 튜플
```
  - 차집합(DIFFERENCE, －): 두 릴레이션에 존재하는 튜플의 차집합을 구함<br/>
```
                         R－S ={t | t ∈ R ∧ t !∈ S} |R－S|≤|R|   *t는 R에 존재하고 S에는 없는 튜플
```
  - 교차곱(CARTESIAN PRODUCT, × ): 두 릴레이션에 존재하는 튜플의 순서쌍을 구함<br/>
```
                         R × S ={ r·s | r ∈ R ∧ s ∈ S} |R × S|≤|R| × |S|   *r은 R에 존재하는 튜플, s는 S에 존재하는 튜플
```
![image](https://user-images.githubusercontent.com/76613385/200228006-435574d7-94ab-45d4-b081-82950e122ec0.png)

### 연산자 우선순위
> (높음) PROJECT > SELECT > CARTESIAN PRODUCT > JOIN / DIVISION >  DIFFERENCE > UNION / INTERSECION (낮음)
