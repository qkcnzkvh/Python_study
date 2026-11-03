1. 자연어 처리 (NLP)
- NLP (Natural Language Processing)
  - 사람이 일상적으로 사용하는 언어(구어체, 문어체)를 컴퓨터가 이해하고 처리할 수 있도록 하는 기술
- 자연어 처리의 목적
  - 컴퓨터가 사람의 언어를 이해하거나 생성할 수 있도록 데이터를 처리하는 모든 기술
자연어 처리 과정
- NLU (Natural Language Understanding)
  - 언어 → 컴퓨터
  - 컴퓨터가 사람의 언어를 이해하는 과정
- NLG (Natural Language Generation)
  - 컴퓨터 → 언어
  - 컴퓨터가 사람의 언어를 생성하는 과정
전산 언어학 (Computational Linguistics)
- 컴퓨터 공학 + 통계학 + 언어학을 결합한 학문

과거 언어 처리의 문제점
- 중의적 표현 해석의 어려움
  - 긍정과 부정 등 문맥에 따라 의미가 달라지는 표현
  - 예: "참 잘~ 한다."
- 예외적인 언어 규칙 해석의 어려움
  - 유연함, 확장성, 관행, 유행, 밈 등
- 음성 언어 처리의 어려움
  - STT(Speech to Text), 사투리, 동의어, 맥락 및 문장 흐름
- 언어 간 차이
  - 국가별 언어 구조가 달라 기계 번역에 어려움 발생
자연어 처리 패러다임 변화
1. 규칙 기반 언어 처리
   - 사전에 정의된 문법적 규칙을 이용하여 언어 처리
   - 다양한 예외와 문맥을 처리하기 어려움
2. 통계 기반 언어 처리
   - 문장에 등장하는 단어의 확률 및 출현 빈도를 분석
   - 맥락 파악이 가능해졌지만 대량의 문장 분석과 중의적 의도 파악에 한계
3. 기계학습 기반 언어 처리 (Text Mining)
   - 데이터의 패턴을 학습하여 텍스트 분석
   - 텍스트 분류, 문장 분류, 유사도 분석, 주제 분석 등으로 발전
4. 신경망 기반 언어 처리
   - 대량의 문장을 분석하고 문맥과 의도를 파악
   - 자연어 이해뿐 아니라 자연어 생성 기술까지 발전

2. 형태소 분석 (Morphological Analysis)
- 문장이나 글을 의미를 가진 가장 작은 단위로 나누고 품사를 부착하는 과정
- 자연어 처리의 기초 단계
- 문장을 구성하는 단어의 형태적 구조를 파악
핵심 용어
- 형태소 (Morpheme)
  - 의미를 가진 가장 작은 언어의 단위
- 품사 (POS, Part of Speech)
  - 단어를 문법적 기능에 따라 분류한 것
Tokenizing + Tagging
1. Tokenizing (토큰화)

텍스트를 특정 단위로 나누는 작업
- 어절 분리 (Word Tokenization)
  - 문장을 단어 단위로 분리
- 문장 분리 (Sentence Tokenization)
  - 문단 내 문장을 개별 문장으로 분리
- 서브워드 분리 (Subword Tokenization)
  - 단어를 더 작은 단위로 분리
  - 딥러닝 및 전이학습에서 활용
  - 미등록 단어(OOV) 처리에 유리
2. Tagging (태깅)
- 나누어진 언어 객체에 항목을 부여하는 작업
- 형태소 분석에서는 품사를 부착하는 과정
- 같은 단어라도 문맥에 따라 품사가 달라질 수 있으므로 문맥을 고려해야 함
개체명 인식 (Named-Entity Recognition, NER)
- 문장 내 특정 명사를 사람, 조직, 장소 등으로 구분하는 기술
- 문장의 맥락을 이해하는 데 활용
- 동음이의어 구분 및 지역 정보 파악 등에 사용

