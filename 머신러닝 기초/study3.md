14. 과적합 (Overfitting)
14.1 개념
- 학습이 아닌 암기에 가까운 상태
- 학습 데이터에 지나치게 최적화된 상태
- 새로운 데이터에서는 성능이 떨어질 수 있음
14.2 과적합 발생 이유
1. 데이터의 한계
   - 데이터 양 부족
   - 편향된 데이터
2. 데이터 내 노이즈
   - 잘못된 라벨
   - 측정 오류
   - 불필요한 값
3. 모델의 과도한 복잡성
14.3 편향과 분산
Bias (편향)
- 실제 정답과 모델이 예측한 값의 평균적인 차이
- 목표 지점과의 거리로 이해할 수 있음
Variance (분산)
- 학습 데이터가 바뀔 때 모델의 예측값이 얼마나 흔들리는지 나타냄
- 예측값의 퍼짐 정도로 이해할 수 있음
14.4 일반화 (Generalization)
어떤 새로운 데이터에서도 균일한 성능을 제공하도록 만드는 것이다.

해결 방법:
1. 모델 단순화
   - 불필요한 특성 제거
   - 의사결정나무의 최대 깊이 제한
   - 신경망의 레이어 및 노드 수 감소
2. 정규화 (Regularization)
   - 패널티를 부과하여 가중치가 지나치게 커지는 것을 방지
   - L1, L2 규제 활용
3. 데이터 스케일링
   - 특성들의 값 범위를 일치시킴
14.5 정규화의 대표적인 3가지 방식
L2 정규화 (Ridge Regression)
\[
Loss = Loss + \lambda \sum w^2
\]

- 가중치의 제곱을 패널티로 추가
- 전체 가중치를 줄이는 방향으로 작동
L1 정규화 (Lasso Regression)
\[
Loss = Loss + \lambda \sum |w|
\]

- 가중치의 절대값을 패널티로 추가
- 일부 가중치를 0으로 만들 수 있음
Elastic-Net Regression

- L1과 L2 정규화를 결합한 방식
방식	특징
Lasso	일부 가중치를 0으로 만들어 특성 제거 가능
Ridge	전체 가중치를 줄임
Elastic-Net	L1과 L2를 함께 사용


15. 분류 (Classification)
지도학습 방식으로 데이터를 범주별로 구분하는 과정이다.
- 이진 분류 (Binary Classification)
- 다중 분류 (Multi-class Classification)
15.1 이진 분류 심층 분석
계단 함수 (Unit Step Function)
- 0 또는 1로 결과를 결정
- 미분이 불가능
- 확신도나 확률 정보를 표현하기 어려움
시그모이드 함수 (Sigmoid Function)
- 전 구간에서 미분 가능
- 결과값이 0~1 사이
- 확률적으로 해석 가능
손실 함수

- BCE Loss (Binary Cross Entropy)
15.2 다중 분류 심층 분석
- 활성화 함수: Softmax
- 손실 함수: Cross-Entropy Loss
15.3 Scikit-Learn 분류 모델
- LogisticRegression을 활용
- 분류 모델은 Classifier 형태로 사용할 수 있음

16. 성능 평가의 함정
16.1 정확도의 한계
- 가장 직관적인 성능 평가 지표
- 데이터 불균형 상황에서는 성능이 왜곡될 수 있음
16.2 혼동 행렬 (Confusion Matrix)
모델의 실제 정답과 예측 결과를 비교하는 행렬이다.
구분	의미
TP (True Positive)	실제 Positive, 예측 Positive
TN (True Negative)	실제 Negative, 예측 Negative
FP (False Positive)	실제 Negative, 예측 Positive
FN (False Negative)	실제 Positive, 예측 Negative

Accuracy (정확도)
\[
Accuracy = \frac{TP+TN}{TP+TN+FP+FN}
\]

Precision (정밀도)
\[
Precision = \frac{TP}{TP+FP}
\]

- 모델이 Positive라고 예측한 것 중 실제 Positive의 비율
- 오탐이 중요한 경우 활용
Recall (재현율)
\[
Recall = \frac{TP}{TP+FN}
\]

- 실제 Positive 중 모델이 Positive로 예측한 비율
- 미탐이 중요한 경우 활용
Precision과 Recall의 트레이드오프

- 일반적으로 정밀도가 올라가면 재현율이 떨어지는 관계가 발생할 수 있음

