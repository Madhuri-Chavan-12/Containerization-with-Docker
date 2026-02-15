# 📌 Multistage Docker 

- Multistage Docker build is a technique where you use multiple stages inside a single Dockerfile.

- Each stage has a specific purpose:

    i. Build Stage → Used to compile/build the application

     ii. Runtime Stage → Used to run the final app with only required files

- This helps create smaller, cleaner, and production-ready Docker images.
- Multistage Docker builds are an industry best practice for creating efficient, lightweight, and secure Docker images.
- They are especially useful for production deployments.

---
### Why Multistage Builds are Useful?

- Without multistage builds, Docker images often include unnecessary things like:

    i. Build tools

   ii. Source code

  iii. Dependencies only needed during compilation

- Multistage builds solve this by copying only the final output into the runtime image.

**Key Benefits:**

✅ Smaller image size  
✅ Faster deployment  
✅ Better security  
✅ Cleaner production containers  

---

### Multistage Dockerfile (Optimized)
```
# Stage 1: Build Stage
FROM node:18 AS builder

WORKDIR /app
COPY . .

RUN npm install
RUN npm run build


# Stage 2: Runtime Stage
FROM node:18-slim

WORKDIR /app

COPY --from=builder /app/dist ./dist

CMD ["node", "dist/index.js"]
```

**How It Works**  
- Stage 1: Builder

   -> Installs dependencies

   -> Builds the project

   -> Produces compiled output

- Stage 2: Runtime

  -> Starts with a lightweight base image

  -> Copies only the build output from Stage 1

  -> Runs the final application

---
### Summary Table
| Feature	| Normal Build	| Multistage Build |   
|--------|----------------|------------------|
| Image Size	| Large	| Small |   
| Extra Build Tools Included	| Yes	| No |   
| Production Ready	| Not Ideal	| Best Practice |   
| Security	| Lower	| Higher |   

---

# 📌 Distroless Docker Images 
- A distroless Docker image is a minimal container image that contains only what is required to run an application.

- Distroless images are a powerful approach for building lightweight, secure, production-ready containers.
They are best used together with multistage Docker builds.

- Unlike traditional base images (Ubuntu, Alpine, Debian), distroless images do not include:

   1. Shell (sh, bash)

   2. Package managers (apt, apk)

   3. Debugging tools (curl, ps, ls)

   4. Extra operating system utilities

- They contain only:

  ✅ Application runtime  
  ✅ Required libraries  
  ✅ Minimal dependencies  

---
### Why are Distroless Images Used?

- Distroless images are mainly used in production environments to create cleaner and more secure containers.

**1. Smaller Image Size**

   - Since unnecessary OS tools are removed, the image becomes lightweight.

  **2. Improved Security**

- Fewer installed tools means a smaller attack surface.

- Even if an attacker gains access, they cannot easily run commands like:

    -- bash

    -- curl

    -- apt install

**3. Production Best Practice**

- Distroless images are widely used in Kubernetes and enterprise deployments.

---
### Distroless vs Traditional Images


| Feature	| Traditional Images	| Distroless Images|   
| ----------| --------------------| -------------------|   
| Shell Access	| Yes	| No|   
| Package Manager	| Yes	| No|   
| Debugging Tools	| Included	| Not Included|   
| Image Size	L| arger	| Smaller|   
| Security	| Moderate	| Higher|   
| Production Use	| Common	| Best Practice|   

---
### Example Distroless Base Images


1. gcr.io/distroless/java17

2. gcr.io/distroless/python3

3. gcr.io/distroless/static

---
### Example: Distroless with Multistage Build (Java)
```
# Stage 1: Build Stage
FROM openjdk:17 AS builder

WORKDIR /app
COPY . .
RUN ./mvnw package


# Stage 2: Distroless Runtime Stage
FROM gcr.io/distroless/java17

COPY --from=builder /app/target/app.jar app.jar

CMD ["app.jar"]

```

Explanation

- Stage 1 builds the application using full build tools

- Stage 2 runs the application using a minimal distroless runtime

---

**Important Limitation**

Distroless images do not contain a shell, so this will not work:

```
docker exec -it <container> sh
```

This makes debugging harder compared to normal images.

---
### When to Use Distroless Images?

- Production deployments

- Secure environments

- Microservices running in Kubernetes






