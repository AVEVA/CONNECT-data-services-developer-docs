---
uid: sds-calculated-summaries
---


# Calculated summaries

When you send an API request to the [List Summaries](xref:sds-stream-data#list-summaries) endpoint, the REST API responds with a list of calculated summaries for each interval queried in the request. Calculated summaries are different types of statistical measures of a data stream that can help you summarize, analyze, or interpret data. The following calculated summaries are included in the response body of your request to the `List Summaries` endpoint:

| Summary | Description |
|--|--|
| **Count** | The simple numerical tally of occurrences or instances of a particular event or category within a dataset. |
| **Kurtosis** | A statistical measure that quantifies the shape and distribution of data in a probability distribution or dataset. It provides insight into the "tailedness" or the extent to which the data in the distribution deviates from a normal distribution. |
| **Maximum** | The largest or highest value observed within a dataset or a set of numerical values. |
| **Mean** | The average of a set of numerical values. |
| **Minimum** | The smallest or lowest value observed within a dataset or a set of numerical values. |
| **None** | The absence or lack of a particular attribute, characteristic, value, or occurrence. It signifies that there is no presence or quantity of the item being considered. |
| **PopulationStandardDeviation** | A measure of the dispersion or spread of data points within a population. It quantifies how much individual data points deviate from the mean (average) of the entire population. |
| **Range** | The difference between the maximum and minimum values within a dataset. |
| **Skewness** | A measure that quantifies the asymmetry of the probability distribution or dataset. It indicates the extent to which the data is skewed (lopsided) to one side of the distribution relative to the other. A distribution or dataset can be skewed to the left (negatively skewed), skewed to the right (positively skewed), or approximately symmetric. |
| **StandardDeviation** | A measure of the dispersion or spread of data points within a dataset. It quantifies how much individual data points deviate from the mean (average) of the dataset. |
| **Total** | The sum or aggregate of all the individual values within a dataset or a specific subset of data. It represents the combined value of all the individual components being considered. |
| **WeightedMean** | A type of average that takes into account not only the values of a dataset but also the index weights associated with each value. It is used when different data points have varying degrees of importance or significance. |
| **WeightedPopulationStandardDeviation** | A measure of the dispersion or spread of data points within a population, where each data point is assigned an index weight based on its importance or significance. This concept extends the traditional population standard deviation by incorporating index weights that reflect the relative importance of individual data points. |
| **WeightedStandardDeviation** | A measure of the dispersion or spread of data points within a dataset with an index weight applied that indicates relative significance to each value in a set of values. Values with a higher value for their index weight are considered as more significant to a sample as compared to the other values in a sample. |
