# Information Gain and implementation

## Why is Information Gain important ?

Let's consider a prediction model. As we know, such a model often contains many features. The problem is that we don't initially know which features are the most important.
Some features are not useful for prediction at all. In fact, some can cause significant prediction errors because they contain no meaningful information related to the target.

For example, we want to predict whether a fruit is an Orange or an Apple based on the given features: **Weight, Size** and **Color**. 
If the model bases its predictions only on Weight, it will not learn properly because this feature has little to do with distinguishing an apple from an orange.

**Therefore, the model must select features that contain the most information about the target.**

>> This is where we need **Information Gain.**


Information Gain helps us :

- To know how much information each variable contains.
- To determine which feature should be used (important for feature selection).
- To identify which features are the most informative.
- To quantify the reduction in uncertainty after splitting in Decision Trees.


>> Before understanding **Information Gain** it is essential to know about **Entropy**



## Entropy is a measure of messiness or uncertainty


**High entropy** :  High entropy: This is like a garden where red, yellow, and white flowers are all
mixed together in the same area. You can't easily count the flowers in each category separately. If you point to a random flower, it is hard to predict its color.


*In the Orange/Apple example:* We know there should be two categories, "Orange" and "Apple," since there are two potential outputs. However, the key point is that neither category is pure. In other words, both categories contain a mix of apples and oranges.

**Low entropy:** The flowers are separated, allowing you to count each category easily. 
You know exactly where the red flowers are and can point to them with high certainty.

*in the Orange/Apple example :* Each category contains olny onr type of fruit : **eiher all Apple or all Orange**.We usually call this *pure data*.

## We calculate information gain using Entropy
We calculate Information Gain by comparing the entropy of a dataset before and after a split. 
>> information Gain = Entropy before split - Entropy after split

# Orange Apple classification example :
## problem : Single feature split is Insufficient
### Initial state :
- **Dataset :** Mixed Oranges and Apples
- **Entropy before split :** High (Heigh impurity /Uncertainty)
  
### Split based on weight alone :
**Abesrvation**
- There are heavy apples and light apples
- There are heavy oranges and light oranges
- Oranges appear in both category
- **Entropy :** High
- **IG :** Low
  
### Solusion : Look for maximum Information Gain(Texture)
To effectively classify Apples and Oranges we have to evaluate multiple features and select the one with **Highest Information Gain**.

- **Weight :** High Entropy and low Information Gain(As we have observed)
- **Size :** (small,large)
  
  - There are small and large apples
  - There are small and larges oranges
  - Both categories contain apples and oranges
  **entropy :**  High
  **Information Gain :** Low
    
- **Color :** (Orange/red)

  - Apples are mostly red
  - Oranges are mostly orange
  - **Entropy :** high
  - **Information Gain :** high

# Implementation 
```python
from sklearn.feature_selection import mutual_info_classif
from sklearn.preprocessing import LabelEncoder
import numpy as np
import pandas as pd

# Sample data
X = pd.DataFrame({
    'weight_g': [120,124,123,
                 95,99,119,
                 134,120,121,
                 100,99,98,
                 111,112,120],
    'color': ['red','orange','red',
              'red','red','red',
              'orange','orange','red',
              'orange','red','red',
              'orange','red','red'],


    'Size':['medium','big','big',
            'small','medium','medium',
            'big','medium','medium',
            'small','small','small',
            'small','small','medium']  
})

#Sample target
y = np.array(['apple','orange','apple',
              'apple','apple','apple',
              'orange','orange','apple',
              'orange','apple','apple',
              'orange','apple','apple']) 
x_encoded = X.apply(LabelEncoder().fit_transform)
ig_scores = mutual_info_classif(x_encoded, y)
ig_scores
# Create a DataFrame for better visualization
feature_importance = pd.DataFrame({
    'feature': X.columns,
    'information_gain': ig_scores
}).sort_values('information_gain', ascending=False)

print(feature_importance)
```

  






  