F1-Score
\[
F1 = 2 \times
\frac{Precision \times Recall}
{Precision + Recall}
\]

- 정밀도와 재현율의 조화 평균
- 값이 높을수록 좋음

17. 데이터 불균형 다루기
17.1 문제점
- 소수 클래스의 데이터가 너무 적은 상태
- 모델이 다수 클래스에 편향될 수 있음
17.2 해결 전략
Under-sampling (언더샘플링)

- 다수 클래스 데이터를 제거하여 비율 조정

Over-sampling (오버샘플링)

- 소수 클래스 데이터를 증식하여 비율 조정

SMOTE

Synthetic Minority Over-sampling Technique
- 오버샘플링 방식 중 하나
- 가까운 이웃 데이터를 이용하여 새로운 합성 데이터를 생성
X_train_resampled, y_train_resampled = smote.fit_resample(    X_train,    y_train)




18. 추가 탐색: 다양한 분류 알고리즘
18.1 의사결정 트리 (Decision Tree)
데이터를 규칙 기반으로 분할하는 나무 구조의 모델이다.
용어	의미
Root	분석 시작점
Splitting	규칙에 따른 가지 분할
Parent / Child	부모 / 자식 노드
Leaf	최종 노드
Pruning	과적합 방지를 위한 가지치기
Depth	트리의 깊이

과적합 방지 방법:
- Depth 제한
- Leaf 제한
- Pruning 적용
18.2 서포트 벡터 머신 (SVM)
- 클래스 간 경계를 최대화하는 결정 경계를 찾는 모델
클래스	용도
SVC	분류
SVR	회귀

18.3 K-NN (K-Nearest Neighbors)
- 가장 가까운 이웃 데이터를 찾는 방식
- K개의 이웃 데이터 중 다수결로 분류
- SMOTE에서 합성 데이터를 생성할 때도 활용
18.4 나이브 베이즈 (Naive Bayes)
- 베이즈 정리를 기반으로 하는 분류 모델
- 자연어 처리 등의 분류에 활용
베이즈 정리

사전 확률과 우도를 이용하여 사후 확률을 추론하는 조건부 확률의 원리이다.
- 사전 확률: 데이터를 관찰하기 전의 확률
- 우도 (Likelihood): 특정 가설이 맞다고 가정했을 때 관찰한 데이터가 나타날 가능성
- 사후 확률: 데이터를 관찰한 후 갱신된 확률
18.5 NLG (Natural Language Generation)
자연어 생성 과정이다.
1. 단어가 주어짐
2. 다음에 올 단어의 확률 계산
3. 다음 단어 선택
4. 문장 완성
5. 다음 문장에 올 확률 계산
6. 반복하여 문장 생성

19. 최적의 질문을 찾는 기준
불순도 (Impurity)
- 데이터를 얼마나 서로 다른 범주가 섞여 있는 상태인지 나타내는 기준
- 불순도가 낮아지는 방향으로 학습 진행
불순도를 측정하는 대표적인 방법
- Gini Index (지니 지수)
- Entropy (엔트로피)

20. 추가 개념: RAG와 LLM
20.1 RAG (Retrieval Augmented Generation)
정보 검색 증강 생성형 AI
- 외부 정보를 검색하여 생성형 AI의 답변을 보완하는 기술
- AI가 필요한 정보를 검색할 수 있도록 지원
20.2 모델과 서비스의 차이
모델과 서비스는 서로 다른 개념이다.

예시:
- GPT-3.5: AI 모델
- ChatGPT: AI 서비스
20.3 LLM (Large Language Model)
- 대규모 언어 모델
20.4 NLP (Natural Language Processing)
- 자연어 처리

21. 핵심 개념 요약
구분	핵심 내용
AI	인간의 지능을 모방하는 기술
머신러닝	데이터에서 패턴과 규칙 학습
딥러닝	심층 신경망을 활용한 학습
Feature	예측에 사용하는 입력 특성
Target	예측하고자 하는 정답
Overfitting	학습 데이터에 과도하게 최적화
Data Leakage	학습 과정에 알 수 없는 정보가 유입
Preprocessing	모델 학습을 위한 데이터 전처리
Regression	연속적인 수치 예측
Classification	범주 예측
Confusion Matrix	실제값과 예측값 비교
SMOTE	소수 클래스 데이터 합성
Regularization	모델의 과적합 방지
RAG	외부 정보 검색을 활용한 생성
LLM	대규모 언어 모델
NLP	자연어 처리