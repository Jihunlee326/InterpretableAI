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
  
여기서 목표는 loss function을 minimize 하는 parameter w를 찾는것.  
  
이제 Y를 Gaussian distribution으로 가정해보자.  
  
p(Y|X,w) --- 식1)
  
그러면 w에 대해 data likelihood를 maximize 하는 식으로 바꿀 수 있다.  
  
여기에 어떠한 uncertainty를 esimate 하는 bayesian 문제로 식을 바꿔보면 다음과 같이 표현할 수 있다.  
  
p(Y|X,w) * p(w) --- 식2)  

그리고 bayesian rule을 통해 확률을 다음과 같이 변경할 수 있다.  
  
p(w|X,Y) = p(Y|X,w) * p(w) / CONSTANT or P(Y|X)   (*CONSTANT 항은 결국 likelihood의 marginal likelihood로 볼 수 있음(=evidence)) --- 식3)  
  
의미론적으로 식을 해석해보면 Posterioir(=p(w|X,Y))는 input, output이 주어졌을 경우의 parameter의 확률,  
Likelihood는 input과 parameter가 주어졌을 때 output의 확률,  
Prior는 parameter의 확률,  
Evidence는 Input이 주어졌을 경우의 output의 확률,  
  
근데, 여기서부터 어떻게 bayes theorm으로 유도했는지 너무 헷갈림  
  
추상적인 관점에서 input과 output을 하나의 dataset으로 바라보자.  
  
P(W|D) = P(D|W) * P(W) / P(D) --- 식4)
  
위에 같이 표현할 수 있을 것이다.  
그리고 식3과 식4를 비교하면서 살펴보면  
식3의 likelihood => Y를 가장 잘 표현할 수 있는 X와 parameter는 무엇인가? 로 해석할 수 있고  
식4의 likelihood => Data를 가장 잘 표현할 수 있는 parameter는 무엇인가? 로 해석할 수 있다.  
결국 같다.  
  
이제 다시 기존의 Deterministic Deep Learning을 보자.  
- Dataset을 학습하여 W가 결정된다.  
- 학습된 W는 고정되어있고, 새로운 입력(uncertainty)에 대해서도 y는 고정된다.  
즉, P(Y|X, W)를 최대화 하는 것이다.  
여기에 P(W)를 추가해서 MAP 문제로 풀어도 W는 고정된 값이다.  
결국은 Posterior를 최대로 만드는 W값 하나를 구하기 때문이다.  
  
이와 다르게, Bayesian NN에서는 W의 확률분포를 결정한다.  
즉, P(W|D)를 구한다.  
  
기존에 MAP문제에서는 P(W|D)를 구하기 위해서 likelihood + prior 를 동시에 maximize 하는 문제로 풀었다.  
W_map = argmax(w)logP(D|W) + logP(w)  
즉, 주어진 데이터에서 P(W|D)를 Maximize하는 w를 구한다.  
  
하지만 uncertainiy가 고려된 P(W|D)를 구하기 위해서는 likelihood + prior를 maximize 하는 문제로 접근해서는 안된다.  
이 부분이 BNN과 MAP의 차이같다.  
  
BNN에서는 수식의 아래부분 CONSTANT = Evidence = Marginal Likelihood를 구하기 위해 Variational Inference를 통해 근사화하는 것부터 시작한다.  
  
이렇게 학습하면 BNN은 입력에 대한 출력으로 Conditional Expectation을 통해 분포를 구하게 된다.  