# 8. Dimensionality Reduction
## The Curse of Dimensionality
고차원일수록 데이터 간 거리가 왜곡되고 모델 학습이 어려워짐

## Main Approaches for Dimensionality Reduction
차원 축소의 두 가지 주요 방식: 투영(projection)과 매니폴드 학습(manifold learning)

### Projection
고차원 데이터를 저차원 평면에 투영하여 구조를 간단히 표현함

### Manifold Learning
비선형 구조를 보존하며 저차원으로 매핑하는 방법

## PCA (Principal Component Analysis)
분산을 최대한 보존하면서 직교 축(주성분)으로 변환하는 선형 차원 축소 기법

### Preserving the Variance
최대 분산 방향을 따라 데이터를 투영하여 정보 손실 최소화

### Principal Components
데이터의 주요 방향(축)을 나타내는 벡터 집합

### Projecting Down to d Dimensions
상위 d개의 주성분을 선택해 d차원으로 축소

### Using Scikit-Learn
PCA 클래스를 이용한 간단한 사용법 소개

### Explained Variance Ratio
각 주성분이 전체 분산에서 차지하는 비율 확인

### Choosing the Right Number of Dimensions
적절한 차원 수 선택을 위한 기준 제시 (예: 누적 분산 비율)

### PCA for Compression
데이터 압축을 위한 PCA 활용 (예: 이미지 압축)

### Randomized PCA
큰 데이터셋에서 빠르게 근사적인 PCA 수행

### Incremental PCA
메모리 제약이 있는 경우, 미니배치 단위로 PCA 수행

## Kernel PCA
비선형 차원 축소를 위한 커널 기반 PCA

### Selecting a Kernel and Tuning Hyperparameters
커널 종류 선택과 하이퍼파라미터 조정 방법 설명

## LLE (Locally Linear Embedding)
지역적 선형 관계를 보존하며 차원 축소하는 비선형 기법

## Other Dimensionality Reduction Techniques
t-SNE, UMAP 등 기타 기법 간략 소개
