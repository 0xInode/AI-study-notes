**Training and Visualizing a Decision Tree**  
Scikit-Learn을 이용한 결정 트리 학습과 시각화 방법  
트리 구조의 해석 가능성과 직관적인 분류 규칙 소개

**Making Predictions**  
학습된 트리를 따라가면서 분기 규칙에 따라 예측 수행  
리프 노드의 클래스 또는 평균값 반환

**Estimating Class Probabilities**  
리프 노드 내 클래스 비율을 기반으로 확률 추정 가능

**The CART Training Algorithm**  
Scikit-Learn이 사용하는 CART (Classification and Regression Tree) 알고리즘 설명  
지니 불순도 또는 엔트로피 기준으로 최적 분할 찾음

**Computational Complexity**  
트리 학습의 시간 복잡도 분석: 일반적으로 𝑂(𝑛log⁡𝑛)

**Gini Impurity or Entropy?**  
분할 기준으로서 지니 불순도와 엔트로피의 차이와 선택 기준

**Regularization Hyperparameters**  
max_depth, min_samples_split 등 과적합 방지를 위한 하이퍼파라미터 설명

**Regression with Decision Trees**  
분류뿐 아니라 회귀 문제에도 적용 가능  
리프 노드에서 평균값 예측

**Instability**  
데이터의 작은 변화에 민감한 결정 트리의 단점  
배깅, 랜덤 포레스트 등 앙상블 기법의 필요성 배경 설명
