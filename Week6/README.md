Dropout as a Bayesian Approximation: Representing Model Uncertainty in Deep Learning

[paper] https://arxiv.org/abs/1506.02142 


#### Neural Network with Dropout

딥러닝은 불확실성 모델링 못함
베이지안은 가능함, 근데 계산량이 큼
우리는 드랍아웃을 이용해 가우시간 프로세스의 베이시안 추론을 추정하겠음
계산량을 줄이면서 NN에서 불확실성을 모델링할 수 있음
RMSE를 계선함을 보여주겠음

1. Introduction
NN에서는 모델의 불확실성을 포착하지 않음
우리는 종종 softmax에서 얻은 예측 결과를 모델의 신뢰도로 잘못 해석함
Gaussian Process(GP)에서 드랍아웃의 사용이 베이지안 근사치로 해석될 수 있음을 보여줬다.
드랍아웃은 overfitting을 피하는 하나의 방법으로 NN에서 주로 사용된다.
(이것에 대한 해석은 학습에서의 탈락이 모델의 가중치에 대략적으로 통합된다는 것이다.)
우린 여기서 버려지는 정보를 추출해서 부확실성을 표현하는 도구를 만들겠다.
이는 정확도를 낮추지도 않고 계산 복잡도 또한 간단하다.

우린 GP와 드랍아웃의 연결에 대한 이론적인 처리 방법을 제공하고
NN에서 불확실성을 모델링할 수 있는 TOOL을 제공한다.
MNIST 데이터를 사용해 RMSE가 상다히 개선됨을 보여줌으로써 증명하겠음

2. Related Research

3. Dropout as a Bayesian Approximation
임의의 depth와 비선형을 갖는 NN에 weight layer의 전 단계에 드랍아웃을 적용한 것이
확률적인 deep gausian process의 근사와 동등하다는 것을 수학적으로 보여주겠음
결과적으로 드랍아웃의 목표는 approximate distribution(근사분포)와 posterior of a deep GP의
KL발산을 최소화한다는 것임

y^은 NN의 아웃풋임
Wi는 가중치 행렬임
bi는 각각의 Ki차원 layer에 대한 가중치 백터임
X입력에 대하 Y가 출력되고, L2 정규화를 사용한다.
L_Dropout을 사용해 각 입력 지점과 계층의 모든 네트워크 단위에 대한 이진 변수를 샘플링한다.

확률적인 deep gausian process의 근사와 동등하다는 것을 수학적으로 보여주겠


3. Contribution
