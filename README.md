
---

## **ETL Pipeline for Intraday Stock Data**

---

### **Introduction**

ETL stands for **'Extract-Transform-Load'** and it is a process wherein data is extracted from one or more sources, necessary transformations are run on the data, and the data is loaded into a singular data repository such as a data warehouse or a data mart.

---

### **Objective**

The objective of this project is to automate the process of ETL on the intraday stock data of Apple Inc., enabling efficient storage and analysis on cloud platforms.

---

### **Technologies Used**

- **Python**: For scripting the ETL process.
- **Alpha Vantage API**: For extracting stock data.
- **MongoDB**: As a staging area for raw data.
- **PySpark**: For data transformation.
- **AWS S3**: For scalable data storage.

---

### **Expected Output**

The final output will be time-stamped CSV files stored in an AWS S3 bucket, containing the transformed stock data with calculated percentage changes in volume and price.

---

### **Working Summary**

The summary of this project is as follows:

#### **Step 1 - Extraction**

**1. Data Extraction:**
- Extract intraday data for the company Apple (NASDAQ:AAPL) at an interval of 5 minutes using the Alpha Vantage API.
- Records such as Open, High, Low, Close, and Volume are extracted.
- The data is received in JSON format.

**2. Data Storage in a Staging Area:**
- Store the JSON data in MongoDB as a staging area.
- The data is stored in a database called 'apple' and the subsequent collection 'intraday_r'.

#### **Step 2 - Transformation**

In this step, we use PySpark to perform transformations on the data to make it suitable for further analysis. We initialize the Spark session and set up the connection with MongoDB, which is our staging area. The transformations applied are:

1. Converting the ObjectID fields in MongoDB to strings for compatibility.
2. Calculating the previous row values for the data.
3. Calculating:
   - a) Percentage change in Volume
   - b) Percentage change in Price
4. Converting the data to a Pandas DataFrame for simplified storage and analysis at the BI end.

#### **Step 3 - Loading**

The transformed data is then stored in an Amazon Web Services (AWS) S3 bucket in CSV format.

---