3. 한국어 자연어 처리 분석기
분석기	특징
Okt (Open Korean Text)	트위터(X) 기반, 구어체 분석에 적합
KKma	Java 기반, 세밀한 형태소 분석, 비교적 느림
Komoran	머신러닝 기반, 공백이 포함된 고유명사 분류에 강점
Hannanum	규칙 기반, 품사 태깅 및 구문 분석에 특화

분석기별 특징
Okt
- 트위터(X)에 올라온 글을 수집하여 개발된 형태소 분석기
- 구어체 분석에 적합
- 사전 기반 분석과 규칙을 통해 품사 부착
KKma
- Java 기반 형태소 분석기
- 규칙 기반 분석
- 속도는 비교적 느리지만 형태소를 세밀하게 분석
Komoran
- 머신러닝 알고리즘 기반 형태소 분석기
- 공백이 포함된 고유명사를 잘 분류
- 성능이 안정적이고 비교적 빠름
- 사전 업데이트가 수작업으로 이루어져 최신 단어 처리에 한계
Hannanum
- 규칙 기반 형태소 분석기
- 품사 태깅과 구문 분석에 특화
- 복잡한 형태소 분석 규칙을 적용하여 문장 구조를 파악
- 속도가 비교적 느림

4. 단어 표현 (Word Representation)
- 언어적 특성을 활용하여 단어를 수치화하고 컴퓨터가 이해할 수 있는 형태로 변환하는 기술
- Word Embedding 또는 Word Vector라고도 함
단어 표현 방식
4-1. 희소 표현 (Sparse Representation)
- 단어를 대부분 0으로 구성된 벡터로 표현
- 구현이 간단하지만 단어 간 의미적 관계를 반영하기 어려움
One-Hot Encoding
- 문장의 모든 단어를 0과 1로 표현
- 특정 단어에 해당하는 위치만 1로 표시
BoW (Bag of Words)
- 문서 내 단어의 출현 빈도를 계산하여 벡터로 표현
- 어떤 단어가 많이 사용되었는지 확인 가능
- 단어의 순서와 문맥은 무시하고 빈도만 반영
TF-IDF (Term Frequency-Inverse Document Frequency)
- 문서 내 단어의 중요도를 가중치로 계산
- 여러 문서에서 흔하게 등장하는 단어에는 낮은 가중치 부여
- 특정 문서에서 상대적으로 중요하게 등장하는 단어에는 높은 가중치 부여
- 문서별 핵심 단어 및 주제 파악에 활용
4-2. 밀집 표현 (Dense Representation)
- 단어를 실수로 구성된 벡터로 표현
- 단어 간 의미적 유사성을 반영할 수 있음
CBOW (Continuous Bag of Words)

- 주변 단어를 활용하여 중심 단어를 예측하는 방식

Skip-Gram

- 중심 단어를 활용하여 주변 단어가 등장할 확률을 예측하는 방식

대표 모델
- Word2Vec
- FastText

5. 문장 표현 (Sentence Representation)
- 텍스트 분류, 연관 분석 등 텍스트 마이닝을 수행하기 위해 문장 단위로 자연어를 수치화하는 기법
Text to Sequence
- 문장 내 단어를 각각 하나의 정수와 매칭하여 문장을 정수의 나열로 변환
- 컴퓨터가 자체적으로 단어 사전을 구성하고 단어에 고유한 번호를 부여
예시:
안녕하세요. 저는 데이터 분석가 홍길동입니다.

안녕 → 1
하세요 → 3
저는 → 2
데이터 → 4
분석가 → 5
홍길동 → 6

변환 결과:
[1, 3, 2, 4, 5, 6]


Padding (패딩)
- 문장마다 길이가 다르기 때문에 Sequence 길이를 동일하게 맞추는 작업
- 일반적으로 부족한 길이를 0 등의 값으로 채움
예시:
문장 A: 안녕 나는 고양이야
문장 B: 안녕 반가워 나는 오늘 기분이 좀 좋은 고양이야

