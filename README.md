<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">

</head>
<body>
    <h1>Boston House Price Prediction with PCA and Non-PCA Features</h1>
    <h2>Data Definition</h2>
    <p>For detailed data definitions, visit the <a href="https://github.com/jvontama96/BostonHousePricePrediction_PCA_vs_NonPCA/tree/main/Dataset%20and%20Data%20Processing">Data Definition Repository</a>.</p>
    <ul>
        <li><strong>CRIM:</strong> Per capita crime rate by town.</li>
        <li><strong>ZN:</strong> Proportion of residential land zoned for lots over 25,000 sq.ft.</li>
        <li><strong>INDUS:</strong> Proportion of non-retail business acres per town.</li>
        <li><strong>CHAS:</strong> Charles River dummy variable (= 1 if tract bounds river; 0 otherwise).</li>
        <li><strong>NOX:</strong> Nitric oxides concentration (parts per 10 million).</li>
        <li><strong>RM:</strong> Average number of rooms per dwelling.</li>
        <li><strong>AGE:</strong> Proportion of owner-occupied units built prior to 1940.</li>
        <li><strong>DIS:</strong> Weighted distances to five Boston employment centers.</li>
        <li><strong>RAD:</strong> Index of accessibility to radial highways.</li>
        <li><strong>TAX:</strong> Full-value property-tax rate per $10,000.</li>
        <li><strong>PTRATIO:</strong> Pupil-teacher ratio by town.</li>
        <li><strong>B:</strong> 1000(Bk−0.63)² where Bk is the proportion of blacks by town.</li>
        <li><strong>LSTAT:</strong> % lower status of the population.</li>
        <li><strong>MEDV:</strong> Median value of owner-occupied homes in $1000s.</li>
    </ul>
    <h2>Data Processing</h2>
    <p>For data processing details, visit the <a href="https://github.com/jvontama96/BostonHousePricePrediction_PCA_vs_NonPCA/tree/main/Dataset%20and%20Data%20Processing">Data Processing Repository</a>.</p>
    <ul>
        <li>No missing values.</li>
        <li>No duplicates.</li>
        <li>Outliers check:
            <ul>
                <li><strong>Before Outlier Handling:</strong></li>
                <img src="https://github.com/jvontama96/BostonHousePricePrediction_PCA_vs_NonPCA/blob/main/Dataset%20and%20Data%20Processing/House_outlier_before.png?raw=true" alt="Outlier Before" style="width:100%; max-width:600px;">
                <ul>
                    <li>CRIM outliers: 13.04%</li>
                    <li>ZN outliers: 13.44%</li>
                    <li>INDUS outliers: 0.00%</li>
                    <li>CHAS outliers: 100.00%</li>
                    <li>NOX outliers: 0.00%</li>
                    <li>RM outliers: 5.93%</li>
                    <li>AGE outliers: 0.00%</li>
                    <li>DIS outliers: 0.99%</li>
                    <li>RAD outliers: 0.00%</li>
                    <li>TAX outliers: 0.00%</li>
                    <li>PTRATIO outliers: 2.96%</li>
                    <li>B outliers: 15.22%</li>
                    <li>LSTAT outliers: 1.38%</li>
                    <li>MEDV outliers: 7.91%</li>
                </ul>
                <li><strong>After Outlier Handling:</strong></li>
                <img src="https://github.com/jvontama96/BostonHousePricePrediction_PCA_vs_NonPCA/blob/main/Dataset%20and%20Data%20Processing/House_outlier_after.png?raw=true" alt="Outlier After" style="width:100%; max-width:600px;">
                Handling outliers in features with more than 10% outliers, such as CRIM, ZN, and B, using data transformation methods.
                <ul>
                    <li>CRIM outliers: 1.19%</li>
                    <li>ZN outliers: 0.00%</li>
                    <li>INDUS outliers: 0.00%</li>
                    <li>CHAS outliers: 100.00%</li>
                    <li>NOX outliers: 0.00%</li>
                    <li>RM outliers: 5.93%</li>
                    <li>AGE outliers: 0.00%</li>
                    <li>DIS outliers: 0.99%</li>
                    <li>RAD outliers: 0.00%</li>
                    <li>TAX outliers: 0.00%</li>
                    <li>PTRATIO outliers: 2.96%</li>
                    <li>B outliers: 15.22%</li>
                    <li>LSTAT outliers: 0.00%</li>
                    <li>MEDV outliers: 7.91%</li>
                </ul>
            </ul>
        </li>
    </ul>
    <h2>Correlation Matrix</h2>
    <img src="https://github.com/jvontama96/BostonHousePricePrediction_PCA_vs_NonPCA/blob/main/Dataset%20and%20Data%20Processing/Correlation_matrix_Before.png?raw=true" alt="Cor Before" style="width:100%; max-width:600px;">
    <p>Strong positive correlations were observed between:</p>
    <ul>
        <li>The number of rooms (RM) and median housing prices (MEDV).</li>
        <li>The percentage of lower status population (LSTAT) and median housing prices.</li>
    </ul>
    <p>Potential multicollinearity was found between:</p>
    <ul>
        <li>Accessibility to radial highways (RAD), property-tax rate (TAX), per capita crime rate (CRIM), and nitric oxides concentration (NOX).</li>
    </ul>
     <p>As a result of this finding, we will drop features with high multicollinearity.</p>
     <img src="https://github.com/jvontama96/BostonHousePricePrediction_PCA_vs_NonPCA/blob/main/Dataset%20and%20Data%20Processing/Correlation_matrix_after.png?raw=true" alt="Cor After" style="width:100%; max-width:600px;">
    <h2>Data Processing, Splitting, Scaling, and PCA</h2>
    <p>Data was split into training and test sets with target feature <strong>"MEDV (Median value of owner-occupied homes in $1000s)"</strong>, and scaled appropriately for modeling. After that, we processed the PCA.<a href="https://github.com/jvontama96/BostonHousePricePrediction_PCA_vs_NonPCA/tree/main/PCA">here</a>.</p>
    <ul>
        <li>A scree plot analysis was performed, resulting in feature reduction to six principal components from the original nine.</li>
        <img src="https://github.com/jvontama96/BostonHousePricePrediction_PCA_vs_NonPCA/blob/main/PCA/Skree_Plot.png?raw=true" alt="Skree Plot" style="width:100%; max-width:600px;">
    </ul>
    <h2><a href="https://github.com/jvontama96/BostonHousePricePrediction_PCA_vs_NonPCA/tree/main/Evaluation">Model Evaluation</a></h2>
    <p>Lasso Regression was used for modeling. The model was fitted to both PCA and non-PCA data.</p>
    <h3>Without PCA Metrics</h3>
    <table border="1">
        <tr>
            <th>Metric</th>
            <th>Test Data</th>
            <th>Train Data</th>
        </tr>
        <tr>
            <td>R-squared</td>
            <td>79.15%</td>
            <td>75.81%</td>
        </tr>
        <tr>
            <td>RMSE</td>
            <td>4.04</td>
            <td>4.56</td>
        </tr>
        <tr>
            <td>MAE</td>
            <td>3.02</td>
            <td>3.21</td>
        </tr>
        <tr>
            <td>MAPE</td>
            <td>15.23%</td>
            <td>16.03%</td>
        </tr>
    </table>
    <h3>With PCA Metrics</h3>
    <table border="1">
        <tr>
            <th>Metric</th>
            <th>Test Data</th>
            <th>Train Data</th>
        </tr>
        <tr>
            <td>R-squared</td>
            <td>79.63%</td>
            <td>72.19%</td>
        </tr>
        <tr>
            <td>RMSE</td>
            <td>3.99</td>
            <td>4.89</td>
        </tr>
        <tr>
            <td>MAE</td>
            <td>2.89</td>
            <td>3.25</td>
        </tr>
        <tr>
            <td>MAPE</td>
            <td>14.85%</td>
            <td>16.67%</td>
        </tr>
    </table>
    <h2>Model Interpretation</h2>
    <h3>Without PCA</h3>
    <p>The linear regression model is described by the following equation:</p>
    <pre>
        target = 22.456080 + 0.164364 * zn - 0.521922 * indus + 0.548867 * chas + 
                 1.776747 * rm + 0.132038 * age - 1.668984 * dis - 1.449816 * ptratio + 
                 0.809496 * b - 5.880111 * lstat
    </pre>
    <p>Interpretation:</p>
    <ul>
        <li><strong>Intercept (22.456080):</strong> Baseline predicted house price when all other predictors are zero.</li>
        <li><strong>ZN (zn):</strong> For each unit increase in the proportion of residential land zoned for large lots, the house price increases by approximately 0.16.</li>
        <li><strong>INDUS (indus):</strong> For each unit increase in the proportion of non-retail business acres, the house price decreases by approximately 0.52.</li>
        <li><strong>CHAS (chas):</strong> If the property bounds the Charles River, the house price increases by approximately 0.55.</li>
        <li><strong>RM (rm):</strong> Each additional room increases the house price by approximately 1.78.</li>
        <li><strong>AGE (age):</strong> For each unit increase in the proportion of owner-occupied units built before 1940, the house price increases by approximately 0.13.</li>
        <li><strong>DIS (dis):</strong> For each unit increase in weighted distances to five Boston employment centers, the house price decreases by approximately 1.67.</li>
        <li><strong>PTRATIO (ptratio):</strong> For each unit increase in the pupil-teacher ratio, the house price decreases by approximately 1.45.</li>
        <li><strong>B (b):</strong> For each unit increase in the calculated variable based on the proportion of blacks, the house price increases by approximately 0.81.</li>
        <li><strong>LSTAT (lstat):</strong> For each percentage increase in the percentage of lower status of the population, the house price decreases by approximately 5.88.</li>
    </ul>
    <h3>With PCA</h3>
    <p>The linear regression model is described by the following equation:</p>
    <pre>
        target = 22.478843 + 3.022652 * pc1 + 3.828501 * pc2 + 0.444471 * pc3 - 
                 2.412008 * pc4 + 0.192367 * pc5 + 1.269731 * pc6
    </pre>
    <p>Interpretation:</p>
    <ul>
        <li><strong>Intercept (22.478843):</strong> Baseline predicted value of the target variable when all other predictors are zero.</li>
        <li><strong>PC1, PC2, PC3, PC5, PC6:</strong> Higher proportions positively impact the target value.</li>
        <li><strong>PC4:</strong> Higher proportion negatively impacts the target value.</li>
    </ul>
    <h2>Comparison: Without PCA vs With PCA</h2>
    <table border="1">
        <tr>
            <th>Metric</th>
            <th>Test Data without PCA</th>
            <th>Test Data with PCA</th>
        </tr>
        <tr>
            <td>R-squared</td>
            <td>79.15%</td>
            <td>79.63%</td>
        </tr>
        <tr>
            <td>RMSE</td>
            <td>4.04</td>
            <td>3.99</td>
        </tr>
        <tr>
            <td>MAE</td>
            <td>3.02</td>
            <td>2.89</td>
        </tr>
        <tr>
            <td>MAPE</td>
            <td>15.23%</td>
            <td>14.85%</td>
        </tr>
    </table>
    <p>The model with PCA performs slightly better for predicting <strong>MEDV (Median value of owner-occupied homes)</strong>:</p>
