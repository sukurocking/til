Figured out how to delete an AI model in Google Cloud using the aiplatform library. 
It lists the available models, specifies a model to delete by its resource name, and then calls 
the delete method on that model. The log output shows the process of deletion, including 
confirmation that the model has been successfully deleted.


```python
aiplatform.Model.list()
```

```
[<google.cloud.aiplatform.models.Model object at 0x7d78272b54e0> 
 resource name: projects/490054848291/locations/us-central1/models/biogpt-1725982935051]
```

```python
model_to_delete = aiplatform.Model("projects/490054848291/locations/us-central1/models/biogpt-1725982935051")
model_to_delete.delete()
```

```log
INFO:google.cloud.aiplatform.base:Deleting Model : projects/490054848291/locations/us-central1/models/biogpt-1725982935051
INFO:google.cloud.aiplatform.base:Model deleted. . Resource name: projects/490054848291/locations/us-central1/models/biogpt-1725982935051
INFO:google.cloud.aiplatform.base:Deleting Model resource: projects/490054848291/locations/us-central1/models/biogpt-1725982935051
INFO:google.cloud.aiplatform.base:Delete Model backing LRO: projects/490054848291/locations/us-central1/models/biogpt-1725982935051/operations/5222967376269541376
INFO:google.cloud.aiplatform.base:Model resource projects/490054848291/locations/us-central1/models/biogpt-1725982935051 deleted.
```