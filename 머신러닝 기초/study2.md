8. 머신러닝 학습 유형
8.1 지도학습 (Supervised Learning)
- 정답이 있는 데이터를 이용하여 학습
- 금융, 의료, 마케팅 등 신뢰할 수 있는 데이터 확보가 중요
- 정답이 없는 경우 직접 정답을 입력하는 Labeling 작업 필요
Labeling 방법:
- 외부 업체 의뢰
- 아웃소싱
- 생성형 AI 활용
8.2 비지도학습 (Unsupervised Learning)
정답이 없는 상태에서 데이터의 패턴을 찾아 그룹으로 나누는 학습 방식이다.

활용 분야:
- 군집화 (Clustering)
- 차원 축소 (Dimensionality Reduction)
- 고차원 데이터 시각화
- 이상치 탐색 (금융 사기 탐지 등)
8.3 준지도학습 (Semi-supervised Learning)
- 일부 데이터에는 정답이 포함되어 있음
- 나머지 데이터에는 정답이 없는 상태
8.4 강화학습 (Reinforcement Learning)
- 정답 대신 보상을 제공
- 누적 보상을 최대화하는 방향으로 학습
- 별도의 영역으로 기본 개념을 이해하는 수준

9. Scikit-Learn
9.1 개념
- 파이썬 머신러닝 라이브러리
- 머신러닝의 전처리 및 모델 학습을 지원하는 프레임워크
설치 확인:
pip list | grep sklearn


9.2 3대 핵심 구성 요소
구성 요소	역할	핵심 메서드
Estimator (추정기)	모델 학습	fit()
Predictor (예측기)	결과 예측	predict()
Transformer (변환기)	데이터 변환	transform(), fit_transform()

Estimator - 학습 단계
model.fit(X_train, y_train)



- 학습용 데이터와 정답을 제공하여 모델을 학습시킴

Predictor - 예측 단계
y_pred = model.predict(X_test)



- 테스트 데이터를 입력하여 모델의 예측 결과를 생성
- y_pred: 모델이 예측한 결과를 저장하는 변수
Transformer - 변환 단계
X_transformed = transformer.fit_transform(X_train)



- 모델이 학습하기 좋은 형태로 데이터를 변환
9.3 분석 청사진
데이터 수집
    ↓
데이터 탐색 및 전처리
    ↓
모델 훈련
    ↓
모델 평가
    ↓
모델 튜닝
    └── 하이퍼파라미터 탐색 (GridSearchCV)



10. Matrix와 Vector
10.1 X (Features)
- 입력 특성 데이터
- Feature Matrix라고도 부름
- 일반적으로 2차원 구조
10.2 y (Target)
- 예측하고자 하는 정답 데이터
- Target 또는 Target Vector라고 부름
- 일반적으로 1차원 구조
10.3 모델 학습 및 예측
1) Train - 모델 생성 및 학습
model = LinearRegression()model.fit(X_train, y_train)



- 모델을 생성하고 학습 데이터를 제공
- 학습을 통해 가중치 등의 값을 결정
2) Predict - 예측 수행
y_pred = model.predict(X_test)



- 학습된 모델에 테스트 데이터를 입력
- 예측 결과를 생성
3) Evaluate - 성능 평가
mse = mean_squared_error(y_test, y_pred)



- 실제 정답과 모델 예측값을 비교
- 모델의 성능을 평가
10.4 평가 지표
모델 유형	평가 기준
분류 (Classification)	전체 데이터 중 얼마나 정확하게 맞혔는지
회귀 (Regression)	실제값과 예측값의 차이가 얼마나 되는지


11. 결측치 처리와 모델 분류
11.1 Missing Value (결측치)
데이터에 값이 비어 있는 상태이다.

대표적인 표현:
- NaN
- Null
- -
주의사항:
- 숫자 0이 실제 결측치를 의미하는 경우도 있음
- 데이터의 도메인 지식을 통해 확인해야 함
예시:
- 혈압 = 0
- 몸무게 = 0
11.2 모델 분류
- 회귀 모델: 숫자형 데이터 예측
- 범주형 모델: 범주형 데이터 분류

12. 머신러닝 데이터 전처리
12.1 기본 전처리 과정
1. 데이터 탐색 및 문제 진단
2. 중복 데이터 제거
3. 결측치 처리
4. 스케일 조정
5. 범주형 데이터 인코딩
6. 이상치 처리
7. 분포 변환 (로그 변환)
12.2 데이터 탐색 및 문제 진단
- 데이터의 특징과 문제점을 확인
- 어떤 모델을 사용할지 판단하는 과정
12.3 중복 데이터 제거
- 중복된 데이터 제거
- 중복으로 인해 데이터 유출과 비슷한 문제가 발생할 수 있음
12.4 결측치 처리
예시:

- 혈압이 0인 경우 실제 결측치인지 확인

SimpleImputer 클래스를 사용하여 결측치를 처리한다.
12.5 수치형 데이터 스케일 조정
각 특성의 값 범위를 비슷하게 만들어주는 작업이다.

MinMax Scaling
- 데이터를 일정 범위로 변환
- 일반적으로 0~1 사이의 값으로 변환
- MinMaxScaler 클래스 사용
from sklearn.preprocessing import MinMaxScalerscaler = MinMaxScaler()X_scaled = scaler.fit_transform(X)



