**Linear SVM Classification**  
선형 결정 경계를 기반으로 한 이진 분류  
최대 마진 원칙에 따라 분류기를 학습함

**Soft Margin Classification**  
완벽한 분리가 어려운 데이터에 대해 일부 마진 침해를 허용하는 방식  
슬랙 변수와 하이퍼파라미터 C를 통해 제어

**Nonlinear SVM & Kernel Trick**  
비선형 데이터 분리를 위한 커널 트릭 사용  
- Polynomial Kernel  
- Gaussian RBF Kernel

**Similarity Features**  
유사도 기반 특성 변환을 통해 고차원 매핑 없이도 비선형 분류 가능

**SVM Regression (SVR)**  
마진 내 예측 오차는 무시하고, 마진 바깥 오차만 고려하는 회귀 방식

**수학적 최적화 배경**(어려워서 생략됨, 나중에 다시 확인)  
- 결정 함수와 예측 방식
- Hard/Soft margin 최적화 목적식
- Quadratic Programming, Dual Problem
- 커널화된 SVM 구조 설명
