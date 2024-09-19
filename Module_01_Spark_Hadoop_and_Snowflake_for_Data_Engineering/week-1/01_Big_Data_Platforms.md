# **Overview of Big Data Platforms**

**Big Data** - Data too big for a single machine. Solutions for this problems usually fits into **Distributed data storage** or **Distributed data processing**.

---

## **Apache Hadoop**
Platform for processing Big Data and also an implementation of **MapReduce** programming model. It distributes work across multiple machines (nodes) and writes intermediate data to disk as a strategy for dealing with large data that can't sit in memory.

Apache Hadoop is an open-source framework designed for **distributed storage** and processing of large volumes of data across clusters of commodity hardware. It offers a scalable solution to handle big data by distributing data across multiple nodes and enabling parallel processing. At its core, Hadoop consists of two main components: Hadoop Distributed File System (HDFS) for storage and Hadoop MapReduce for processing.

### Benefits:
* Scalability: Hadoop's distributed storage (HDFS) and processing (MapReduce) architecture make it suitable for handling vast amounts of data across clusters of commodity hardware.
* Batch Processing: Hadoop excels in batch processing scenarios, where large datasets are processed sequentially using MapReduce jobs.
* Ecosystem: Hadoop offers a rich ecosystem of tools, including Hive for querying, Pig for data processing, and more, making it versatile for various data-related tasks.
* Data Resilience: HDFS's data replication ensures data redundancy and fault tolerance, safeguarding against node failures.
* Cost-Effectiveness: Hadoop's open-source nature and ability to run on commodity hardware can offer cost-effective solutions for storing and processing large datasets.

### Drawbacks:
* Latency: Hadoop's batch processing nature can result in higher latencies for real-time processing needs.
* Complexity: Setting up, configuring, and managing a Hadoop cluster can be complex and require specialized skills.
* Programming Model: MapReduce's programming model can be intricate, and developing applications might require more effort compared to newer alternatives.


For the most up-to-date information on accessing and installing Hadoop, please visit: 
* [What is Hadoop (AWS)](https://aws.amazon.com/emr/details/hadoop/what-is-hadoop/).

---

## **Apache Spark**
Big Data analytics engine. It uses RAM memory to store data, becoming generally faster than Hadoop (especially for iterative work) and it also attaches to a number of cluster management systems. Requires a distributed data store.

Apache Spark is an open-source, powerful, and versatile data processing engine designed for efficient **distributed data processing** and analytics. It provides a unified platform for batch processing, interactive queries, machine learning, and streaming data analysis.

### Concepts:
* Driver send jobs to executors
* Jobs are divided into stages
* Data is partitioned with tasks running per partition
* Resilient Distributed Dataset - RDD

### Benefits:
* Speed: Spark's in-memory processing enables significantly faster data processing compared to disk-based processing in Hadoop's MapReduce.
* Versatility: Spark supports batch processing, interactive queries, machine learning, and streaming data processing in a unified platform.
* Ease of Use: Spark's APIs are more intuitive and developer-friendly, making it easier for newcomers to get started.
* Advanced Analytics: Spark's MLlib library offers machine learning capabilities, allowing data engineers to perform advanced analytics tasks.
* Real-time Processing: Spark Streaming enables real-time data processing, making it suitable for use cases requiring quick insights from streaming data.

### Drawbacks:
* Memory Requirement: Spark's in-memory processing can demand substantial memory resources, which might lead to higher infrastructure costs.
* Learning Curve: While more user-friendly than MapReduce, Spark still requires a learning curve, especially for more complex tasks.
* Compatibility: Spark is relatively newer than Hadoop, so certain legacy systems might be more compatible with Hadoop-based solutions.


For the most up-to-date information on Spark and accessing the Spark ecosystem, please visit the following resources:
* [What is Apache Spark? (Google Cloud)](https://cloud.google.com/learn/what-is-apache-spark)
* [What is Spark? (AWS)](https://aws.amazon.com/big-data/what-is-spark/)
* [Spark Cluster Overview (Apache Spark)](https://spark.apache.org/docs/latest/cluster-overview.html)

---

## **Choosing between Hadoop and Spark**
New data engineers need not strictly decide between Hadoop and Spark; both have their places in the data engineering landscape. The choice depends on factors like:

* **Use Case**: Hadoop might be preferred for batch processing, while Spark is more suitable for real-time processing and versatile analytics.
* **Skill Set**: If you're more comfortable with Java or have MapReduce expertise, Hadoop might be a natural choice. Spark's easier APIs might be appealing if you're starting fresh.
* **Infrastructure**: Consider your existing infrastructure. If you have a Hadoop cluster in place, it might make sense to continue leveraging it.
* **Performance**: Spark's speed advantage can be crucial for time-sensitive applications, but Hadoop's ecosystem might be preferred for certain tasks.

In many cases, organizations use both Hadoop and Spark together. Hadoop serves as a reliable storage layer, while Spark accelerates processing. Data engineers can leverage both tools based on their strengths and requirements. Ultimately, understanding both Hadoop and Spark is beneficial, as they provide a broader skill set and the ability to choose the right tool for the task at hand.

---

## **Resilient Distributed Datasets (RDD)**
Abstraction of data and tasks partitioned across nodes. There are two types of operations associated with RDDs:
* Transformation (lazy)
* Action (return computation)

They are called resilient because if a node fails, it's able to recover and recompute the data that would have been computed by the node.

Resilient Distributed Datasets (RDDs) are a fundamental data structure in the Apache Spark framework, designed to facilitate distributed data processing across clusters. RDDs serve as the foundational building blocks for Spark applications, enabling fault-tolerant, parallelized data processing in a distributed computing environment.

Shuffle operations in Spark are transformations that require data to be repartitioned across the cluster. This typically happens when the output of a transformation depends on data from multiple partitions, such as in operations like `groupByKey`, `reduceByKey`, `join`, and `distinct`.

Key characteristics of RDDs include:
* **Resilience**: RDDs are "resilient" because they can recover from node failures. Through lineage information, Spark can recreate lost data partitions by recomputing them from the original data and transformations.
* **Distributed**: RDDs are distributed across multiple nodes in a Spark cluster, allowing for parallel processing of data. Each RDD is divided into partitions, with each partition residing on a separate node.
* **Immutable**: RDDs are immutable, meaning their content cannot be changed once created. Instead, transformations applied to RDDs produce new RDDs, preserving data integrity.
* **In-Memory Processing**: RDDs are stored in memory, enabling faster data access and computation compared to traditional disk-based storage. This in-memory processing contributes to Spark's speed advantage.
* **Transformation and Action Operations**: RDDs support two types of operations: transformations (e.g., map, filter, reduceByKey), which create new RDDs from existing ones, and actions (e.g., count, collect, saveAsTextFile), which trigger computations and return results.
* **Data Partitioning**: RDDs allow users to control data partitioning, which can optimize data locality and enhance processing efficiency.

For more information, check out these resources:
* [Resilient Distributed Datasets (RDDs)](https://www.databricks.com/glossary/what-is-rdd) (Databricks)
* [Apache Spark RDD](https://www.tutorialspoint.com/apache_spark/apache_spark_rdd.htm) (Tutorials Point)


