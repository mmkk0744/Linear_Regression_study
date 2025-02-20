# 선형회귀 스터디

## 1. 상관계수
<img src="https://github.com/user-attachments/assets/56d7188a-8c9b-4058-979b-71f32e557b7e" width="800">

-1 ≤ r ≤ 1의 범위로 두 변수의 상관성을 표현함.

### 1.1 인과성과 상관성

- 아이스크림 판매량과 모기 개체수 상관관계가 1에 가깝다! (아이스크림 1개 팔릴 때 마다 모기 개체수도 1씩 오른다.)
- ❌ 상관성만 있을뿐, 인과성은 없다.
<img width="323" alt="Image" src="https://github.com/user-attachments/assets/efd777a3-09bb-457b-a60d-89fc18d28962" />

### 1.2 상관계수에 대한 오해
- 상관계수가 두 연속형 변수의 상관성을 나타내는 수치인 것은 맞다.
- 하지만, 상관계수 낮다 - > 둘은 상관성이 없다. 라는 논리는 위험하다.
- 상관계수 높다. > 상관성이 있다. 라는 논리도 위험하다.

## 2. 선형 회귀
- 독립변수가 변화할 때 종속변수가 얼마나 변하는지를 나타내기 때문에 선형회귀로 인과성을 도출할 수 있다고 하지만,
- 사실 이건 틀린말로 인과성을 도출하기 위해서는 더 깊은 연구가 필요하다.

<div style="display: flex; align-items: center;">
  <img width="400" alt="Image" src="https://github.com/user-attachments/assets/520c6ab3-73bc-4b72-a6fb-596c7e0b028c" />
  <img width="410" alt="Image" src="https://github.com/user-attachments/assets/d08f61bf-871b-4e59-9e58-399841ddf6dc" />
</div>

- 예측: 모든 모델링의 공통 목적
- 설명력: 머신러닝의 단점은 블랙박스, 모델에 대한 설명력이 명확하지 않음. 선형 회귀와 같은 통계 모델은 설명력이 뛰어난편

## 2.2 모형식

- 독립변수 X 종속변수 Y
  - 공부 시간(X1) 을 늘릴 수록 성적(Y)이 잘나온다
  - 지각(X2)이 많을 수록 성적(Y)이 안나온다.
    - 이처럼 독립변수 X는 `독립적으로` 값이 변하지만, 종속변수 Y는 x의 값에 의해서 `종속적으로` 바뀌기 때문에 종속변수라고 한다.
   
## 2.3 회귀분석에서 가정 사항 
<img width="511" alt="Image" src="https://github.com/user-attachments/assets/7a2c75c1-815d-4c42-adc7-2ba9224c13c7" />

- 선형성은 데이터 분포에 대한 가정, 나머지 3가지는 오차항에 대한 가정

### 2.3.1 선형성

: 종속변수  Y는 독립변수 X에 대하여 선형적인 관계를 갖는다.

- 데이터 분포에 대한 가정

### 2.3.2 독립성 (오차항)

: 오차는 랜덤 변수로서, 독립적이며 동일하게 분포하는 확률분포다. ( iid )

- 즉, 오차에 경향성이 있으면 안된다.
    1. 중요한 변수가 누락된 경우 
        
        : 중요 변수가 누락된다는 것은 중요한 변수가 독립변수가 아닌 오차항에 존재하는 것. 그로 인해 오차항에 경향성이 생긴다.
       <img width="323" alt="Image" src="https://github.com/user-attachments/assets/ebdfe9ea-01fd-4a23-b435-26d7747962d0" />
   2. 시계열 데이터를 사용하는 경우 (시계열 데이터로 선형회귀를 적용한다는 것은 가정 자체가 틀린것. ex) 부산으로 해외 여행)
   3. 비선형 자료에 대해 선형 회귀 적용하는 경우

   4.  다중공선성이 있는 경우 (오차에 편향이 생김_ 수식적인 이해 필요)

### 2.3.3 정규성 (오차항)

- 오차는 모두 평균이 0이고, 분산이 동일한 정규분포이다.
- 정규성 가정이 성립하지 않는다면
    - F-test를 통한 회귀 모형식에 대한 검정이 불가능, (f 통계량이 카이제곱통계량으로 이루어져있는데, 카이제곱은 정규성을 가정하기 때문)
 
### 2.3.4 등분산성 (오차항)
<img width="500" alt="Image" src="https://github.com/user-attachments/assets/8b55ed26-60e4-420c-95cb-2d4616c0ccd0" />

## 2.4 회귀 모형 도출: 최소제곱법 OLS
<img width="450" alt="Image" src="https://github.com/user-attachments/assets/745326ca-6196-4920-a9db-3046980d9df3" />

- 실제값 - 예측값(모델) 제곱합을 최소화하는 회귀 직선을 만들자 !
    - 이는 오차를 최소화하겠다는 개념으로 ML개념에서도 통하는 개념 >> 경사하강법, 손실함수
      
w도출과정: 편미분

<img width="525" alt="Image" src="https://github.com/user-attachments/assets/e08b1127-45d3-4b62-b359-63246329e145" />

<img src="https://github.com/user-attachments/assets/aa427502-0860-41ea-8ed4-988fbceda3aa" width="500">  

<img width="521" alt="Image" src="https://github.com/user-attachments/assets/d66f84a9-d865-4fc0-8252-18c18741cd00" />

: 최소제곱법을 통해 오차가 가장 적은 빨간 회귀선이 선형회귀 모델로 선정되는 것.

## 3. 헷갈리는 개념: 오차와 잔차 ?

### 3.1 모집단과 표본
![Image](https://github.com/user-attachments/assets/1149f89b-0a53-44b2-9b06-06df5b874548)

- 통계학: 모집단에서 표본 추출 >  표본으로 모집단을 추정

<img width="493" alt="Image" src="https://github.com/user-attachments/assets/b13b69eb-ba7d-4ee1-ab9a-54b9e5501367" />

- 잔차(residual)는 표본(sample)으로 추정한 회귀식과 실제 관측값의 차이
    - 잔차가 최소가 되는 회귀 직선 찾고
    - 잔차가 얼마나 작은지 평가지표로 활용
    - 잔차의 합은 0이됨
 
<img width="600" alt="Image" src="https://github.com/user-attachments/assets/8eff6fb1-6454-41bf-a8e4-c6619e82101c" />

- 오차(error)는 모집단(population)으로부터 추정한 회귀식으로부터 얻은 예측값과 실제 관측값의 차이
    - 우리는 모집단을 알 수 없음. 그 합도 알 수 없음 (모집단에서 표본을 추출한 것이기 때문)

<img width="600" alt="Image" src="https://github.com/user-attachments/assets/61c476af-6e06-4a90-aa7f-5873252672b9" />
