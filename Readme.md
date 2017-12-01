# Compare descriptors and Machine Learning Algorithms
Compare different HOG descriptor parameters and ML approaches.

The python script eval_train_classify.py perform following tasks:
 * read all dataset, split in train and test 
 * create HOG descritors for all train dataset for a variation of HOG parameters
 * create models for different machine learning algorithm like SVM, random forest
 * classify immediately the split testset and get accuracy of model
 * create a table with all results

The objective is to use the table to decide the best algorithm and HOG parameters to use for solve your problem.
Here the image dataser is MNIST, the hand-writing Digits Dataset. You can use any image dataset with few modifications.

## MNIST Dataset
MNIST is a widely used dataset for computer vision. It has tenths of thousands of labeled digits in gray images of 28x28 pixels size.
Moreover there is a test set, it means a also large set of unlabeled images (in Kaggle) so that one can test its model.
The dataset used in this repository is from https://www.kaggle.com/c/digit-recognizer/data.

## MNIST Classification 
One approach to perform MNIST classification is through HOG descriptors.

HOG means Histogram of Oriented Gradients. It generates a histogram of gradients of images countours and edges.
With this image descriptor we can compare images and check whether they are similar (same digit)
or not.

Machine learning algorithm takes many examples (train dataset) of digit images, digit label (the 
digit name) and the HOG descriptor of many samples and learn from it.

After learning model is created, one can predict new digits label (values) from the test dataset.

Then we compare the real values with the predicted values. With these values we calculate accuracy.
The table below shows the accuracy of each Machine Learning algorithm in this list:

 * SVM - Support Vector Machine
 * DTC - Decision Tree Classifier
 * Random Forest - a set of decision trees split for better prediction
 * (to increase soon)

And many different configurations of HOG descriptor with following parameters:

 * Orientations
 * Pixels Per Cell
 * Cells Per Block

As we can see, changing this parameters affects completely in accuracy.

With this tool one can compare image based classifications based in HOG and find the best result to 
train an actual model for its system and then predict.

## Technical Stack
* Python
* sklearn

## Usage
```
python3 eval_train_classify.py --dataset data/train.csv
```

After you selected your parameters, algorithm based in results of evaluation, you can train your dataset:
```
python3 train.py --dataset data/train.csv --model models/rf.cpickle
```

And classify the test vector:
```
python3 classify_mnist.py --model models/rf.cpickle --test data/test.csv
```

## Output from eval_train_classify.py (performance table)

Train data shape (29399, 28, 28) Target shape (29399,)
Unique elements in targets:  [0 1 2 3 4 5 6 7 8 9]
Feature: HOG


