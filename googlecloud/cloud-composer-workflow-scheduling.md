# Workflow scheduling
Below is a guide to workflow scheduling in Apache Airflow, particularly within the context of Google Cloud Composer. It would a nice take for someone new to Apache Airflow:

### Introduction to Workflow Scheduling

- **What is Workflow Scheduling?**: It's the process of automating when and how your workflows (DAGs) are run. It can be done either on a set schedule or based on specific triggers.

### Two Ways to Run Workflows

1. **Set Schedule**: You can schedule your workflow to run periodically, like daily at 6:00 AM or weekly on Saturdays. This is a common approach.
2. **Trigger-Based**: Your workflow can be run based on specific events, such as when new CSV files are loaded into a Cloud Storage bucket.

### Understanding DAGs in Airflow

- **Viewing DAGs**: In the Airflow web UI, you can navigate to the DAGs tab to view existing workflows.
- **Scheduled vs. Event-Driven**: Some DAGs may have a daily schedule, while others may be event-driven, meaning they run based on specific triggers rather than a set schedule.

### Event-Driven Workflows

- **Using Cloud Functions**: You can create Cloud Functions that watch for specific events, like new files in a Cloud Storage bucket, to trigger your DAGs.
- **Push vs. Pull Architecture**:
    - **Push**: Your workflow kicks off when a new file is pushed to Cloud Storage (event-triggered).
    - **Pull**: Airflow looks in your Cloud Storage folder at a set time and takes all contents for its workflow run (time-triggered).
- **Push Technology Applications**: Useful for real-time transactions, disaster notifications, and irregularly arriving data, such as in ML workflows.

### Creating a Cloud Function to Trigger a DAG

- **Choosing a Trigger**: You can specify triggers like new files in a Cloud Storage bucket, HTTP requests, Pub/Sub, Firestore, Firebase, etc.
- **Writing the Function**: You'll write a JavaScript function, such as `triggerDAG`, to specify the Airflow environment and DAG to be triggered.
- **Boilerplate Code**: Most of the code for triggering Airflow DAGs can be copied as a starting point.
- **Specifying Details**: You'll need to specify the correct DAG name, construct the Airflow URL, and make the actual request to the Airflow server.
- **Creating the Cloud Function**: Once the code and metadata are ready, you'll specify the function to execute, being mindful of case sensitivity.
- **Monitoring**: You can actively watch your Cloud Storage bucket for file uploads and monitor logs to ensure everything is working as intended.

### Summary

- **Workflow scheduling in Apache Airflow** allows you to automate the running of your DAGs either on a set schedule or based on specific triggers.
- **Google Cloud Composer** integrates with Airflow to enable seamless scheduling and triggering of workflows, utilizing Cloud Functions and various trigger mechanisms.
- **Both scheduled and event-driven approaches** have their applications, and the choice depends on the specific needs of your data workflows.