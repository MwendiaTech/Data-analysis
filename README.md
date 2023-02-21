# Data-analysis-with-Python
## Objectives
1) Review and download the Kaggle Automobile Dataset from: 

        https://www.kaggle.com/datasets/toramky/automobile-dataset

2) Supplement this dataset with additional records for cadillac, ford, chrysler, gmc, kia(at leat 3 records for each, total of 15 or more additonal records)

3) Perform full data quality analysis on this dataset and perform the following:

        a) Handle missing field values such as drop, replace by mean, replace by frequency
        b)correct data format
        c)standardize data
        d)Normalize data
        e)perform binning
        f)add new variable(s) (ex:indicator variable, of which you would use as a special feature).


## Data Wrangling procedure

### 1. Handle missing values
* Convert "?" to NaN -- In the car dataset, missing data comes with the question mark "?".
* Evaluating for Missing Data -- Here, check wether there were any anymore missing data
* Count missing values in each column -- Using a for loop in Python, count the number of null values in each column.

#### 1.1 Deal with missing data
In this section, i explain how i handles the missing data and justify the reasons for handling data in the way it was done.

##### 1.1.1 Drop data:
* Drop the whole row -- since "price" had 4 missing values, I simply deleted the whole row because price is what we want to predict. Any data entry without price data cannot be used for prediction; therefore any row now without price data is not useful to us

##### 1.1.2 Replace data
###### Replace it by mean:
Replace the missing data with the average of the column. Below columns were replaced with average values;
* "normalized-losses": 41 missing data, "stroke": 4 missing data, "bore": 4 missing data, "horsepower": 2 missing data, "peak-rpm": 2 missing data

##### Replace it by frequency
* Replace "num-of-doors" which has 2 missing data, with "four". -- Reason being : 84% sedans is four doors. Since four doors is most frequent, it is most likely to occur

### 2. Correct data format: 
Ensure that the data columns are in there correct data types before performing further analysis. The procedure I followed was:

* list the data types for each column
* Convert data types to proper format
        * bore,stroke, price and peak-prm to float
        * normalised losses to integer
* list the columns after the conversion
        
### 3. Standardize data
 * `Standardization` is the process of transforming data into a common format, allowing for meaningful comparison. In my dataset, the fuel consumption columns "city-mpg" and "highway-mpg" are represented by mpg (miles per gallon) unit. Assume we are developing an application in a country that accepts the fuel consumption with L/100km standard. We will need to apply data transformation to transform mpg into L/100km. The formula for unit conversion is: L/100km = 235 / mpg
        
### 4. Normalize data
* `Normalization` is the process of transforming values of several variables into a similar range
*  I, for example, scaled the columns "length", "width" and "height". I normalized these variables so their value ranges from 0 to 1. Approach: replace original value by (original value)/(maximum value)        
        
### 5. Binning
* `Binning` is a process of transforming continuous numerical variables into discrete categorical 'bins' for grouped analysis.
* Example: --> In my dataset, "horsepower" is a real valued variable ranging from 48 to 288 and it has **57** unique values. What if we only care about the price difference between cars with high horsepower, medium horsepower, and little horsepower (3 types)? Can we rearrange them into three ‘bins' to simplify analysis?
        I used the pandas method 'cut' to segment the 'horsepower' column into 3 bins.
* Bins Visualization - Here, i visualized the bins created above to see there distributions
        
### 6. Indicator Variable (or Dummy Variable)
We use indicator variables so we can use categorical variables for regression analysis in the later modules. The column "fuel-type" has two unique values: "gas" or "diesel". Regression doesn't understand words, only numbers. To use this attribute in regression analysis, we convert "fuel-type" to indicator variables.

***