# Design Justification

## Storage Systems

In this system, different types of storage are used for different purposes to make everything efficient. A **Data Lake** is used to store all raw data coming from hospital systems like patient records, lab reports, billing, and ICU devices. This is useful because we keep all original data safely for future use and analysis.

A **Data Warehouse** is used for cleaned and organized data. This helps in generating monthly reports like bed usage and department costs. It also supports the system where doctors can ask questions in simple English. Since the data is structured, it gives faster and more accurate results.

For ICU monitoring, a **NoSQL or Time-Series Database** is used. ICU devices send data continuously (like heart rate every second), so we need a system that can handle fast and large amounts of data. This database helps in quickly storing and accessing real-time patient data.

The machine learning model that predicts patient readmission uses data from the Data Warehouse because it needs clean and well-organized historical data to give accurate predictions.

## OLTP vs OLAP Boundary

OLTP systems are the hospital’s main working systems like EHR, billing, and lab databases. These systems handle daily operations such as updating patient details, recording treatments, and generating bills. They are designed to work quickly and handle many small transactions.

The boundary between OLTP and OLAP comes at the **ETL process**. When data is taken from these systems and moved into the Data Lake, it stops being transactional and becomes analytical.

OLAP systems start from the Data Lake and Data Warehouse. These systems are used for analysis, reporting, and AI models. For example, management reports, doctor queries, and prediction models all work on OLAP data.

This separation is important so that heavy analysis does not slow down the hospital’s daily operations.

## Trade-offs

One major trade-off in this design is between **speed and complexity**. To support both real-time ICU data and historical analysis, we need different systems and pipelines. This makes the overall system more complex and harder to manage.

To reduce this problem, we can use tools that handle both batch and real-time data together, like Apache Spark. We can also use automation and monitoring tools to manage the system easily.

Even though the system becomes more complex, this design is necessary to provide both real-time alerts for critical patients and detailed analysis for better decision-making.