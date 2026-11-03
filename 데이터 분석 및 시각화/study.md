데이터 분석 및 시각화 학습 자료
목표: 복잡한 데이터에서 인사이트 도출
- 데이터 분석이란?
    원본 데이터에서 유의미한 정보를 얻어내는 과정
  → AI 모델 설계의 기초
    TIP. 모델의 성능 < 데이터의 깔끔함
- 기본 프로세스
    수집/저장 → 탐색/계획 → 정제/가공 → 인사이트 도출
    TIP. 필요한 데이터를 뽑아내는 능력이 필요하다
- 데이터 타입
  - 숫자형 데이터
      연속형
          소수점 값이 존재, 구간별 분포가 존재, 회귀분석에 적합
    
      이산형
          정수로만 표현, 카운트 데이터가 대표적, 포아송 분포, 이산확률분포 적용, 횟수 개수 분석에 적합
  - 범주형 데이터 (그룹으로 묶을 수 있는 형태)
      명목형
      범주 간 순서 없음, 자주 사용하진 않음
      순서형
      명확한 순서나 등급이 존재, 스피어만 상관계수 사용
      TIP. 순서형은 평균값을 구하는 것이 아니라 중앙값이나 최빈값을 이용한다.
Pandas 기초
- Python의 데이터 분석 및 조작을 위한 핵심 라이브러리
    numpy는 숫자 전용 / pandas 엑셀처럼 행,열 이용할 때
    TIP. import pandas as pd 추가로 약자로 자주 씀
  - series
      1차원 배열로 인덱스와 값의 쌍으로 구성
    인덱스: 값 ex) 김철수: 13세, 김영희: 16세
  - 생성 문법
      pd.Series(데이터, index = 라벨목록)
  - dataframe
      행: 하나의 객체를 의미(관측 대상)
    컬럼: 데이터 속성(데이터의 속성)
      생성 문법
    pd.DataFrame()
    pd.DataFrame(patient_records, index=patient_names, columns=columns)
CSV 파일
- 저장, 불러오기
    저장 방법
  변수.to_csv(원하는 파일명,
  index=False,                  # 행 번호(인덱스)는 저장하지 않음
  encoding='utf-8-sig')
    불러오기
  변수.read_csv(원하는 파일명)
  판다스는 인덱스를 자동으로 불러옴
- 데이터 탐색 메소드
    df = pd.read_csv('clinic_health_data.csv')
  df.shape - 행,열을 알려줌
  df.shape[0] - 행 개수 / df.shape[1] - 열 개수
  
  df.head(n) - n행까지 미리보기
  df.tail(n) - n행부터 미리보기
  df.info( ) - 데이터 요약을 보여줌 (결측치(비어있는 값)을 빠르게 확인 가능)
  df.describe( ) - 정보 설명( 평균, 최대,최소 값 등)
  df - 전체 미리보기
  value_counts( )  - 특정 열(Series)에 있는 고유한 값들의 빈도수를 계산하여 많은 순서대로 반환하는 함수
  df['흡연'].value_counts()
고급 인덱싱 기술
- iloc vs loc
    integer location의 약자로 (0부터 시작함)
    iloc[행(row), 열(column)] - 인덱스 번호로 정보를 가져옴
  df.iloc[:3] df의 0-2번째 행 선택 [1,3,5] 이런 식으로도 가능함
    loc
  loc[조건, 열라벨] - 라벨(컬럼명과 인덱스명)을 기반으로 데이터 선택
  슬라이싱 시 끝에 라벨이 포함됨
  인덱스 번호로 뽑을 시 .loc[df.index[-1], '이름']
    index값 바꾸기
  set.index('환자ID')
  0, 1, 2, … → p001, p002, p003, …
조건부 필터링
- Boolean 마스크 [  ]
    조건 결과를 True/False 값으로 나열시키고
    True의 결과값만 추출
  df[ ] (마스크)를 씌우고 True/False 값 추출 → [ ] 한번 더 씌우면 True 값만 추출→ len( ) 함수로 수 확인
    ex) age_mask = df['나이'] >= 50  → [true, false, true, true, …]
  df[age_mask] → [true, true, true, …]
    조건문 작성시 &(and), |(or),~(not)으로 작성