Text to Sequence

A: [1, 2, 3]
B: [1, 4, 2, 5, 6, 7, 8, 3]

Padding 적용

A: [1, 2, 3, 0, 0, 0, 0, 0]
B: [1, 4, 2, 5, 6, 7, 8, 3]



6. RNN 순환신경망 (Recurrent Neural Network)
- Sequence Data(순차적 데이터)를 처리하기 위한 딥러닝 모형
- 자연어 및 시계열 데이터 처리에 활용
- 데이터의 순서 정보를 보존하면서 학습
주요 특징
1. 순환 구조

- 이전 시간 단계의 출력 정보를 다음 시간 단계의 입력으로 사용

2. 파라미터 공유
- 각 시간 단계에서 동일한 가중치를 사용
- 각 시간 단계마다 별도의 가중치를 학습하지 않음
3. 시간 의존성 모델링

- 시간적으로 연속된 입력 데이터의 패턴을 학습
RNN의 한계점
1. 기울기 소실 (Gradient Vanishing)
- Sequence 길이가 길어지면 초기 정보가 점점 희석됨
- 장기 의존성(Long-term Dependency) 학습이 어려움
- 이를 보완하기 위해 LSTM, GRU, 양방향 RNN 등이 개발됨
2. 병렬 처리의 어려움
- 이전 시간 단계의 결과가 다음 단계에 영향을 주기 때문에 순차적으로 처리
- 학습 시간이 오래 걸릴 수 있음

7. LSTM (Long Short-Term Memory)
- RNN의 장기 의존성 문제를 해결하기 위해 개발된 변형 모델
- Cell State를 추가하여 중요한 정보를 장기적으로 전달하도록 설계
구성 요소
1. Cell State (장기 기억)

- 중요한 정보를 유지하면서 각 Hidden State에 정보 제공

2. Input Gate
- 새로운 정보를 Cell State에 추가할지 결정
- Sigmoid: 새로운 정보의 반영 정도를 0~1 사이의 값으로 결정
- Tanh: Cell State에 추가할 후보 정보를 -1~1 사이의 값으로 생성
- 두 값을 곱하여 실제 추가할 정보 결정
3. Forget Gate
- 기존 정보를 얼마나 유지하거나 삭제할지 결정
- Sigmoid 출력값 기준
  - 1: 기존 정보 유지
  - 0: 기존 정보 삭제
4. Output Gate
- Cell State에서 어떤 정보를 Hidden State로 전달할지 결정
- Sigmoid: 출력할 정보의 양 결정
- Tanh: Cell State 정보를 -1~1 사이로 변환
- 두 값을 곱하여 Hidden State 결정
5. Hidden State (단기 기억)
- 현재 시점에서 처리된 출력 정보
- 다음 시간 단계의 계산에도 활용

8. GRU (Gated Recurrent Unit)
- LSTM의 복잡한 구조를 단순화한 RNN 변형 모델
- LSTM의 연산량과 파라미터를 줄이고 학습 속도를 개선하기 위해 개발
구성 요소
1. Update Gate
- 이전 정보를 얼마나 유지하고 새로운 정보를 얼마나 반영할지 결정
- LSTM의 Input Gate와 Forget Gate 역할을 통합
2. Reset Gate
- 과거 정보를 얼마나 무시할지 결정
- 과거 정보의 영향을 줄이고 현재 입력을 중심으로 계산하도록 조절
특징
- LSTM보다 구조가 단순하고 파라미터 수가 적음
- 연산 효율이 높고 학습 속도가 빠를 수 있음
- 일반적으로 LSTM의 Cell State를 별도로 사용하지 않음

