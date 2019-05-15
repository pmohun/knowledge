# Google Cloud Platform

### Containers

This walkthrough demonstrates how to upload a Docker container to Google Container Registry. 

Some helpful guides:

* [Google Container Registry Documentation](https://cloud.google.com/container-registry/docs/)

**Ensure the Docker image on your local device is up to date**

```text
docker build -t <YOUR-IMAGE> .
gcloud auth configure-docker ## use GCP credentials
[HOSTNAME]/[PROJECT-ID]/[IMAGE] ## hostname = us.gcr.io
docker tag [SOURCE_IMAGE] [HOSTNAME]/[PROJECT-ID]/[IMAGE]
docker push [HOSTNAME]/[PROJECT-ID]/[IMAGE]
```

