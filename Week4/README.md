#1 TRAINING CONFIDENCE-CALIBRATED CLASSIFIERS FOR DETECTING OUT-OF-DISTRIBUTION SAMPLES

[paper] https://arxiv.org/abs/1711.09325

We consider a new loss function, called “confidence loss”.  

Our key idea on the proposed loss is to additionally minimize the Kullback- Leibler (KL) divergence from the predictive distribution on out-of-distribution samples to the uniform one in order to give less confident predictions on them. Then, in- and out-of-distributions are expected to be more separable. 
