---
title: "Wifi Indoor Positioning" # Title of your project
weight: 1 # Order in which to show this project on the home page
external_link: "" # Optional external link instead of modal
resources:
    - src: wifi.jpg
draft: true
output: 
  blogdown::html_page:
    toc: false
    fig_width: 8
    dev: "svg"
---

```{r setup, include=FALSE}
knitr::opts_chunk$set(
  echo = FALSE, message = F, warning = F
  )
```


## Overview

*Many real world applications need to know the localization of a user in the world to provide their services. Therefore, automatic user localization has been a hot research topic in the last years. Automatic user localization consists of estimating the position of the user (latitude, longitude and altitude) by using an electronic device, usually a mobile phone. Outdoor localization problem can be solved very accurately thanks to the inclusion of GPS sensors into the mobile devices. However, indoor localization is still an open problem mainly due to the loss of GPS signal in indoor environments. Although, there are some indoor positioning technologies and methodologies, this database is focused on WLAN fingerprint-based ones (also know as WiFi Fingerprinting).* Source [UCI Machine Learning Repository](https://archive.ics.uci.edu/ml/datasets/UJIIndoorLoc)

## The project

### Dataset 

*The UJIIndoorLoc database covers three buildings of Universitat Jaume I with 4 or more floors and almost 110.000m2. It can be used for classification, e.g. actual building and floor identification, or regression, e.g. actual longitude and latitude estimation. It was created in 2013 by means of more than 20 different users and 25 Android devices. The database consists of 19937 training/reference records (trainingData.csv file) and 1111 validation/test records (validationData.csv file).* Source [UCI Machine Learning Repository](https://archive.ics.uci.edu/ml/datasets/UJIIndoorLoc)

### Technologies 

**Python** as a programming language. Libraries used: 

* *Data manipulation*: Pandas and Numpy
* *Visualizations*: Matplotlib, Seaborn and Plotly
* *Machine learning*: Scikit-Learn

*JupyterLab* has been used as IDE. 

### Results 

This challenge is divided in two types of machine learning problems; classification & regression. 

+ Classification: 
    - Building: 100% Accuracy, 1.00 Kappa
    - Floor: 94% Accuracy, 0.92 Kappa

The target variables for regression are *LATITUDE* and *LONGITUDE*. The results are:

```{r}
# res_regr <- tribble(
#   ~" "       , ~R.squared, ~RMSE          , ~MEA          ,
#   "LATITUDE" , 0.98      , "10.68 meters" , "6.51 meters" ,  
#   "LONGITUDE", 0.99      , "11.87 meters" , "7.37 meters"
# )
# res_regr %>% 
#   kable() %>% 
#   kable_styling(
#     bootstrap_options = c("striped", "hover", "condensed", "responsive"),
#     full_width = F
#     )
```

## Conclusion

Wifi signal can be used to predict the position of people in a building, and can be implemented on other buildings like shopping malls. 

The main problems are (sorted in order of importance): 

1. Data collection: the WAP (Wireless Access Point) should be placed in an area without interferences and other noise effects (like some specific materials on walls) and they have to maintain a similar distance between all the WAPs (a structure structure would be great). 
2. Data cleaning: with a good placement of the WAPs, the complexity of this step will be reduced, as the time to start having good models. We will also have problems with the different signals received by different types of phones. This can be normalized to reduce the impact into our machine learning models. 
3. Machine Learning: it is very easy for some models like K-Nearest Neighbours to cause overfitting in this task. To avoid that, it requires to be sure about the data we are using to train them, and be certain that the validation data has the same distribution in all the areas than the training data. 
