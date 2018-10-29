## 1. MLE(Maximum Likelihood Estimation)  
Random variable의 parameter를 estimate하는 방법  

다음과 같이 생각해보자.  
  
**'Machine learning = 주어진 데이터를 잘 표현하는 함수 = probability densitiy를 찾는 과정**

이때, 확률분포를 가정하고 적절한 parameter를 유추하는 과정을 살펴보면,  
주어진 data가 gaussian distribution으로 drawn될 때 => 데이터 현상을 가장 잘 표현하는 mean과 covariance를 찾는 것이다.  

확률밀도함수(PDF) f에서 X=(X1, X2, X3, ... , Xn)는 그 확률로 추청된 data 그리고 f는 θ로 parameterize 되었다고 가정을 해보자.  
이때, X가 주어지고 θ값을 알면 쉽게 f(X|θ)의 값을 계산할 수 있다.  
만약 f가 가우시안 분포라면 θ는 mean = μ, covariance = Σ 일 것이다.  
  
이때, likelihood는 L(θ; x1, x2, ... , xn) = L(θ;X) = f(X|θ) = f(x1, x2, ..., xn|θ)
따라서 MLE는 likelihood를 최대로 하는 θ를 추정하는 방법이라 볼 수 있다.  

정리하면 θ^ = argmax_θ L(θ;X) = argmax_θ f(X|θ)  

## 2. MAP(Maximum A Posterior estimation)  
주어진 데이터에 대해 최대확률을 가지는 θ를 estimate하는 방법  
  
θ^ = argmax_θ f(θ|X)  
  
MLE는 오직 현재 주어진 데이터만을 잘 설명하는 parameter를 찾는 반면에,  
MAP는 여러 parameter 중 데이터가 주어졌을 때 가장 확률이 높은 θ를 찾는것  
  
*but! MAP를 계산하기 위해서는 f(θ|X)가 필요한데, 우리가 관찰할 수 있는것은 f(X|θ) 뿐...  
--> 여기서 Bayes' Theorm 개념이 등장*  

## 3. Bayes' Theorm  
