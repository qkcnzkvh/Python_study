10. 이미지 증강 (Data Augmentation)
10-1. 이미지 증강이란?
원본 이미지를 회전, 이동, 확대, 밝기 조정 등의 변형을 적용하여 학습 데이터를 인위적으로 확장하는 기법
10-2. 이미지 증강의 효과
1. 데이터 확장
   - 매 Epoch마다 조금씩 다른 이미지를 학습할 수 있음
   - 제한된 원본 데이터로 다양한 학습 효과 기대
2. 불변성 학습
   - 이미지의 위치나 밝기 등이 달라져도 중요한 특징을 인식하도록 학습
   - 모델이 무시해야 하는 변화와 찾아야 하는 특징을 구분하는 데 도움
3. 정규화 효과
   - 모델이 특정 이미지의 픽셀값을 그대로 외우는 현상을 줄임
   - 과적합 방지에 도움
   - Dropout, L2 Regularization과 유사한 정규화 목적의 기법
10-3. 이미지 증강 시 주의사항
- 학습 데이터에만 적용
- 검증 및 평가 데이터에는 원칙적으로 적용하지 않음
- 증강된 이미지는 새로운 독립적인 정보가 아님
- 증강만으로 성능이 크게 향상되지 않을 수 있음
- 좌우 대칭 및 상하 반전은 데이터의 의미가 바뀌지 않는지 확인
- 의료 영상에서는 신장, 치아, 좌우 병변 위치 등 도메인 특성을 고려
10-4. 이미지 증강의 종류
① 기하학적 변환 (Geometric Transformation)
- 회전 (Rotation)
- 이동 (Translation)
- 확대 및 축소 (Scaling)
- 좌우 및 상하 반전 (Flip)
- 탄성 변형 (Elastic Transformation)
② 강도 변환 (Intensity Transformation)
- 밝기 조정 (Brightness)
- 대비 조정 (Contrast)
- 노이즈 추가 (Noise)
- 블러 처리 (Blur)
③ 영역 변환 (Region Transformation)
- 일부 영역 가리기 (Cutout)
- 두 이미지 섞기 (Mixup)
- 이미지 일부를 잘라 다른 이미지와 결합 (CutMix)

11. 객체 검출 / 탐지 (Object Detection)
11-1. 객체 검출이란?
이미지 내 특정 객체의 위치를 찾고 해당 객체가 무엇인지 분류하는 작업

기본 출력
이미지 1장
→ Bounding Box 여러 개
→ 객체 Class
→ Confidence Score


- 이미지 내 객체의 위치와 종류를 동시에 예측
- 출력되는 객체의 개수가 정해져 있지 않음
- 위치를 예측하는 회귀(Regression)와 종류를 예측하는 분류(Classification)를 동시에 수행
- 객체가 없는 배경 영역이 대부분을 차지하여 극단적인 클래스 불균형 문제가 발생할 수 있음
11-2. 이미지 분류와 객체 검출의 라벨 차이
구분	이미지 분류	객체 검출
라벨	이미지 전체에 1개 이상	객체마다 라벨
위치 정보	없음	Bounding Box 필요
작업 난이도	상대적으로 낮음	상대적으로 높음
라벨링 시간	비교적 짧음	객체마다 박스를 그려야 하므로 오래 걸림

11-3. Bounding Box 표현법
Bounding Box란?

컴퓨터 비전 및 이미지 처리 분야에서 객체의 위치를 나타내기 위해 사각형으로 둘러싼 영역

같은 박스라도 라이브러리에 따라 표현하는 좌표 방식이 다름.
① 코너 좌표 (Corner Coordinates)
- 픽셀 좌표를 기준으로 표현
- X축 최소값, Y축 최소값
- X축 최대값, Y축 최대값
xmin, ymin, xmax, ymax


주요 활용:
- Pascal VOC
- Torchvision
- 이미지 시각화
② 중심 및 크기 좌표 (Center Coordinates)
- 박스의 중심점과 너비, 높이로 표현
cx, cy, width, height


