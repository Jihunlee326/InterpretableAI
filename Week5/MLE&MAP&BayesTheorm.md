### MLE(Maximum Likelihood Estimation)  
Random variable의 parameter를 estimate하는 방법  

다음과 같이 생각해보자.  
**'Machine learning = 주어진 데이터를 잘 표현하는 함수 = probability densitiy를 찾는 과정**

이때, 확률분포를 가정하고 적절한 parameter를 유추하는 과정을 살펴보면,  
주어진 data가 gaussian distribution으로 drawn될 때 => 데이터 현상을 가장 잘 표현하는 mean과 covariance를 찾는 것이다.  

확률밀도함수(PDF) f에서 X=(X1, X2, X3, ... , Xn)는 그 확률로 추청된 data, f는 θ로 parameterize 되었다고 가정을 해보자.  
이때, X가 주어지고 θ값을 알면 쉽게 f(X|θ)의 값을 계산할 수 있다.  
  
만약 f가 가우시안 분포라면 θ는 mean = \mu, covariance = /sigma 일 것이다.
이때, likelihood는 L(θ; x1, x2, ... , xn) = L(θ;X) = f(X|θ) = f(x1, x2, ..., xn|θ)
따라서 MLE는 likelihood를 최대로 하는 θ를 추정하는 방법이라 볼 수 있다.  

