---
title: Linear regression and Ordinary least squares
key: 20210524
tags: linear regression, ordinary least squares, OLS
---
(작성 중)

## 1. Linear regression 이란?
Linear regression 모델은 $\mathbf{y}$(dependent variable) 를 $\mathbf{X}$(independent variable, design matrix) 의 선형 결합으로 나타내는 모델이라고 할 수 있다. 수식으로 나타내면 다음과 같다. 


$$\mathbf{y} = \mathbf{Xw} + \mathbf{\epsilon}$$


## 2. 파라미터 추정/계산 관점
- Algebraic solution with pseudoinverse
- Lagrange multipliers with constraints
- Least absolute deviation (LAD)
- Ordinary least squares (OLS)
- Maximum likelihood estimation


## 3. Ordinary least squares (OLS)
OLS 는 오차 제곱의 합(sum of squared residuals)을 최소화 하는 파라미터 $\mathbf{\hat{w}}$ 를 추정/계산하는 방법이다. 
MLE 관점에서 오차 값($\mathbf{\epsilon}$)을 gaussian 분포로 가정한 경우와 동일하다.

## 4. OLS 의 계산
- 대수적으로 pseudoinverse 를 통해 다음과 같이 계산할 수 있다. 하지만, 이는 closed form solution 이 아니다. 왜냐면 $\mathbf{X}^{T}\mathbf{X}$ 가 sinular matrix 일 수 있기 때문이며, 이 경우 해당 방정식은 여러 해를 가질 수 있다.

$$\mathbf{\hat{w}} = {(\mathbf{X}^{T} \mathbf{X})}^{-1} \mathbf{X}^{T}\mathbf{y}$$

- 해석학적 솔루션으로, 오차 제곱 항의 그래디언트가 0 을 만족하는 $\mathbf{w}$ 를 계산할 수 있다. 이 경우 대수적으로 구한 결과와 동일한 결과를 얻을 수 있다.
- numerical solution 으로, Gradient Descent. 


## 5. 왜 invertible 하지 않은가?
- 해당 행렬은 positive semi-definite 이라서 0 인 eigenvalue 를 가질 수 있다. 따라서 항상 invertaible 하지 않음
- independent variable 의 차원 보다 데이터가 적을 경우 또는 피처간 선형 독립이 아닐 경우 (full rank square matrix 가 아닌 경우)

 
## 6. Regularized least squares
- 오버 피팅 조절을 위해 regularization term 을 추가한 것으로 생각할 수 있음
- MLE 관점에서는 parameter 의 분포를 normal 분포로 가정하면 L2 (Ridge), laplace 분포로 가정하면 L1 (Lasso) 가 됨
- regularization term 이 추가되면, 대수 또는 해석학적 솔루션에서 역행렬이 존재하지 않는 문제가 해결된다. 왜냐면 해당 메트릭스가 positive definite 행렬이 되기 때문임.


## 7. 기타
- Design matrix 는 incremental 하게 업데이트 될 수 있음 (예시 - A Contextual-Bandit Approach to Personalized News Article Recommendation)
- 잘 설명해보려고 준비했는데, 막상 글쓰니 귀찮다. 일단 대충 적어두고 꾸준히 업데이트해야겠다.


## 8. 주석

