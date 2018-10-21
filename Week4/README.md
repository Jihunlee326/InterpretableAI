#1 TRAINING CONFIDENCE-CALIBRATED CLASSIFIERS FOR DETECTING OUT-OF-DISTRIBUTION SAMPLES

[paper] https://arxiv.org/abs/1711.09325

We consider a new loss function, called “confidence loss”.  

Our key idea on the proposed loss is to additionally minimize the Kullback- Leibler (KL) divergence from the predictive distribution on out-of-distribution samples to the uniform one in order to give less confident predictions on them. Then, in- and out-of-distributions are expected to be more separable. 

—> out-of-distribution에서 예측되는 분포로부터 uniform한 분포로 예측되는 KL 분포의 값을  minimize하는데 새로 정의한 confidence loss가 사용된다.
—> 이를 통해 in- and out- distribution의 차이는 명확해 질 것이다.
—> 하지만 최적화된 confidence loss값을 찾기 위해서는 많은 양의 out-of-distribution 데이터가 필요하다.
—> 이 문제를 해결하기 위해 새로운 generative adversarial network를 제안한다.
—> GAN은 out-of-distribution data(boundrary samples)를 생성하기 위해 사용된다.
—> 마지막으로 classifier loss와 confidence loss를 동시에 minimize할 수 있는 joint training scheme를 구성한다.
—> 또한, 동등하게 confident classifier는 GAN의 성능도 향상시킨다. 




#2 Uncertainty-Aware Learning from Demonstration Using Mixture Density Networks with Sampling-Free Variance Modeling

[paper] https://arxiv.org/abs/1709.02249
