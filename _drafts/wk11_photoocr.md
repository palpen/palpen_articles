29 August 2017

# Photo OCR

## ML pipelines

## creating artificial data (artificial data synthesis) to increase training dataset: character image from font packages
    - low bias important before collecting more data
    - If learning model exhibits high bias, then no point in collecting more data.
    - To fix this, just add more features in algorithm until you have a low bias classifier

## other way to get data: crowd source (Amazon mechanical Turk)

- sanity check----learning curves (use this more often)

## Ceiling analysis for evaluating where inthe pipeline you should spend the most time on
- A ML pipeline is a series of steps towards some end goal where in the final step a classification is made. A common example of this is in character recognition. Ceiling analysis is a process to evaluate the contribution of each step in the ML pipeline

# Summary of course
* Supervised learning: Linear reg, logistic reg, neural net, svm
* Unsupervised learning: K-means, PCA, anomaly detection
* Special app: Reccomender systems, large scale ML
* Advice: bias/variance, regularization; eval. of learning algos, learning curves, error analysis, ceiling analysis
