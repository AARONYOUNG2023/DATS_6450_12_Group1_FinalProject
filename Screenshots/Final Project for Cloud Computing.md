# Final Project for Cloud Computing

## Step 1 - Data Storage with Amazon S3

1. #### Create Amazon S3

![image-20241113170801664](C:\Users\aaron\AppData\Roaming\Typora\typora-user-images\image-20241113170801664.png)

2. #### Upload dataset into Amazon S3

![image-20241113171218257](C:\Users\aaron\AppData\Roaming\Typora\typora-user-images\image-20241113171218257.png)

3. Result

![image-20241113171357463](C:\Users\aaron\AppData\Roaming\Typora\typora-user-images\image-20241113171357463.png)

## Step 2 - Data Cleaning with AWS Glue

1. ### Crawler Setup

![image-20241113174217799](C:\Users\aaron\AppData\Roaming\Typora\typora-user-images\image-20241113174217799.png)

![image-20241113174427911](C:\Users\aaron\AppData\Roaming\Typora\typora-user-images\image-20241113174427911.png)

2. Create Jobs

![image-20241114171048489](C:\Users\aaron\AppData\Roaming\Typora\typora-user-images\image-20241114171048489.png)

3. Cleaning data with AWS Glue

#### 3.1 Drop null values and empty string

![image-20241114174751837](C:\Users\aaron\AppData\Roaming\Typora\typora-user-images\image-20241114174751837.png)

#### 3.2 Select features through domain knowledge

![image-20241114174659990](C:\Users\aaron\AppData\Roaming\Typora\typora-user-images\image-20241114174659990.png)

![image-20241114175159205](C:\Users\aaron\AppData\Roaming\Typora\typora-user-images\image-20241114175159205.png)

#### 3.3 Set up the S3 Target

![image-20241114204340902](C:\Users\aaron\AppData\Roaming\Typora\typora-user-images\image-20241114204340902.png)



## Step 3 - Model Training with Amazon SageMaker

### 3.1 Create a sagemaker

![image-20241114210129227](C:\Users\aaron\AppData\Roaming\Typora\typora-user-images\image-20241114210129227.png)

### 3.2 Create a notebook

![image-20241114210354553](C:\Users\aaron\AppData\Roaming\Typora\typora-user-images\image-20241114210354553.png)

3.3 Model training

![image-20241115201551223](C:\Users\aaron\AppData\Roaming\Typora\typora-user-images\image-20241115201551223.png)

![image-20241115200536004](C:\Users\aaron\AppData\Roaming\Typora\typora-user-images\image-20241115200536004.png)

![image-20241115200553881](C:\Users\aaron\AppData\Roaming\Typora\typora-user-images\image-20241115200553881.png)

![image-20241115200605208](C:\Users\aaron\AppData\Roaming\Typora\typora-user-images\image-20241115200605208.png)

## Step 4 - Storing Results with Amazon RDS (Relational Database Service)

4.1 Create database

![image-20241115205321413](C:\Users\aaron\AppData\Roaming\Typora\typora-user-images\image-20241115205321413.png)

![image-20241115231011855](C:\Users\aaron\AppData\Roaming\Typora\typora-user-images\image-20241115231011855.png)

![image-20241115205417615](C:\Users\aaron\AppData\Roaming\Typora\typora-user-images\image-20241115205417615.png)

```python
import pymysql

# Connect to the RDS database
connection = pymysql.connect(
    host='database-1.ctaog4kc8e9z.us-west-2.rds.amazonaws.com',
    port=3306,
    user='admin',
    password='yang8329200',
)

# Create a database and use it
with connection.cursor() as cursor:
    cursor.execute("CREATE DATABASE IF NOT EXISTS database_1;")
    cursor.execute("USE database_1;")

# Create a table for predictions
with connection.cursor() as cursor:
    create_table_query = """
    CREATE TABLE IF NOT EXISTS predictions (
        id INT AUTO_INCREMENT PRIMARY KEY,
        hour INT,
        distance FLOAT,
        cab_type VARCHAR(255),
        cab_company VARCHAR(255),
        predicted_price FLOAT,
        actual_price FLOAT
    );
    """
    cursor.execute(create_table_query)
    connection.commit()

# Insert predictions into the table
with connection.cursor() as cursor:
    for _, row in predictions_df.iterrows():
        insert_query = """
        INSERT INTO predictions (hour, distance, cab_type, cab_company, predicted_price, actual_price)
        VALUES (%s, %s, %s, %s, %s, %s);
        """
        cursor.execute(insert_query, (
            row['hour'], row['distance'], row.get('cab_type', 'N/A'), row.get('cab_company', 'N/A'),
            row['predicted_price'], row['actual_price']
        ))
    connection.commit()

# Query data from the table to verify
with connection.cursor() as cursor:
    cursor.execute("SELECT * FROM predictions;")
    results = cursor.fetchall()
    

# Close the connection
connection.close()
```

![image-20241115231040862](C:\Users\aaron\AppData\Roaming\Typora\typora-user-images\image-20241115231040862.png)

![image-20241115231027561](C:\Users\aaron\AppData\Roaming\Typora\typora-user-images\image-20241115231027561.png)

## Step 5 - Data Visualization with Amazon QuickSight

5.1 





5.2 Graphs

Price by Distance by cab_type

![image-20241115185324039](C:\Users\aaron\AppData\Roaming\Typora\typora-user-images\image-20241115185324039.png)

price by distance

![image-20241115185435005](C:\Users\aaron\AppData\Roaming\Typora\typora-user-images\image-20241115185435005.png)

price by surge_multipler

![image-20241115185655641](C:\Users\aaron\AppData\Roaming\Typora\typora-user-images\image-20241115185655641.png)

price by company

![image-20241115185850912](C:\Users\aaron\AppData\Roaming\Typora\typora-user-images\image-20241115185850912.png)

price by humidity

![image-20241115190112993](C:\Users\aaron\AppData\Roaming\Typora\typora-user-images\image-20241115190112993.png)

price by temperature

![image-20241115190251838](C:\Users\aaron\AppData\Roaming\Typora\typora-user-images\image-20241115190251838.png)





