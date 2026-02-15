# RUN vs CMD vs ENTRYPOINT

## 1. RUN Instruction

- RUN executes commands at build time.

- It is mainly used to Install packages, Download dependencies, Configure the environment

- The result is stored permanently in the Docker image.

- Example: Installing curl
```
# Use an official Ubuntu base image
FROM ubuntu:20.04

# Update repository and install curl
RUN apt-get update && apt-get install -y curl

# Print curl version during build
RUN curl --version
```
**Key Points:**

- Runs only when building the image (docker build)

- Creates a new image layer

- Output becomes part of the final image

---

## 2. CMD Instruction

- CMD specifies the default command that runs when the container starts.

- It can be overridden when you run the container manually.  

- Example: Default command to show curl version
```
# Use Ubuntu base image
FROM ubuntu:20.04

# Install curl
RUN apt-get update && apt-get install -y curl

# Default command when container starts
CMD ["curl", "--version"]
```
- Override Example
```
docker run myimage echo "Hello"
```

This replaces the CMD command.

**Key Points:**

- Runs at container startup, not build time

- Only the last CMD is used

- Easy to override

---

## 3. ENTRYPOINT Instruction

- ENTRYPOINT defines the main executable of the container.

- Unlike CMD, it is not easily overridden.

- It makes the container behave like a fixed command-line tool.

- Example: Container behaves like curl
```
# Use Ubuntu base image
FROM ubuntu:20.04

# Install curl
RUN apt-get update && apt-get install -y curl

# Set curl as main executable
ENTRYPOINT ["curl"]
```
- Usage Example
```
docker run myimage https://example.com
```

- This runs:
```
curl https://example.com
```

**Key Points:**

- Container becomes an executable tool

- Arguments can be passed dynamically

- Harder to override than CMD
---

### CMD vs ENTRYPOINT 

| Feature	|  CMD	|  ENTRYPOINT |   
| ---------| -------| ------------|   
| Purpose	| Default command	| Fixed executable|   
| Override possible?	| Yes	| Not easily|   
| Best use	| Default behavior	| Tool-like containers|   
| Arguments support	| Limited	| Strong |   

---

###  ENTRYPOINT + CMD Together

You can combine both:

```
ENTRYPOINT ["curl"]
CMD ["--version"]
```

Now:

- Default runs curl --version
- User can override arguments:
```
docker run myimage https://google.com
```

Runs:
```
curl https://google.com
```
---
### Summary 

- Use RUN to build the image

- Use CMD for default startup behavior

- Use ENTRYPOINT when the container should act like a tool
