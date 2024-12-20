# House-Prices---Regression-Techniques


## Summary: 
This project aimed to predict house sale prices using machine learning techniques in Python. After preparing the data to reduce dimensionality, I tested models such as Linear Regression and Random Forest, while making several submissions (which are not included in the notebook). Based on the Logarithmic Root Mean Squared Error (LOG RMSE), I found that XGBoost was the most efficient model due to its ability to handle more parameters effectively. Key features used in the model included 'TotalSF', 'LotArea', and 'GrLivArea'. In conclusion, XGBoost provided the best balance between efficiency and accuracy for forecasting house prices.


## DataSet info:
The datasets used in this project can be accessed from this repository in a folder called Data or through the following link:
<a href="https://www.kaggle.com/competitions/house-prices-advanced-regression-techniques/data" target="_blank"> Here are the DataSets</a>
- train.csv
- test.csv
- data_description.txt - Detailed feature descriptions for both training and test sets.
- submission.csv - Contains predicted SalesPrice values along with their corresponding IDs.
The training dataset contains 81 features, while the test dataset contains 80 features. The SalesPrice feature is available in the training set but not in the test set.


## Techniques used:
- **Visualizing Data Distributions with Histograms**: Used to assess feature skewness for imputation and better understand the data. An image of the histograms is included to illustrate these distributions.
![image](https://github.com/user-attachments/assets/0621e81b-644f-4ee2-835c-110550c19f6c)

- **Data Preparation for the Training Set**: The data preparation process involved handling missing values, encoding categorical variables, and feature scaling to ensure the dataset was ready for modeling. To keep the notebook clean, organized, and efficient, the data preparation process was summarized within a pipeline, which was written in a separate Python file: [preprocessed_data.py](./preprocessed_data.py)

- **Test Set Preparation for Final Prediction**: The same Python script used for the training data was applied to the test set. This ensures consistency in imputation and encoding, maintaining the integrity of the model evaluation and preventing data leakage. The script is located in [preprocessed_data.py](./preprocessed_data.py).

- **XGBoost**: Employed the DMatrix to improve training speed and memory efficiency.


## Features Engineering:
Due to their high percentage of missing values, I dropped several features from both the training and testing datasets, including: 
- 'Alley', 'PoolQC', 'Fence', and 'Utilities'.

After feature engineering, I also removed:
- 'TotalBsmtSF', '1stFlrSF', '2ndFlrSF', 'FullBath', 'HalfBath', 'BsmtFullBath',
- 'BsmtHalfBath', 'OpenPorchSF', '3SsnPorch', 'EnclosedPorch',
- 'ScreenPorch', 'WoodDeckSF', 'YrSold', 'YearBuilt', 'YearRemodAdd', 'OverallQual', 'OverallCond'.

These were replaced by features like:
- 'TotalQual_Cond', 'AgeRemod', 'Age', 'TotalPorchSF', 'TotalBathrooms', and 'TotalSF' to improve model performance. Combining these features reduced the dimensionality of the dataset, contributing to a more efficient model and helping to prevent overfitting. The remaining features were left unchanged, as they improved the model's accuracy.


## Feature Importance:
The top 10 important features identified by the XGBoost model in order were: 
- Id, LotArea, BsmtUnfSF, GrLivArea, LotFrontage,
- TotalPorchSF, GarageArea, TotalSF, BsmtFinSF1, MasVnrArea.
Below is a chart of the list of top 10 most import features in order.
![image](https://github.com/user-attachments/assets/b0410fff-087f-4d5c-8622-813ee75f2b55)


## Evaluation:
The model's performance was evaluated using the Root Mean Squared Error between the logarithms of the predicted values and the observed sales prices (LOG RMSE).


## Results and conclusion:
The images below display the model's results. The first image shows the LOG RMSE score on Kaggle, while the second image presents the predicted SalePrice values alongside their respective IDs:

<img width="708" alt="Screenshot 2024-10-01 at 12 28 22 PM" src="https://github.com/user-attachments/assets/1747529e-1576-4a98-be56-3e2b8f8046eb">

<img width="152" alt="Screenshot 2024-10-01 at 12 31 46 PM" src="https://github.com/user-attachments/assets/f244bf9d-4f2c-4fd5-ac64-b3a405ba9b0e">


Initially, I used linear regression, but the LOG RMSE results showed it wasn’t the best choice, with a score of 0.18864. I then tested the Random Forest model, which was also less accurate. Ultimately, I found that XGBoost provided the most accurate and efficient predictions.

For the full code and project details, refer to [House_prices_regression_project.ipynb](./House_prices_regression_project.ipynb) for training and model evaluation. 

For a more comprehensive report and a more in depth analysis, check out the [House_prices_report.md](./House_prices_report.md) and [House_prices_EDA.ipynb](./House_prices_EDA.ipynb) document.
