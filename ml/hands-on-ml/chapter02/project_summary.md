이것은 《핸즈온 머신러닝》 2판의 Chapter 2 내용을 따라가며 아래 단계를 실습한 내용입니다:

# Get the data

1. **작업환경 설정**
   - 가상환경 생성 및 필수 패키지 설치 (`jupyter`, `pandas`, `matplotlib`, `scikit-learn` 등)

2. **데이터 다운로드 및 준비**
   - `housing.tgz` 압축 파일을 URL에서 다운로드
   - `housing.csv` 파일로 압축 해제 및 로딩
   - `pandas`를 이용해 데이터프레임 구조 확인 (`head()`, `info()`, `describe()`)

3. **데이터 탐색**
   - 카테고리 필드 확인 (`ocean_proximity`)
   - 각 필드의 히스토그램 시각화 (`housing.hist()`)

4. **테스트셋 분리**
   - 무작위 샘플링 (`train_test_split`)
   - 해시 기반 샘플링 (ID 고정)
   - **소득 수준(`median_income`) 기반 stratified sampling** 구현

5. **Stratified Sampling 적용**
   - `income_cat` 필드를 기반으로 계층적 분할 수행
   - 분포 확인 → 무작위 샘플보다 대표성이 높음
   - 사용 후 `income_cat` 필드 제거
  


# Discover and visualize the data to gain insights

1. **훈련 세트 복사**
   - `strat_train_set`을 복사하여 탐색용 `housing` 데이터프레임 생성

2. **지리적 데이터 시각화**
   - 위도(`latitude`)와 경도(`longitude`) 산점도 생성
   - `alpha` 값을 활용해 밀도 시각화
   - 인구(`population`)를 원 크기로, 주택 가격(`median_house_value`)을 색상으로 표현

3. **상관관계 분석**
   - 수치형 특성 간 상관계수(`.corr()`) 계산
   - `median_house_value`와 가장 관련 깊은 특성 탐색

4. **산점도 행렬 (scatter matrix)**
   - 주요 특성들 간의 시각적 관계 분석 (`median_income`, `total_rooms` 등)

5. **소득과 주택 가격의 관계 분석**
   - `median_income`과 `median_house_value` 산점도
   - 가격 상한선($500,000) 등의 데이터 이상치 확인

6. **파생 특성 생성**
   - `rooms_per_household`, `bedrooms_per_room`, `population_per_household` 등 새 특성 생성
   - 새 특성들과 주택 가격 간 상관계수 확인
  
# Prepare the Data for Machine Learning Algorithms

1. **결측치 처리**

   - total_bedrooms 속성의 결측값 처리
   - 행 삭제: dropna()
   - 열 삭제: drop()
   - 중앙값으로 대체: fillna() 또는 Imputer(strategy="median")

2. **범주형 특성 처리**

   - LabelEncoder로 텍스트 → 정수 인코딩
   - OneHotEncoder 또는 LabelBinarizer로 원-핫 인코딩

3. **사용자 정의 변환기**

   - CombinedAttributesAdder 클래스로 파생 특성 자동 생성

   - add_bedrooms_per_room 하이퍼파라미터로 조정 가능

4. **특성 스케일링**

   - MinMaxScaler: 정규화 (0~1)

   - StandardScaler: 표준화 (평균 0, 분산 1)

5. **파이프라인 구성**

   - Pipeline으로 변환 순서 정의

   - FeatureUnion으로 수치형/범주형 변환 결합

   - DataFrameSelector 사용자 정의 변환기로 Pandas → NumPy 변환

# Select a Model and Train It

1. **모델 학습**

   - LinearRegression: RMSE 약 68,628 → 과소적합

   - DecisionTreeRegressor: 훈련셋 RMSE = 0 → 심각한 과적합

   - RandomForestRegressor: 훈련셋 RMSE 약 22,542 → 가장 우수한 성능

2. **교차 검증**

   - cross_val_score로 10-겹 교차 검증

   - 평균 RMSE와 표준편차로 모델의 일반화 능력 평가

   - 결정트리는 과적합으로 인해 평균 성능이 낮음

# Fine-Tune Your Model

1. **Grid Search**

   - GridSearchCV로 n_estimators, max_features 조합 탐색

   - 총 18개 조합 × 5겹 = 90번 학습

   - 최적 조합: n_estimators=30, max_features=6

   - RMSE 약 49,959

2. **특성 중요도 분석**

   - feature_importances_로 주요 특성 파악

   - median_income, bedrooms_per_room, rooms_per_household 중요

   - 일부 ocean_proximity 카테고리는 거의 기여하지 않음

# Present Your Solution

1. **최종 테스트셋 평가**

   - full_pipeline.transform()을 사용해 변환

   - 테스트셋에서 RMSE 약 48,209

   - 검증셋과 성능 유사함 → 과적합 심하지 않음

   - 하이퍼파라미터 조정 후 테스트셋을 이용해 성능 확정

# Launch, Monitor, and Maintain Your System

1. **운영 준비 및 배포**

   - 실제 데이터와 연결, 테스트 코드 작성

   - 실시간 성능 모니터링 설정

   - 입력 데이터 품질 모니터링 중요

2. **주기적 재학습 및 버전 관리**

   - 모델을 주기적으로 재학습해 데이터 드리프트 대응

   - 온라인 학습의 경우 상태 스냅샷 저장 필요

## 도출된 인사이트

- `median_income`, `bedrooms_per_room`, `rooms_per_household` 는 `median_house_value` 예측에 가장 **중요한 특성**으로 나타남  
- `bedrooms_per_room` 은 음의 상관관계가 강하며, 파생 특성 중 예측력 향상에 크게 기여  
- `DecisionTreeRegressor` 는 훈련 데이터에 과적합되어 실제 예측 성능이 낮음 → 단순 모델에 과도한 신뢰 금물  
- `RandomForestRegressor` 는 일반화 성능이 가장 우수하며, 하이퍼파라미터 튜닝으로 **`RMSE` 를 약 `49,959` 까지 감소**  
- `GridSearchCV` 를 통해 최적 하이퍼파라미터 조합(`n_estimators=30`, `max_features=6`)을 효율적으로 탐색 가능  
- `Pipeline` 과 `FeatureUnion` 을 활용한 데이터 전처리 자동화는 **재현성과 유지보수성**을 높임  
- 테스트셋 `RMSE` 가 교차 검증과 유사 → 모델의 **과적합이 심하지 않고 일반화 성능 안정적**  
- 모델 성능을 지속적으로 유지하려면 **데이터 품질 모니터링 및 정기 재학습** 체계가 필요함  
- 온라인 학습 시스템은 주기적인 **상태 저장 및 복구 전략** 마련이 중요함

## 사용된 기술

- Python 3.10+
- Pandas, Numpy, Matplotlib
- Scikit-learn

## 📁 참고
- [책 GitHub 저장소](https://github.com/ageron/handson-ml)