9. RNN 파생 모델
Bidirectional RNN (양방향 순환 신경망)
- 문장을 정방향과 역방향 두 방향으로 각각 처리
- 두 방향의 결과를 결합하여 문맥 파악
- 앞뒤 문맥을 모두 활용할 수 있음
- 출력 차원과 연산량이 증가할 수 있음
Stacked RNN (순환층 쌓기)
- CNN에서 Convolution Layer를 여러 개 쌓는 것처럼 RNN Layer도 여러 층으로 구성
- 각 층이 서로 다른 수준의 패턴을 학습하도록 설계
return_sequences=True
- RNN의 각 시간 단계에서 나온 출력값을 모두 반환
- 반환된 결과를 다음 RNN Layer의 입력으로 전달
학습 구조
- 아래층: 단어 수준의 짧은 패턴 학습
- 위층: 문장 수준의 복잡하고 긴 패턴 학습

10. Topic Modeling (토픽 모델링)
- 텍스트 문서 집합에서 숨겨진 주제 구조를 발견하는 과정
- 문서 간 유사성을 기반으로 여러 주제를 식별하는 비지도학습 기법
LDA (Latent Dirichlet Allocation)
- 문서와 단어 사이의 확률적 관계를 활용하여 주제를 추출하는 모델

핵심 가정
1. 문서는 여러 주제가 섞여 있다.
   - 문서-주제 분포
   - 하나의 문서에 각 주제가 몇 %씩 포함되어 있는지 계산
2. 주제는 여러 단어로 구성된다.
   - 주제-단어 분포
   - 특정 주제에서 어떤 단어가 자주 등장하는지 계산
LDA의 추론 방법
1. 변분 베이즈 추론 (Variational Bayes)
- 정확한 사후 분포를 직접 계산하기 어려울 때 사용
- 더 간단한 확률분포를 이용하여 실제 분포를 근사하는 방법
2. 깁스 샘플링 (Gibbs Sampling)
- 복잡한 다변수 확률분포에서 표본을 추출하는 방법
- 각 단어에 적절한 주제를 반복적으로 배정
- 유사한 단어들이 같은 주제에 모이도록 확률을 갱신
LDA 학습 단계
1. 초기화
   - 문서 내 각 단어에 임의의 주제 부여
2. 주제 추정
   - 문서 내 다른 단어와의 관계를 기반으로 주제 추정
   - 문서-주제 분포 계산
   - 주제-단어 분포 계산
3. 추출 및 갱신
   - 계산된 확률을 바탕으로 각 단어의 주제를 재배정
   - 문서 내 주제 분포와 주제별 단어 분포 갱신
4. 반복
   - 분포의 변화가 작아질 때까지 반복 수행

11. 자연어 생성
Seq2Seq (Sequence to Sequence)
- 입력 Sequence를 바탕으로 새로운 출력 Sequence를 생성하는 구조
- 주로 RNN, LSTM 등의 순환신경망을 활용
- 기계 번역, 챗봇, 문장 요약, STT 등에 사용
Seq2Seq 구조
1. Encoder
- 입력 문장을 받아 순차적으로 처리
- 문장 정보를 하나의 벡터로 변환
- 처리된 정보를 Context Vector로 전달
2. Context Vector
- Encoder가 처리한 입력 문장의 정보를 담는 고정 크기 벡터
- Decoder가 적절한 출력 문장을 생성할 수 있도록 정보 전달
3. Decoder
- Context Vector를 바탕으로 출력 Sequence 생성
- 다음에 등장할 확률이 높은 단어를 순차적으로 예측
학습 및 추론 방식
Teacher Forcing
- 학습 시 정답 문장을 Decoder의 다음 입력으로 사용
- 이전 단계의 정답을 활용하여 다음 단어를 학습
- 학습이 안정적이고 빠르게 진행될 수 있음
Autoregressive (자기회귀)
- 추론 시 모델이 직전에 예측한 단어를 다음 입력으로 사용
- 정답이 없으므로 예측 결과를 반복적으로 연결하여 문장 생성
Seq2Seq 작동 순서
1. 입력 문장을 토큰화하여 단어 단위로 분리
2. Encoder의 RNN에 단어를 순서대로 입력
3. Encoder의 마지막 상태를 Context Vector로 변환
4. Context Vector를 Decoder에 전달
5. SOS(Start of Sequence) 토큰을 입력하여 생성 시작
6. Decoder가 다음 단어를 예측
7. EOS(End of Sequence)가 등장하거나 최대 길이에 도달할 때까지 반복
8. 최종 Output Sequence 출력
한계점
- 입력 문장이 길어질수록 Context Vector에 정보가 압축되면서 손실 발생
- 고정된 크기의 벡터에 모든 문장 정보를 담기 어려움
- 학습과 추론의 입력 방식이 달라지는 노출 편향(Exposure Bias) 문제 발생 가능

