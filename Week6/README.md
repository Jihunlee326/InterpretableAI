Dropout as a Bayesian Approximation: Representing Model Uncertainty in Deep Learning

[paper] https://arxiv.org/abs/1506.02142 

#### Bayesian Neural Networks
: model parameter를 deterministic 하게 point로 보지 않고 distribution 으로 보는 것
: 이 distribution을 계산하기 위해 intractable posterior p(w|X,Y)를 계산해야 하고
: 이를 근사하기 위해 Variational Inference를 사용함
: VI를 사용해서 porsterior 를 근사하는 q(W) 를 계산하면 inference 가능함
==> 계산량이 많을듯..

#### Bayesian NN 자세한 설명

전통적인 NN의 Linear regression prediction을 생각해보면,
Y = w * X
labels Y given data X with weights w.

여기서 목표는 loss function을 minimizing 하는 parameter w를 찾는것.

이제 Y를 Gaussian distribution으로 가정해보자.

p(Y|X,w)

그러면 w에 대해 data likelihood를 maximizing 하는 식으로 바꿀 수 있다.

여기에 어떠한 uncertainty를 esimate 하는 bayesian 문제로 식을 바꿔보면 다음과 같이 표현할 수 있다.

p(Y|X,w) * p(w)

그리고 bayesian rule을 통해 확률을 다음과 같이 변경할 수 있다.

p(w|X,Y) = p(Y|X,w) * p(w) / CONSTANT   (*CONSTANT 항은 결국 likelihood의 marginal likelihood로 볼 수 있음(=evidence))

의미론적으로 식을 해석해보면 Posterioir

#### Neural Network with Dropout