Standard Scaling
- 평균 0, 표준편차 1인 표준화 방식
- StandardScaler 클래스 사용
from sklearn.preprocessing import StandardScalerscaler = StandardScaler()X_scaled = scaler.fit_transform(X)



주의사항
- 모든 모델에서 스케일링이 필요한 것은 아님
- 트리 계열 모델은 일반적으로 스케일링이 필요하지 않음
12.6 범주형 데이터 인코딩
머신러닝 모델은 대부분 문자열을 직접 처리할 수 없으므로 숫자형으로 변환해야 한다.

Label Encoding (레이블 인코딩)

문자열 범주를 정수로 변환한다.

예시:
원래 데이터	변환 데이터
정상	0
당뇨병	1

사용 방법:
- LabelEncoder
- replace()
- map()
One-Hot Encoding (원-핫 인코딩)

범주의 개수만큼 새로운 변수를 생성한다.

예시:
지역	서울	부산	제주
서울	1	0	0
부산	0	1	0
제주	0	0	1

사용 함수:
pd.get_dummies(df)



12.7 이상치 처리
데이터 분포에서 비정상적으로 떨어져 있는 값이다.

IQR을 이용한 통계적 이상치 기준
- Q1: 1사분위수
- Q3: 3사분위수
- IQR = Q3 - Q1
이상치 범위:
\[
Q1 - 1.5 \times IQR
\]

\[
Q3 + 1.5 \times IQR
\]

이 범위를 벗어나는 값을 이상치 후보로 판단한다.
- 도메인 지식을 통해 실제 이상치인지 확인해야 함
- 비지도학습에서는 IsolationForest 방식 활용
12.8 분포 변환 - 로그 변환
- 한쪽으로 치우친 우편향 데이터의 간격을 줄이는 방법
- 데이터 분포를 보다 대칭적인 형태로 변환하는 대표적인 전처리 기법

13. 회귀 (Regression)
연속적인 값을 예측하기 위한 모델링 방식이다.
- 좋은 성능: 실제 정답에 얼마나 근접하게 예측하는지
- regression, regressor라는 명칭이 있으면 일반적으로 회귀 모델
- 단, Logistic Regression은 이진 분류 모델로 사용됨
13.1 선형 회귀 모델
기본 수식:
\[
y = wx + b
\]

기호	의미
x	입력값 (Feature)
w	가중치 (Weight), 직선의 기울기
b	편향 (Bias), 직선의 절편
y	모델의 예측값

- 입력값을 이용하여 연속적인 수치를 예측하는 모델
13.2 손실 함수 (Loss Function)
- 실제값과 예측값의 차이를 계산
- 손실값을 최소화하는 방향으로 모델의 파라미터를 조정
RSS (Residual Sum of Squares)

잔차 제곱합
\[
RSS = \sum (y_i - \hat{y}_i)^2
\]

- \(y_i\): 실제값
- \(\hat{y}_i\): 예측값
오차를 제곱하는 이유:
- 양수와 음수 오차가 서로 상쇄되는 현상 방지
- 큰 오차에 더 큰 패널티 부여
다중공선성 주의
- 독립 변수끼리 상관관계가 지나치게 높은 경우
- 모델의 계수 추정이 불안정해질 수 있음
13.3 회귀 모델의 성능 평가 지표
지표	정식 명칭	의미
MSE	Mean Squared Error	평균 제곱 오차
RMSE	Root Mean Squared Error	평균 제곱근 오차
MAE	Mean Absolute Error	평균 절대 오차
MAPE	Mean Absolute Percentage Error	평균 절대 백분율 오차
RMSLE	Root Mean Squared Logarithmic Error	평균 제곱 로그 오차의 제곱근
R²	R-squared	결정 계수

MSE

실제값과 예측값의 차이를 제곱하여 평균을 구한다.
mse = mean_squared_error(y_test, y_preds)



RMSE

MSE에 제곱근을 적용한다.
mse = mean_squared_error(y_test, y_preds)rmse = np.sqrt(mse)



MAE

실제값과 예측값의 차이를 절대값으로 변환한 뒤 평균을 계산한다.

MAPE

오차를 실제값으로 나눈 백분율 오차의 절대값 평균이다.
mape = mean_absolute_percentage_error(y_test, y_pred)



- 실제값이 0이면 분모가 0이 되므로 계산에 주의해야 함

RMSLE

실제값과 예측값에 로그를 적용하여 오차를 계산하는 방식이다.

- 음수 값이 있으면 계산에 주의해야 함

R² (결정 계수)

모델이 데이터의 변동성을 얼마나 설명하는지 나타낸다.
R² 값	의미
1	데이터의 변동성을 완벽하게 설명
0	평균값으로 예측하는 것과 동일한 수준
0 미만	평균값으로 예측하는 것보다 성능이 나쁨

r2 = r2_score(y_test, y_pred)



주의사항:
- Feature가 많아질수록 R² 값이 증가할 수 있음
- 따라서 R²만으로 모델의 신뢰도를 판단하기 어려움
Adjusted R² (수정된 결정 계수)

독립 변수의 개수를 고려하여 조정한 결정 계수이다.
\[
Adjusted\ R^2 =
1 - (1-R^2)\frac{n-1}{n-p-1}
\]

- n: 데이터 개수
- p: 독립 변수 개수