③ 정규화 중심 및 크기 좌표 (Normalized Center Coordinates)
- 이미지 크기를 기준으로 좌표와 박스 크기를 0~1 범위로 정규화
cx, cy, width, height


- YOLO에서 주로 사용
- 이미지 크기가 달라도 동일한 기준으로 좌표 표현 가능
④ 좌상단 및 크기 좌표 (Top-Left Coordinates)
- 이미지 원점을 기준으로 좌상단 위치와 박스의 너비, 높이로 표현
x, y, width, height


정규화를 하는 이유
- 픽셀 좌표는 이미지 크기에 따라 값이 달라짐
- 이미지 크기가 달라도 동일한 기준으로 좌표를 표현하기 위해 정규화 사용
- 일반적으로 이미지의 가로 및 세로 크기로 나누어 0~1 범위로 변환

12. 객체 검출의 평가지표
12-1. IoU (Intersection over Union)
예측한 Bounding Box와 정답 Bounding Box가 얼마나 겹치는지 측정하는 지표
\[
IoU = \frac{교집합의\ 넓이}{합집합의\ 넓이}
\]

- 0에 가까울수록 겹치는 영역이 적음
- 1에 가까울수록 두 박스가 정확하게 겹침
IoU Threshold
- IoU ≥ 0.5: 일반적으로 정답과 일치하는 것으로 판단하는 기준 (AP50)
- IoU ≥ 0.75: 더 엄격한 기준 (AP75)
12-2. TP / FP / FN
용어	의미	설명
TP	True Positive	정답 박스와 IoU 기준을 만족하고 클래스도 일치
FP	False Positive	정답이 아니거나 잘못된 클래스 또는 중복 예측
FN	False Negative	정답 객체를 찾지 못한 경우

주의사항
- 정답 박스 하나에는 예측 박스 하나만 TP로 인정
- 같은 물체에 박스 3개를 예측했다면 하나만 TP, 나머지 두 개는 FP가 될 수 있음
12-3. NMS (Non-Maximum Suppression)
객체 탐지 모델이 동일한 객체 주변에 여러 개의 Bounding Box를 생성하는 문제를 해결하기 위한 후처리 기법

목적
- 중복된 Bounding Box 제거
- 신뢰도가 높은 박스만 남김
- 불필요한 예측 감소
주요 용어
- Confidence Score
  - 해당 박스에 객체가 존재하고 특정 클래스에 속한다고 모델이 판단하는 신뢰도 점수
- Confidence Threshold
  - 신뢰도 기준값
  - 기준보다 낮은 박스는 제거
- NMS IoU Threshold
  - 선택된 박스와 다른 박스의 IoU가 일정 기준 이상이면 중복 박스로 판단하여 제거
NMS 절차
1. Confidence Threshold보다 낮은 박스 제거
2. 남은 박스를 신뢰도 내림차순으로 정렬
3. 신뢰도가 가장 높은 박스 선택
4. 선택된 박스와 IoU를 계산
5. NMS Threshold 이상으로 겹치는 박스 제거
6. 남은 박스가 없어질 때까지 반복
7. 일반적으로 클래스별로 수행
12-4. AP / mAP (Average Precision)
AP (Average Precision)

객체 검출 모델이 정답을 얼마나 정확하고 빠짐없이 찾아내는지 평가하는 지표
- Confidence Score를 기준으로 예측 결과 정렬
- TP와 FP 판정
- Precision과 Recall 계산
- Precision-Recall 곡선 아래의 면적으로 AP 계산
AP를 사용하는 이유
- 확실한 박스 1개만 생성하는 경우
  - 잘못된 예측은 적지만 대부분의 객체를 놓칠 수 있음
- 박스를 수백 개 생성하는 경우
  - 정답을 많이 찾을 수 있지만 중복 예측이 많아 FP가 증가할 수 있음
AP는 이러한 Precision과 Recall의 균형을 종합적으로 평가함.

