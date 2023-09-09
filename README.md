# Datascience_Assignments
import pandas as pd
import numpy as np
import seaborn as sns
# import the dataset
iris=sns.load_dataset("iris")
# Create a DataFrame with the data
data=pd.DataFrame(iris)
# Rename the column name
data.rename(columns={'sepal_length':'SL','sepal_width':'SW','petal_length':'PL','petal_width':'PW'},inplace=True)
# Selecting the column sepal_width(SW) for finding Z_scores
sw = data['SW']
# Finding the mean and standard deviation of each column
means = sw.mean()
std_devs = sw.std()
# Finding the z_scores
z_scores = (sw - means) / std_devs
# Findout the Outliers in the column sepal_width(SW)
def outliers_z_scores(z_scores):
    outliers = []
    for i in z_scores:
        if i < -3 or i > 3:
            outliers.append(i)
    return outliers
# we already calculate the z_scores
outliers = outliers_z_scores(z_scores)
print(outliers)       

