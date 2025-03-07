# Types and Sources of Big Data

## Introduction to Big Data
Big data refers to extremely large and complex data sets that traditional data processing applications are inadequate to deal with. The concept encompasses not just the volume of data but also its variety and the velocity at which it needs to be processed.

## Types of Big Data

### 1. Structured Data
- Data that resides in fixed fields within records or files
- Examples: Relational databases, spreadsheets, data warehouses
- Characteristics: Easily searchable, follows a schema, machine-readable

### 2. Unstructured Data
- Data that doesn't have a predefined data model or organization
- Examples: Text files, social media posts, videos, images, audio files
- Characteristics: Difficult to analyze using conventional methods, comprises approximately 80% of all data

### 3. Semi-structured Data
- Data that doesn't reside in a relational database but has some organizational properties
- Examples: XML files, JSON documents, email
- Characteristics: Contains tags or markers to separate elements, but lacks rigid structure of relational databases

## Sources of Big Data

### Internal Sources
- Enterprise resource planning (ERP) systems
- Customer relationship management (CRM) systems
- Web server logs and clickstream data
- Internal documents and communications
- Transactional data

### External Sources
- Social media platforms (Twitter, Facebook, Instagram)
- IoT devices and sensors
- Public datasets (government data, weather data)
- Third-party market research
- Web scraping

## Big Data in Business Context

### Key Business Applications
1. **Customer Analytics**
   - Personalization and recommendation engines
   - Customer segmentation and profiling
   - Sentiment analysis and voice of the customer
   - Churn prediction and prevention

2. **Operational Optimization**
   - Supply chain optimization
   - Predictive maintenance
   - Process automation
   - Inventory management

3. **Risk Management**
   - Fraud detection
   - Credit risk assessment
   - Compliance monitoring
   - Cybersecurity threat detection

4. **Product Innovation**
   - R&D enhancement
   - Market trend analysis
   - Product usage analytics
   - A/B testing at scale

5. **Strategic Decision Making**
   - Competitive intelligence
   - Market forecasting
   - Business performance analytics
   - Strategic planning

### Business Value of Big Data
- **Revenue Growth**: Identifying new market opportunities, optimizing pricing, improving customer acquisition and retention
- **Cost Reduction**: Improving operational efficiency, reducing waste, optimizing resource allocation
- **Enhanced Decision Making**: Data-driven decisions based on complete information rather than intuition
- **Innovation Acceleration**: Faster product development cycles based on real user feedback and needs

# Hadoop Framework

## Requirement of Hadoop Framework
The development of Hadoop was driven by several key requirements:

1. **Handling Massive Data Volumes**: Ability to store and process petabytes of data
2. **Scalability**: Easy horizontal scaling by adding commodity hardware
3. **Fault Tolerance**: Ability to continue operating despite hardware/system failures
4. **High Throughput**: Optimized for high data processing throughput rather than low latency
5. **Cost Effectiveness**: Utilizing commodity hardware instead of expensive specialized systems
6. **Flexibility**: Processing various data types (structured, semi-structured, unstructured)

## Design Principles of Hadoop

1. **Move Processing to Data**: Rather than moving data to where processing happens, Hadoop moves computation to where data resides
2. **Scale Out, Not Up**: Adding more machines rather than upgrading existing ones
3. **Expect and Handle Failures**: Hardware failure is treated as the norm rather than the exception
4. **Simple Coherency Model**: "Write once, read many" approach simplifies data coherency
5. **Data Locality Optimization**: Minimizing network congestion by keeping data and processing close
6. **Portability Across Hardware**: Works on heterogeneous hardware and operating systems

## Hadoop Components

### Core Components

1. **Hadoop Distributed File System (HDFS)**
   - Distributed file system providing high-throughput access to application data
   - Primary storage system for Hadoop applications
   - Designed for reliability and scalability

2. **YARN (Yet Another Resource Negotiator)**
   - Resource management and job scheduling for Hadoop clusters
   - Enables multiple data processing engines to run on the same cluster
   - Manages how applications get access to cluster resources

3. **MapReduce**
   - Programming model for large-scale data processing
   - Consists of Map phase (parallel processing) and Reduce phase (aggregation)
   - Handles data partitioning, distribution, and result collection

4. **Hadoop Common**
   - Common utilities and libraries that support other Hadoop modules
   - Includes Java libraries, utilities, OS-level abstractions, and interfaces

## Hadoop Ecosystem

Beyond the core components, the Hadoop ecosystem includes numerous tools:

1. **Data Ingestion**
   - **Apache Flume**: Service for collecting, aggregating, and moving large amounts of log data
   - **Apache Sqoop**: Tool for transferring data between Hadoop and relational databases
   - **Apache Kafka**: Distributed streaming platform for building real-time data pipelines

