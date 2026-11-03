16. 객체 검출 데이터 처리
16-1. Pascal VOC에서 YOLO 형식으로 변환
YOLO 모델에서 학습할 수 있도록 기존 객체 검출 데이터를 YOLO 형식으로 변환
16-2. YOLO 데이터 폴더 구조
학습 데이터와 검증 데이터를 구분하고 각 폴더 안에 이미지와 라벨 텍스트 파일을 저장
dataset/
├── images/
│   ├── train/
│   └── val/
│
├── labels/
│   ├── train/
│   └── val/
│
└── data.yaml


16-3. data.yaml
- 학습 및 검증 이미지의 경로 지정
- 클래스 개수 지정
- 클래스 이름 지정
- YOLO 모델이 데이터를 불러올 수 있도록 설정
16-4. Label Text 파일 구성
이미지 한 장에 여러 객체가 존재할 수 있으며, 객체 하나당 한 줄로 라벨 정보 기록

YOLO 라벨 형식
class_id cx cy width height


항목	의미
class_id	객체 클래스 번호
cx	Bounding Box 중심 X 좌표
cy	Bounding Box 중심 Y 좌표
width	Bounding Box 너비
height	Bounding Box 높이

정규화 좌표
- 이미지의 가로 및 세로 크기를 기준으로 좌표 정규화
- 모든 좌표와 크기를 0~1 범위로 표현
16-5. 객체 탐지 기능의 단계별 분류
객체 탐지 기능을 목적에 따라 4단계로 구분
구분	기능
Single	추간공의 위치만 탐지
Side	추간공의 위치 및 좌우 구분
Grade	협착 등급 판정 (좌우 구분 제외)
Full	위치 탐지, 좌우 구분, 협착 등급 판정 모두 수행


17. 핵심 개념 요약
개념	핵심 내용
Computer Vision	컴퓨터가 이미지와 영상을 인식하고 분석하는 기술
CNN	합성곱 연산으로 이미지 특징을 자동 추출
Convolution	필터를 이용한 이미지 특징 추출
Pooling	특징 맵의 크기를 줄이는 작업
Fully Connected	추출한 특징을 종합하여 최종 예측
Transfer Learning	사전학습된 모델의 가중치 재사용
Feature Extraction	기존 가중치를 동결하고 새로운 분류기 학습
Fine-Tuning	기존 모델의 일부 Layer를 재학습
ResNet	Skip Connection을 활용한 잔차 학습
ViT	이미지를 Patch 단위로 나누어 Attention 학습
Data Augmentation	이미지 변형으로 학습 데이터 확장
Object Detection	객체의 위치와 종류를 동시에 예측
Bounding Box	객체의 위치를 나타내는 사각형
IoU	예측 박스와 정답 박스의 겹치는 정도
NMS	중복된 예측 박스 제거
AP	객체 탐지의 Precision-Recall 성능 평가
mAP	클래스별 AP의 평균
YOLO	빠른 실시간 객체 탐지 모델
FPN	깊은 Layer의 의미 정보를 얕은 Layer로 전달
PAN	얕은 Layer의 위치 정보를 깊은 Layer로 전달
SAHI	이미지를 잘라 소형 객체 탐지 성능 개선
GIoU / DIoU / CIoU	IoU를 개선하여 박스 위치 학습을 보완