# Classification-Evaluation-Review

    Summary of some common performance metrics for classification problems.



 ##### 1.  Definitions

 | Terms    |   Definitions      | 
 | ---------|:----------------:  |
 | TP       |   True Positive  | 
 | FP       |   False Positve  |   
 | TN       |   True Negative  |    
 | FN       |   False Negative |    





##### 2.  Accuracy, Precision, Recall, and F1 Score

   | Metrics    | Calculations            | Descriptions                                                |                   
   | -----------|:----------------------|:--------------------------------------------------------------|
   | Accuracy   | (TP+TN)/(TP+TN+FP+FN)  | out of all samples, how many are correctly predicted   | 
   |            |                        |                                                               |
   | Precision  | TP/(TP+FP)             | out of total predicted positives, how many are actual positive |
   |            |                        |                                                                |
   | Recall     | TP/(TP+FN)             | out of total actual positives, how many are predicted positive |
   |            |                        |          |
   | F1 score   | 2*(precision*recall)/(precision + recall)| seek balance between precision and recall |

 
 
##### 3. F1 score in Multiclass Classifications

###### A multiclass scenario:

    classes: a, b, c
    sample number for each class: n1, n2, n3 
    F1 score for each class: F1a, F1b, F1c


   ###### Macro F1 Score:  

    Macro F1 = (F1a + F1b + F1c)/3 (Sklearn uses this)
    It’s a simple arithmetic mean of per-class F1-scores

    A second way of calculation (Sokolova paper):
    Macro F1 = (Macro precision * Macro recall)/(Macro precision + Macro recall)
     

   ###### Weighted-F1 Score:  
   
    Weighted F1 = (F1a*n1 + F1b*n2 + F1c*n3)/(n1+n2+n3)
    Weighted by sample numbers


   ###### Micro F1 Score: 
   
    Look at all classes together, so TP, TN, FN, FP are each a sum from their individual counterparts.
    Micro F1 = Micro Precision = Micro Recall = Accuracy


   ###### Be cautious with F1 scores
   
    They assign equal weights to precision and recall.
    F1 scores do not take into consideration that prediction errors (FP vs. FN) may have different implications. 


##### 4. MCC: Matthew’s Correlation Coefficient

![MCC](https://user-images.githubusercontent.com/18686382/70392158-b92b9f80-19aa-11ea-9216-45dba400691d.png)
    
    MCC has a range of -1 to 1, with 1 indicating all predictions are correct, -1 indicating all predictions are wrong. 
    "[MCC] takes into account true and false positives and negatives and is generally regarded as a balanced measure which can be used even if the classes are of very different sizes."


##### 5. ROC Curve

    ROC(Receiver operating characteristic) is a probability curve and AUC (Area under ROC) represents degree or measure of separability. 
    
    The ROC curve is plotted with TPR against the FPR where TPR is on y-axis and FPR is on the x-axis. 
    It tells how much model is capable of distinguishing between classes.
    ROC AUC doesn't distinguish the costs of different kinds of errors.
 

###### References
 
         1. https://scikit-learn.org/stable/modules/model_evaluation.html
         2. https://towardsdatascience.com/a-tale-of-two-macro-f1s-8811ddcf8f04
         3. https://www.sciencedirect.com/science/article/pii/S0306457309000259 (Sokova paper)
         4. other online sources
         
