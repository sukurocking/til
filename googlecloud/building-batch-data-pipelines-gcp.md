# Building batch data pipelines on Google Cloud


### Data Loading Methods: ELT vs ETL
- **ELT (Extract, Load, Transform)**: This approach is useful when the data transformations are minor and can be done after loading the data into the data warehouse. For example, you can load raw data into BigQuery and then perform SQL transformations to create a new table.
  
- **ETL (Extract, Transform, Load)**: This is more suitable for complex transformations or when dealing with large volumes of data. In such cases, it's more efficient to transform the data before loading it. Dataflow is often used for this kind of batch pipeline.

### Data Transformation in BigQuery
- The course covered how to use SQL in BigQuery to perform common operations that prepare your structured data for analytics.

### Serverless Batch Pipelines with Dataflow
- You learned how to build batch pipelines using Dataflow, either from templates or by writing your own code.
- **P Collection**: This is the fundamental unit of logical data in Dataflow pipelines, which stands for "parallel collection."
- **Serverless and Autoscaling**: Dataflow is a serverless application that automatically scales the number of worker VMs based on the workload.

### Hadoop and Dataproc
- You can migrate your existing Hadoop workloads to Google Cloud's Dataproc service without changing the code.
- Once in the cloud, you can optimize by using Cloud Storage instead of HDFS, which is more efficient and cost-effective.

### Managing Data Pipelines
- **Cloud Data Fusion**: This tool allows data analysts and ETL developers to visually build data pipelines. It also provides data lineage features.
  
- **Cloud Composer**: This is a managed Apache Airflow service that allows you to orchestrate complex operations using DAGs (Directed Acyclic Graphs). These DAGs can be triggered either on a schedule or by events, such as uploading a new CSV to a Cloud Storage bucket.

### Next Steps
- Next, we will be learning about building resilient streaming analytics systems on Google Cloud.