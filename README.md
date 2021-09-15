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
