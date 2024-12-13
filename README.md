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





