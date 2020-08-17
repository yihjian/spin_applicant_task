# SPIN Task Submission

By Yihong Jian

### Data

The original data is cropped into 128*128, resulting in around 3300 pictures as training set. The set is randomly split into train and test with ratio 10:1. 

### Model

A modified U-net model is used for this task. Batch norm layer was added after each convolutional layer to generalize the model predictions. The model was trained with Adam optimizer(learning rate 1e-3) for 50 epoch with learning rate reduced to 1/10 at plateau. Early stop was triggered at epoch 47 as validation loss no longer decrease. 

The confusion matrix output for the validation set:

```
              precision    recall  f1-score   support

        corn      0.898     0.927     0.913   2353217
     soybean      0.918     0.930     0.924   2248811
       other      0.858     0.751     0.801    853844

    accuracy                          0.901   5455872
   macro avg      0.891     0.870     0.879   5455872
weighted avg      0.900     0.901     0.900   5455872
```

And the accuracy matrix for validation set:

```
		corn       soybeans   others
corn    0.92738111 0.0445471  0.02807178
soybean 0.05155302 0.93046281 0.01798417
others  0.15367093 0.09566502 0.75066406
```

As it can be observed, corn and soybeans are classified pretty accurately while others could be mis-interpreted as corn or soybeans.

### Code and Visualization

See this [repo](https://github.com/yihjian/spin_applicant_task).