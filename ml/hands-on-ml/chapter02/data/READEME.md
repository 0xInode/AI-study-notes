📁 데이터 파일 설명 (data/ 폴더)  
이 프로젝트에서는 전처리된 데이터와 모델을 재사용하기 위해 .pkl 파일들을 저장했습니다.  
이 파일들은 전체 파이프라인 실행 없이도 바로 예측 및 분석 작업을 수행할 수 있도록 도와줍니다.

- housing_prepared.pkl	전처리 파이프라인(full_pipeline)을 거친 훈련 데이터셋 (X_train)
- housing_labels.pkl	훈련용 타겟값(y_train)
- final_model.pkl	GridSearchCV로 튜닝된 최종 랜덤 포레스트 회귀 모델
- full_pipeline.pkl	수치형 + 범주형 처리 포함 전체 전처리 파이프라인 객체

🔁 필요 시 joblib.load() 또는 pickle.load()를 사용해 로드할 수 있습니다.

🔄 예시 코드 (로컬에서 불러오기)
import joblib

X_train = joblib.load("data/housing_prepared.pkl")  
y_train = joblib.load("data/housing_labels.pkl")  
model = joblib.load("data/final_model.pkl")  
pipeline = joblib.load("data/full_pipeline.pkl")  
