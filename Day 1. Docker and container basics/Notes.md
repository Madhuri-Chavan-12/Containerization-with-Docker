# 🐳 1. Docker 

- Docker is an open-source containerization platform that helps developers build, ship, and run applications in isolated environments called containers.

- It ensures the app runs the same in development, testing, and production.

## Key Components of Docker:
**1. Docker Engine:**   
   - Core software that enables containerization

  -  Builds, runs, and manages containers

**2. Images & Containers:**

- Image → Read-only template containing app + dependencies

- Container → Running instance of an image

**3. Storage & Volumes**

- Containers are temporary, so Docker provides volumes

- Volumes store data outside containers so it persists after restarts

**4. Docker Compose & Hub**

- Docker Compose → Manage multi-container apps using docker-compose.yml

- Docker Hub → Cloud registry to store and share Docker images

**5. Networking & Registry**

- Docker networks allow containers to communicate securely

- Registries store and distribute images (public or private)
---

### Why Use Docker?

**1. ✅ Consistency Across Environments:**

   - Works the same everywhere

**2. ⚡ Rapid Deployment:**

- Containers start in seconds

**3. 🧩 Microservices Friendly:**

- Each service runs independently

**4.📈 Scalable:**

- Easy to replicate containers based on load
---

### Business Use Cases

* Healthcare → Secure patient data & reproducible environments

* IT Industry → Fast development/testing setup

* Finance → Compliance + secure microservices

* Retail → Handle traffic spikes + ML personalization

* Telecom → Network virtualization & cost reduction
---

### Docker Architecture 
<img width="1019" height="543" alt="image" src="https://github.com/user-attachments/assets/e7ace404-3654-4693-a8fb-0500493a466c" />


**1. Docker Client** → Runs commands like docker build, docker run.

**2. Docker Host (Daemon)** → Builds & manages containers/images.

**3. Docker Registry** → Stores images (Docker Hub).

---


### Workflow Commands
- **docker build** --->     Builds an image from a Dockerfile

- **docker pull**
 ---> Downloads an image from registry

- **docker run**
---> Creates and starts a container from an image
---

### Docker Architecture Components  
| Component	| Description  |   
| ----------| -------------|   
| Client	| Interface for user commands |    
| Daemon	| Runs containers, builds images  |   
| Host	    | Machine running Docker daemon  |   
| Registry	| Stores and shares Docker images  |   
| Networks	| Connect containers securely  |   
| Storage	| Volumes/bind mounts for persistence  |  

--- 
## 2. Docker  Engine 

Docker Engine provides the base containerization technology and ensures platform-independent execution of applications.

---
## 3. Docker Image

- A Docker image is a read-only template used to create containers.

 - Contains application code + dependencies

- Works like a snapshot in Virtual Machines

- Built using a Dockerfile
---

### Docker Image Workflow
~~~
- Dockerfile  →  Image  →  Container
~~~

- docker build creates an image

- docker run creates + starts a container from the image
---
### Parts of a Docker Image
**1. Base Image:**
 
- First layer of an image

- Can be built from scratch

**2. Parent Image:**

- Reused foundation image (e.g., Ubuntu, Node)

**3. Layers:**

- Each instruction adds a new layer

- Helps in caching and efficiency

**4. Container Layer:**

- Writable layer added when container runs

- Used for runtime changes

**5. Docker Manifest:**

- JSON file describing image metadata
---
### Dockerfile

- A Dockerfile is a text file containing instructions to build an image.

Build Command
~~~
docker build .
~~~

- . represents the build context (current directory files)
---
## 4. Docker Container

- A Docker container is a running instance of an image.

- Lightweight and isolated process

- Has its own filesystem, networking, and process space

- Runs consistently across environments

- Running a Container
~~~
docker run <image-name>
~~~



### Container Lifecycle States
| State	|  Description |   
| -----------| ----------| 
| Created	| Container exists but not started|  
| Running	| Container processes are active|  
| Paused	| Processes temporarily stopped|  
| Stopped	| Container execution ended|  
| Deleted	| Container removed completely|  

---


### Important Container Commands
**1. Create Container:**
~~~
docker create --name <container-name> <image-name>
~~~
**2. Start Container:**
~~~
docker start <container-name>
~~~

**3. Run (Create + Start Together):**
~~~
docker run -it --name <container-name> <image-name>
~~~~

**4. Pause Container:**
~~~
docker pause <container-name>
~~~

**5. Stop Container:**
~~~
docker stop <container-name>
~~~

**6. Remove All Containers:**
~~~
docker rm $(docker container ps -a)
~~~