12. Attention Mechanism (어텐션 메커니즘)
- Seq2Seq의 Context Vector가 가진 정보 압축 문제를 보완한 구조
- 입력 문장의 모든 요소를 다시 참조하여 중요한 정보에 높은 가중치를 부여
- Decoder가 단어를 예측할 때 Encoder의 전체 정보를 활용
핵심 원리
- Encoder의 각 시점 출력을 Key와 Value로 구성
- Decoder의 현재 상태를 Query로 사용
- Query와 Key의 유사도를 계산하여 Attention Score 생성
- Attention Score를 바탕으로 중요한 정보에 높은 가중치 부여
- 가중치와 Value를 결합하여 Context Vector 생성
구성 요소 (Q / K / V)
1. Query (질의)
- 현재 출력 시점에서 필요한 정보
- 일반적으로 Decoder의 현재 State 사용
2. Key (검색 기준)
- 입력 문장의 각 요소를 검색할 수 있도록 표현
- Encoder의 각 시점 출력 정보 사용
3. Value (실제 정보)
- 입력 문장의 실제 정보
- Key와 동일하게 Encoder 출력에서 생성
- Attention Score를 가중치로 적용하여 최종 Context Vector 생성
Attention 계산 순서
1. Score 계산
- Query와 Key의 내적을 통해 유사도 계산
2. Weight 계산
- Softmax를 적용하여 가중치 정규화
- 모든 가중치의 합은 1
3. Context 계산
- Weight와 Value를 곱하여 가중합 계산
4. Context 전달
- 계산된 Context Vector를 Decoder에 전달

13. Transformer
- Attention Mechanism을 기반으로 발전한 신경망 모델
- RNN이나 LSTM처럼 Sequence를 순차적으로 처리하지 않고 전체 Sequence를 병렬로 처리
- 자연어 처리 성능과 학습 효율을 크게 개선
Transformer 구성
1. Encoder
- 입력 Sequence를 이해하고 고차원 벡터로 변환
- Multi-Head Self-Attention: 입력 문장 내 단어 간 관계 학습
- Position-wise Feed Forward Neural Network(FFNN): 학습된 특징을 비선형적으로 변환
2. Decoder
- Encoder의 정보를 활용하여 출력 Sequence 생성
- Masked Multi-Head Self-Attention: 이전에 생성된 단어만 참조
- Encoder-Decoder Attention: Encoder 정보를 참조하여 다음 단어 예측
- FFNN: 출력 정보를 비선형적으로 변환
3. Position Encoding (위치 인코딩)
- Transformer는 전체 Sequence를 병렬로 처리하므로 단어의 순서 정보가 별도로 필요
- Sin/Cos 함수를 활용하여 위치 정보를 벡터로 변환
- 기존 단어 정보와 위치 정보를 결합하여 Encoder와 Decoder에 전달
Transformer Attention 종류
종류	역할
Multi-Head Self-Attention	입력 문장 내 단어 간 관계 파악
Masked Multi-Head Self-Attention	Decoder에서 미래 단어를 참조하지 않고 이전 단어만 활용
Encoder-Decoder Attention	Encoder의 정보를 Decoder가 활용하도록 연결