2. **Data Storage**
   - **HBase**: Non-relational, distributed database for real-time read/write access
   - **Apache Cassandra**: Highly scalable, distributed NoSQL database
   - **MongoDB**: Document-oriented NoSQL database

3. **Data Processing**
   - **Apache Spark**: Fast, in-memory data processing engine
   - **Apache Flink**: Stream processing framework with powerful event-time semantics
   - **Apache Storm**: Distributed real-time computation system
   - **Apache Tez**: Data-flow driven framework that generalizes the MapReduce paradigm

4. **Data Access**
   - **Apache Hive**: Data warehouse infrastructure providing SQL-like interface
   - **Apache Pig**: High-level platform for creating MapReduce programs
   - **Impala**: MPP (Massively Parallel Processing) SQL query engine

5. **Data Governance and Integration**
   - **Apache Atlas**: Data governance and metadata framework
   - **Apache Ranger**: Framework for security across the Hadoop ecosystem
   - **Apache Falcon**: Data management and processing platform

6. **Machine Learning and Analytics**
   - **Apache Mahout**: Scalable machine learning library
   - **Apache Spark MLlib**: Machine learning library for Spark
   - **TensorFlow on Hadoop**: Deep learning on Hadoop clusters

## Hadoop 2 Architecture

Hadoop 2 represented a significant evolution from Hadoop 1, primarily due to the introduction of YARN, which separated resource management from the MapReduce processing model.

### Key Components of Hadoop 2 Architecture:

1. **HDFS Layer**
   - **NameNode**: Manages file system namespace and regulates access to files
   - **DataNodes**: Store actual data blocks, serve read/write requests
   - **Secondary NameNode**: Performs periodic checkpoints of the namespace

2. **YARN Layer**
   - **ResourceManager**: Global resource manager, arbitrates resources among applications
   - **NodeManager**: Per-node agent responsible for containers, monitoring resource usage
   - **ApplicationMaster**: Per-application entity negotiating resources from ResourceManager

3. **MapReduce Layer**
   - Now runs as a YARN application
   - **JobTracker** functionality moved to ApplicationMaster
   - **TaskTracker** functionality moved to NodeManager

4. **High Availability Features**
   - HDFS NameNode high availability through active/standby architecture
   - ResourceManager high availability for YARN

## YARN Architecture in Detail

YARN (Yet Another Resource Negotiator) was designed to separate the resource management layer from the processing layer, allowing multiple processing frameworks to efficiently share a Hadoop cluster.

### Components:

1. **ResourceManager (RM)**
   - **Scheduler**: Allocates resources to applications based on requirements and constraints
   - **Applications Manager**: Accepts job submissions, negotiates first container for ApplicationMaster
   - Global entity overseeing all applications in the system

2. **NodeManager (NM)**
   - Agent running on each node in the cluster
   - Responsible for containers, monitoring resource usage (CPU, memory, disk, network)
   - Reports to ResourceManager

3. **ApplicationMaster (AM)**
   - Framework-specific entity, one per application
   - Negotiates resources from ResourceManager
   - Works with NodeManagers to execute and monitor tasks
   - Handles application failures

4. **Container**
   - Resource allocation unit (memory, CPU, etc.)
   - Granted by the ResourceManager
   - Used by applications to execute tasks

### YARN Workflow:

1. Client submits application to ResourceManager
2. ResourceManager allocates container for ApplicationMaster
3. ApplicationMaster starts and registers with ResourceManager
4. ApplicationMaster negotiates containers from ResourceManager
5. ApplicationMaster launches tasks in containers on NodeManagers
6. Application execution with monitoring and dynamic resource allocation
7. ApplicationMaster reports completion to ResourceManager and shuts down

## Advantages of YARN

1. **Multi-tenancy**: Multiple processing engines can run simultaneously on the same cluster
2. **Improved Resource Utilization**: Dynamic allocation and release of resources
3. **Scalability**: Can scale to thousands of nodes and petabytes of data
4. **Flexibility**: Support for various programming models beyond MapReduce
5. **Backward Compatibility**: Existing MapReduce applications run without modification
6. **High Availability**: Built-in failover mechanisms for ResourceManager
7. **Resource Isolation**: Prevents applications from interfering with each other
8. **Better Cluster Utilization**: Efficient packing of workloads

## YARN Commands

### Basic YARN Commands:
```
yarn application -list                # List all applications
yarn application -status <appId>      # Get application status
yarn application -kill <appId>        # Kill an application
yarn logs -applicationId <appId>      # Get application logs
yarn node -list                       # List all nodes in the cluster
yarn rmadmin -refreshQueues           # Reload queue configuration
yarn queue -status <queueName>        # Get queue status
```

### Administrative Commands:
```
yarn rmadmin -refreshNodes            # Refresh the hosts information
yarn rmadmin -refreshUserToGroupsMappings  # Refresh user-group mappings
yarn rmadmin -refreshSuperUserGroupsConfiguration  # Refresh superuser proxy groups
yarn rmadmin -refreshAdminAcls        # Refresh ACLs for administration
yarn rmadmin -refreshServiceAcl       # Refresh service-level authorization
yarn rmadmin -getGroups <username>    # Get groups for a user
```

