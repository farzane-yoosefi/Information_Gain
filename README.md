# Information Gain and implementation

## Why is Information Gain important ?

Let's consider a prediction model. As we know, such a model often contains many features. The problem is that we don't initially know which features are the most important.
Some features are not useful for prediction at all. In fact, some can cause significant prediction errors because they contain no meaningful information related to the target.

For example, we want to predict whether a fruit is an Orange or an Apple based on the given features: Weight, Size, and Color. 
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


**Heigh entropy** :  It is like a garden in which red , yellow and white flowers are all in the same area.So that you can't count each individual flowers separately. 
If you point to random flower it is hard to predict the color.

*in Orange/Apple example :* Actually we already know thare should be 2 categories :**Orange and Apple** ,since there are two potential outputs.
. But the point is that neither of them are pure.In other words , both categories are fulled with a mix of apples and oranges .

**Low entropy**  : Flowers are seperate so that you can countn each category separately.You know where red flowers are and point directly at this position with 
heigh certainty.


*in Orange/Apple example :* Each category has one single data : **eiher Apple or Orange**.We usually call them as *pure data*.
## We calculate information gain using Entropy
  