mAP (Mean Average Precision)
- 여러 클래스의 AP를 평균한 값
- 객체 검출 모델의 전체 성능을 평가할 때 사용

13. 객체 검출 모델의 계열
13-1. 2-Stage 계열 모델
객체가 있을 만한 후보 영역을 먼저 찾고 이후 분류 및 위치 보정을 수행

처리 절차
1. Region Proposal
   - 객체가 존재할 가능성이 높은 후보 영역 탐색
2. Classification
   - 후보 영역의 객체 종류 분류
   - Bounding Box 위치 보정
특징
- 일반적으로 높은 정확도
- 처리 속도가 상대적으로 느림
- 정밀도가 중요한 의료 영상 검출 등에 활용
13-2. 1-Stage 계열 모델
후보 영역을 별도로 추출하지 않고 한 번에 객체의 위치와 클래스를 예측

대표 모델
- YOLO (You Only Look Once)
- SSD (Single Shot MultiBox Detector)
- RetinaNet
YOLO
- 이미지를 격자 형태로 나누어 객체의 위치와 클래스를 동시에 예측
- 실시간 객체 탐지에 강점
- Streaming Data 및 Live Data 처리에 적합
13-3. Transformer 계열 모델
- Transformer 구조를 활용하여 객체의 위치와 클래스를 예측
- 객체를 집합(Set) 형태로 한 번에 예측하는 방식 활용
대표 모델
- DETR
  - Bounding Box를 집합 형태로 예측
  - 중복 예측을 줄이는 구조로 NMS가 필요하지 않음
- RT-DETR
  - 실시간 객체 탐지를 목표로 개선된 DETR 계열 모델
- D-FINE
  - 객체 검출의 정밀도를 개선하기 위한 Transformer 기반 모델

14. YOLO 모델 구조
14-1. YOLO란?
YOLO (You Only Look Once)

이미지를 한 번에 분석하여 객체의 위치와 클래스를 동시에 예측하는 객체 검출 모델
14-2. YOLOv8 Nano 모델 구조
YOLO의 주요 구성 요소는 Backbone, Neck, Head로 구분
① Backbone
이미지에서 특징을 추출하는 영역
- 이미지의 해상도를 줄임
- 채널을 확장하여 다양한 특징 추출
- 선, 모서리, 질감, 형태 등 기본적인 특징부터 추상적인 특징까지 학습
주요 구성
- Convolution
  - 합성곱 연산을 통해 이미지의 특징 추출
  - 해상도를 줄이고 채널 수를 확장
- C2f
  - 특징을 효율적으로 전달하고 학습하는 블록
  - 입력 특징을 여러 경로로 나누어 일부는 깊게 처리하고 일부는 전달
  - 특징 재사용 및 정보 흐름 개선
- SPPF (Spatial Pyramid Pooling Fast)
  - 다양한 크기의 영역에서 문맥 정보를 추출
  - Max Pooling을 연속적으로 수행
  - 연산 효율을 높인 Spatial Pyramid Pooling 구조
Backbone의 출력
- P3
- P4
- P5
서로 다른 해상도와 의미 정보를 가진 특징 맵
② Neck
Backbone에서 추출한 서로 다른 크기의 특징을 결합하여 객체의 위치와 종류를 파악하는 영역

FPN (Feature Pyramid Network)
- 깊은 Layer의 의미 정보를 얕은 Layer로 전달
- 작은 객체부터 큰 객체까지 다양한 크기의 객체를 탐지할 수 있도록 도움
PAN (Path Aggregation Network)
- 얕은 Layer의 위치 정보를 깊은 Layer로 전달
- 위치 정보를 보완하여 객체의 위치 예측에 도움
③ Head
최종적으로 객체의 위치와 클래스를 예측하는 영역
- Bounding Box 예측
- Class 분류
- Confidence Score 계산
- 여러 크기의 특징 맵을 활용하여 객체 탐지

