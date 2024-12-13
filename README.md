# Docker on Windows

## 1. Installing Docker Desktop

Refer to the official documentation for installation:  
[Install Docker Desktop on Windows](https://docs.docker.com/desktop/setup/install/windows-install/)

---

### **Pre-requisites**:
1. **Open CMD**:
   - Type `wsl`:
     - If it's not installed, run `wsl --install`.
   - Type `winver`:
     - To check the version of your operating system.
2. **Enable WSL (Windows Subsystem for Linux)**:
   - Search for **"Turn Windows features on or off"**.
   - Check the box for **Windows Subsystem for Linux** if it's not already selected.
3. **Check CPU Virtualization**:
   - Press `Ctrl + Shift + Esc` to open **Task Manager**.
   - Navigate to **Performance > CPU** and ensure **Virtualization** is enabled.

---

## 2. Post-Installation Verification

### **Using CMD**:
1. Type `docker`:
   - If Docker is installed, this will display Docker details.
2. Type `docker -v`:
   - This will check the Docker version installed.
3. Run `docker run -it ubuntu`:
   - Installs the Ubuntu image if not already present.

**Example Output**:

C:\Users\Admin>Docker run -it ubuntu
Unable to find image 'ubuntu:latest' locally
latest: Pulling from library/ubuntu
de44b265507a: Download complete
Digest: sha256:80dd3c3b9c6cecb9f1667e9290b3bc61b78c2678c02cbdae5f0fea92cc6734ab
Status: Downloaded newer image for ubuntu:latest

This command will generate an Ubuntu image in Docker Desktop.

---

# Docker Commands

## Common Docker Commands:
1. `docker start {Container_id}`:
   - Starts the specified container.
2. `docker attach {Container_id}`:
   - Opens the container console.
3. `docker container ls`:
   - Lists all running Docker containers.
4. `docker container ls -a`:
   - Lists all containers, including stopped ones.
5. `docker exec -it {image_name} bash`:
   - Executes multiple commands in the specified container from the local desktop.

---

## Port Mapping

### Example:

C:\Users\Admin>docker run -it mailhog/mailhog

output :

```
Unable to find image 'mailhog/mailhog:latest' locally
latest: Pulling from mailhog/mailhog
df20fa9351a1: Download complete
ed8968b2872e: Download complete
f17c8f1adafb: Download complete
368ee3bc1dbb: Download complete
03954754c53a: Download complete
a92cc7c5fd73: Download complete
60493946972a: Download complete
Digest: sha256:8d76a3d4ffa32a3661311944007a415332c4bb855657f4f6c57996405c009bea
Status: Downloaded newer image for mailhog/mailhog:latest
2024/12/12 14:58:57 Using in-memory storage
[HTTP] Binding to address: 0.0.0.0:8025
2024/12/12 14:58:57 Serving under http://0.0.0.0:8025/
2024/12/12 14:58:57 [SMTP] Binding to address: 0.0.0.0:1025
Creating API v1 with WebPath:
Creating API v2 with WebPath:
[APIv1] KEEPALIVE /api/v1/events
```


```
Output shows mailhog/mailhog running on port 1025.
However, accessing localhost:1025 may show an error because the port is not mapped to the local machine.
```

# Solution: Map App Port to Localhost

*Command:
```
docker run -it -p {YOUR_PORT}:{APP_PORT} file_name

Example:
docker run -it -p 6000:9000 xyz/mynodeapp
```


here, 6000 is our port on which we are mapping 9000 port.

# Validation:
```
Open in Browser: localhost:6000
Use Postman: localhost:6000
Note: The container must be in a running state.
```

---


## Building a Docker Image

# Folder Structure:

```
DOCKER_PROJECT/
├── Dockerfile
├── main.py

```

# Dockerfile:
```
FROM python:3.8

ADD main.py .

RUN pip install datetime

CMD [ "python", "./main.py"]

```
Note : the CMD contains should be in double quotes only. Will face issue otherwise.


# main.py

```
from datetime import datetime

print(f'Current date & time: {datetime.now()}')

```
---

## Building the Docker Image:

Open a terminal in the project directory (e.g., VS Code).
Run the following command :

```
docker build -t python_date .
```

* This creates a Docker image named python_date.



