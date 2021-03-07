# Springboard_Capstone_3
# Clinical and Imaging Analyses to Predict Alzheimer’s Disease
Alzheimer’s disease is a neurodegenerative disease that involves the death of neurons within the brain. According to the Alzheimer’s Association, over 5 million people suffer from Alzheimer’s in the United States, and it is estimated to increase to 14 million by 2050. Therefore, being able to predict and identify factors that influence Alzheimer’s progression as well as being able to identify which stage of the disease’s progression a patient is affected by is becoming more essential.

The analyses performed here aimed to predict whether a participant suffered from Alzheimer’s Disease as well as which stage of Alzheimer’s they were affected by.

The [final report]( https://github.com/ballard-s/Springboard_Capstone_3/blob/main/Final%20Report/Capstone3_Final_Report.pdf) of these analyses expands on the summary below.

## Data
The data utilized in the analyses are from 3 separate data sets. Note that the term "demented" is used to describe a participant affected by Alzheimer's Disease.

a. The first [data set](https://www.kaggle.com/jboysen/mri-and-alzheimers) consists of clinical measurements and MRI measurements (note: not images) from a cross-sectional study. Participants were young or middle aged, and nondemented or demented older adults. This was used to try to predict which individuals are affected by Alzheimer's disease as well as to identify which clinical measurements contribute to this prediction.

b. The second [data set](https://www.kaggle.com/jboysen/mri-and-alzheimers) consists of clinical measurements and MRI measurements (note: not images) from a longitudinal study. Participants were non-demented and demented older adults that were imaged at least 2 times in subsequent visits that spanned at least 1 year. This information was used to try to predict which individual are affected or will become affected by Alzheimer's Disease.

c. The third [data set](https://www.kaggle.com/tourist55/alzheimers-dataset-4-class-of-images?select=Alzheimer_s+Dataset) consists of MRI images that classifies Alzheimer’s and Dementia patients into 4 classes (non-demented, very mildly demented, mildly demented, and moderately demented). These images were to attempt to identify which stage of Alzheimer's Disease a patient is affected by.

## DataWrangling
[Data Wrangling Notebook]( https://github.com/ballard-s/Springboard_Capstone_3/blob/main/Data%20Wrangling%20and%20EDA/Capstone3_DW_EDA.ipynb)

The following points summarize the Data Wrangling steps performed for each dataset:

a.	 Cross sectional study
•	Participants with several features missing were removed
•	Missing values for Categorical features were filled in with the mode value
•	Non-essential features were dropped
b.	 Longitudinal Study
•	Missing values for Categorical features were filled in with the mode value
•	Non-essential features were dropped
c.	MRI Images
•	Image Augmentation was performed for training set of images so that all classes contained the same number of images

## Exploratory Data Analysis
[EDA Notebook]( https://github.com/ballard-s/Springboard_Capstone_3/blob/main/Data%20Wrangling%20and%20EDA/Capstone3_DW_EDA.ipynb)

The following observations were noted from the 3 datasets:

a.	Using the Clinical Dementia Rating (CDR) as the response variable classes, it was noted that the Mini-mental state examination scores and Normalized whole brain volume values decreased as the severity of Alzheimer’s disease increased.

![MMSE Scores]( https://github.com/ballard-s/Springboard_Capstone_3/blob/main/Figures/Cross%20sectional%20study/MMSE%20boxplot.png)

![nWBV]( https://github.com/ballard-s/Springboard_Capstone_3/blob/main/Figures/Cross%20sectional%20study/nWBV%20boxplot.png)

b.	Using the Group feature as the response variable classes, it was noted that the Mini-mental state examination scores were significantly different between the Non-demented group and Demented or Converted groups. There was also a difference between Demented and Converted groups. In addition, there were significant differences in nWBV between the Non-demented group and Demented or Converted groups.

![MMSE Scores]( https://github.com/ballard-s/Springboard_Capstone_3/blob/main/Figures/Longitudinal%20study/MMSE%20graph.png)

![nWBV]( https://github.com/ballard-s/Springboard_Capstone_3/blob/main/Figures/Longitudinal%20study/nWBV%20graph.png)

c.	From the MRI image dataset, the average image was determined for each class (see below). In addition, Principal Component Analysis was performed to find the images that best represented each class (see Final Report).

![Average Non-demented]( https://github.com/ballard-s/Springboard_Capstone_3/blob/main/Figures/Imaging%20study/non_mean.png)

![Average Very Mild demented]( https://github.com/ballard-s/Springboard_Capstone_3/blob/main/Figures/Imaging%20study/verymild_mean.png)

![Average Mild demented]( https://github.com/ballard-s/Springboard_Capstone_3/blob/main/Figures/Imaging%20study/mild_mean.png)

![Average Moderate demented]( https://github.com/ballard-s/Springboard_Capstone_3/blob/main/Figures/Imaging%20study/moderate_mean.png)


## Modeling
[Modeling Notebook]( https://github.com/ballard-s/Springboard_Capstone_3/blob/main/Modeling/Capstone3_Modeling.ipynb)

Four different models were tested for the Cross-sectional (a) study and Longitudinal Study (b):
1.	K-nearest neighbors
2.	Random Forest
3.	One vs Rest (Logistic Regression)
4.	One vs Rest (Multi-Layer Perceptron)
The Model Metrics for each study are given below:


![Cross-sectional Study](https://github.com/ballard-s/Springboard_Capstone_3/blob/main/Figures/Cross%20sectional%20study/A%20model%20metrics.png)

![Longitudinal Study]( https://github.com/ballard-s/Springboard_Capstone_3/blob/main/Figures/Longitudinal%20study/B%20model%20metrics.png)

From these metrics the KNN model was recommended for the Cross-sectional study, and the One vs Rest (MLP) model was recommended for the Longitudinal study.

One model (Convolutional Neural Network Model) was tested for the imaging dataset. The metrics of this model are given below.

![Imaging Study]( https://github.com/ballard-s/Springboard_Capstone_3/blob/main/Figures/Imaging%20study/C%20model%20metrics.png)


## Identifying features of importance that influence Cross-sectional and Longitudinal studies

The Random Forest model was used for both the Cross-sectional and Longitudinal studies to find the features that are important for predicting which group a participant would be classified as.

For the Cross-sectional study, these features were the MMSE score and nWBV value.

For the Longitudinal study, these features were the CDR value and MMSE score.


## Future Research and Recommendations

* expand the analyses
- having additional participants that have CDR values of 2 and 3
- more participants in the Converted Group
- more participants with MRI images that could be classified as Moderate Demented
- Follow up images of participants in the imaging study

* Test more models for image dataset, including:
Xception and ResNet50


## Who would benefit from these analyses?

* provide physician’s, researchers, and patients with predictions of Alzheimer’s Disease and classification of the stage of Alzheimer’s Disease
* academic or pharmaceutical researchers could utilize image analyses to determine in their drug/treatment of interest can slow the progression of Alzheimer’s disease using MRI images as their experimental output
![image](https://user-images.githubusercontent.com/51376836/110250983-58dc3280-7f4c-11eb-9775-5c274ba526f7.png)