평균은 대표값으로 쓸 수 없다. ex) 심슨의 역설
- 컬럼 추가, 제거
  - 새로운 컬럼을 추가하고 싶을 때
      df['병원'] = '서울대병원' → 병원 행과 서울대 병원 컬럼 추가하고 싶을 때
  - 수정하고 싶을 땐
      수정변수 = df['병원'] 조건
      df.loc[수정변수, '원하는 열 명'] = '원하는 결과 값'
  - 원하는 열만 가져오기
      df[['이름', '나이', '원하는 거 아무거나']]
  - 값 추가 (행 추가)
      직관적인 방법 : 직접 다 넣기
    df['데이터프레임'] = ['김길동', 32, 170, …]
    
    여러명 추가할 때
    concat() 함수 이용
    
    기존 데이터프레임에 합치기
    df_extended = pd.concat([df, new_df], ignore_index=True)
  - 데이터 삭제 방법 - 열(컬럼)
      drop() 함수를 이용한다
    drop(['원하는 열', '원하는 다른열'], axis=1)
  inplace = False (기본값): 새로운 DataFrame 반환, 원본 유지
  inplace = True: 원본 DataFrame 직접 수정하고 None 반환
  axis = 0 (기본값): 행(인덱스) 삭제 (표현 안 해도 됨)
  axis = 1 :열(컬럼) 삭제
  - 데이터 삭제 방법 - 행
      df.drop(원하는 행)
    df.drop([df.index[원하는 행])
    df.drop([1, 3, 5]) - 선택한 행 삭제
    df.drop(df[조건부 작성한 행].index # 조건문 작성하여 만족한 행 삭제
  - 열과 행 동시 삭제
      ex) df_removed = df.drop(
    index=df.(조건)index,
    columns=['조건', '원하는 열']
    )
- 데이터 분석
  - 중심경향성 분포
      데이터가 어느 값 주변에 모여있는지 나타내는 대푯값
    - 대푯값 (3m)
        평균(Mean)
      중앙값(Median) - 정중앙에 위치한 값
      최빈값(Mode) - 빈도수가 가장 높은 값
  - 분산성
      데이터가 중심값에서 얼마나 퍼져있는지를 나타냄
      분산: 값이 흩어져 있는 정도의 값(.var)
    범위: 최댓값(.max) - 최솟값(.min) (데이터가 퍼져있는 전체 폭)
    표준편차: 분산을 제곱한 값(.std)
      TIP. 분산 보다는 표준편차가 실제 해석에 유용함(표준편차는 단위가 같기 때문에 유리)
  - 빈도
      절대빈도: .value_counts( ) 함수를 이용 - 원래 값이 몇개 들었는가 나옴
    상대빈도: (normalize=True): 전체 합이 1이 되도록 비율 변환 시켜 줌
  - 교차분석
      변수의 빈도를 교차로 묶어 표로 만들고 유의미한 값이 있는지 확인
    .crosstab() 함수를 이용
  - 그룹별 분석
      groupby( ) 함수
    정의대로 컬럼을 나눔 
      .agg 함수
  - 상관관계
      .corr(method='pearson') 기본값 함수
    .corr(method='spearman') 데이터에 순위가 있거나 직선 아니지만 한 쪽이 커질 때 다른 쪽도 커지는 경향을 볼 때 사용
- 데이터 전처리
  - 데이터 정제
      더러운 데이터 깔끔하게 만드는 단계
    - 결측치: 누락 데이터(NaN, None, Null)
        결측치가 있으면 AI 모델이 학습을 시작조차 못함
      - 결측치 탐지 방법
          df_파일명.info() 로 확인
        isnull( ) - 결측치 위치를 True로 나머지는 False로 표시 (isna( )도 같지만 덜 사용)
        isnull( ).sum( ) - 컬럼별 결측치 수량 확인
        isnull( ).sum( ).sum( ) - 전체 결측치 확인
          notnull( ) 반대로 정상 값만 확인
      - 결측치 패턴 분석
          any(axis = 1) 각 행에 결측치가 하나라도 있는지 확인
        isna( ).all( ) 모든 값이 결측치인 컬럼 확인
      - 결측치 처리 방법
        - 결측치를 삭제
            .dropna( ) 로 결측치 있는 행/열 삭제
          (axis = 0) 행 삭제 (기본값), (axis=1) 열 삭제, (subset=['컬럼명']),
          (thresh = 숫자)(최소 유효값)
        - 결측치를 다른 값으로 채우기
            df['컬럼'].fillna(값)
          value 대체할 값
          ex) .fillna(value = 1) None 자리를 1로 채우겠다
          .fillna(value).mean 평균값으로 채우겠다.
          
          inplace=True 원본 데이터 직접 수정
        - 앞 값으로 채우기
          .ffill( )
    - 중복 데이터 탐지 및 제거
        중복 데이터 찾기
      duplicated( subset = [ ] 중복된 행을 True / False 로 확인
        중복 행 제거
      drop_duplicates( )
      keep = last (마지막으로 나타난 행 유지 ), keep = first (첫 번째로 나타난 행 유지 (기본값))
  - 이상치 탐지
      이상치란 다른 데이터들과 현저하게 다른 값들
      IQR 방법으로 탐지
      (Q1 - 1.5) x IQR ~ (Q3 + 1.5) x IQR
  - 데이터 타입 문제
      AI가 처리할 수 없는 데이터 타입으로 들어간 경우
    ex) 나이가 문자열로 들어가면 평균을 구할 수 없음
    - 강제 타입 변환
        astype( ) 오류가 종종 발생할 수 있어 자주 사용하지는 않음
    - pandas로 변환 (주로 사용)
        pd.to_numeric( ) 문자열을 숫자로 변환
        pd.to_datetime( )문자열을 날짜로 변환
