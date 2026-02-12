# Docker Volumes & Bind Mounts 
## 1. Docker Volumes

Docker volumes are used to persist container data even after containers stop or restart.

- Managed directly by Docker

- Best option for long-term storage

#### Types of Docker Volumes:
| Type	| Description|  
| --------| ----------|  
| Named Volumes	| Created with a custom name, managed by Docker |   
| Anonymous Volumes	| Auto-created, not meant for long-term persistence |   
| Host Volumes	| Data stored directly on host filesystem |  
| tmpfs Volumes	| Stored in memory, removed when container stops |   

---
#### Benefits of Volumes

✅ Data Persistence  
✅ Easy Backup & Restore  
✅ Cross-platform Support  
✅ Better Security  
✅ Simple Management  

---

### Create a Docker Volume
```
docker volume create <volume_name>
```



### Mount Volume to a Container
```
docker run -v <volume_name>:<container_path> <image_name>
```

You can also use --volume.

---
### When to Use Docker Volumes?

1. Use volumes when you need:

2. Persistent storage across containers

3. Better portability

4. Higher performance

5. More secure container-managed storage

---

## 2. Bind Mounts

- Bind mounts allow sharing files/directories between:

1. Host machine

2. Docker container

Mostly used in development for live code syncing.



### Bind Mount Syntax
```
docker run -v <host_path>:<container_path> <image_name>
```

- Example: Mount local folder into container.
---


### When to Use Bind Mounts?

1. Use bind mounts when you need:

2. Direct access to host files

3. Real-time file synchronization

4. Development environment setup

5. Legacy app integration
