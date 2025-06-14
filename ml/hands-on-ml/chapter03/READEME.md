Chapter 3 요약: 분류(Classification)

✅ 1. MNIST 데이터셋 소개 및 준비  
MNIST: 손글씨 숫자 이미지 데이터셋 (28x28, 0~9 숫자)  
데이터 로딩: fetch_openml()을 사용하여 X (이미지 데이터), y (레이블) 분리  
시각화: imshow()로 숫자 이미지 출력

✅ 2. 이진 분류 (Binary Classification)  
목표: 숫자 5를 맞추는 분류기 훈련 (y_train_5 = (y_train == 5))  
사용 모델: SGDClassifier  
평가 방법  
 - 교차 검증: cross_val_score(), StratifiedKFold  
 - 정확도, 정밀도(Precision), 재현율(Recall), F1 Score 계산  
 - 임의 분류기(Never5Classifier)와 비교  

✅ 3. 정밀도/재현율 트레이드오프  
Threshold 조정을 통해 Precision/Recall 간의 균형을 조정  
precision_recall_curve() 및 시각화로 이해  
원하는 정밀도(예: 90%)에 맞는 threshold 선택  

✅ 4. ROC 곡선 (Receiver Operating Characteristic)  
roc_curve()로 FPR(위양성율) vs TPR(재현율) 시각화  
roc_auc_score()로 모델 성능 비교  
SGDClassifier vs RandomForestClassifier 비교  

✅ 5. 다중 분류 (Multiclass Classification)  
숫자 0~9 분류  
알고리즘: SVC, SGDClassifier, OneVsRestClassifier  
decision_function()을 통해 클래스 점수 비교  

✅ 6. 스케일링 및 성능 향상  
StandardScaler를 사용한 특성 스케일링  
스케일링 후 정확도 향상 확인  

✅ 7. 에러 분석 (Error Analysis)  
confusion_matrix()로 클래스별 오차 확인  
정규화된 혼동 행렬 시각화로 주요 오차 파악  
특정 클래스 간 혼동 예시 시각화 (예: 3 vs 5)  

✅ 8. 멀티레이블 분류 (Multilabel Classification)  
예: 숫자가 7 이상인지 + 홀수인지 동시에 판단  
다중 타겟: y_multilabel = np.c_[cond1, cond2]  
모델: KNeighborsClassifier  
평가: f1_score(average='macro')  

✅ 9. 다중 출력 분류 (Multioutput Classification)  
예: 잡음이 섞인 숫자 이미지 → 원본 이미지 복원  
타겟 자체가 이미지 (다차원 벡터)  
모델: KNN 사용하여 이미지 복원  

✅ 10. 스팸 분류기 만들기  
데이터 준비  
 - SpamAssassin 공개 데이터셋 다운로드   
 - HTML, 평문 등 다양한 구조의 이메일 존재

텍스트 전처리  
 - HTML → 텍스트 변환  
 - URL, 숫자, 특수문자 정리   
 - 단어 분리 + Stemming (PorterStemmer)  
 - 이메일 → 단어 카운트 변환

피처 벡터화  
 - 단어 카운트 → 희소 행렬 벡터화 (CSR matrix)  
 - 가장 자주 나오는 단어만 선택 (vocabulary_size)

모델 훈련 및 평가  
 - 로지스틱 회귀로 훈련  
 - 교차검증으로 정확도 98.5% 이상

테스트셋 평가  
 - Precision: 95.88%  
 - Recall: 97.89%  




| 구분    | 주요 내용                                           |
| ----- | ----------------------------------------------- |
| 데이터셋  | MNIST, Titanic, Spam                            |
| 분류 종류 | 이진, 다중, 멀티레이블, 다중출력                             |
| 알고리즘  | SGD, SVM, KNN, RandomForest, LogisticRegression |
| 평가 지표 | Accuracy, Precision, Recall, F1, ROC-AUC        |
| 실습 핵심 | 전처리, 시각화, 평가, 모델 튜닝                             |
