# GCP

* [Google Cloud Storage does not have folders or subdirectories.](https://stackoverflow.com/questions/38416598/how-to-create-an-empty-folder-on-google-storage-with-google-api)

* Remember to set the project ID before trying some commands

* Update gcloud

```console
gcloud components update
```

* Run before using gcloud with terminal

```console
gcloud auth login
```

* [ssh port forwarding to a VM](https://stackoverflow.com/questions/27294267/ssh-port-forwarding-google-compute-engine)

```console
gcloud beta compute ssh --ssh-flag="-N" --ssh-flag="-L localhost:8888:localhost:8888" --zone [ZONE] [INSTANCE_NAME] --project [PROJECT_NAME]
```
* [copy a large number of files in parallel](https://cloud.google.com/storage/docs/gsutil/commands/cp)

```console
gsutil -m cp -r dir gs://my-bucket
```
