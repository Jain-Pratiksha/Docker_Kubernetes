# 🚀 Kerberos KDC Docker Image: Build on Laptop, Use on VM

This document outlines the full process of creating a Docker image for Kerberos KDC on a local laptop, pushing it to Docker Hub, and using it inside a VM where public internet access is limited.

---
I did all these things because I was not able to pull public image (access internet) from the vm due to restrictions.

Make sure you have docker installed on your laptop.
### 1. Prepare Dockerfile and Required Files (on Laptop)

Directory structure:

kdc-deployment/

├── Dockerfile

├── krb5.conf

├── kdc.conf

├── kadm5.acl

### 2. Build and Run Docker Image (on Laptop)
Cmd, Open terminal inside the kdc-deployment folder:

```bash
docker build -t pratiksha-kdc:latest .
docker run -it --rm --name test-kdc pratiksha-kdc:latest
```
Run just to see if the build is working and has no errors.

### 3. Tag Docker Image for Docker Hub

```bash
docker tag pratiksha-kdc:latest <your-dockerhub-username>/pratiksha-kdc:latest
Example:
docker tag pratiksha-kdc:latest pratikshajain/pratiksha-kdc:latest
```
You can run 'docker image' to see your image.

### 4. Login to docker
```bash
docker login
```
This will prompt for username (dockerhub username) and password.

### 5. Push Image to Docker Hub
```bash
docker push pratikshajain/pratiksha-kdc:latest
```
On docker hub you'll find a image created which can be used in vm

### 6. Pull Image on VM (if there is any base image (to access internet maybe) then add it before)
```bash
docker pull pratikshajain/pratiksha-kdc:latest

or

docker pull base-image/pratikshajain/pratiksha-kdc:latest
```


📝 Notes
If kdb5_util fails with permission denied during deployment, add this to your Kubernetes YAML:

```bash
securityContext:
  runAsUser: 0
```
This ensures the container runs with root permissions to initialize the KDC database on mounted volumes.

Woho, you are done. Your pod will be up.
