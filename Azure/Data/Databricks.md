> The [[Azure Data]]bricks Lakehouse Platform provides a unified set of tools for building, deploying, sharing, and maintaining enterprise-grade data solutions at scale. Azure Databricks integrates with cloud storage and security in your cloud account, and manages and deploys cloud infrastructure on your behalf.

## Terminology
- **Data Lake**: A data lake is a centralized repository that allows you to store all your structured and unstructured data at any scale. You can store your data as-is, without having to first structure the data, and run different types of analytics—from dashboards and visualizations to big data processing, real-time analytics, and machine learning to guide better decisions.
- **Delta Lake**: Delta Lake is the optimized storage layer that provides the foundation for storing data and tables in the Databricks Lakehouse Platform. Delta Lake is open source softwarethat extends Parquet data files with a file-based transaction log for ACID transactions and scalable metadata handling.
- **Lakehouse**: A data lakehouse is a new, open data management architecture that combines the flexibility, cost-efficiency, and scale of data lakes with the data management and ACID transactions of data warehouses, enabling business intelligence (BI) and machine learning (ML) on all data.
- **Parquet data files**: Apache Parquet is an open source, column-oriented data file format designed for efficient data storage and retrieval. It provides efficient data compression and encoding schemes with enhanced performance to handle complex data in bulk. Apache Parquet is designed to be a common interchange format for both batch and interactive workloads. It is similar to other columnar-storage file formats available in Hadoop, namely RCFile and ORC.
- **ACID Transactions**: ACID are guarantees provided by the open source Delta Lake protocol that stands for atomicity, consistency, isolation, and durability:
	- **Atomicity** means that all transactions either succeed or fail completely.
	- **Consistency** guarantees relate to how a given state of the data is observed by simultaneous operations.
	- **Isolation** refers to how simultaneous operations potentially conflict with one another.
	- **Durability** means that committed changes are permanent.

## Structure
![[DataLakehouse.png]]
Text

## ETL Pipeline
![[DatabricksETL.png]]
Text

## Links
- [High-Performance Modern Data Warehousing with Azure Databricks and Azure SQL Data Warehouse - The Databricks Blog](https://www.databricks.com/blog/2019/02/07/high-performance-modern-data-warehousing-with-azure-databricks-and-azure-sql-dw.html)
