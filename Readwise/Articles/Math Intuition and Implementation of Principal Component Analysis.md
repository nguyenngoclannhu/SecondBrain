# Math Intuition and Implementation of Principal Component Analysis

![rw-book-cover](https://miro.medium.com/v2/resize:fit:997/1*PtaeFuNJxdZVz99WfYrpZA.png)

## Metadata
- Author: [[Arun Amballa]]
- Full Title: Math Intuition and Implementation of Principal Component Analysis
- Category: #articles
- Summary: Principal Component Analysis (PCA) is a technique used for dimensionality reduction, allowing us to extract significant features from a large set of variables without losing important information. It transforms high-dimensional data into a lower-dimensional space by creating new, independent variables called principal components. PCA helps to simplify data visualization and modeling by reducing redundancy and capturing essential patterns in the data.
- URL: https://medium.com/analytics-vidhya/math-intuition-and-implementation-of-principal-component-analysis-6f02253ceef9

## Highlights
- find a subset of the original set of variables, or features, to get a smaller subset ([View Highlight](https://read.readwise.io/read/01jkded0w6re72kexb5kg0qf4d))
- Advantages of feature Selection methods include simplicity and maintaining interpretability of your variables. ([View Highlight](https://read.readwise.io/read/01jkdedgqbqvjcwvq8msx9krr6))
- As a disadvantage, though, you gain no information from those variables you’ve dropped ([View Highlight](https://read.readwise.io/read/01jkdedmrtj1ftdw7zq97xgr1k))
- By eliminating features, we’ve also entirely eliminated any benefits those dropped variables would bring ([View Highlight](https://read.readwise.io/read/01jkdee0bma483pzb9ehkvtrx9))
- we create ten “new” independent variables, where each “new” independent variable is a combination of each of the ten “old” independent variables. ([View Highlight](https://read.readwise.io/read/01jkdeeeg405zb4qp9j3ve03ac))
- This is a benefit because the assumptions of linear model require our independent variables to be independent of one another ([View Highlight](https://read.readwise.io/read/01jkdex0xmwh93w4v6gzpm0v3d))
- > Space required to store the data is reduced as the number of dimensions comes down.
  > 
  > 2.Less dimensions lead to less computation/training time.
  > 
  > 3.Some algorithms do not perform well when we have a large dimension. So, reducing these dimensions needs to happen for the algorithm to be useful.
  > 
  > 4.It takes care of multi-collinearity by removing redundant features. For example, you have two variables — ‘time spent on treadmill in minutes’ and ‘calories burnt’. These variables are highly correlated as the more time you spend running on a treadmill, the more calories you will burn. Hence, there is no point in storing both as just one of them does what you require.
  > 
  > 5.It helps in visualizing data. As discussed earlier, it is very difficult to visualize data in higher dimensions so reducing our space to 2-D or 3-D may allow us to plot and observe patterns more clearly ([View Highlight](https://read.readwise.io/read/01jkdey6yxg7wf9dkc4w5ea9s6))
    - Note: 1. less space
      2. less time / no strong computation
      3. algorithm efficiency
      4. remove redundant features
      5. easy to visualize
- principal components are the new set of variables that are obtained from the initial set of variables ([View Highlight](https://read.readwise.io/read/01jkdf13bd2rkd4hdqe1p920y7))
