7. 분류 모델 (Classification)
분류 모델은 입력 데이터를 특정 범주 또는 클래스로 구분하는 모델이다.
7-1. 이진 분류 (Binary Classification)
정답이 0 또는 1, 두 가지로 구분되는 문제이다.

예시:
- 정상 / 비정상
- 폐렴 / 정상
- 스팸 / 정상 메일
Sigmoid 함수
모델의 출력값을 0~1 사이의 확률로 변환한다.
\[
\sigma(x)=\frac{1}{1+e^{-x}}
\]

예를 들어 출력값이 0.9라면 양성 클래스일 확률이 90%라는 의미로 해석할 수 있다.

BCELoss
nn.BCELoss()는 예측 확률과 실제 정답 사이의 오차를 계산하는 손실 함수이다.
- 실제 정답이 1이면 예측값이 1에 가까울수록 손실 감소
- 실제 정답이 0이면 예측값이 0에 가까울수록 손실 감소
예시:
실제 정답	예측 확률	결과
1	0.9	좋은 예측
1	0.2	잘못된 예측
0	0.1	좋은 예측
0	0.8	잘못된 예측

참고로 BCELoss를 사용할 때는 Sigmoid를 별도로 적용한다. BCEWithLogitsLoss를 사용하면 Sigmoid가 내부에 포함되어 있어 별도로 적용하지 않는다.
np.where()
조건에 따라 값을 선택하는 NumPy 함수이다.
np.where(조건, True일 때 값, False일 때 값)



예시:
np.where(pred >= 0.5, 1, 0)



예측 확률이 0.5 이상이면 1, 미만이면 0으로 변환한다.
8. 다중 분류 모델 (Multi-class Classification)
다중 분류는 세 개 이상의 클래스로 데이터를 분류하는 문제이다.

예시:
- 개 / 고양이 / 새
- 정상 / 폐렴 / 기타 질환
- 숫자 0~9 손글씨 분류
Softmax 함수
여러 출력 노드의 값을 하나의 확률 분포로 변환한다.
- 각 클래스의 확률을 계산
- 모든 클래스 확률의 합은 1
- 가장 높은 확률을 가진 클래스를 예측 결과로 선택

CrossEntropyLoss
PyTorch의 nn.CrossEntropyLoss()는 내부적으로 LogSoftmax와 NLLLoss를 결합한 손실 함수이다.

따라서 모델 출력에 Softmax를 별도로 적용하지 않고 원본 출력값(Logits)을 전달한다.
loss_fn = nn.CrossEntropyLoss()



Argmax
가장 높은 예측값을 가진 클래스의 인덱스를 반환한다.
pred = output.argmax(dim=1)



예를 들어 출력 확률이 다음과 같다면,
[0.1, 0.7, 0.2]



가장 높은 값은 0.7이므로 인덱스인 1을 예측 클래스로 반환한다.
Integer Encoding
문자열로 된 정답 데이터를 숫자로 변환하는 작업이다.

예시:
원래 데이터	변환값
Normal	0
Pneumonia	1
Other	2

9. MNIST (손글씨 숫자 분류)
MNIST는 0~9까지의 손글씨 숫자 이미지로 구성된 대표적인 딥러닝 학습 데이터셋이다.

Flatten (평탄화)
이미지 데이터를 1차원 벡터로 변환하는 과정이다.

예를 들어 8×8 이미지라면 다음과 같이 변환한다.
\[
8\times8=64
\]

원본 이미지: 8 × 8
       ↓
Flatten
       ↓
1 × 64


MNIST의 일반적인 이미지는 28×28 픽셀이므로 다음과 같이 변환할 수 있다.
\[
28\times28=784
\]

Flatten을 수행하면 이미지의 픽셀 정보를 1차원 입력 데이터로 전달할 수 있다.
Confusion Matrix (혼동 행렬)
분류 모델이 어떤 클래스를 정확하게 예측했고, 어떤 클래스를 잘못 예측했는지 확인하는 방법이다.

ConfusionMatrixDisplay를 활용하면 오분류 결과를 시각화할 수 있다.

10. 클래스 선언과 객체지향 프로그래밍
함수 기반 코드의 한계
딥러닝 모델을 함수만으로 구성하면 다음과 같은 문제가 발생할 수 있다.
- 코드 중복 증가
- 유지보수 및 수정 어려움
- 코드 재사용과 확장에 제약
이러한 문제를 해결하기 위해 클래스를 활용한다.
클래스 기반 모델 선언
PyTorch에서는 nn.Module을 상속받아 딥러닝 모델을 구현한다.
import torchimport torch.nn as nnclass MyModel(nn.Module):    def __init__(self):        super().__init__()        self.layer = nn.Linear(10, 1)    def forward(self, x):        x = self.layer(x)        return x



주요 구성 요소
구성 요소	역할
nn.Module	PyTorch 모델의 기본 클래스
__init__()	모델의 계층과 변수를 초기화
super().__init__()	부모 클래스의 초기화 실행
forward()	데이터가 각 계층을 통과하는 순서 정의
self	현재 객체 자신을 참조

