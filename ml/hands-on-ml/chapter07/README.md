# Chapter 7: Ensemble Learning and Random Forests

## Voting Classifiers
여러 모델의 예측을 결합하여 더 강력한 예측을 생성하는 방식  
하드/소프트 보팅 방식

## Bagging and Pasting
같은 알고리즘을 여러 데이터 샘플에 학습시켜 결과를 평균  
Bagging은 샘플링에 중복 허용, Pasting은 미허용 

### Bagging and Pasting in Scikit-Learn
BaggingClassifier를 사용해 손쉽게 구현 가능   
병렬 처리도 지원되어 효율적

### Out-of-Bag Evaluation
훈련 샘플 중 모델이 보지 못한 OOB 샘플을 활용해 별도 검증 세트 없이 성능 평가 가능 

## Random Patches and Random Subspaces
입력 특성과 샘플을 랜덤하게 선택하여 모델 학습  
더욱 다양성을 높이는 기법

## Random Forests
여러 개의 결정 트리를 활용한 강력한 앙상블 기법  
각 트리는 무작위 특성과 데이터로 학습됨

### Extra-Trees
Random Forest보다 더 무작위적인 트리 구성  
학습 속도가 빠르고 과적합 방지 효과 있음

### Feature Importance
모델이 각 특성에 부여한 중요도를 확인 가능  
특성 선택 및 해석에 유용

## Boosting
약한 학습기를 순차적으로 연결하여 강력한 모델을 만드는 방법  
이전 오차를 보완하며 학습

### AdaBoost
오차가 큰 샘플에 가중치를 두는 방식의 부스팅 기법   
간단하지만 효과적

### Gradient Boosting
잔여 오차를 줄이는 방식으로 새로운 모델을 순차적으로 추가 
성능 우수

## Stacking
여러 모델의 예측을 기반으로 최종 예측기를 학습시키는 방식  
메타 모델이 핵심 역할 수행