|    ML Algo    | orientations  | pixelsPerCell | cellsPerBlock |     Score     |     Time      |
|---------------|---------------|---------------|---------------|---------------|---------------|
|      SVM      |       2       |    (2, 2)     |    (1, 1)     |    0.5677     |    447.74     |
|      DTC      |       2       |    (2, 2)     |    (1, 1)     |    0.8107     |    402.42     |
| Random Forest |       2       |    (2, 2)     |    (1, 1)     |    0.9475     |    413.58     |
|      SVM      |       2       |    (2, 2)     |    (2, 2)     |    0.7965     |    496.72     |
|      DTC      |       2       |    (2, 2)     |    (2, 2)     |    0.8193     |    480.40     |
| Random Forest |       2       |    (2, 2)     |    (2, 2)     |    0.9521     |    417.86     |
|      SVM      |       2       |    (2, 2)     |    (3, 3)     |    0.8219     |    404.21     |
|      DTC      |       2       |    (2, 2)     |    (3, 3)     |    0.8193     |    416.96     |
| Random Forest |       2       |    (2, 2)     |    (3, 3)     |    0.9556     |    376.84     |
|      SVM      |       2       |    (2, 2)     |    (4, 4)     |    0.8322     |    407.08     |
|      DTC      |       2       |    (2, 2)     |    (4, 4)     |    0.8180     |    416.41     |
| Random Forest |       2       |    (2, 2)     |    (4, 4)     |    0.9520     |    340.62     |
|      SVM      |       2       |    (2, 2)     |    (5, 5)     |    0.8506     |    363.25     |
|      DTC      |       2       |    (2, 2)     |    (5, 5)     |    0.8233     |    420.84     |
| Random Forest |       2       |    (2, 2)     |    (5, 5)     |    0.9548     |    308.51     |
|      SVM      |       2       |    (3, 3)     |    (1, 1)     |    0.4566     |    233.81     |
|      DTC      |       2       |    (3, 3)     |    (1, 1)     |    0.7972     |    170.29     |
| Random Forest |       2       |    (3, 3)     |    (1, 1)     |    0.9359     |    176.00     |
|      SVM      |       2       |    (3, 3)     |    (2, 2)     |    0.7987     |    326.14     |
|      DTC      |       2       |    (3, 3)     |    (2, 2)     |    0.8064     |    195.30     |
| Random Forest |       2       |    (3, 3)     |    (2, 2)     |    0.9427     |    197.80     |
|      SVM      |       2       |    (3, 3)     |    (3, 3)     |    0.8487     |    326.58     |
|      DTC      |       2       |    (3, 3)     |    (3, 3)     |    0.8060     |    151.50     |
| Random Forest |       2       |    (3, 3)     |    (3, 3)     |    0.9433     |    143.82     |
|      SVM      |       2       |    (3, 3)     |    (4, 4)     |    0.8610     |    176.11     |
|      DTC      |       2       |    (3, 3)     |    (4, 4)     |    0.8082     |    131.57     |
| Random Forest |       2       |    (3, 3)     |    (4, 4)     |    0.9447     |    119.18     |
|      SVM      |       2       |    (3, 3)     |    (5, 5)     |    0.8364     |     81.40     |
|      DTC      |       2       |    (3, 3)     |    (5, 5)     |    0.8042     |    110.37     |
| Random Forest |       2       |    (3, 3)     |    (5, 5)     |    0.9461     |     97.50     |
|      SVM      |       2       |    (4, 4)     |    (1, 1)     |    0.5052     |    172.23     |
|      DTC      |       2       |    (4, 4)     |    (1, 1)     |    0.8152     |    105.12     |
| Random Forest |       2       |    (4, 4)     |    (1, 1)     |    0.9352     |    109.47     |
|      SVM      |       2       |    (4, 4)     |    (2, 2)     |    0.7560     |    269.14     |
|      DTC      |       2       |    (4, 4)     |    (2, 2)     |    0.8434     |    102.56     |
| Random Forest |       2       |    (4, 4)     |    (2, 2)     |    0.9483     |    107.45     |
|      SVM      |       2       |    (4, 4)     |    (3, 3)     |    0.8333     |    168.32     |
|      DTC      |       2       |    (4, 4)     |    (3, 3)     |    0.8452     |     87.67     |
| Random Forest |       2       |    (4, 4)     |    (3, 3)     |    0.9521     |     89.80     |
|      SVM      |       2       |    (4, 4)     |    (4, 4)     |    0.7730     |     58.09     |
|      DTC      |       2       |    (4, 4)     |    (4, 4)     |    0.8413     |     67.36     |
| Random Forest |       2       |    (4, 4)     |    (4, 4)     |    0.9516     |     70.56     |
|      SVM      |       2       |    (4, 4)     |    (5, 5)     |    0.7222     |     41.07     |
|      DTC      |       2       |    (4, 4)     |    (5, 5)     |    0.8522     |     47.84     |
| Random Forest |       2       |    (4, 4)     |    (5, 5)     |    0.9508     |     52.44     |
|      SVM      |       3       |    (2, 2)     |    (1, 1)     |    0.6707     |    401.62     |
|      DTC      |       3       |    (2, 2)     |    (1, 1)     |    0.8382     |    389.46     |
| Random Forest |       3       |    (2, 2)     |    (1, 1)     |    0.9618     |    391.26     |
|      SVM      |       3       |    (2, 2)     |    (2, 2)     |    0.8364     |    427.47     |
|      DTC      |       3       |    (2, 2)     |    (2, 2)     |    0.8499     |    440.72     |
| Random Forest |       3       |    (2, 2)     |    (2, 2)     |    0.9670     |    417.82     |
|      SVM      |       3       |    (2, 2)     |    (3, 3)     |    0.8598     |    412.61     |
|      DTC      |       3       |    (2, 2)     |    (3, 3)     |    0.8568     |    438.28     |
| Random Forest |       3       |    (2, 2)     |    (3, 3)     |    0.9677     |    395.92     |
|      SVM      |       3       |    (2, 2)     |    (4, 4)     |    0.8756     |    427.62     |
|      DTC      |       3       |    (2, 2)     |    (4, 4)     |    0.8581     |    460.18     |
| Random Forest |       3       |    (2, 2)     |    (4, 4)     |    0.9707     |    352.78     |
|      SVM      |       3       |    (2, 2)     |    (5, 5)     |    0.8968     |    418.87     |
|      DTC      |       3       |    (2, 2)     |    (5, 5)     |    0.8576     |    533.97     |
| Random Forest |       3       |    (2, 2)     |    (5, 5)     |    0.9661     |    324.66     |
|      SVM      |       3       |    (3, 3)     |    (1, 1)     |    0.6105     |    222.27     |
|      DTC      |       3       |    (3, 3)     |    (1, 1)     |    0.8383     |    165.54     |
| Random Forest |       3       |    (3, 3)     |    (1, 1)     |    0.9529     |    169.00     |
|      SVM      |       3       |    (3, 3)     |    (2, 2)     |    0.8605     |    259.22     |
|      DTC      |       3       |    (3, 3)     |    (2, 2)     |    0.8518     |    170.99     |
| Random Forest |       3       |    (3, 3)     |    (2, 2)     |    0.9585     |    169.66     |
|      SVM      |       3       |    (3, 3)     |    (3, 3)     |    0.8964     |    283.74     |
|      DTC      |       3       |    (3, 3)     |    (3, 3)     |    0.8403     |    157.29     |
| Random Forest |       3       |    (3, 3)     |    (3, 3)     |    0.9584     |    145.01     |
|      SVM      |       3       |    (3, 3)     |    (4, 4)     |    0.9085     |    175.19     |
|      DTC      |       3       |    (3, 3)     |    (4, 4)     |    0.8408     |    137.83     |
| Random Forest |       3       |    (3, 3)     |    (4, 4)     |    0.9576     |    121.32     |
|      SVM      |       3       |    (3, 3)     |    (5, 5)     |    0.8937     |     81.74     |
|      DTC      |       3       |    (3, 3)     |    (5, 5)     |    0.8415     |    122.93     |
| Random Forest |       3       |    (3, 3)     |    (5, 5)     |    0.9594     |     98.46     |
|      SVM      |       3       |    (4, 4)     |    (1, 1)     |    0.6778     |    174.03     |
|      DTC      |       3       |    (4, 4)     |    (1, 1)     |    0.8472     |    105.66     |
| Random Forest |       3       |    (4, 4)     |    (1, 1)     |    0.9560     |    109.68     |
|      SVM      |       3       |    (4, 4)     |    (2, 2)     |    0.8438     |    274.80     |
|      DTC      |       3       |    (4, 4)     |    (2, 2)     |    0.8696     |    104.46     |
| Random Forest |       3       |    (4, 4)     |    (2, 2)     |    0.9646     |    107.37     |
|      SVM      |       3       |    (4, 4)     |    (3, 3)     |    0.8957     |    173.80     |
|      DTC      |       3       |    (4, 4)     |    (3, 3)     |    0.8732     |     91.56     |
| Random Forest |       3       |    (4, 4)     |    (3, 3)     |    0.9668     |     89.63     |
|      SVM      |       3       |    (4, 4)     |    (4, 4)     |    0.8584     |     59.12     |
|      DTC      |       3       |    (4, 4)     |    (4, 4)     |    0.8741     |     72.78     |
| Random Forest |       3       |    (4, 4)     |    (4, 4)     |    0.9652     |     71.22     |
|      SVM      |       3       |    (4, 4)     |    (5, 5)     |    0.8218     |     42.35     |
|      DTC      |       3       |    (4, 4)     |    (5, 5)     |    0.8752     |     52.48     |
| Random Forest |       3       |    (4, 4)     |    (5, 5)     |    0.9675     |     52.55     |
|      SVM      |       4       |    (2, 2)     |    (1, 1)     |    0.7029     |    405.15     |
|      DTC      |       4       |    (2, 2)     |    (1, 1)     |    0.8172     |    390.41     |
| Random Forest |       4       |    (2, 2)     |    (1, 1)     |    0.9598     |    390.08     |
|      SVM      |       4       |    (2, 2)     |    (2, 2)     |    0.8473     |    431.55     |
|      DTC      |       4       |    (2, 2)     |    (2, 2)     |    0.8295     |    443.91     |
| Random Forest |       4       |    (2, 2)     |    (2, 2)     |    0.9642     |    420.43     |
|      SVM      |       4       |    (2, 2)     |    (3, 3)     |    0.8702     |    416.68     |
|      DTC      |       4       |    (2, 2)     |    (3, 3)     |    0.8276     |    443.09     |
| Random Forest |       4       |    (2, 2)     |    (3, 3)     |    0.9653     |    381.82     |
|      SVM      |       4       |    (2, 2)     |    (4, 4)     |    0.8843     |    426.56     |
|      DTC      |       4       |    (2, 2)     |    (4, 4)     |    0.8342     |    460.31     |
| Random Forest |       4       |    (2, 2)     |    (4, 4)     |    0.9664     |    347.20     |
|      SVM      |       4       |    (2, 2)     |    (5, 5)     |    0.9026     |    382.19     |
|      DTC      |       4       |    (2, 2)     |    (5, 5)     |    0.8399     |    484.30     |
| Random Forest |       4       |    (2, 2)     |    (5, 5)     |    0.9670     |    313.76     |
|      SVM      |       4       |    (3, 3)     |    (1, 1)     |    0.6533     |    222.34     |
|      DTC      |       4       |    (3, 3)     |    (1, 1)     |    0.8099     |    166.51     |
| Random Forest |       4       |    (3, 3)     |    (1, 1)     |    0.9519     |    169.77     |
|      SVM      |       4       |    (3, 3)     |    (2, 2)     |    0.8732     |    257.97     |
|      DTC      |       4       |    (3, 3)     |    (2, 2)     |    0.8123     |    178.98     |
| Random Forest |       4       |    (3, 3)     |    (2, 2)     |    0.9571     |    171.29     |
|      SVM      |       4       |    (3, 3)     |    (3, 3)     |    0.9032     |    295.34     |
|      DTC      |       4       |    (3, 3)     |    (3, 3)     |    0.8168     |    163.01     |
| Random Forest |       4       |    (3, 3)     |    (3, 3)     |    0.9565     |    146.89     |
|      SVM      |       4       |    (3, 3)     |    (4, 4)     |    0.9148     |    180.59     |
|      DTC      |       4       |    (3, 3)     |    (4, 4)     |    0.8162     |    149.30     |
| Random Forest |       4       |    (3, 3)     |    (4, 4)     |    0.9559     |    123.59     |
|      SVM      |       4       |    (3, 3)     |    (5, 5)     |    0.8987     |     83.57     |
|      DTC      |       4       |    (3, 3)     |    (5, 5)     |    0.8210     |    127.07     |
| Random Forest |       4       |    (3, 3)     |    (5, 5)     |    0.9568     |    101.53     |
|      SVM      |       4       |    (4, 4)     |    (1, 1)     |    0.7379     |    177.68     |
|      DTC      |       4       |    (4, 4)     |    (1, 1)     |    0.8471     |    106.48     |
| Random Forest |       4       |    (4, 4)     |    (1, 1)     |    0.9598     |    110.33     |
|      SVM      |       4       |    (4, 4)     |    (2, 2)     |    0.8699     |    286.01     |
|      DTC      |       4       |    (4, 4)     |    (2, 2)     |    0.8628     |    108.82     |
| Random Forest |       4       |    (4, 4)     |    (2, 2)     |    0.9644     |    110.05     |
|      SVM      |       4       |    (4, 4)     |    (3, 3)     |    0.9112     |    176.43     |
|      DTC      |       4       |    (4, 4)     |    (3, 3)     |    0.8669     |     99.09     |
| Random Forest |       4       |    (4, 4)     |    (3, 3)     |    0.9665     |     92.66     |
|      SVM      |       4       |    (4, 4)     |    (4, 4)     |    0.8802     |     60.62     |
|      DTC      |       4       |    (4, 4)     |    (4, 4)     |    0.8699     |     80.38     |
| Random Forest |       4       |    (4, 4)     |    (4, 4)     |    0.9656     |     74.32     |
|      SVM      |       4       |    (4, 4)     |    (5, 5)     |    0.8519     |     44.45     |
|      DTC      |       4       |    (4, 4)     |    (5, 5)     |    0.8699     |     59.10     |
| Random Forest |       4       |    (4, 4)     |    (5, 5)     |    0.9665     |     56.08     |
|      SVM      |       6       |    (2, 2)     |    (1, 1)     |    0.7607     |    406.91     |
|      DTC      |       6       |    (2, 2)     |    (1, 1)     |    0.8080     |    395.91     |
| Random Forest |       6       |    (2, 2)     |    (1, 1)     |    0.9587     |    395.01     |
|      SVM      |       6       |    (2, 2)     |    (2, 2)     |    0.8628     |    434.92     |
|      DTC      |       6       |    (2, 2)     |    (2, 2)     |    0.8203     |    455.43     |
| Random Forest |       6       |    (2, 2)     |    (2, 2)     |    0.9616     |    424.93     |
|      SVM      |       6       |    (2, 2)     |    (3, 3)     |    0.8795     |    431.59     |
|      DTC      |       6       |    (2, 2)     |    (3, 3)     |    0.8253     |    479.00     |
| Random Forest |       6       |    (2, 2)     |    (3, 3)     |    0.9636     |    389.71     |
|      SVM      |       6       |    (2, 2)     |    (4, 4)     |    0.8942     |    439.47     |
|      DTC      |       6       |    (2, 2)     |    (4, 4)     |    0.8273     |    529.83     |
| Random Forest |       6       |    (2, 2)     |    (4, 4)     |    0.9651     |    356.95     |
|      SVM      |       6       |    (2, 2)     |    (5, 5)     |    0.9105     |    430.39     |
|      DTC      |       6       |    (2, 2)     |    (5, 5)     |    0.8328     |    570.45     |
| Random Forest |       6       |    (2, 2)     |    (5, 5)     |    0.9649     |    342.79     |
|      SVM      |       6       |    (3, 3)     |    (1, 1)     |    0.7480     |    228.09     |
|      DTC      |       6       |    (3, 3)     |    (1, 1)     |    0.7922     |    168.23     |
| Random Forest |       6       |    (3, 3)     |    (1, 1)     |    0.9502     |    170.27     |
|      SVM      |       6       |    (3, 3)     |    (2, 2)     |    0.8907     |    261.73     |
|      DTC      |       6       |    (3, 3)     |    (2, 2)     |    0.8074     |    182.63     |
| Random Forest |       6       |    (3, 3)     |    (2, 2)     |    0.9553     |    173.76     |
|      SVM      |       6       |    (3, 3)     |    (3, 3)     |    0.9118     |    284.44     |
|      DTC      |       6       |    (3, 3)     |    (3, 3)     |    0.8006     |    176.43     |
| Random Forest |       6       |    (3, 3)     |    (3, 3)     |    0.9553     |    150.49     |
|      SVM      |       6       |    (3, 3)     |    (4, 4)     |    0.9193     |    188.65     |
|      DTC      |       6       |    (3, 3)     |    (4, 4)     |    0.8005     |    166.91     |
| Random Forest |       6       |    (3, 3)     |    (4, 4)     |    0.9564     |    127.38     |
|      SVM      |       6       |    (3, 3)     |    (5, 5)     |    0.9088     |     89.53     |
|      DTC      |       6       |    (3, 3)     |    (5, 5)     |    0.8069     |    152.78     |
| Random Forest |       6       |    (3, 3)     |    (5, 5)     |    0.9579     |    108.62     |
|      SVM      |       6       |    (4, 4)     |    (1, 1)     |    0.8053     |    184.38     |
|      DTC      |       6       |    (4, 4)     |    (1, 1)     |    0.8509     |    107.66     |
| Random Forest |       6       |    (4, 4)     |    (1, 1)     |    0.9621     |    111.45     |
|      SVM      |       6       |    (4, 4)     |    (2, 2)     |    0.8918     |    289.62     |
|      DTC      |       6       |    (4, 4)     |    (2, 2)     |    0.8518     |    116.97     |
| Random Forest |       6       |    (4, 4)     |    (2, 2)     |    0.9700     |    111.78     |
|      SVM      |       6       |    (4, 4)     |    (3, 3)     |    0.9204     |    188.93     |
|      DTC      |       6       |    (4, 4)     |    (3, 3)     |    0.8541     |    112.89     |
| Random Forest |       6       |    (4, 4)     |    (3, 3)     |    0.9683     |     95.93     |
|      SVM      |       6       |    (4, 4)     |    (4, 4)     |    0.8986     |     63.41     |
|      DTC      |       6       |    (4, 4)     |    (4, 4)     |    0.8573     |     99.39     |
| Random Forest |       6       |    (4, 4)     |    (4, 4)     |    0.9701     |     79.80     |
|      SVM      |       6       |    (4, 4)     |    (5, 5)     |    0.8772     |     47.23     |
|      DTC      |       6       |    (4, 4)     |    (5, 5)     |    0.8548     |     72.41     |
| Random Forest |       6       |    (4, 4)     |    (5, 5)     |    0.9695     |     60.55     |
|      SVM      |      18       |    (2, 2)     |    (1, 1)     |    0.8022     |    415.57     |
|      DTC      |      18       |    (2, 2)     |    (1, 1)     |    0.7768     |    419.54     |
| Random Forest |      18       |    (2, 2)     |    (1, 1)     |    0.9438     |    405.65     |
|      SVM      |      18       |    (2, 2)     |    (2, 2)     |    0.8718     |    460.13     |
|      DTC      |      18       |    (2, 2)     |    (2, 2)     |    0.7877     |    553.30     |
| Random Forest |      18       |    (2, 2)     |    (2, 2)     |    0.9487     |    450.64     |
|      SVM      |      18       |    (2, 2)     |    (3, 3)     |    0.8870     |    529.68     |
|      DTC      |      18       |    (2, 2)     |    (3, 3)     |    0.7903     |    780.02     |
| Random Forest |      18       |    (2, 2)     |    (3, 3)     |    0.9496     |    463.83     |
|      SVM      |      18       |    (2, 2)     |    (4, 4)     |    0.9003     |    618.61     |
|      DTC      |      18       |    (2, 2)     |    (4, 4)     |    0.7918     |    1003.52    |
| Random Forest |      18       |    (2, 2)     |    (4, 4)     |    0.9510     |    499.87     |
|      SVM      |      18       |    (2, 2)     |    (5, 5)     |    0.9117     |    722.95     |
|      DTC      |      18       |    (2, 2)     |    (5, 5)     |    0.7938     |    1370.02    |
| Random Forest |      18       |    (2, 2)     |    (5, 5)     |    0.9524     |    480.86     |
|      SVM      |      18       |    (3, 3)     |    (1, 1)     |    0.8161     |    231.41     |
|      DTC      |      18       |    (3, 3)     |    (1, 1)     |    0.7543     |    180.59     |
| Random Forest |      18       |    (3, 3)     |    (1, 1)     |    0.9317     |    178.47     |
|      SVM      |      18       |    (3, 3)     |    (2, 2)     |    0.9000     |    269.27     |
|      DTC      |      18       |    (3, 3)     |    (2, 2)     |    0.7671     |    216.17     |
| Random Forest |      18       |    (3, 3)     |    (2, 2)     |    0.9397     |    186.23     |
|      SVM      |      18       |    (3, 3)     |    (3, 3)     |    0.9155     |    347.92     |
|      DTC      |      18       |    (3, 3)     |    (3, 3)     |    0.7656     |    250.39     |
| Random Forest |      18       |    (3, 3)     |    (3, 3)     |    0.9390     |    173.89     |
|      SVM      |      18       |    (3, 3)     |    (4, 4)     |    0.9213     |    242.25     |
|      DTC      |      18       |    (3, 3)     |    (4, 4)     |    0.7659     |    269.63     |
| Random Forest |      18       |    (3, 3)     |    (4, 4)     |    0.9366     |    153.32     |
|      SVM      |      18       |    (3, 3)     |    (5, 5)     |    0.9069     |    107.44     |
|      DTC      |      18       |    (3, 3)     |    (5, 5)     |    0.7627     |    261.41     |
| Random Forest |      18       |    (3, 3)     |    (5, 5)     |    0.9383     |    131.96     |
|      SVM      |      18       |    (4, 4)     |    (1, 1)     |    0.8744     |    196.86     |
|      DTC      |      18       |    (4, 4)     |    (1, 1)     |    0.8288     |    118.74     |
| Random Forest |      18       |    (4, 4)     |    (1, 1)     |    0.9543     |    117.41     |
|      SVM      |      18       |    (4, 4)     |    (2, 2)     |    0.9201     |    298.79     |
|      DTC      |      18       |    (4, 4)     |    (2, 2)     |    0.8393     |    149.20     |
| Random Forest |      18       |    (4, 4)     |    (2, 2)     |    0.9630     |    122.23     |
|      SVM      |      18       |    (4, 4)     |    (3, 3)     |    0.9327     |    208.38     |
|      DTC      |      18       |    (4, 4)     |    (3, 3)     |    0.8357     |    166.96     |
| Random Forest |      18       |    (4, 4)     |    (3, 3)     |    0.9642     |    111.94     |
|      SVM      |      18       |    (4, 4)     |    (4, 4)     |    0.9119     |     77.23     |
|      DTC      |      18       |    (4, 4)     |    (4, 4)     |    0.8306     |    163.70     |
| Random Forest |      18       |    (4, 4)     |    (4, 4)     |    0.9614     |     94.53     |
|      SVM      |      18       |    (4, 4)     |    (5, 5)     |    0.8917     |     58.91     |
|      DTC      |      18       |    (4, 4)     |    (5, 5)     |    0.8310     |    132.81     |
| Random Forest |      18       |    (4, 4)     |    (5, 5)     |    0.9612     |     74.49     |
|      SVM      |      24       |    (2, 2)     |    (1, 1)     |    0.7996     |    421.30     |
|      DTC      |      24       |    (2, 2)     |    (1, 1)     |    0.7714     |    430.16     |
| Random Forest |      24       |    (2, 2)     |    (1, 1)     |    0.9418     |    412.88     |
|      SVM      |      24       |    (2, 2)     |    (2, 2)     |    0.8699     |    474.92     |
|      DTC      |      24       |    (2, 2)     |    (2, 2)     |    0.7764     |    609.04     |
| Random Forest |      24       |    (2, 2)     |    (2, 2)     |    0.9457     |    466.62     |
|      SVM      |      24       |    (2, 2)     |    (3, 3)     |    0.8874     |    562.12     |
|      DTC      |      24       |    (2, 2)     |    (3, 3)     |    0.7798     |    910.05     |
| Random Forest |      24       |    (2, 2)     |    (3, 3)     |    0.9488     |    490.25     |
|      SVM      |      24       |    (2, 2)     |    (4, 4)     |    0.8983     |    659.17     |
|      DTC      |      24       |    (2, 2)     |    (4, 4)     |    0.7897     |    1295.90    |
| Random Forest |      24       |    (2, 2)     |    (4, 4)     |    0.9472     |    517.15     |
|      SVM      |      24       |    (2, 2)     |    (5, 5)     |    0.9096     |    704.71     |
|      DTC      |      24       |    (2, 2)     |    (5, 5)     |    0.7916     |    4479.23    |
| Random Forest |      24       |    (2, 2)     |    (5, 5)     |    0.9464     |    705.41     |
|      SVM      |      24       |    (3, 3)     |    (1, 1)     |    0.8217     |    234.92     |
|      DTC      |      24       |    (3, 3)     |    (1, 1)     |    0.7446     |    182.86     |
| Random Forest |      24       |    (3, 3)     |    (1, 1)     |    0.9292     |    180.71     |
|      SVM      |      24       |    (3, 3)     |    (2, 2)     |    0.8995     |    285.90     |
|      DTC      |      24       |    (3, 3)     |    (2, 2)     |    0.7638     |    228.87     |
| Random Forest |      24       |    (3, 3)     |    (2, 2)     |    0.9320     |    191.21     |
|      SVM      |      24       |    (3, 3)     |    (3, 3)     |    0.9166     |    362.78     |
|      DTC      |      24       |    (3, 3)     |    (3, 3)     |    0.7522     |    287.64     |
| Random Forest |      24       |    (3, 3)     |    (3, 3)     |    0.9308     |    181.64     |
|      SVM      |      24       |    (3, 3)     |    (4, 4)     |    0.9195     |    250.14     |
|      DTC      |      24       |    (3, 3)     |    (4, 4)     |    0.7549     |    311.50     |
| Random Forest |      24       |    (3, 3)     |    (4, 4)     |    0.9298     |    164.07     |
|      SVM      |      24       |    (3, 3)     |    (5, 5)     |    0.9034     |    116.76     |
|      DTC      |      24       |    (3, 3)     |    (5, 5)     |    0.7495     |    320.25     |
| Random Forest |      24       |    (3, 3)     |    (5, 5)     |    0.9310     |    147.50     |
|      SVM      |      24       |    (4, 4)     |    (1, 1)     |    0.8810     |    204.91     |
|      DTC      |      24       |    (4, 4)     |    (1, 1)     |    0.8256     |    123.23     |
| Random Forest |      24       |    (4, 4)     |    (1, 1)     |    0.9541     |    118.87     |
|      SVM      |      24       |    (4, 4)     |    (2, 2)     |    0.9225     |    308.32     |
|      DTC      |      24       |    (4, 4)     |    (2, 2)     |    0.8289     |    158.07     |
| Random Forest |      24       |    (4, 4)     |    (2, 2)     |    0.9607     |    124.95     |
|      SVM      |      24       |    (4, 4)     |    (3, 3)     |    0.9333     |    227.19     |
|      DTC      |      24       |    (4, 4)     |    (3, 3)     |    0.8346     |    196.75     |
| Random Forest |      24       |    (4, 4)     |    (3, 3)     |    0.9588     |    117.16     |
|      SVM      |      24       |    (4, 4)     |    (4, 4)     |    0.9114     |     81.49     |
|      DTC      |      24       |    (4, 4)     |    (4, 4)     |    0.8286     |    200.64     |
| Random Forest |      24       |    (4, 4)     |    (4, 4)     |    0.9600     |     99.57     |
|      SVM      |      24       |    (4, 4)     |    (5, 5)     |    0.8918     |     63.80     |
|      DTC      |      24       |    (4, 4)     |    (5, 5)     |    0.8283     |    163.17     |
| Random Forest |      24       |    (4, 4)     |    (5, 5)     |    0.9618     |     80.01     |
 _______________________________________________________________________________________________
Summary totalPass each: 	90

|__AVG Score__  |       |
|---------------|-------|
|      SVM      |  0.85 |
|      DTC      |  0.82 |
| Random Forest |  0.95 |

|__AVG Time__   |       |
|---------------|-------|
|      SVM      | 281.85|
|      DTC      | 332.58|
| Random Forest | 219.89|

|__Max Score__  |       |
|---------------|-------|
|      SVM      | 0.9333|
|      DTC      | 0.8752|
| Random Forest | 0.9707|
