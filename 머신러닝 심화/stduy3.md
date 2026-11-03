16. 대용량 파일 처리 팁
16.1 Google Drive에서 데이터 바로 불러오기
Google Drive에 저장된 CSV 파일을 URL을 통해 불러올 수 있다.
import pandas as pdfile_id = "1KbeeIi13TTl01YnVEhvg_oiFBktFk3-I"url = f"https://drive.google.com/uc?id={file_id}"df = pd.read_csv(url)df.head()



16.2 데이터 읽기 속도 확인
%%timeitdf = pd.read_csv(url)



- %%timeit: 코드 실행 시간을 반복 측정하는 매직 명령어
16.3 데이터 저장 방식 비교
df.to_csv("data.csv", index=False)  # 기본 CSVdf.to_pickle("data.pkl")            # Pickledf.to_parquet("data.parquet")       # Parquet



저장 형식	특징
CSV	범용성이 높고 다른 프로그램과 호환성이 좋음
Pickle	파이썬 객체 저장에 유용하며 읽기 속도가 빠를 수 있음
Parquet	컬럼 기반 저장 형식으로 용량 및 분석 효율에 유리


17. 핵심 개념 요약
구분	핵심 개념
KNN	가까운 K개 데이터를 이용한 예측
거리 측정	유클리드, 맨해튼, 해밍, 민코프스키
PCA	주성분 분석을 통한 차원 축소
K-Means	중심점 기반 군집화
Mean Shift	밀도 기반 군집화
DBSCAN	밀도와 이웃 반경 기반 군집화
GMM	확률 분포 기반 군집화
Feature Engineering	모델에 적합한 Feature 생성 및 변환
Cross Validation	데이터를 나누어 반복 검증
SVM	최적의 결정 경계 탐색
Bagging	독립 모델의 예측 결과 결합
Random Forest	여러 결정 트리를 결합한 모델
Boosting	이전 모델의 오차를 보완하는 방식
XGBoost	정규화와 최적화를 적용한 부스팅
LightGBM	대용량 데이터에 효율적인 부스팅
CatBoost	범주형 변수 처리에 특화된 부스팅
Stacking	서로 다른 모델의 예측 결과 결합
SHAP	모델의 예측 결과 설명
HPO	하이퍼파라미터 최적화