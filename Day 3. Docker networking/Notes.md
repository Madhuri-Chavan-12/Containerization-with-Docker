

# 🌐 Docker Networking 

Docker networking allows containers to:

- Communicate with each other

- Connect to external services

- Stay isolated and secure

Docker provides multiple network modes like Bridge, Host, Overlay, MACVLAN, None.

---

## Networking Concepts  

### Network Drivers

- Control how container networking is implemented.

  Examples:

    i. Bridge

    ii. Overlay

    iii. MACVLAN

### IP Address Management (IPAM)

- Automatically assigns IPs to containers

- Ensures smooth internal communication

### DNS Resolution

- Containers can communicate using names instead of IPs

- Built-in service discovery in user-defined networks

---

## Types of Docker Networks

| Network Type	| Description	| Use Case |   
| --------------| --------------| ---------| 
| Bridge (default)	| Containers communicate on same host	| Local microservices |   
| Host	| Container shares host network stack	| High performance apps |   
| Overlay	| Multi-host networking via Swarm	| Distributed services |   
| MACVLAN	| Container appears as physical device	| Legacy apps |   
| None	| No networking at all	| Fully isolated tasks |   

---

### 1. Bridge Network
- Default Network on Docker Host

- Created automatically as docker0

- Containers get private IPs

- Use Case: Container-to-container communication on same machine



**Advantages over default bridge:**

✅ Custom subnet + gateway  
✅ Automatic DNS resolution  
✅ Better isolation  
✅ Containers can attach/detach dynamically  

**a. Create User-Defined Bridge Network:**    
```
docker network create my-net
```

**b. Custom subnet:**  
```
docker network create \
--subnet=172.16.0.0/16 \
--gateway=172.16.0.1 my-net
```

**c. Inspect network:**
```
docker network inspect my-net
```

---
### 2. Host Network

- No network isolation

- Container uses host’s interface directly

- Faster networking (no NAT)

**a. Run container with host mode:**
```

docker run --network host nginx
```

**b. Swarm service example:**
```
docker service create --network host nginx
```
---

### 3. Overlay Network (Swarm)

- Connects containers across multiple hosts

- Supports encrypted communication

- Used in Docker Swarm

**Key Ports Required:**

i. TCP 2377 (cluster management)

ii. TCP/UDP 7946 (node communication)

iii. UDP 4789 (overlay traffic)

---

### 4. MACVLAN Network

- Assigns unique MAC address to each container

- Container behaves like a real device on LAN

- Use Case: Legacy applications needing direct network access

- Precaution: Limit number of MAC addresses to avoid conflicts.

---

### 5. None Network

- Networking disabled completely

- No eth0 interface

Example:
```

docker run --network none alpine

```
- Use Case: Secure isolated workloads

