9. SVM (Support Vector Machine)
분류에서 최적의 결정 경계를 찾기 위한 머신러닝 알고리즘이다.
9.1 주요 개념
Support Vector

- 결정 경계와 가장 가까운 데이터 포인트

Hyperplane (초평면)

- 데이터를 구분하는 결정 경계

Margin (마진)

- 결정 경계와 양쪽 클래스의 가장 가까운 데이터 포인트 사이의 거리
9.2 SVC와 SVR
모델	용도	설명
SVC	분류	두 데이터 그룹 사이의 마진을 최대화하는 결정 경계 탐색
SVR	회귀	예측값이 허용 오차 범위 안에 있도록 회귀 함수 학습

9.3 커널 트릭 (Kernel Trick)
- 2차원에서 선형적으로 구분할 수 없는 데이터를 고차원 공간으로 매핑
- 고차원 공간에서 선형적으로 분리할 수 있도록 지원
주요 커널:
커널	특징
Linear	선형 결정 경계
RBF	비선형 데이터 분류에 활용되는 대표적인 커널


10. 앙상블 모델 (Ensemble Model)
여러 개의 모델을 결합하여 하나의 모델보다 더 나은 예측 성능을 얻는 방법이다.
10.1 Bagging (Bootstrap Aggregating)
- 복원 추출 방식으로 여러 데이터셋 생성
- 동일한 알고리즘의 모델을 독립적으로 학습
- 여러 모델의 예측 결과를 결합
복원 추출 (Bootstrap)
- 데이터를 추출한 후 다시 넣고 추출
- 중복된 데이터가 포함될 수 있음
진행 과정:
복원 추출
    ↓
여러 데이터셋 생성
    ↓
동일한 알고리즘으로 독립 학습
    ↓
예측 결과 결합
    ↓
최종 결과


- 분류: 다수결 투표
- 회귀: 예측값의 평균
- 동종 모델을 병렬로 결합
10.2 Random Forest
Bagging을 활용한 대표적인 앙상블 모델이다.

주요 특징:
- 여러 개의 의사결정 트리 사용
- Bootstrap을 통한 데이터 샘플링
- Feature를 무작위로 선택
- 행 방향과 열 방향으로 데이터를 다양하게 추출
- 모델 간 상관관계를 낮추어 일반화 성능 향상에 도움
분류 방식
- Hard Voting: 다수결 투표
- Soft Voting: 각 클래스의 예측 확률을 평균하여 결정
회귀 방식

- Averaging: 여러 트리의 예측값 평균

주요 하이퍼파라미터
파라미터	설명
n_estimators	생성할 트리 개수
criterion	분할 품질 평가 기준
max_depth	트리의 최대 깊이
max_features	각 노드에서 고려할 최대 특성 수
min_samples_split	노드를 분할하기 위한 최소 샘플 수
min_samples_leaf	리프 노드에 필요한 최소 샘플 수
random_state	난수 시드 고정

10.3 Extra Trees (Extremely Randomized Trees)
- 극도의 무작위성을 추가하는 앙상블 방식
- 무작위 분할 지점을 사용
- 분산을 줄이는 전략
- 편향이 소폭 증가할 수 있음
- 기본적으로 bootstrap=False
10.4 Boosting
- 여러 모델을 순차적으로 학습하는 방식
- 이전 모델의 오차를 다음 모델이 보완
- 동종 모델을 직렬로 결합
강의 예시: 오답노트를 작성한 뒤 다시 시험을 보는 방식

진행 과정
1. 첫 번째 모델이 전체 데이터 학습
2. 예측 결과 확인
3. 잘못 예측한 데이터에 가중치 부여
4. 다음 모델이 어려운 데이터를 중심으로 학습
5. 반복 학습 후 최종 예측
Boosting 모델의 발전
AdaBoost
    ↓
GBM
    ↓
XGBoost / LightGBM / CatBoost


10.5 Gradient Descent (경사 하강법)
- 손실 함수의 기울기(Gradient)를 이용하여 가중치를 조정
- 손실값이 작아지는 방향으로 최적의 파라미터 탐색
10.6 AdaBoost
- Adaptive Boosting
- 잘못 예측한 데이터 샘플의 가중치를 높임
- 다음 모델이 어려운 데이터에 집중하여 학습
- 반복 학습 후 최종 분류기 생성
10.7 Gradient Boosting
- 손실 함수를 계산하여 모델의 예측 오차를 줄이는 방식
- 이전 모델의 잔차를 보완하면서 최적의 예측값 탐색