<ul>
  <li><strong>R-squared</strong>: The PCA model (79.63%) has a slightly higher R-squared compared to the non-PCA model (79.15%), indicating a marginally better fit.</li>
  <li><strong>RMSE</strong>: The PCA model (3.99) has a lower RMSE, meaning its predictions are closer to actual values than the non-PCA model (4.04).</li>
  <li><strong>MAE</strong>: The PCA model (2.89) shows fewer absolute errors compared to the non-PCA model (3.02).</li>
  <li><strong>MAPE</strong>: The PCA model (14.85%) has better relative accuracy than the non-PCA model (15.23%).</li>
</ul>
<p>Overall, <strong>the PCA model is slightly better</strong> for predicting house prices.</p>
<h2>Business Implementations and Actions</h2>
<ol>
    <li><strong>Targeted Pricing Strategies:</strong> Based on feature analysis, businesses can adjust pricing by focusing on key factors like the number of rooms (RM), proximity to the Charles River (CHAS), and socio-economic indicators (LSTAT). This can help optimize pricing based on property characteristics.</li>
    <li><strong>Investment in Property Development:</strong> Investment strategies could prioritize areas with higher values for ZN (land zoning for large lots) and CHAS (proximity to the Charles River) to increase the appeal of properties, especially in high-demand regions.</li>
    <li><strong>Optimized Marketing Campaigns:</strong> Marketing campaigns could emphasize features that positively impact price predictions, such as a higher number of rooms (RM) or low pupil-teacher ratios (PTRATIO), attracting potential buyers in regions with these desirable traits.</li>
</ol>
</body>
</html>