- 데이터 시각화 (그래프로 만드는 코딩은 직접말고 AI 이용하자)
  - Matplotlib
      파이썬의 기본이 되는 시각화 라이브러리
    - 선그래프 - 시간에 따른 변화를 나타낼 때
      # 차트 그리기
      plt.figure(figsize=(8, 5))   # 새로운 차트 생성 및 크기 설정
      
      # 선 그래프 그리기
      plt.plot(days, blood_pressure,    # x, y 데이터
               marker='o',              # 점 모양 표시
               color='red',             # 선 색상
               linewidth=2)             # 선 두께
      
      # 차트 꾸미기
      plt.title('환자 혈압 변화 추이', fontsize=14)      # 제목 및 글자 크기
      plt.xlabel('치료 일수', fontsize=12)             # x축 라벨
      plt.ylabel('수축기 혈압 (mmHg)', fontsize=12)    # y축 라벨
      plt.grid(True, alpha=0.5)                     # 격자 표시, 투명도
      
      plt.show()  # 차트를 화면에 출력
    - 막대그래프 - 변수간 비교할 때
      # 차트 그리기
      plt.figure(figsize=(8, 5))  # 새로운 차트 생성 및 크기 설정
      
      # 막대 차트 그리기
      plt.bar(departments, patient_counts,               # x, y 데이터
              color=['skyblue', 'lightgreen', 'salmon', 'gold'],  # 막대별 색상
              alpha=0.7)                                 # 투명도
      
      # 차트 꾸미기
      plt.title('진료과별 환자 수')
      plt.ylabel('환자 수 (명)')
      plt.xticks(rotation=45)  # x축 라벨 45도 회전
      
      plt.show()
  - Seaborn
      좀 더 개선된 라이브러리
    - 빈도그래프 (Countplot) - 범주형 데이터 볼 때
        sns.countplot 으로 그래프 생성
      # 당뇨병 데이터로 환자 특성 분포 분석
      plt.figure(figsize=(6, 4))
      
      # 성별별 환자 분포
      sns.countplot(data=df, x='Sex',            # 그릴 데이터 (성별 컬럼)
                    hue='Sex',                   # 색상 구분 기준
                    legend=False,                # 범례 숨김
                    palette='Set2')              # 색상 테마 (파스텔톤)
      
      plt.title('성별 분포')                     # 차트 제목
      plt.xlabel('성별')                         # X축 이름
      plt.ylabel('환자 수')                      # Y축 이름
      plt.xticks([0, 1], ['여성', '남성'])       # X축 데이터: 숫자(0,1)를 한글로 변경
      
      plt.show()  # 차트를 화면에 출력
      
      print("\n📊 환자 구성 분석:")
      print(f"여성 비율: {(df['Sex']==0).mean()*100:.1f}%")
    - 히스토그램 (Histplot + Hue) - 그룹별 분포를 볼 때
        연속형 데이터, 순위형 데이터, 그룹별 패턴
      # BMI 분포 히스토그램 (당뇨병 여부별)
      plt.figure(figsize=(12, 5))  # 2개 차트용 캔버스
      
      #  범례 표기를 위해 0/1 숫자를 한글로 변환
      df['Label'] = df['Diabetes_binary'].replace({0.0: '정상', 1.0: '당뇨병'})  # 여러개를 한꺼번에 변환
      
      # 1. 첫 번째 차트: BMI 분포 분석
      plt.subplot(1, 2, 1)                  # 1행 2열 중 첫 번째 칸 선택
      sns.histplot(data=df, x='BMI',        # 분석할 데이터
                  hue='Label',              # 비교 그룹 (정상 vs 당뇨)
                  bins=30,                  # 막대 개수 (데이터 세분화 정도)
                  alpha=0.7,                # 투명도
                  palette='Reds')           # 색상 테마
      
      plt.title('당뇨병 여부별 BMI 분포')
      plt.xlabel('BMI (체질량지수)')
      plt.ylabel('환자 수')
      
      # 2. 두 번째 차트: 건강상태 분포 분석
      plt.subplot(1, 2, 2)                  # 1행 2열 중 두 번째 칸 선택
      sns.histplot(data=df, x='GenHlth',    # 분석할 데이터 (순위형 점수)
                  hue='Label',              # 비교 그룹
                  bins=5,                   # 점수 범위 (1~5)
                  alpha=0.7,                # 투명도
                  palette='viridis',        # 색상 테마
                  discrete=True)            # 정수값 처리 (막대를 숫자에 딱 맞춤)
      
      plt.title('당뇨병 여부별 전반적 건강상태')
      plt.xlabel('건강상태 (1=매우좋음 ~ 5=매우나쁨)')
      plt.ylabel('환자 수')
      
      # 차트 위치 조정
      plt.tight_layout()  # 레이아웃 최적화
      plt.show()  # 차트를 화면에 출력
    - 박스플롯 (Boxplot) - 데이터의 중앙값, 분산 등을 한번에 볼 때
      # 차트 크기 및 스타일 설정
      plt.figure(figsize=(12, 5))
      
      # 1. 첫 번째 차트: 당뇨병 여부별 BMI 분포
      plt.subplot(1, 2, 1)
      sns.boxplot(data=df,
                  x='Diabetes_binary',   # x축: 그룹 구분
                  y='BMI',               # y축: BMI 데이터
                  hue='Diabetes_binary', # 색상 구분
                  palette='coolwarm',    # 색상 테마
                  legend=False)          # 범례 숨김
      plt.title('당뇨병 여부별 BMI 분포')
      plt.xlabel('진단 여부')
      plt.ylabel('BMI (체질량지수)')
      plt.xticks([0, 1], ['정상', '당뇨병'])
      # 💡해석: 정상군에 비해 당뇨군의 BMI 분포가 오른쪽(높은 수치)으로 치우쳐 있어, 비만이 주요 위험 인자임을 확인 가능
      
      # 2. 두번째 차트: 당뇨병 여부별 연령대 분포
      # 연령대 라벨 리스트 생성 (1~13 매핑)
      age_labels = ['18-24', '25-29', '30-34', '35-39', '40-44', '45-49',
                    '50-54', '55-59', '60-64', '65-69', '70-74', '75-79', '80+']
      
      plt.subplot(1, 2, 2)
      sns.boxplot(data=df,
                  x='Diabetes_binary',   # x축: 그룹 구분
                  y='Age',               # y축: 연령대 (1~13단계)
                  hue='Diabetes_binary', # 색상 구분
                  palette='pastel',      # 색상 테마
                  legend=False)          # 범례 숨김
      
      plt.title('당뇨병 여부별 연령대 분포')
      plt.xlabel('진단 여부')
      plt.ylabel('연령대')
      plt.xticks([0, 1], ['정상', '당뇨병'])
      plt.yticks(ticks=range(13), labels=age_labels, rotation=45)
      # 💡해석:  당뇨군은 정상군보다 박스가 전체적으로 상단에 위치하여, 연령대가 높을수록 당뇨 발병 비중이 커지는 '연령의 영향력' 확인 가능
      
      plt.tight_layout()
      plt.show()
    - 히트맵 (Heatmap) - 상관관계 비교 할 때
      # 히트맵 차트
      
      plt.figure(figsize=(10, 6))  # 히트맵용  캔버스
      mask = np.triu(np.ones_like(correlation_matrix, dtype=bool))  # 상삼각 마스킹
      
      sns.heatmap(correlation_matrix,  # 상관계수 데이터프레임
                  mask=mask,  # 중복 제거용 마스크
                  annot=True,  # 숫자 표시
                  cmap='RdBu_r',  # 빨강-파랑 색상맵
                  center=0,  # 0 중심 색상
                  square=True,  # 정사각형 셀
                  fmt='.2f',  # 소수점 2자리
                  cbar_kws={'label': '상관계수', 'shrink': 0.8})  # 컬러바 설정
      
      plt.title('당뇨병 데이터: 의료 변수들 간의 상관관계', fontsize=18, pad=20)
      plt.xticks(rotation=45, ha='right', fontsize=10)  # x축 라벨 회전
      plt.yticks(rotation=0, fontsize=10)  # y축 라벨
      plt.tight_layout()  # 레이아웃 최적화
      plt.show()  # 차트를 화면에 출력
TIP. 명확한 우선, 정절한 차트 선택, 통계적 의미 부여