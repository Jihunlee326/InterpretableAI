#1 TRAINING CONFIDENCE-CALIBRATED CLASSIFIERS FOR DETECTING OUT-OF-DISTRIBUTION SAMPLES

[paper] https://arxiv.org/abs/1711.09325

We consider a new loss function, called “confidence loss”.  

Our key idea on the proposed loss is to additionally minimize the Kullback- Leibler (KL) divergence from the predictive distribution on out-of-distribution samples to the uniform one in order to give less confident predictions on them. Then, in- and out-of-distributions are expected to be more separable. 

Our motivation is that such inference algorithms can work better if the classifiers are trained so that they map the samples from in- and out-of-distributions into the output space separately. Namely, we primarily focus on training an improved classifier, and then use prior detectors under the trained model to measure its performance.

: Out-of-distribution에서 예측되는 분포로부터 uniform한 분포로 예측되는 KL 분포의 값을  minimize하는데 새로 정의한 confidence loss가 사용된다.
-> 이를 통해 in- and out- distribution의 차이는 명확해 질 것이다.
: 하지만 최적화된 confidence loss값을 찾기 위해서는 많은 양의 out-of-distribution 데이터가 필요하다.
-> 이 문제를 해결하기 위해 새로운 generative adversarial network를 제안한다.
-> GAN은 out-of-distribution data(boundrary samples)를 생성하기 위해 사용된다.
: 마지막으로 classifier loss와 confidence loss를 동시에 minimize할 수 있는 joint training scheme를 구성한다.
: 또한, 동등하게 confident classifier는 GAN의 성능도 향상시킨다. 

2.1 CONFIDENT CLASSIFIER FOR OUT-OF-DISTRIBUTION

#### Confidence loss

<p align="center"><img src="../images/week4_paper_eq_1.png" width="320"></p>

where KL denotes the Kullback-Leibler (KL) divergence, U (y) is the uniform distribution and β > 0 is a penalty parameter. 

새로 제안하는 confidence loss는 out-of-distribution 샘플에 대해서는 uniform한 형태(zero)만든다. 
반면에 in-distribution 샘플은 label-dependent probability를 따른다. 
--> in-distribuion 샘플이 out-distribution보다 높은 예측값을 출력하 수 있도록 설계되었다. 
--> 물론 KL발산으로 인해 예측값이 변경될 수 있지만 네트워크의 표현력이 더 강하기 때문에 영향력이 미비한것을 확인했다. 

사실 KLD를 최소화하기 위해서는 거의 무한한 out-distribution 샘플으 학습해야 한다. 
근데 불가능하잖아..  
To address the issue, we suggest to sample out-of-distribution close to in-distribution, which could be more effective in improving the detection performance, without any assumption on testing out-of-distribution.
그럼 더 효율적인 out-distribution 샘플을 생성해보자!  

<p align="center"><img src="../images/week4_paper_fi_1.png" width="320"></p>

figure 1은 이에 대한 실험 결과  
(a) [-20, 20]^2 region에서 green sample(out-of-distribution)을 생성한 결과
(b) 이에 대한 decision boundrary of classifier
(c) 같은 영역에서 다른 분포로 out-distribution 을 생성함
(d) 이에 대한 decision boundrary of classifier  

이러한 실험 결과는 다음을 암시한다.
This implies that training out-of-distribution samples nearby the in-distribution region could be more effective in improving the detection performance. Our underlying intuition is that the effect of boundary of in-distribution region might propagate to the entire out-of-distribution space.
즉, 분산 영역 근처의 샘플으 학습하는 것이 성능을 향상시키는데 효과적일 수 있고, 근본적인 직관은 분배 영역 경계의 영향이 전체 분배 영역 밖으로 전파될 수 있다는 것이다.  
--> 따라서 이러한 out-distribuion samples를 생성할 수 있느 새로운 GAN을 제안하겠다. 




#2 Uncertainty-Aware Learning from Demonstration Using Mixture Density Networks with Sampling-Free Variance Modeling

[paper] https://arxiv.org/abs/1709.02249
