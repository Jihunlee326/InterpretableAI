#1 PREDICTION UNDER UNCERTAINTY WITH ERROR- ENCODING NETWORKS

[paper] https://arxiv.org/abs/1711.04994  

시계열 데이터에서 다음 프레임을 예측하기 위한 ERROR ENCODING NETWORKS[ENN] 제안  
  
A major challenge in this task is how to handle the multi-modal nature of many time series. 
By training a model deterministically, we can obtain this factorization in the form of the model’s prediction together with. the prediction error with respect to the true state. 
This error can be encoded as a low- dimensional latent variable which is fed back into the model to accurately correct the determinisic prediction by incorporating this additional information. 
  
--> 확률론적을 학습을 수행해서(Auto Encoder 이야기 하는듯..) 잘못된 예측을 얻으 후 Residual learning으로 이 에러를 저차원의 잠재변수(latent)로  
인코딩하여 정확히 다음 프레임을 예측하 수 있는 형태의 학습 방법을 제안한는듯..   

[그림 1]

위의 모델을 EEN으로 부르겠음
해당 모델에서 3가지의 function mappong을 수행하는데..  
1) 현재 상태(current state)를 미래 상태(feature state)로 매핑
--> 첫번째 학습 과정에서 Observation을 auto encoder를 통해 Prediction하는 과정인듯
2) feature state의 non-deterministic을 저차원의 잠재 변술 매핑
--> Redisual Prediction Error를 통해 Latent을 갱신하는 과정인듯
3) feature state의 모드 정보를 인코딩하는 latent vector를 조건으로 하여 current state를 feature state로 매핑
--> 갱신된 latent vector를 통해 다음 프레임을 예측하는 과정인듯

# 결국은 처음의 학습 과정을 통해 예측된 프레임을 Y와의 error를 통해 latent space를 학습시키고 학습된 매개변수를 사용해 infernece과정에서 빠르게 다음 프래임을 예측할 수 있다는 이야기인듯.. #

One natural way of dealing with uncertainty is through latent variables, which can be made to account for aspects of the target that are not explainable from the observed input. 
--> 논문에서는 불확실성을 다루는 하나으 방법으로 잠재 변수를 다룰것을 제안한다.

기존의 전통적인 방법(k-means, mixtures of gaussian)은 잠재 변수와 모델 매개 변수에 대한 손실을 교대로 최소화함으로써 훈련된다. 
확률론적으로 이는 expectation-maximization algorithm이다.

NN 모델의 경우 연속적인 잠재 변수는 경사 하강법으로 최적화 할 수 있고 다음과 같은 학습 절차를 따른다.
Algorithm 1 : Train latent variable model with alternating minimization
First, the latent variable z should represent what is not explainable using the input xi. 
Second, if we are using gradient descent to optimize the latent variables, z will be a continuous function of xi and yi, although a possibly highly nonlinear one. 
--> 결국 기존의 NN은 경사하강법을 사용해 잠재 변수를 최적호 하는데 이럴경우 z는 xi와 yi으 연속 함수가 될 수 있지만 맹 비선형적이 수 있다??



#2 What Uncertainties Do We Need in Bayesian Deep Learning for Computer Vision?

[paper] https://arxiv.org/abs/1703.04977
