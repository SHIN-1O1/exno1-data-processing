# Exno:1
Data Cleaning Process

# AIM
To read the given data and perform data cleaning and save the cleaned data to a file.

# Explanation
Data cleaning is the process of preparing data for analysis by removing or modifying data that is incorrect ,incompleted , irrelevant , duplicated or improperly formatted. Data cleaning is not simply about erasing data ,but rather finding a way to maximize datasets accuracy without necessarily deleting the information.

# Algorithm
STEP 1: Read the given Data

STEP 2: Get the information about the data

STEP 3: Remove the null values from the data

STEP 4: Save the Clean data to the file

STEP 5: Remove outliers using IQR

STEP 6: Use zscore of to remove outliers

# Coding and Output
            import numpy as np
            import matplotlib.pyplot as plt

            X = np.array(eval(input('X values:')))
            Y = np.array(eval(input('Y values:')))

            X_mean = np.mean(X)
            Y_mean = np.mean(Y)
            num = 0
            denom = 0

            for i in range(len(X)):
                num += (X[i] - X_mean) * (Y[i] - Y_mean)
                denom += (X[i] - X_mean) ** 2

            m  = num/denom
            b = Y_mean - m*X_mean

            print('slope:',m)
            print('Y-intercept:',b)

            y_predicted = m*X+b
            print('Predicted values:',y_predicted)

            plt.scatter(X,Y)
            plt.plot(X,y_predicted,color = 'red')
            plt.title('Linear Regression')
            plt.xlabel('X')
            plt.ylabel('Y')
            plt.show()

slope: -1.1064189189189189
Y-intercept: 14.08108108108108
Predicted values: [ 5.22972973 11.86824324  1.91047297  7.44256757  8.54898649  9.65540541 0.80405405  4.12331081  7.44256757 12.97466216]

# Result
![download](https://github.com/user-attachments/assets/41914a90-6702-4f8f-ad54-676ca04e890c)
