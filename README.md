# Fonterra Milk Loss Outlier Detection Problem

Interviewee: Pascal Eun Sig Cheon

When a piece of equipment is cleaned at a manufacturing site, any milk residue left inside is washed away down the drain. The murkiness of the water is directly proportional to the loss of milk. Our task is to build an algorithm to determine when the loss is more than "normal" at the daily level. 

This task can be formulated as an unsupervised outlier detection problem. In other words, we will define what the "normal" daily loss is and what it means to be an outlier from the "normal" value. The approach we have considered for this is the "Z-score analysis". For a given observation $x$, the z-score of $x$ is defined by $Z \coloneqq \frac{x - \mu}{\sigma}$ where $\mu$ and $\sigma$ are the mean and standard deviation of the dataset, respectively. In other words, the z-score is a measure of how far away an observed value $x$ is from the expected value $\mu$. In the context of our task, the $x$ is the observed milk wastage on a day, $\mu$ is the expected daily wastage, and $\sigma$ represents how confident we are of the expected wastage amount.

Before the z-score analysis, we carried out a data preprocessing. The provided data consisted of murkiness and flow at the minute-level. However, there were some rows in the data with NaNs. Since there were not many rows with NaNs in the murkiness column, we took those rows out of the analysis. For the rows with NaNs in the flow column, we replaced with the mean of the flow. We also carried out a feature engineering. Since we were interested in the loss of milk, we defined a new variabled called "wastage" to represent how much milk was wasted down the drain, computed by (murkiness * flow). Furthermore, we defined the daily wastage measure to be the daily mean of the wastage. From this, the z-score analyses were carried out on this daily mean wastage variable. 

For the demonstration of the performance of the described approach, we carried out the analysis in two ways (1) using the whole dataset as both the training set and the testing set (2) separating out the dataset into a training and a testing set. 

In the notebook, we also present conclusions on the discussed approach, alternative approaches, future work, further questions to extend the presented approach, and the data quality issues we identified.