# HDFS (Hadoop Distributed File System)

## Design of HDFS

HDFS was designed to be a distributed file system that provides high-throughput access to application data, particularly for large-scale data processing workloads.

### Architectural Components:

1. **NameNode**
   - Master server managing file system namespace
   - Maintains the file system tree and metadata for all files and directories
   - Tracks file block locations across the cluster
   - Single point of control in HDFS architecture

2. **DataNodes**
   - Slave nodes storing actual data blocks
   - Serve read/write requests from clients
   - Perform block creation, deletion, and replication upon instruction from NameNode
   - Send heartbeats to NameNode with block reports

3. **Secondary NameNode**
   - Performs periodic checkpoints of the file system metadata
   - Merges the edit logs with fsimage to prevent edit log from becoming too large
   - Not a hot standby for the NameNode (despite its name)

### Key Design Features:

1. **Block Storage**: Files are split into blocks (default 128MB), which are replicated across DataNodes
2. **Replication**: Each block replicated to multiple DataNodes (default: 3 copies) for fault tolerance
3. **Rack Awareness**: Block placement considers network topology to optimize data transfer
4. **Write-Once-Read-Many**: Files in HDFS are write-once and cannot be modified after creation
5. **Data Coherency**: Simplified by the write-once model, ensuring consistent reads
6. **Data Integrity**: Checksums for all data written to HDFS to detect corruption
7. **Metadata in Memory**: File system metadata kept in NameNode's memory for fast access

## Benefits of HDFS

1. **Fault Tolerance**: Multiple copies of data ensure no data loss due to hardware failure
2. **High Availability**: Continuous operation even when some nodes fail
3. **High Throughput**: Optimized for batch processing and streaming data workloads
4. **Large Data Sets**: Designed to handle petabytes of data across thousands of nodes
5. **Portability**: Can run on commodity hardware and various operating systems
6. **Scalability**: Easily scales horizontally by adding more nodes
7. **Cost Effectiveness**: Works with inexpensive commodity hardware
8. **Data Locality**: Computation moves to data, reducing network congestion

## Challenges of HDFS

1. **Single Point of Failure**: Traditional NameNode is a single point of failure (addressed in newer versions with HA)
2. **Not Suitable for Low-Latency Access**: Optimized for throughput, not latency
3. **Small File Problem**: Inefficient for storing many small files due to NameNode memory limitations
4. **No Random Writes**: Files can only be written once and appended to, not randomly modified
5. **No Built-in Encryption**: Earlier versions lacked data encryption at rest (addressed in newer versions)
6. **Limited Metadata Scaling**: NameNode keeps all metadata in memory, limiting scaling
7. **Complex Administration**: Requires specialized knowledge for efficient operation

## HDFS Commands

### Basic File Operations:
```
hdfs dfs -ls <path>                  # List files and directories
hdfs dfs -mkdir <path>               # Create directory
hdfs dfs -put <localSrc> <dest>      # Upload file from local to HDFS
hdfs dfs -get <src> <localDest>      # Download file from HDFS to local
hdfs dfs -cat <file>                 # View file content
hdfs dfs -rm <file>                  # Remove file
hdfs dfs -rmr <dir>                  # Remove directory recursively
hdfs dfs -mv <src> <dest>            # Move file or directory
hdfs dfs -cp <src> <dest>            # Copy file or directory
hdfs dfs -chmod <mode> <path>        # Change file permissions
hdfs dfs -chown <owner> <path>       # Change file ownership
```

### Administrative Commands:
```
hdfs dfsadmin -report                # Get filesystem statistics and info
hdfs dfsadmin -safemode enter|leave  # Enter or leave safe mode
hdfs dfsadmin -refreshNodes          # Update DataNodes list
hdfs fsck <path>                     # Run HDFS filesystem check
hdfs dfs -count -q <path>            # Count files, directories and sizes
hdfs dfs -du <path>                  # Show disk usage
hdfs balancer                        # Run balancer to redistribute blocks
hdfs dfs -setrep <rep> <path>        # Set replication factor for a file
hdfs dfs -expunge                    # Empty trash
```

### Debugging and Information Commands:
```
hdfs dfs -stat <path>                # Display file statistics
hdfs dfs -test -e <path>             # Check if file exists
hdfs dfs -checksum <file>            # Display file checksum
hdfs oiv                             # Offline image viewer for fsimage files
hdfs dfs -df -h                      # Show free space in human-readable format
hdfs getconf -confKey <key>          # Get configuration value
```

By using these commands, administrators and users can effectively manage and operate the HDFS filesystem, ensuring optimal performance and availability of the Hadoop cluster.