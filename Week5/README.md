#1 PREDICTION UNDER UNCERTAINTY WITH ERROR- ENCODING NETWORKS

[paper] https://arxiv.org/abs/1711.04994  

불확실성이 존재할 때 시간예측을 수행할 수 있는 방법 제안
예측할 수 없는 샘플을 저차원으로 인코딩해서 feed forward 입력에 넣겠다?
A major challenge in this task is how to handle the multi-modal nature of many time series. 
메인 첼린지는 시걔열 데이터의 멀티 모달 특성을 다루는 것임
However, a generator which covers a single mode can also fool the discriminator and converge, and this behavior of mode collapse has been widely observed in practice. 
싱글모드를 커버하는 generator는 충분히 discriminator를 속이고 수렴할 수 있고 이는 결국은 붕괴를 야기한다.
By training a model deterministically, we can obtain this factorization in the form of the model’s prediction together with the prediction error with respect to the true state. 
확률론적으로 학습을 수행함으로써 모델 예측의 인수분해 형태와 잘못된 예측을 얻을 수 있다.
This error can be encoded as a low- dimensional latent variable which is fed back into the model to accurately correct the determinisic prediction by incorporating this additional information. 
이 에러를 저차원의 잠수 변수로 인코딩하여 정확한 예측을 수행할 수 있는 피드백 형식으로 사용할 수 있다.
이 모델을 EEN이라 부르겠음.
이는 각각의 timestep마다 3가지의 function mapping을 포함함
1) 현재 상태(current state)를 미래 상태(feature state)로 매핑 --> 이는 미래 상태를 deterministic과 non-deterministic으로 나눈다.
2) feature state의 non-deterministic을 저차원의 잠재 변수로 매핑
3) 미래 상태의 모드 정보를 인코딩하는 잠복 벡터를 조건으로하여 현재 상태에서 미래 상태로의 매핑.
모델은 end-to-end의 지도학습으로 수행되며 잠재 변수는 학습된 매개 변수 함수를 사용함으로 쉽고 빠르게 계산될 수 있다.
결국은 비디오 프레임 예측인듯
One natural way of dealing with uncertainty is through latent variables, which can be made to account for aspects of the target that are not explainable from the observed input. 
불확실성을 다루는 하나의 방법은 잠새 변수를 다루는 것이다. 잠재 변수는 관찰된 입력에서 설명 할 수 없는 대상의 측면을 설명하기 위해 만들 수 있습니다.
Assume we have a set of continuous vector-valued input-target pairs (xi,yi), where the targets depend on both the inputs and some inherently unpredictable factors. 
연속 백터와 input target이 있다고 가정할 때, target은 입력과 예측할 수 없는 요소에 의존한다.
즉, 입력들은 연속적인 비디오 프레임들의 세트일 수 있고,  타겟은 다음 프레임일 수 있다.
Classical latent variable models such as k-means or mixtures of Gaussians are trained by alternately minimizing the loss with respect to the latent variables and model parameters; in the probabilistic case this is the Expectation-Maximization algorithm (Dempster et al., 1977). 
기존의 전통적인 방법(k-means, mixtures of gaussian)은 잠재 변수와 모델 매개 변수에 대한 손실을 교대로 최소화함으로써 훈련된다. 확률론적으로 이는 expectation-maximization algorithm이다.
In the case of a neural network model fθ(xi, z), continuous latent variables can be optimized using gradient descent and the model can be trained with the following procedure: 
NN 모델의 경우 연속적인 잠재 변수는 경사 하강법으로 최적화 할 수 있고 다음과 같은 학습 절차를 따른다.
—> Algorithm 1 : Train latent variable model with alternating minimization
First, the latent variable z should represent what is not explainable using the input xi. 
먼저 잠재 변수 z는 인풋 x_i를 사용해 설명할 수 없는것을 나타내여야 한다. 즉 이상적인 모델은 입력 x_i와 잠재 변수 z만을 사용해서 예측할 수 없는 것을 설명해야 한다.
Second, if we are using gradient descent to optimize the latent variables, z will be a continuous function of xi and yi, although a possibly highly nonlinear one. 
잠재 변수를 최적화하기 위해 그래디언트 디센트를 사용하는 경우 z는 xi와 yi의 연속 함수가 될 수 있지만 매우 비선형 일 수 있습니다.
Our model has two settings: a deterministic setting, where it produces a prediction using only xi, and a conditional setting where is produces a prediction using xi and a latent variable z. We can switch to the deterministic setting by fixing z = 0; optionally, we can also have a separate network or set of weights for each setting. 
우리 모델에서는 


#2 What Uncertainties Do We Need in Bayesian Deep Learning for Computer Vision?

[paper] https://arxiv.org/abs/1703.04977