15. Small Object Detection (소형 객체 탐지)
15-1. 소형 객체란?
일반적으로 32x32 픽셀 미만의 작은 객체를 의미하며, 전체 이미지에서 차지하는 면적이 매우 작은 객체
15-2. 소형 객체 탐지가 어려운 이유
- CNN은 깊은 Layer로 갈수록 해상도가 낮아짐
- 깊은 Layer에서 의미 정보는 풍부해지지만 작은 객체의 세부적인 위치 정보가 소실될 수 있음
- 소형 객체는 1~2픽셀 수준으로 축소될 수 있음
- IoU가 작은 위치 변화에도 민감하게 반응
- 학습 초기에는 예측 박스와 정답 박스가 겹치지 않는 경우가 많음
15-3. 소형 객체 탐지의 해결 방법
① 데이터 관점: 고해상도 입력
- 입력 이미지의 해상도를 높임
- 작은 객체의 세부 정보 보존
- 단점: 연산량 및 메모리 사용량 증가
② 입력 처리 관점: 타일링 / SAHI
SAHI (Slicing Aided Hyper Inference)
- 이미지를 작은 영역으로 나누어 각각 추론
- 겹치는 영역을 설정하여 객체가 잘리는 문제 완화
- 각 영역의 탐지 결과를 병합
특징
- 모델 구조를 변경하지 않고 적용 가능
- 기존 객체 검출 모델에 적용하기 쉬움
- 이미지 내 객체의 상대적인 크기를 키워 탐지 성능 개선
- 추론 횟수가 증가하여 처리 시간이 늘어날 수 있음
③ 신경망 구조 관점: FPN
FPN (Feature Pyramid Network)

CNN의 해상도와 의미 정보 사이의 Trade-off를 보완하는 구조
- 얕은 Layer
  - 해상도가 높음
  - 위치 정보가 정확함
  - 의미 정보가 상대적으로 부족
- 깊은 Layer
  - 해상도가 낮음
  - 위치 정보가 상대적으로 부족
  - 의미 정보가 풍부함
Bottom-Up + Top-Down 구조
- Bottom-Up
  - 얕은 Layer에서 깊은 Layer 방향으로 특징 추출
  - 해상도는 낮아지고 의미 정보는 풍부해짐
- Top-Down
  - 깊은 Layer의 의미 정보를 얕은 Layer로 전달
  - 작은 객체의 특징을 보완
④ 위치 정보 전달: PAN
PAN (Path Aggregation Network)
- 얕은 Layer가 가진 위치 정보를 깊은 Layer로 전달
- 다양한 해상도의 특징을 결합
- 객체 위치 예측 성능 개선
⑤ 손실함수 및 평가지표: IoU 개선
기존 IoU의 문제점
- 예측 박스와 정답 박스가 겹치지 않으면 IoU가 0
- IoU 기반 손실함수에서 위치를 개선할 방향에 대한 학습 신호가 부족할 수 있음
- 소형 객체는 이러한 문제가 더 자주 발생
GIoU (Generalized IoU)
- 두 박스를 모두 포함하는 최소 외접 박스를 계산
- 외접 박스와 두 박스 사이의 관계를 활용하여 추가적인 학습 신호 제공
- 두 박스가 겹치지 않는 상황에서도 학습 가능
DIoU (Distance IoU)
- IoU와 두 박스 중심점 사이의 거리를 함께 고려
- 중심점 간 유클리드 거리를 활용
- 박스가 겹치지 않는 경우에도 위치를 개선할 방향 제공
CIoU (Complete IoU)
- IoU
- 두 박스 중심점 사이의 거리
- 박스의 종횡비(Aspect Ratio)
위 세 가지 요소를 함께 고려하여 박스 위치를 개선
⑥ 데이터 배정 관점: ATSS
ATSS (Adaptive Training Sample Selection)
- 객체 탐지 모델에서 학습에 사용할 양성 샘플(Positive Sample)을 선택하는 방법
- 객체의 크기와 위치 등을 고려하여 학습 대상 선정
- 작은 객체에 대한 학습 신호를 효과적으로 유지하는 데 도움