## EECS 731 Project 6: Anomaly Detection by Matthew Taylor

### Overview

This project is an introduction to time series anomaly detection. Various anomaly detection techniques will be used to find abnormalities in real-world data. The performance and accuracy of these techniques will be compared to illustrate the strengths and weaknesses of each.

### Approach

I began by downloading [this dataset](https://www.kaggle.com/boltzmannbrain/nab). This dataset contains real-world information about the utilization of one of Amazon's EC2s over a span of a few days. Plotting this dataset shows sustained utilization around 90-100% with a short-lived drop down to around 20%. This behavior is ideal when detecting anomalies. This characteristic helps us easily identify the anomalies that our models should detect. Once the dataset was selected, I detected anomalies using interquartile range, an isolation forest, and a one class support vector machine. The results were plotted with the outliers colored red and the normal points colored black.

### How to Run

This project was written in a Jupyter Notebook running Python 3.7.2. This project relies on a small number of modules, which can be installed by running this command:
```
pip3 install -r requirements.txt
```

Once the requirements are installed, each of the cells in the Jupyter Notebook can be executed. However, this is not required as each cell has already been executed and the results are shown.

### Results

All three of the models trained and detected anomalies very quickly. Performance between them was nearly identical. Each of the models were able to detect the obvious anomaly where utilization dropped to around 20%. The main differences between the models were the classification of points near the usual utilization. It could be argued that these points are either normal or outliers. The IQR model was by far the simplest to understand and implement, and it classified the least ambiguous points near the mean. The isolation forest classified the most ambiguous points as outliers. For this dataset, this behavior seems incorrect. However, this behavior may be desirable for other datasets. Lastly, the one class support vector machine had a kind of "happy-medium" between the two previous models, as it classified more ambiguous points as the IQR model, but fewer than the isolation forest. Despite the differences in the handling of ambiguous points between these three models, it's important to remember that all of them were able to correctly detect the blatant anomalies.

### Future Work and Optimizations

Given more time to work on this project, I would have created a generative adversarial network, as these have state-of-the-art performance. Furthermore, I would have tested these models on another dataset with slightly more ambiguous outliers to see how they perform. All three of the models I used here could easily detect the substantial outliers. The interesting differences between the models occurred near the a majority of the normal points. These differences may have been more visible had the models been classifying outliers with another dataset.
