1. 핵심 엔진
1.1 베이즈 정리 (Bayes' Theorem)
- 사전 확률과 우도를 통해 사후 확률을 추론하는 조건부 확률의 원리
- 새로운 데이터를 관찰한 후 기존 확률을 갱신하는 방법
1.2 KNN (K-Nearest Neighbors)
- K 최근접 이웃 알고리즘
- 지도학습 기반의 분류 및 회귀 알고리즘
- 새로운 데이터와 가까운 K개의 데이터를 찾아 결과를 예측

2. 거리 측정 지표
KNN 등에서 데이터 간의 가까움을 판단할 때 사용하는 방법이다.
거리 측정 방식	설명
유클리드 거리 (Euclidean Distance)	두 점 사이의 직선 거리
맨해튼 거리 (Manhattan Distance)	좌표축을 따라 이동하는 거리의 합
해밍 거리 (Hamming Distance)	같은 길이의 문자열이나 벡터에서 값이 다른 위치의 개수
민코프스키 거리 (Minkowski Distance)	유클리드 거리와 맨해튼 거리를 일반화한 형태


3. BERT와 GPT
구분	BERT	GPT
구조	Encoder	Decoder
주요 영역	NLU	NLG
의미	자연어 이해	자연어 생성

- NLU (Natural Language Understanding): 자연어 이해
- NLG (Natural Language Generation): 자연어 생성

4. 비지도학습 (Unsupervised Learning)
정답이 없는 데이터를 이용하여 데이터 내부의 패턴과 구조를 발견하는 학습 방식이다.
4.1 군집화 (Clustering)
- 데이터를 유사한 특징을 가진 그룹으로 나누는 비지도학습
- K-Means는 미리 정해진 K개의 군집으로 데이터를 분류
- 각 군집의 중심과 군집 내 데이터 사이의 거리 제곱합을 최소화하는 방향으로 학습
K-Means 군집화 순서
1. 랜덤으로 중심점 선정
2. 각 데이터와 중심점 사이의 거리 계산
3. 가까운 중심점을 기준으로 군집 형성
4. 군집 내 데이터의 평균값으로 중심점 재조정
5. 중심점의 위치 변화가 없을 때까지 반복
K-Means++
- 초기 중심점을 최대한 멀리 떨어지도록 선정
- 초기 중심점 선정의 효율을 높이는 방법
4.2 차원 축소 (Dimensionality Reduction)
데이터의 특성(Feature) 개수를 줄여 데이터를 효율적으로 분석하는 방법이다.

차원 축소가 필요한 이유
1. 차원의 저주 (Curse of Dimensionality)
   - 차원이 증가할수록 데이터 공간이 팽창
   - 데이터 밀도가 희소해짐
   - 과적합 위험 증가 및 일반화 성능 저하
2. 다중공선성 (Multicollinearity)
   - 독립 변수(Feature) 사이에 높은 선형 상관관계가 존재
   - 회귀 계수 추정이 불안정해짐
   - 모델 해석력 및 예측 성능에 악영향
3. 계산 효율성 저하
   - 불필요한 변수가 많을수록 학습 및 예측 시간 증가
   - 컴퓨팅 자원 사용량 증가
PCA (Principal Component Analysis)
- 주성분 분석
- 서로 유사한 특징을 가진 Feature들을 새로운 Feature(주성분)로 변환
- 데이터의 주요 정보를 최대한 유지하면서 차원을 축소
pca.explained_variance_ratio_



- 각 주성분이 전체 데이터의 분산을 얼마나 설명하는지 확인
4.3 이상 탐지 (Anomaly Detection)
- 정상적인 데이터 패턴에서 벗어난 데이터를 탐색하는 과정
- IsolationForest 알고리즘 활용

5. 군집화 알고리즘의 종류
군집화는 데이터를 어떤 기준으로 나누는지에 따라 구분할 수 있다.
5.1 중심 기반 (Centroid-based)
중심점을 기준으로 데이터를 구분한다.

K-Means
- K개의 군집 수를 미리 지정
- 중심점과 가까운 데이터끼리 군집 형성
5.2 밀도 기반 (Density-based)
데이터가 밀집되어 있는 영역을 찾아 군집을 형성한다.

Mean Shift
- 데이터 밀도가 높은 곳으로 중심점을 이동
- 밀도가 높은 영역을 중심으로 군집 형성
- KDE (Kernel Density Estimation)를 활용
KDE (커널 밀도 추정)
- 데이터가 특정 영역에 얼마나 밀집되어 있는지 추정하는 방법
- 대역폭(Bandwidth, h)을 이용하여 밀도를 측정
대역폭의 특징:
대역폭	결과
큰 h	군집 범위가 넓어지고 군집 개수가 감소할 수 있음
작은 h	세부적인 밀도 변화에 민감해짐

- 큰 h: 과소적합 가능성
- 작은 h: 과적합 가능성
DBSCAN
- 데이터의 밀도를 기준으로 군집을 형성
- 데이터의 모양이 중요한 경우 활용
- 이상치 탐지에도 활용 가능
주요 용어:
용어	설명
Epsilon (eps)	이웃 데이터로 판단하는 반경
MinPts	핵심 포인트가 되기 위한 최소 데이터 수
Core Point	주변에 충분한 데이터가 존재하는 핵심 포인트
Noise Point	군집에 포함되지 않는 노이즈 데이터

진행 과정:
1. 핵심 포인트 선정
2. 주변 경계 영역 설정
3. 밀도를 기준으로 군집 확장
4. 경계 밖의 포인트는 노이즈로 분류
5.3 계층 기반 (Hierarchical-based)
- 나무 구조 형태로 데이터를 구분
- 데이터 간의 계층적인 관계를 기반으로 군집 형성
5.4 분포 기반 (Distribution-based)
- 데이터가 특정 확률 분포의 조합으로 이루어져 있다고 가정

GMM (Gaussian Mixture Model)
- 2개 이상의 정규분포를 가정하여 데이터를 군집화
- 각 데이터가 여러 가우시안 분포 중 어디에 속할 가능성이 높은지 계산
주요 용어:
용어	설명
평균 (Mean)	각 가우시안 분포의 중심 위치
혼합 가중치 (Mixture Weight)	각 가우시안 분포가 차지하는 비율

CLT (Central Limit Theorem, 중심극한정리)
- 동일한 모집단에서 표본을 반복적으로 추출하고 평균을 계산하면, 표본평균의 분포가 정규분포에 가까워지는 원리
- 강의 예시: 주사위를 여러 번 던져 얻은 평균값의 분포

6. AI Agent 기초
6.1 Moltbook
- AI Agent를 위한 소셜 네트워크
6.2 생성형 AI와 AI Agent
- 생성형 AI: 두뇌 역할
- AI Agent: 실제 작업 수행 역할
MCP (Model Context Protocol)

- AI 모델과 외부 도구 및 데이터 소스를 연결하는 표준 프로토콜
6.3 AI Agent의 작업 순서
목표 및 지시사항
      ↓
계획 수립
      ↓
Task 실행
      ↓
Reflect (결과 검토)
      ↓
보고



7. Feature Engineering (피처 엔지니어링)
7.1 개념
- 데이터에 숨겨진 의미를 파악하는 과정
- 원시 데이터에서 Feature를 추출
- 머신러닝 모델에 적합한 형식으로 변환하는 모든 과정
7.2 주요 방법
방법	설명
피처 선택 (Feature Selection)	모델 성능에 기여하는 유용한 특성만 선택하고 불필요한 특성 제거
피처 생성 (Feature Creation)	기존 Feature를 결합하거나 변환하여 새로운 파생 변수 생성
피처 변환 (Feature Transformation)	기존 Feature를 다른 형식이나 스케일로 변환

- 피처 생성 시 다중공선성에 주의해야 함
7.3 피처 처리 방법
숫자형 Feature
- 표준화 (Standardization)
- 정규화 (Normalization)
- 강건한 스케일링 (Robust Scaling)
범주형 Feature
- 레이블 인코딩 (Label Encoding)
- 원-핫 인코딩 (One-Hot Encoding)
시계열 데이터
- 시차 Feature (Lag Feature)
- 이동 통계량 (Rolling Statistics)
- 변동성 Feature
비정형 데이터
- 텍스트: TF-IDF
- 이미지: 이미지 데이터 특성 추출
신호 처리
- 푸리에 변환 (Fourier Transform)
- 웨이블릿 변환 (Wavelet Transform)
자동화 기법

- 오토인코더 (Autoencoder)
7.4 Feature Selection 방법
방식	설명
필터 기법 (Filter Methods)	통계적인 기준으로 Feature 선택
래퍼 기법 (Wrapper Methods)	모델을 반복적으로 학습하고 평가하여 최적의 Feature 조합 탐색
내장 기법 (Embedded Methods)	모델 학습 과정에서 Feature 중요도를 반영하여 선택


8. 교차 검증 (Cross Validation)
8.1 K-Fold Cross Validation
데이터를 K개의 동일한 부분집합으로 나누어 반복적으로 검증하는 방법이다.

진행 과정:
1. 데이터를 K개의 폴드로 분할
2. K-1개 폴드를 훈련 데이터로 사용
3. 나머지 1개 폴드를 검증 데이터로 사용
4. 검증 데이터의 위치를 변경하면서 K번 반복
5. 각 검증 결과를 종합하여 모델 성능 평가
주요 함수
from sklearn.model_selection import cross_val_score, cross_validate



- cross_val_score(): 교차 검증 점수 계산
- cross_validate(): 여러 평가 지표 및 추가 정보를 포함한 교차 검증