모델 선언 방식
1. 기본형

각 계층을 직접 선언하고 forward()에서 계산 과정을 작성한다.

2. 중첩형

forward() 내부에서 여러 계층을 순서대로 통과시킨다.

3. 모듈형

계층을 변수로 미리 선언하고 forward()에서는 간단하게 호출한다.

4. 다중 입력 레이어

입력 데이터의 일부 특징을 별도 경로로 처리한 다음 결과를 결합하는 구조이다.

예를 들어 환자의 나이와 혈액검사 수치를 별도 계층에서 처리한 뒤 결합할 수 있다.
11. 딥러닝 모델 튜닝 (Model Tuning)
모델의 과적합을 줄이고 새로운 데이터에서도 좋은 성능을 낼 수 있도록 조정하는 과정이다.
11-1. Early Stopping (조기 종료)
학습이 진행되는 동안 검증 데이터의 손실값이 더 이상 개선되지 않으면 학습을 중단하는 방법이다.

목적
- 과적합 방지
- 불필요한 학습 시간 감소
- 가장 성능이 좋았던 모델 저장
if val_loss > best_loss:    counter += 1    print(f'--> early stopping status, best_loss : {best_loss:4f}')else:    best_loss = val_loss    counter = 0    torch.save(model, PATH)# 조기 종료 조건 확인if counter >= patience:    print("Early Stopping!")    break



- val_loss: 검증 데이터의 손실값
- best_loss: 지금까지 가장 낮았던 손실값
- counter: 개선되지 않은 횟수
- patience: 학습을 더 기다릴 횟수
- PATH: 모델 저장 경로
11-2. Dropout (드롭아웃)
학습 과정에서 일부 뉴런을 확률적으로 비활성화하는 방법이다.

목적
- 특정 뉴런에 지나치게 의존하는 현상 방지
- 과적합 감소
- 모델의 일반화 성능 향상
일반적으로 0.2 ~ 0.4 정도를 사용해 볼 수 있지만 데이터와 모델에 따라 달라진다.
nn.Dropout(0.3)



위 코드는 학습 중 뉴런의 30%를 확률적으로 비활성화한다.
11-3. 가중치 규제 (Regularization)
가중치가 지나치게 커지는 것을 제한하여 모델의 복잡도를 조절하는 방법이다.

L1 규제

가중치의 절댓값 합에 페널티를 부여한다.
\[
L1=\lambda\sum |w|
\]

- 중요도가 낮은 가중치를 0에 가깝게 만들 수 있음
- 불필요한 특징을 줄이는 데 도움
L2 규제

가중치의 제곱 합에 페널티를 부여한다.
\[
L2=\lambda\sum w^2
\]

- 가중치가 지나치게 커지는 것을 방지
- 일반화 성능 향상에 도움
구분	L1 규제	L2 규제
계산 방식	절댓값 합	제곱 합
특징	일부 가중치를 0으로 유도	가중치를 전반적으로 작게 유도
목적	불필요한 특징 제거	가중치 크기 제한


12. 전체 핵심 개념 요약
구분	핵심 용어	기억할 내용
프로젝트 방법론	CRISP-DM	데이터 기반 문제 해결 과정
데이터 구조	Tensor	다차원 숫자 데이터
프레임워크	PyTorch	딥러닝 모델 구현 및 학습
데이터 처리	DataLoader	Batch 단위 데이터 제공
모델 구조	Input / Hidden / Output	신경망의 기본 구성
활성화 함수	ReLU	비선형성 추가
손실 함수	MSELoss	회귀 오차 계산
손실 함수	BCELoss	이진 분류 오차 계산
손실 함수	CrossEntropyLoss	다중 분류 오차 계산
활성화 함수	Sigmoid	0~1 확률 변환
활성화 함수	Softmax	다중 클래스 확률 변환
최적화	Gradient Descent	기울기를 이용한 가중치 조정
최적화	Adam	적응형 학습률 최적화
평가	Confusion Matrix	분류 결과 및 오분류 확인
튜닝	Early Stopping	검증 성능에 따라 조기 종료
튜닝	Dropout	일부 뉴런 비활성화
튜닝	L1 / L2	가중치 규제

13. 꼭 기억해야 할 학습 흐름
딥러닝 전체 과정
1. 데이터 준비
   
   결측치 처리 → 스케일링 → 데이터 분할
2. Tensor 변환
   
   Tensor → TensorDataset → DataLoader
3. 모델 설계
   
   Input → Hidden → Output
4. 학습 설정
   
   Loss Function + Optimizer + Learning Rate
5. 모델 학습
   
   순전파 → 손실 계산 → 역전파 → 가중치 업데이트
6. 모델 평가
   
   예측 → 실제 정답 비교 → 성능 평가
7. 모델 튜닝
   
   Early Stopping → Dropout → L1/L2