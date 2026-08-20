# Math Intuition and Implementation of Principal Component Analysis

![rw-book-cover](https://miro.medium.com/v2/resize:fit:997/1*PtaeFuNJxdZVz99WfYrpZA.png)

## Metadata
- Author: [[Arun Amballa]]
- Full Title: Math Intuition and Implementation of Principal Component Analysis
- Category: #articles
- Summary: Principal Component Analysis (PCA) is a technique used for dimensionality reduction, allowing us to extract significant features from a large set of variables without losing important information. It transforms high-dimensional data into a lower-dimensional space by creating new, independent variables called principal components. PCA helps to simplify data visualization and modeling by reducing redundancy and capturing essential patterns in the data.
- URL: https://medium.com/analytics-vidhya/math-intuition-and-implementation-of-principal-component-analysis-6f02253ceef9

## Full Document
Understanding Math behind Principal Component Analysis and how new feature space is obtained..! A one stop shop for PCA….!!!

![](https://miro.medium.com/v2/resize:fit:1400/1*PtaeFuNJxdZVz99WfYrpZA.png)Dimensionality Reduction 
### **Curse of Dimensionality:**

Machine Learning in general works wonders when the data set provided for training the machine is large and concise. Usually having a good amount of data lets us build a better predictive model since we have more data to train the machine with. However, using a large data set has its own pitfalls. The biggest pitfall is the curse of dimensionality.

It turns out that in large dimensional datasets, there might be lots of inconsistencies in the features or lots of redundant features in the data set, which will only increase the computation time and make data processing and Exploratory Data Analysis more convoluted.

![](https://miro.medium.com/v2/resize:fit:1400/1*0E6cCYvYwSfJV0LzZG50Kg.png)Curse of Dimensionality 

> Let’s say you have a straight line 100 yards long and you dropped a penny somewhere on it. It wouldn’t be too hard to find. You walk along the line and it takes two minutes.
> 
> Now let’s say you have a square 100 yards on each side and you dropped a penny somewhere on it. It would be pretty hard, like searching across two football fields stuck together. It could take days.
> 
> Now a cube 100 yards across. That’s like searching a 30-story building the size of a football stadium. The difficulty of searching through the space gets a *lot* harder as you have more dimensions.
> 
> To get rid of the curse of dimensionality, a process called dimensionality reduction was introduced. Dimensionality reduction techniques can be used to filter only a limited number of significant features needed for training and this is where PCA comes in.
> 
> 

### **There are many ways to achieve dimensionality reduction, but most of these techniques fall into one of two classes:**

> 1.Feature Selection
> 
> 2.Feature Extraction
> 
> 

### **Feature Selection:**

In this, we try to find a subset of the original set of variables, or features, to get a smaller subset which can be used to model the problem. It usually involves three ways:

> 1. Filter
> 
> 2. Wrapper
> 
> 3. Embedded
> 
> Suppose we have a data set with 1000 variables to calculate the GDP of a country, instead of considering every single variable, we might drop all variables except the 10 we think will best predict what the Gross domestic product will look like. Advantages of feature Selection methods include simplicity and maintaining interpretability of your variables.
> 
> As a disadvantage, though, you gain no information from those variables you’ve dropped. If we only use last year’s GDP, the proportion of the population in manufacturing jobs per the most recent American Community Survey numbers, and unemployment rate to predict this year’s GDP, we’re missing out on whatever the dropped variables could contribute to our model. By eliminating features, we’ve also entirely eliminated any benefits those dropped variables would bring.
> 
> 

### **Feature Extraction:**

> Feature extraction**,** however, doesn’t run into this problem. Say we have ten independent variables. In feature extraction, we create ten “new” independent variables, where each “new” independent variable is a combination of each of the ten “old” independent variables. However, we create these new independent variables in a specific way and order these new variables by how well they predict our dependent variable.
> 
> You might say, “Where does the dimensionality reduction come into play?” Well, we keep as many of the new independent variables as we want, but we drop the “least important ones.” Because we ordered the new variables by how well they predict our dependent variable, we know which variable is the most important and least important. But — and here’s the kicker — because these new independent variables are combinations of our old ones, we’re still keeping the most valuable parts of our old variables, even when we drop one or more of these “new” variables!
> 
> Principal component analysis is a technique for *feature extraction* — so it combines our input variables in a specific way, then we can drop the “least important” variables while still retaining the most valuable parts of all of the variables! *As an added benefit, each of the “new” variables after PCA are all independent of one another.* This is a benefit because the assumptions of linear model require our independent variables to be independent of one another.
> 
> 

### **Dimensionality Reduction:**

> Dimensionality reduction is a method of converting the high dimensional variables into lower dimensional variables without changing the specific information of the variables. To overcome the issue of the curse of dimensionality, Dimensionality Reduction is used to reduce the feature space with consideration by a set of principal features.
> 
> 

### Why is Dimensionality Reduction required?

Here are some of the benefits of applying dimensionality reduction to a data set:

> 1.Space required to store the data is reduced as the number of dimensions comes down.
> 
> 2.Less dimensions lead to less computation/training time.
> 
> 3.Some algorithms do not perform well when we have a large dimension. So, reducing these dimensions needs to happen for the algorithm to be useful.
> 
> 4.It takes care of multi-collinearity by removing redundant features. For example, you have two variables — ‘time spent on treadmill in minutes’ and ‘calories burnt’. These variables are highly correlated as the more time you spend running on a treadmill, the more calories you will burn. Hence, there is no point in storing both as just one of them does what you require.
> 
> 5.It helps in visualizing data. As discussed earlier, it is very difficult to visualize data in higher dimensions so reducing our space to 2-D or 3-D may allow us to plot and observe patterns more clearly
> 
> 

### What is Principal Component Analysis?

> In simple words, PCA is a method of obtaining important variables (in form of components) from a large set of variables available in a data set. It extracts low dimensional set of features by taking a projection of irrelevant dimensions from a high dimensional data set with a motive to capture as much information as possible. With fewer variables obtained while minimizing the loss of information, visualization also becomes much more meaningful. PCA is more useful when dealing with 3 or higher dimensional data.
> 
> Principal components analysis (PCA) is a dimensionality reduction technique that enables you to identify correlations and patterns in a data set so that it can be transformed into a data set of significantly lower dimension without loss of any important information.
> 
> It is always performed on a symmetric correlation or covariance matrix. This means the matrix should be numeric and have standardized data.
> 
> Let’s understand it using an example:
> 
> Let’s say we have a data set of dimensions 300 (*n*) × 50 (*p*). *n* represents the number of observations and *p* represents number of predictors. Since we have a large p = 50, there can be `p(p-1)/2` scatter plots i.e. more than 1000 plots possible to analyse the variable relationship. Wouldn’t it be a tedious job to perform exploratory analysis on this data?
> 
> In this case, it would be a lucid approach to select a subset of *p* *(p << 50)* predictor which captures as much information. Followed by plotting the observation in the resultant low dimensional space.
> 
> The image below shows the transformation of a high dimensional data (3 dimension) to low dimensional data (2 dimension) using PCA. Not to forget, each resultant dimension is a linear combination of *p* features
> 
> 

![](https://miro.medium.com/v2/resize:fit:1180/1*Owm-UrVGipi6Gu6Kscb4Pw.png)Principal Component Analysis 
### What are Principal Components?

> Simply put, principal components are the new set of variables that are obtained from the initial set of variables. The principal components are computed in such a manner that newly obtained variables are highly significant and independent of each other. The principal components compress and possess most of the useful information that was scattered among the initial variables.
> 
> If your data set is of 5 dimensions, then 5 principal components are computed, such that, the first principal component stores the maximum possible information and the second one stores the remaining maximum info and so on.
> 
> Now we know the Intuition behind PCA. But you might wonder how these principal components are achieved for a given data set. Let’s Understand the Mathematical Intuition behind PCA. We will try to understand the process in Six steps.
> 
> 

#### Why is normalization of variables necessary in PCA?

> The principal components are supplied with normalized version of original predictors. This is because, the original predictors may have different scales. For example: Imagine a data set with variables’ measuring units as gallons, kilometres, light years etc. It is definite that the scale of variances in these variables will be large.
> 
> Performing PCA on un-normalized variables will lead to insanely large loading for variables with high variance. In turn, this will lead to dependence of a principal component on the variable with high variance. This is undesirable.
> 
> As shown in image below, PCA was run on a data set twice (with un scaled and scaled predictors). This data set has ~40 variables. You can see, first principal component is dominated by a variable Item\_MRP. And, second principal component is dominated by a variable Item\_Weight. This domination prevails due to high value of variance associated with a variable. When the variables are scaled, we get a much better representation of variables in 2-D space.
> 
> 

![](https://miro.medium.com/v2/resize:fit:1400/1*gtqORnzV91lHxrMwjnMsXg.png)
PCA can be thought of as an unsupervised learning problem. The whole process of obtaining principle components from a raw data set can be simplified in six parts:

> 1. Take the whole data set consisting of *d+1 dimension* and ignore the labels such that our new data set becomes *d dimensional.*
> 
> 2. Compute the *mean* for every dimension of the whole data set.
> 
> 3. Compute the *covariance matrix* of the whole data set.
> 
> 4. Compute *eigenvectors* and the corresponding *eigenvalues*.
> 
> 5. Sort the eigenvectors by decreasing eigenvalues and choose k eigenvectors with the largest eigenvalues to form a *d × k dimensional* matrix V.
> 
> 6. Use this *d × k eigenvector matrix* to transform the samples onto the new subspace.
> 
> 

### **So, let’s unfurl the math behind each of this one by one.**

#### **STEP 1 — Take the whole data set consisting of *d+1 dimension’s* and ignore the labels such that our new data set becomes *d dimensional.***

> In general, suppose if we have a data set which is *d+1 dimensional*. Where d could be thought as *Independent Variables* and 1 could be thought as Dependent Variable*(labels)* in modern machine learning paradigm. So, *Independent variables + Dependent Variable* makes up our complete data set.
> 
> So, after we drop the labels, we are left with *d dimensional* data set and this would be the data set we will use to find the principal components.
> 
> 📢NOTE: Here I have taken only two dimensions for easy understanding of Mathematics behind PCA and also the data set consist of a smaller number of records we don’t split our data set into training and testing sets. So, what we actually focus on is when we implement PCA on a particular data set we get the principal components. But we don’t know what is the actual mathematics behind it. So, let’s find it out.
> 
> Here we will find the Principal components for a given data set by doing some math what actually PCA follows and we will implement the PCA using sklearn and compare the principal components of both the approaches to verify whether the math behind PCA we know is same as what actually PCA follows.
> 
> Also, let’s assume we are left with a two-dimensional data set after ignoring the labels i.e. d = 2.
> 
> Let our data matrix x be as given below where and b are our independent variables:
> 
> 

![](https://miro.medium.com/v2/resize:fit:390/1*4H41ryrZ9TqnB4-aInjydQ.png)Data Set- A 
### **STEP:2- Compute the mean of every dimension of the whole data set.**

> The data from the above table can be represented in matrix A.
> 
> 

![](https://miro.medium.com/v2/resize:fit:378/1*SA5_7DyEpicePgjT5hSiNw.png)Matrix A 

> So, the mean of matrix A would be
> 
> 

![](https://miro.medium.com/v2/resize:fit:586/1*IfCvTOXsLsadaksEd85sUQ.png)Mean Vector 

> Here 1.81 is the mean of independent variable a and 1.91 is the mean of independent variable b.
> 
> 

### **STEP:3- Compute the *covariance matrix* of the whole data set.**

> · So, we can compute the covariance of two variables X and Y using the following formula
> 
> 

![](https://miro.medium.com/v2/resize:fit:870/1*9WvER4NXlPhwN12Cap8TxA.png)Covariance Formula 

> · Where x̅ and y̅ are the mean values of a and b
> 
> · Using the above formula, we can find the covariance matrix of A. Also, the result would be a *square matrix of d ×d dimensions i.e. 2 x 2. We have three dimensions it would be 3 x 3*
> 
> · Let’s rewrite our original matrix like this
> 
> 

![](https://miro.medium.com/v2/resize:fit:330/1*bFpSRny4wFkinKNe3vVxRw.png)Matrix A 

> Its c*ovariance matrix* would be
> 
> 

![](https://miro.medium.com/v2/resize:fit:896/1*pdTczCTHkYWi3seJvvm8Nw.png)Covariance Matrix 2 x 2 

> So substituting the values in the above formula we get the following covariance
> 
> 

![](https://miro.medium.com/v2/resize:fit:1138/1*pTZcBuwiPRm4iqyEiF8lFQ.png)Covariance Matrix for Data Set A 

> Suppose if we have three independent variables our covariance matrix would be as shown below.
> 
> 

![](https://miro.medium.com/v2/resize:fit:1098/1*J_TuZcokSwoeAovIilK-uA.png)Covariance Matrix for 3 x 3 

> Covariance Matrix of A
> 
> Few points that can be noted here is:
> 
> The covariance between a and a ,b and b are just the variance in their distribution
> 
> The covariance between a and b is positive (0.61544444), and the covariance between b and a is positive (0.61544444). This means the scores tend to co-vary in a positive way. As value on a go up, value on b also tend to go up; and vice versa.
> 
> 

### **STEP:4- Compute Eigenvectors and corresponding Eigenvalues**

> Intuitively, an eigenvector is a vector whose direction remains unchanged when a linear transformation is applied to it.
> 
> Now, we can easily compute eigenvalue and eigenvectors from the covariance matrix that we have above.
> 
> Let *A* be a square matrix, ν a vector and λ a scalar that satisfies *A*ν = λν, then λ is called eigenvalue associated with eigenvector ν of *A*.
> 
> The eigenvalues of *A* are roots of the characteristic equation
> 
> 

![](https://miro.medium.com/v2/resize:fit:302/1*tBkji8asm8W6p78CqeLxBw.png)

> Calculating *det(A-λI)* first, *I* is an identity matrix:
> 
> 

![](https://miro.medium.com/v2/resize:fit:896/1*kWKkpo6vyyJQowFF-o3Zzg.png)

> Simplifying the matrix first, we can calculate the determinant later,
> 
> 

![](https://miro.medium.com/v2/resize:fit:732/1*FL5a8Uifz9r88C-djFxNuA.png)

> Now that we have our simplified matrix, we can find the determinant of the same:
> 
> 

![](https://miro.medium.com/v2/resize:fit:872/1*wTsuBaerrLezZQ8WKF6aNA.png)

> We now have the equation and we need to solve for *λ,* so as to get the *eigenvalue of the matrix.* So, equating the above equation to zero:
> 
> 

![](https://miro.medium.com/v2/resize:fit:710/1*B--NZ78IO5Oly0CzQ53rCg.png)

> After solving this equation for the value of *λ,* we get the following value Eigenvalues
> 
> 

![](https://miro.medium.com/v2/resize:fit:744/1*MYZO2z-BY9Ac-M40Qlg0Xg.png)

> Now, we can calculate the eigenvectors corresponding to the above eigenvalues.
> 
> 

![](https://miro.medium.com/v2/resize:fit:1178/1*2PCMjGIMLRHsMwA8dv3eKQ.png)

> To get the eigen vectors we will multiply the above matrix by x1 and y1 where x1 and y1 are the eigen vectors:
> 
> 

![](https://miro.medium.com/v2/resize:fit:1038/1*XO6guiY63YN8yGh74yeoUg.png)Unit Eigen Vector 

> Substituting Values for x1 and y1 we can get different Eigen Vectors. It is important for PCA that eigen vectors are unit eigen vectors.
> 
> 

### **Unit Eigen Vectors**:

![](https://miro.medium.com/v2/resize:fit:1400/1*y9JETquFpaqm3xsWgk_KGg.png)Unit Eigen Vector 

> Substituting value for x1=-1 we get the following
> 
> 

![](https://miro.medium.com/v2/resize:fit:1116/1*58ZsT869_kM9N7L3SD6rYQ.png)Eigen Vectors 

> But for PCA Eigen vectors should be Unit Eigen Vectors. So, Normalizing the above matrix we get.
> 
> 

![](https://miro.medium.com/v2/resize:fit:874/1*617GjALBwz4d45w0ApoHCg.png)Eigen Vectors 

> The above are the Eigen Vectors associated with the Eigen Value 0.0490 similarly for Eigen Value=1.2840 we get another set of Eigen Vectors as given below.
> 
> 

![](https://miro.medium.com/v2/resize:fit:614/1*Cco06DxnITPWWZZ3j7QX-g.png)

> So, after solving for *eigenvectors* we would get the following solution for the corresponding *eigenvalues*
> 
> 

![](https://miro.medium.com/v2/resize:fit:880/1*67BfkiWA-kvHfGCK-8fsLA.png)
### **STEP:5- Sort the eigenvectors by decreasing eigenvalues and choose k eigenvectors with the largest eigenvalues to form a *d × k dimensional* matrix V**.

> We started with the goal to reduce the dimensionality of our feature space, i.e., projecting the feature space via PCA onto a smaller subspace, where the eigenvectors will form the axes of this new feature subspace. However, the eigenvectors only define the directions of the new axis, since they have all the same unit length 1.
> 
> So, in order to decide which eigenvector(s) we want to drop for our lower-dimensional subspace, we have to take a look at the corresponding eigenvalues of the eigenvectors. Roughly speaking, the eigenvectors with the lowest eigenvalues bear the least information about the distribution of the data, and those are the ones we want to drop.
> 
> The common approach is to rank the eigenvectors from highest to lowest corresponding eigenvalue and choose the top *k* eigenvectors.
> 
> So, after sorting the eigenvalues in decreasing order, we have
> 
> 

![](https://miro.medium.com/v2/resize:fit:742/1*2cOtu-Zhc1EabVBjU8RbfQ.png)
![](https://miro.medium.com/v2/resize:fit:742/1*rvN9VTD9-w2o86nN15NgKA.png)

> For our simple example, where we are converting a 2-dimensional feature space to a 2-dimensional feature subspace. we are combining the 2 eigen vectors with the highest eigenvalues to construct our *d×k* dimensional eigenvector matrix W.
> 
> NOTE: We have not reduced the dimensions for the better understanding of the problem but you can convert the 2-D into 1-D if you wish. We will do it in the Implementation Section with python.
> 
> So, *eigenvectors* corresponding to one maximum eigen values are:
> 
> 

![](https://miro.medium.com/v2/resize:fit:664/1*PV3fVghp0lRzCg_Rh0udag.png)V 

> V=
> 
> 

### **STEP 6- Transform the samples onto the new subspace**

> In the last step, we use the 2 x 2 dimensional matrix ***V*** that we just computed to transform our samples onto the new subspace via the equation *new sub space= V× old sub space.*
> 
> The below is the transformed samples after applying PCA by following Step by Step approach and Sklearn PCA method.
> 
> 

![](https://miro.medium.com/v2/resize:fit:1400/1*iZRu3B4Y0e_kjqmvU-N35w.png)NOTE: This transformation is not done on the data set we have taken. 

> Looking at the 2 plots above, the distributions along the component axes look identical, only the center of the data is slightly different.If we want to mimic the results produced by scikit-learn’s `PCA` class, we can subtract the mean vectors from the samples `A` to center the data at the coordinate system’s origin (thanks to a suggestion by Alexander Guth) – that is, replacing the original data set into new sub space= V× old sub space by new sub space= V x (old sub space -Mean vector)
> 
> I have shown the Step by Step approach using numpy and also using sklearn below.
> 
> 

![](https://miro.medium.com/v2/resize:fit:1400/1*JkVQvf7vf6ZllwvtIzxocQ.png)new sub space 
![](https://miro.medium.com/v2/resize:fit:1400/1*oYbjQXi_Te9s0pCOva4uog.png)new sub space 
![](https://miro.medium.com/v2/resize:fit:1400/1*zD1Y9y578MTqHIVFXcz9fg.png)new sub space 
![](https://miro.medium.com/v2/resize:fit:1400/1*wFYNwba1tTQTba_JdA2IDA.png)new sub space 

> In order to mimic the results with PCA replacing the original data set into new sub space= V× old sub space by new sub space= V x (old sub space -Mean vector). Above we have converted old sub space by subtracting the mean values of corresponding variable.
> 
> So lastly, we have computed our two principal components and projected the data points onto the new subspace. Now we will train our model on these new\_sub\_space or Principal Components.
> 
> 

### **Implementation Using Sklearn:**

![](https://miro.medium.com/v2/resize:fit:1400/1*YYdf2FGig5GxcDMD0GGaJA.png)

> You can observe the new sub space obtained using Step by Step approach and PCA is exactly same. You might be wondering the new sub spaces[0] that is obtained using Step by Step approach has different observations when comparing with new sub space[0] that is obtained using Sklearn approach.similarly for new sub space[1].
> 
> So Here is the reason behind it. When we follow the sklearn PCA approach what it does is it sorts the eigen vector in decreasing order of eigen values. So the first eigen vector is the vector corresponding to the Highest Eigen value.However when we follow the step by step approach we dont sort the eigen vectors. So here we have taken first eigen vector as vector corresponding to the lowest eigen value. Observe the code carefully …….
> 
> 

### **Implementation Using Python :**

Here we are predicting malignant and benign cancer cells of breast Tumor

![](https://miro.medium.com/v2/resize:fit:1400/1*9TJhMtQzn_NiX4xcUYhreQ.png)
![](https://miro.medium.com/v2/resize:fit:1400/1*Mm59jW2PzKE74mWSIuj7fg.png)
![](https://miro.medium.com/v2/resize:fit:1400/1*3YZ3kR1JaeL1SgkgbEId6Q.png)
![](https://miro.medium.com/v2/resize:fit:1400/1*5wGfcMqnwRfjmLy5xwI6Rg.png)
![](https://miro.medium.com/v2/resize:fit:1400/1*9MJC_9pfQWvPUT9pEgIhzw.png)
![](https://miro.medium.com/v2/resize:fit:1400/1*e_LXao9hYsBinQL8DIgc0g.png)

> You can observe we have achieved the accuracy around 96 % using 33 dimensions and when we reduced the dimensions into 5 we got the same accuracy without any loss of information and less training time and no correlation between Independent Variables.
> 
> 

Let’s discuss in comments if you find anything wrong in the post or if you have anything to add:P  

Thanks.

**Credits and Sources:**

1. [Sebastian Raschka Blog](http://sebastianraschka.com/Articles/2014_pca_step_by_step.html)
2. [www.Analyticsvidhya.com](https://www.analyticsvidhya.com/blog/2016/03/pca-practical-guide-principal-component-analysis-python/)
