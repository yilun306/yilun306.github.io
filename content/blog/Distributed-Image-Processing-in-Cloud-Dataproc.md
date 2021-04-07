---
title: "Distributed Image Processing in Cloud Dataproc"
date: 2021-03-20T17:55:56-04:00
draft: true
---

[Github Link: https://github.com/yilun306/Distributed-Image-Processing-in-Cloud-Dataproc](https://github.com/yilun306/Distributed-Image-Processing-in-Cloud-Dataproc)
## GCP VM Setup
1. Make sure Editor role is enabled for the developer account
2. Setup VM in Compute Engine > VM Instances > Create.
3. Choose Series N1, 2 vCPUs (n1-standard-2 instance) as Machine Type, and allow full access to all Cloud APIs.
4. Click create, and access the console using the SSH button.

## Install Software
1. Set up Scala and sbt
```bash
sudo apt-get install -y dirmngr unzip
sudo apt-get update
sudo apt-get install -y apt-transport-https
```
```bash
echo "deb https://dl.bintray.com/sbt/debian /" | \
sudo tee -a /etc/apt/sources.list.d/sbt.list
```
```bash
sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv 642AC823
sudo apt-get update
sudo apt-get install -y bc scala sbt
```

2. Set up the Feature Detector Files
```bash
sudo apt-get update
```
```bash
gsutil cp gs://spls/gsp124/cloud-dataproc.zip .
unzip cloud-dataproc.zip
```
```bash
cd cloud-dataproc/codelabs/opencv-haarcascade
```
3. Launch Build
```bash
sbt assembly
```

## Create a Cloud Storage bucket and collect images
```bash
GCP_PROJECT=$(gcloud config get-value core/project)
```
```bash
MYBUCKET="${USER//google}-image-${RANDOM}"
```
```bash
echo MYBUCKET=${MYBUCKET}
```
```bash
gsutil mb gs://${MYBUCKET}
```
```bash
curl https://www.publicdomainpictures.net/pictures/20000/velka/family-of-three-871290963799xUk.jpg | gsutil cp - gs://${MYBUCKET}/imgs/family-of-three.jpg
curl https://www.publicdomainpictures.net/pictures/10000/velka/african-woman-331287912508yqXc.jpg | gsutil cp - gs://${MYBUCKET}/imgs/african-woman.jpg
curl https://www.publicdomainpictures.net/pictures/10000/velka/296-1246658839vCW7.jpg | gsutil cp - gs://${MYBUCKET}/imgs/classroom.jpg
```
```bash
gsutil ls -R gs://${MYBUCKET}
```

## Create a Cloud Dataproc cluster
```bash
MYCLUSTER="${USER/_/-}-qwiklab"
echo MYCLUSTER=${MYCLUSTER}
```
```bash
gcloud config set dataproc/region us-central1
```
```bash
gcloud dataproc clusters create ${MYCLUSTER} --bucket=${MYBUCKET} 
--worker-machine-type=n1-standard-2 --master-machine-type=n1-standard-2 
--initialization-actions=gs://spls/gsp010/install-libgtk.sh --image-version=2.0  
```

## Submit your job to Cloud Dataproc
```bash
curl https://raw.githubusercontent.com/opencv/opencv/master/data/haarcascades/haarcascade_frontalface_default.xml 
| gsutil cp - gs://${MYBUCKET}/haarcascade_frontalface_default.xml
```
```bash
cd ~/cloud-dataproc/codelabs/opencv-haarcascade
```
```bash
gcloud dataproc jobs submit spark \
--cluster ${MYCLUSTER} \
--jar target/scala-2.12/feature_detector-assembly-1.0.jar -- \
gs://${MYBUCKET}/haarcascade_frontalface_default.xml \
gs://${MYBUCKET}/imgs/ \
gs://${MYBUCKET}/out/
```
## Monitor the job
Navigation menu > Dataproc > Jobs

## Check Processed Image
Navigation menu > Storage