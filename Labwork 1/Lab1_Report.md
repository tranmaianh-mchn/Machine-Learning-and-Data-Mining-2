# ML2 - Labwork 1: Principle component analysis

*16 November - 22 November 2026*

| Name | Student ID |
|---|---|
| Tran Mai Anh | 2410093 |
| Nguyen Van Khanh | 2410460 |

## I. Study the dataset
### 1. Dataset 1: Brazilian E-Commerce Public Dataset by Olist
### 1.1. Overview and Description
- Data source: [Olist Products](https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce?select=olist_products_dataset.csv)
- The dataset contains 32951 product records and 9 columns, including 7 numerical attributes, 1 categorical attribute and 1 product identifier

| **Feature** | **Brief Description** | **Feature Type** |
|---|---|---|
| `product_id`<br>`product_category_name` | Unique product identifier <br> Original product category in Portuguese | Qualitative, Categorical |
| `product_name_lenght`<br> `product_description_lenght`<br> `product_photos_qty` | Number of characters in the product name <br> Number of characters in the product description <br> Number of published product photos | Quantitative, Numerical, Discrete |
| `product_weight_g`<br> `product_length_cm`<br> `product_height_cm`<br> `product_width_cm` | Product weight measured in grams <br> Product length measured in centimeters <br> Product height measured in centimeters <br> Product width measured in centimeters | Quantitative, Numerical, Continuous |

- The feature `product_category_name` attribute in this dataset can be used as a target variable for a multi-class classification, where product categories are predicted using other product attributes. When working on this problem, the `product_id` will not be used as the input feature.


### 1.2. Data Cleaning
*Identify missing values, duplicate records, incorrect values, inconsistencies, outliers*

By applying different data cleaning operations, here is the result of this process:

| | Before | After |
|---|---|---|
| **Total records** | 32951 | 32336 |
| **Missing numerical value records** | 611 | 0 |
| **Zero weight value records** | 4 | 0 |
| **Duplicate records** | 0 | 0 |
| **Records with detected inconsistencies** | 0 | 0 |

- A total of 615 records (1.87% of the original dataset) were removed, including 611 records with at least one missing numerical value anf 4 records with zero product weight. The record removal instead of adding missing values generally can preserve the data integrity, avoid artificial values that could affect variance and correlation, maintain the statistical reliability. Moreover, the removed instances is not too much and the remaining data is still enough for the data analysis and data visualization.

- As usual, the duplicate records can repeat the observations, leading to the problem of data distribution. In this dataset, it is detected that there is no duplicate records, so the duplicate removal was unnecessary.

- No inconsistencies were detected during the consistency checks; therefore, no additional corrections were required. 

- Outlier detection: IQR method is applied in this stage. It is a non-parametric, distribution-agnostic technique used to identify anomalies or extreme values in a dataset. The IQR method is expressed as:  
                            $$IQR = Q_3 - Q_1$$
where $Q_1$ (The first quartile) is denoted as the median of the lower half of the data and $Q_3$ (The third quartile) is the median of the upper half of the data. The data point (denoted as $x$) is flagged as an outlier is displayed as:
$$
x < Q_1 - 1.5IQR
\quad \text{or} \quad
x > Q_3 + 1.5IQR
$$
The outliers are not necessarily incorrect values. In outlier handling, the IQR method can detect statistically abnormal values instead of determine whether extreme values are wrong. Retaining outliers can preserve the natural variability because removing all the outliers may lead to the loss of valid extreme observations. Furthermore, keeping the outliers can avoid unnecessary information loss as extreme observations may be useful for the dataset. In contrast, IQR also has some limitations. The outliers may increase the variance, affecting the covariance and correlation and also the directions of principal components in PCA later on. The result of applying IQR in this dataset

- IQR outlier detection in Olis Product dataset is applied for all 7 numerical features. Here is the result table:

| Feature | Flagged outliers | Percentage (%) |
|---|---|---|
| `product_name_lenght` | 290 | 0.90 |
| `product_description_lenght` | 2078 | 6.43 |
| `product_photos_qty` | 849 | 2.63 |
| `product_weight_g` | 4551 | 13.81 |
| `product_length_cm`| 1380 | 4.19 |
| `product_height_cm` | 1892 | 5.74 |
| `product_width_cm` | 912 | 2.77 |

From the above result, the `product_weight_g` has the highest proportion of flagged outliers (13.81%), meaning that the weight of the product is significantly variable and has many values outside the IQR range. In contrast, the `product_name_lenght` accounts for the lowest outliers percentage (0.9%), indicating that the number of extreme values according to IQR rules is relatively small. In general, numerical features may vary across product categories, so it should not automatically be considered that outliers are erroneous values.

### 1.3. Data Integration and Transformation
