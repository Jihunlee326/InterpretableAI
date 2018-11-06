Dropout as a Bayesian Approximation: Representing Model Uncertainty in Deep Learning

[paper] https://arxiv.org/abs/1506.02142 

#### Bayesian Neural Networks
: model parameter를 deterministic 하게 point로 보지 않고 distribution 으로 보는 것
: 이 distribution을 계산하기 위해 intractable posterior p(w|X,Y)를 계산해야 하고
: 이를 근사하기 위해 Variational Inference를 사용함
: VI를 사용해서 porsterior 를 근사하는 q(W) 를 계산하면 inference 가능함