11. GBM의 발전 모델
11.1 XGBoost
Extreme Gradient Boosting
- Gradient Boosting을 개선한 알고리즘
- 손실 함수에 L1/L2 정규화 적용
- 일부 병렬 처리로 시스템 최적화
- 트리 가지치기를 통해 모델 복잡도 제어
11.2 LightGBM
Light Gradient Boosting Machine
- Histogram 기반 알고리즘 사용
- 분기점 탐색 속도 개선
- 대용량 데이터셋을 빠르고 효율적으로 학습
기존 GBDT 방식
- 모든 Feature의 데이터 포인트를 탐색하여 최적의 분할 지점 계산
- 연산 병목 발생 가능
LightGBM의 주요 기법
1. GOSS (Gradient-based One-Side Sampling)
   - 기울기의 절대값이 큰 데이터에 집중
   - 기울기가 작은 데이터는 일부 무작위 샘플링
2. EFB (Exclusive Feature Bundling)
   - 희소한 Feature들을 묶어 Feature 개수를 줄이는 방식
11.3 CatBoost
Categorical Boosting
- 범주형 변수 처리에 특화된 알고리즘
- 범주형 데이터 처리 과정에서 발생할 수 있는 타겟 누수 문제를 줄이는 방식 활용
Greedy 방식

- 전체 데이터의 평균 정보를 활용

Ordered Target Statistics

- 현재 데이터보다 앞서 계산된 타겟 정보만 활용하여 타겟 통계량 계산
11.4 용어 사전
용어	설명
Epoch	전체 데이터를 한 번 학습하는 단위
OOM (Out of Memory)	메모리 공간 부족
Sparse	데이터가 듬성듬성 존재하는 상태
Dense	데이터가 밀집되어 있는 상태


12. 하이퍼파라미터 최적화 (HPO)
Hyperparameter Optimization

모델의 성능을 높이기 위해 최적의 하이퍼파라미터 조합을 탐색하는 과정이다.
12.1 수동 탐색 (Manual Search)
- 분석가가 직접 하이퍼파라미터 값을 변경하며 성능 확인
12.2 Grid Search
- 미리 지정한 하이퍼파라미터 후보 조합을 모두 탐색
- 최적의 조합을 찾는 방식
예시 파라미터:
- n_estimators
- max_depth
- min_samples_leaf
- learning_rate
단점:
- 후보값이 많아질수록 탐색 시간이 증가
- 차원이 증가할수록 탐색 조합이 급격히 증가
12.3 Random Search
- 지정한 최소값과 최대값 범위 내에서 무작위로 조합 선택
- n_iter로 탐색 횟수 지정
12.4 Optuna
- 하이퍼파라미터 최적화를 위한 프레임워크
- 베이지안 최적화 등의 탐색 전략 활용
진행 과정:
1. 목적 함수 정의
2. Study 생성 및 알고리즘 설정
3. 최적화 실행
4. 최적의 하이퍼파라미터 탐색
베이지안 최적화
- 과거 평가 결과를 활용
- 아직 평가하지 않은 하이퍼파라미터 조합 중 유망한 값을 선택

13. 스태킹 (Stacking)
서로 다른 종류의 모델을 결합하는 앙상블 방식이다.

진행 과정
입력 데이터
    ↓
모델 A     모델 B     모델 C
    ↓        ↓         ↓
각 모델의 예측값 생성
    ↓
메타 모델 (Meta Model)
    ↓
최종 예측 결과


- 서로 다른 모델의 예측 결과를 결합
- 메타 모델이 최종 예측 수행
단일 모델
- Estimators 또는 Learners는 앙상블을 구성하는 개별 모델을 의미

14. 설명 가능한 AI (Explainable AI, SHAP)
14.1 SHAP
- 게임 이론의 Shapley Value를 기반으로 하는 설명 기법
- 각 Feature가 모델 예측에 기여한 정도를 계산
- 모델의 예측 결과를 해석하는 데 활용
14.2 SHAP Explainer 선택
유형	적용 대상
Tree-based	트리 기반 모델
Deep Learning	딥러닝 모델
Any Black-Box Model	SVM, SVC, SVR 등 다양한 모델

14.3 Force Plot
- 각 Feature가 예측값을 높이거나 낮추는 방향으로 얼마나 기여했는지 시각화
- SHAP Value를 활용하여 예측 결과를 설명

15. 편향과 분산 (Bias-Variance Trade-off)
모델의 편향과 분산 사이의 균형을 의미한다.
- 하나를 줄이려 할 때 다른 하나가 증가할 수 있는 관계
- 두 요소 사이의 적절한 균형점을 찾는 것이 중요
15.1 Bias (편향)
- 실제 정답과 예측 중심 사이의 차이
- 편향이 높으면 과소적합 발생 가능
15.2 Variance (분산)
- 여러 학습 데이터에서 모델의 예측값이 얼마나 퍼지는지 나타냄
- 분산이 높으면 과적합 발생 가능
15.3 Sweet Spot
- 편향과 분산 사이의 적절한 균형점
- 일반화 성능이 좋은 모델을 만들기 위한 목표