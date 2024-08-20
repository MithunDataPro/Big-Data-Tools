# Hadoop

**Definition:**  
Hadoop is an open-source framework that allows for the distributed processing of large data sets across clusters of computers using simple programming models. It is designed to scale up from single servers to thousands of machines.

**Components:**

- **HDFS (Hadoop Distributed File System):** Stores large volumes of data across multiple nodes.
- **MapReduce:** A programming model for processing large data sets with a parallel, distributed algorithm.
- **YARN (Yet Another Resource Negotiator):** Manages resources and scheduling tasks in the cluster.

**Use Cases:**

- **Data Warehousing:** Storing and processing large data sets for analysis.
- **Log Analysis:** Analyzing large volumes of log data for patterns and insights.

## Hadoop – Architecture

_Last Updated: 03 Jan, 2023_

Hadoop is a framework written in Java that utilizes a large cluster of commodity hardware to maintain and store big data. Hadoop works on the MapReduce Programming Algorithm introduced by Google. Many big brand companies, such as Facebook, Yahoo, Netflix, and eBay, use Hadoop to handle big data. The Hadoop Architecture mainly consists of four components:

- MapReduce
- HDFS (Hadoop Distributed File System)
- YARN (Yet Another Resource Negotiator)
- Common Utilities or Hadoop Common

Let’s understand the role of each component in detail.

### 1. MapReduce

MapReduce is an algorithm or data structure based on the YARN framework. The primary feature of MapReduce is to perform distributed processing in parallel in a Hadoop cluster, making Hadoop efficient for big data. When dealing with Big Data, serial processing is ineffective. MapReduce mainly involves two tasks, divided phase-wise:

- **First phase:** The Map function is utilized.
- **Next phase:** The Reduce function is utilized.

#### MapReduce Workflow

The input is provided to the `Map()` function, and its output is used as input to the `Reduce()` function, leading to the final output.

**Map Task:**

- **RecordReader:** Breaks the records and provides key-value pairs in the `Map()` function. The key is locational information, and the value is the associated data.
- **Map:** A user-defined function that processes tuples obtained from the RecordReader. It may generate multiple key-value pairs.
- **Combiner:** Groups data in the Map workflow, similar to a local reducer. It's optional.
- **Partitioner:** Fetches key-value pairs from the Mapper phase, generates shards corresponding to each reducer, and determines the hash code of each key.

**Reduce Task:**

- **Shuffle and Sort:** The Reducer task begins with this step, sorting data using its key value.
- **Reduce:** Gathers tuples from Map and performs sorting and aggregation.
- **OutputFormat:** Writes key-value pairs into a file, with each record in a new line and the key and value space-separated.

### 2. HDFS (Hadoop Distributed File System)

HDFS is utilized for storage permission and is designed to work on commodity hardware. HDFS is built to store large chunks of data rather than small data blocks. It provides fault tolerance and high availability in the storage layer.

**Data Storage Nodes in HDFS:**

- **NameNode (Master):** Stores metadata, such as transaction logs, file names, sizes, and block locations. It instructs DataNodes with operations like delete, create, and replicate.
- **DataNode (Slave):** Stores the actual data in a Hadoop cluster.

**File Block in HDFS:**

Data in HDFS is stored in blocks, typically 128MB in size, which can be adjusted. For example, a 400MB file would be divided into blocks of 128MB each.

**Replication in HDFS:**

Replication ensures data availability by making copies of file blocks. The default replication factor is 3, meaning each block is replicated three times for fault tolerance.

**Rack Awareness:**

A rack is a physical collection of nodes in a Hadoop cluster. Namenode uses rack information to choose the closest Datanode for read/write operations, reducing network traffic.

### 3. YARN (Yet Another Resource Negotiator)

YARN is a framework on which MapReduce works. YARN performs job scheduling and resource management. The Job Scheduler divides tasks into smaller jobs and assigns them to various slaves in a Hadoop cluster, while the Resource Manager manages all resources available for running a Hadoop cluster.

**Features of YARN:**

- **Multi-Tenancy**
- **Scalability**
- **Cluster-Utilization**
- **Compatibility**

### 4. Hadoop Common or Common Utilities

Hadoop Common or Common Utilities consist of Java libraries and scripts necessary for running a Hadoop cluster. These utilities are used by HDFS, YARN, and MapReduce to verify and handle hardware failures automatically.


