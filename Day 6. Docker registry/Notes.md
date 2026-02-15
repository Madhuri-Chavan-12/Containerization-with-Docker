# 📌 Docker Registry 

- A Docker Registry is a storage and distribution system for Docker images.

- It allows you to:

     > Upload Docker images

     > Store them securely

     > Share them with others

     > Pull images for deployment
---
### Types of Docker Registries
**1. Public Registry**

 - Accessible to everyone.

- Example:
```
Docker Hub
https://hub.docker.com
```

**2. Private Registry**

- Restricted access, used inside companies.

- Examples:
~~~
AWS ECR

Azure Container Registry

Google Artifact Registry

Self-hosted Docker Registry
~~~

---

###  Key Concepts

**1. Docker Image:**
 A packaged application with all dependencies.

**2. Repository:** 
A collection of image versions.

   Example:
  ```
  nginx
  myapp/backend
```

**3. Tag:** Version label of an image.

Example:
```
nginx:latest
nginx:1.25
```
---
###
Common Docker Registry Commands  
 
1. Login to Registry:  
 ```docker login```

3. For private registry:   
```docker login myregistry.com```

4. Pull Image from Registry:   
```docker pull nginx:latest```
 
5. Push Image to Registry:   
   Step 1: Tag the image   
   ```docker tag myapp:latest username/myapp:latest```

   Step 2: Push   
   ```docker push username/myapp:latest```

6. Start a local registry container:  
```docker run -d -p 5000:5000 --name registry registry:2```

7. Push image to local registry:   
``` docker push localhost:5000/myapp```

8. Pull image:   
```docker pull localhost:5000/myapp```

