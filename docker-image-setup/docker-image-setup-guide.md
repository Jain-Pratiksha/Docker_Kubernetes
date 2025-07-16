# 🚀 Docker Image Workflow: Build on Laptop, Use on VM

This guide explains how to build a Docker image locally (on a laptop), push it to Docker Hub and then pull and use it on a VM — especially useful when the VM has no internet access to pull public base images directly.

---

## 📌 Why This Workflow?

Sometimes, your VM environment might:
- Lack internet access
- Restrict public registry access
- Fail pulling base images or tools from Docker Hub

In such cases, building and testing locally, and then pushing to a registry is the cleanest approach.

---

### 🛠️ 1. Prepare Dockerfile & App Files (on Laptop)

Create a folder with a `Dockerfile` and a simple app (like a `hello.txt`, `app.py`, or any static file).

Example folder structure:

simple-app/

├── Dockerfile

├── hello.txt

### 2. Build Docker Image (on Laptop)
Open terminal in the simple-app folder:

```bash
docker build -t simple-app:latest .
```
✅ This creates an image tagged simple-app:latest

### 3. Test the Image Locally (Optional)
```bash
docker run --rm simple-app:latest
```
Should print:

<content of hello.txt>
  
### 4. Tag Docker Image for Docker Hub
Replace <username> with your Docker Hub username.

```bash
docker tag simple-app:latest <username>/simple-app:latest
Example:
docker tag simple-app:latest pratikshajain/simple-app:latest
```

### 5. Login to Docker Hub

```bash
docker login
```
Enter your Docker Hub username and password.

### 6. Push Image to Docker Hub

```bash
docker push pratikshajain/simple-app:latest
```
You’ll see the image on your Docker Hub profile.

### 7. Pull Image on VM
Log into your VM terminal and run:
```bash
docker pull pratikshajain/simple-app:latest
```

If successful, run the image:
```bash
docker run --rm pratikshajain/simple-app:latest
```

✅ Woho, Done!
You now have a locally built and pushed image available for use anywhere — even in restricted VM environments.
