Quality Control
===============

Paper Reading
---------------
[78] CDAS: A Crowdsourcing Data Analytics System 2012
    —— 固定的工人答题正确率
[51] Active Learning from Crowds
[59] Quality Management on AMT
[94] Incremental Quality Inference in Crowdsourcing
    —— 变化的工人答题正确率

###[78]CDAS: A Crowdsourcing Data Analytics System 2012
    * The core part of CDAS is a quality-sensitive model

Introduction
    * Voting strategy is costly
    * Quality-sensitive model: a prediction model and a verification model (a 2-phase processing strategy)

        * The prediction model estimate how many workers are required to achieve a specific accuracy by collecting distribution of all workers’ historical performances
        * The verification model combines vote distribution and workers’ performances based on probability
    * It provides an approximate answer with confidence and refines it gradually as more answers are returned

        * Workers finish the work asynchronously -> offer the option of an approximate answer
    * To evaluate the model and the performance of CDAS, 2 jobs were employed: TSA (Twitter sentimental analytics) and IT (Image tagging)

OVERVIEW2.1 Architecture of CDAS3 components: job manager, crowdsourcing engine and program executerverification model select the correct answer based on the probability estimationPREDICTION MODEL3.3 Sampling-based Accuracy Estimationembed m questions, whose ground truth are known beforehand -- as testing samples to estimate the workers' accuracyhas known the number of workers, which can be used in the later verification model ?VERIFICATION MODEL4.1 Probability-based Verification
    * apply Bayesian theorem to estimate the accuracy of each result
    * Equation 4
    * DEFINITION 2: worker​ confidence

        * related positively to the worker accuracy
    * DEFINITION 3: answer confidence

        * the probability of r being the correct answer
        * the answer with the highest confidence is accepted as the final result​

4.2 Online Processing
    * workers submit aysnchronously

        * has to wait for sufficient number of answers to be submitted
        * provide an approximate result based on the answers received so far (and uncertainty and approximation cannot be avoided in crowdsourcing systems
        * extend the data fusion to estimate the answer's confidence​
    * 4.2.1 Finding the Correct Answer Online

        * a partial observation for the answer distribution
        * Theorem 6 shows that the confidence of a partial result can also be computed by Equation 4​
    * 3 strategies to teminate the  processing 

PERFORMANCE EVALUATION5.1.4 Effect of Sampling
    * the workers' approval rate in AMT is very different from that of real accuracy in TSA --> they adopt a sampling approach to estimate workers' accuracy
    * both mean accuracy and average error are stable when the sampling rate is higher than 10%
    * The result meets all of the user required accuracy only with a sampling rate no less than 20%
    * the authors use 20% sampling rate in all of the verification experiments​


