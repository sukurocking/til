These days, I am working on using GCP dataproc clusters. 
While using the cluster(s), I generally, as an efficiency/performance practise, try to know 

### 1. Which clusters are currently available in GCP Dataproc
```sh
gcloud dataproc clusters list
```

### 2. How much memory is allocated to each of the clusters
```sh
gcloud dataproc clusters describe clustername | grep "highmem"
```

### 3. How many jobs were running in each of the clusters
```sh
gcloud dataproc jobs list --cluster=clustername | grep "RUNNING"
```

These 3 commands I was running daily, to see which clusters have bandwidth and I can work on my spark submit commands accordingly for best performance results

Today, a thought crossed my mind, why dont I optimize this also. 
I didnt have much confidence in Bash scripting, so had to rely on ChatGPT and after a few prompts was able to optimize to this below loop in bash script

```sh
gcloud dataproc clusters list | awk "NR>1 && !/^$/ {print $1}" | while read -r cluster; do      # Starting a loop from the output of clusters list
    echo "Cluster: $cluster";                                                                   # Printing Cluster name
    running_jobs=$(gcloud dataproc jobs list --cluster="$cluster" | grep 'RUNNING' | wc -l);    # Storing running jobs count in a variable
    echo "RUNNING JOBS: $running_jobs";                                                         # Printing RUNNING JOBS
    gcloud dataproc clusters describe "$cluster" 2>/dev/null | awk '/highmem/ {print $2}';      # Getting RAM config of the clusters
    echo "";                                                                                    # Newline at the end of the loop
done
```

I put this in a check_clusters_mem.sh file, added executable permissions to the file in the command line and Finally executed it!

```sh
chmod +x check_clusters_mem.sh          # Adding executable permission to the shell script
./check_clusters_mem.sh                 # Executing the script
```
