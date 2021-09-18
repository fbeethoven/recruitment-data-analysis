# recrutiment-data-analysis
Imagine that you run a candy factory, in which you manufacture various types of candy, chocolate bars and marshmallows.
You have very advanced machines that can manufacture multiple types of sweetness, but they may sometimes make mistakes (e.g. add chocolate to the marshmallows) and you’d like to detect this kind of mistakes before you ship the goods to stores.
Luckily, the machines measure some parameters of the produced sweetness, such as volume and weight of each produced item along with the machine id and timestamp.

Your goal is to identify outliers in that data (so that you can quickly detect that a machine is not functioning properly)

Directions:
 - Use pandas to load and clean the data (there may be some incorrect readings in the data set)
 - visualise the data (you may use matplotlib)
 - cluster the data and analyse distances of data points from the cluster centroids to detect outliers. You do not need to implement clustering on your own, find an implementation in sklearn.

Expected completion time: ca 1.5 hours

# Solution:

We use pandas to run a KMeans clustering algorithm on Jupyter Notebooks. We clean the data and find 4 to be the number of optimal clusters according to the Elbow Method. 
A different approach is to use MeanShift but KMeans works well for this task.

### Conclusion

Based on the Cluster Analysis we can identify two main operations on the clusters 0 and 1
(elements at cluster 0 are smaller and much lighter, maybe they are marshmallows, and elements at cluster 1 are both heavier and bigger).

The outliers are in clusters 2 and 3. Maybe this is due to marshmallows treated as chocolate bars (cluster 2),
and chocolate bars treated as marshmallows (cluster 3).

In September 16, all elements are in cluster 2, indicating that someone made a mistake.
We can speculate that September 16 was going to be dedicated to producing only chocolate bars and someone thought they were going to produce only marshmallows.
In any case all output from September 16 is compromised in some manner.

We also noticed that all mistakes in September 15 were due to *machine_1*, either because is malfunctioning or because the people operating
this machine have less experience.
However this have nothing to do with the issue on September 16 since both machines are in cluster 2, and the outliers are not significant
(~5.8% of the output of Sepmber 15).

The model we produced allow us to improve quality in two ways:
* Track all elements and if they are not in cluster 0 or 1 they can be classified as low quality.
* Track batches, and if the weighted score is >0.001 classify the batch as low quality.