자연어 생성 모델 비교
모델	특징	한계 및 장점
Seq2Seq	고정 크기 Context Vector로 정보 전달	긴 문장에서 정보 손실, 순차 처리
Attention	입력 문장의 중요한 부분을 다시 참조	긴 문장 처리 개선, 연산량 증가
Transformer	Attention을 병렬 처리	빠른 학습과 높은 성능

Transformer 기반 모델
- BERT
  - Transformer Encoder 부분만 활용
  - 자연어 이해에 강점
- GPT
  - Transformer Decoder 부분만 활용
  - 다음 단어 예측 및 자연어 생성에 강점

14. NLP Pre-training (사전 학습)
- 대규모 언어 데이터를 이용하여 미리 학습된 모델을 다른 모델이나 애플리케이션에 적용하는 기법
- 신경망 알고리즘의 전이학습을 활용
- 자기지도학습(Self-Supervised Learning)의 대표적인 활용 사례
자기지도학습 (Self-Supervised Learning)
- 정답 라벨 없이 입력 데이터 자체에서 학습 신호를 생성하는 방식
- 데이터의 일부를 가리거나 변형하여 원래 정보를 예측하도록 학습
BERT (Transformer Encoder Model)
- Bidirectional Encoder Representations from Transformers
- 자연어 이해 작업에 주로 활용
- 문장의 양방향 문맥을 파악할 수 있음
BERT 핵심 학습 방식

1. MLM (Masked Language Model)
- 문장 내 일부 단어를 가림
- 양방향 문맥을 활용하여 가려진 단어를 예측
2. NSP (Next Sentence Prediction)
- 두 문장이 문맥적으로 이어지는 관계인지 예측
사전 학습 데이터
- Wikipedia 약 25억 개 단어
- BooksCorpus 약 8억 개 단어
- 레이블이 없는 대규모 텍스트 데이터로 사전 학습
BERT 핵심 구조

- Word Embedding
- WordPiece Embedding: 단어를 서브워드 단위로 분리하여 벡터화
- Positional Embedding: 단어의 위치 정보 표현
- Segment Embedding: 문장 및 문단 구분 정보 표현
- Bidirectional Transformer
- 양방향 문맥을 활용하여 문장 이해
- MLM, NSP 등의 사전 학습 수행
Fine-Tuning
- 사전 학습된 BERT 모델을 특정 작업에 맞게 추가 학습
- 텍스트 분류, 감정 분석, 개체명 인식 등에 활용
GPT (Transformer Decoder Model)
- GPT (Generative Pre-trained Transformer)
- 주어진 문장이나 데이터를 바탕으로 다음 단어를 예측하고 생성하는 모델
- 자연어 생성에 주로 활용
핵심 특징
- Autoregressive (자기회귀) 방식
- 이전에 생성된 토큰을 바탕으로 다음 토큰 예측
- 일반적으로 왼쪽에서 오른쪽으로 순차적으로 생성

핵심 개념 빠르게 복습하기
개념	핵심 역할
NLP	컴퓨터가 자연어를 이해하고 생성하는 기술
NLU	자연어 이해
NLG	자연어 생성
Tokenizing	텍스트를 작은 단위로 분리
Tagging	단어에 품사 등 항목 부여
NER	사람, 조직, 장소 등의 개체명 인식
One-Hot Encoding	단어를 0과 1로 표현
TF-IDF	문서 내 단어의 중요도 계산
Word2Vec	단어의 의미적 관계를 벡터로 학습
Padding	Sequence 길이 맞추기
RNN	순차적인 데이터 처리
LSTM	장기 의존성 문제 보완
GRU	LSTM 구조 단순화 및 연산 효율 개선
LDA	문서 내 숨겨진 주제 추출
Seq2Seq	입력 Sequence를 출력 Sequence로 변환
Attention	중요한 정보에 높은 가중치 부여
Transformer	Attention 기반 병렬 처리
BERT	양방향 문맥을 활용한 자연어 이해
GPT	다음 토큰 예측 기반 자연어 생성