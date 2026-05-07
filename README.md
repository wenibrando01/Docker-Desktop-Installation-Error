** Docker-Desktop-Installation-Error**

This error means the C:\ProgramData\DockerDesktop folder exists but isn't owned by an Administrator account. Here's how to fix it:
Fix: Reset folder ownership

Open Command Prompt as Administrator (right-click → "Run as administrator")
Run this command:

     takeown /f "C:\ProgramData\DockerDesktop" /r /d y

Then grant full permissions:

     icacls "C:\ProgramData\DockerDesktop" /grant Administrators:F /t

Delete the folder (since it's likely corrupted from a previous install):

     rmdir /s /q "C:\ProgramData\DockerDesktop"

Re-run the Docker Desktop installer as Administrator.



#MANUAL CONFIGURATION

Step 1: Take Ownership of the Folder

Open File Explorer → navigate to C:\ProgramData

(If you don't see it, enable hidden folders: View → Show → Hidden items)


Right-click DockerDesktop folder → Properties
Go to Security tab → click Advanced
At the top next to Owner, click Change
Type Administrators → click Check Names → OK
Check "Replace owner on subcontainers and objects" → Apply → OK


Step 2: Grant Full Permissions

Still in Security tab → click Edit
Select Administrators → check Full Control → Apply → OK


**Enable Virtualization on Windows**
 1. 
 
     https://support.microsoft.com/en-gb/windows/enable-virtualization-on-windows-c5578302-6e43-4b4b-a449-8ced115f58e1
2.


        dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart
4.


        dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all /norestart
6.


        dism.exe /online /enable-feature /featurename:Microsoft-Hyper-V-All /all /norestart
Then restart your PC.

**Docker Commands**

1. Check Docker version
   
          docker --version

Purpose:
Shows installed Docker version.

📌 2. Test Docker installation

     docker run hello-world

Purpose:
Runs a test container to confirm Docker is working properly.

📌 3. List running containers

     docker ps

Purpose:
Shows currently running containers.

📌 4. List all containers (including stopped)

     docker ps -a

Purpose:
Shows all containers on your system.

📌 5. List downloaded images

     docker images

Purpose:
Shows all Docker images stored locally.

📌 6. Pull an image from Docker Hub

     docker pull ubuntu

Purpose:
Downloads an image (example: Ubuntu Linux).

📌 7. Run a container

     docker run ubuntu

Purpose:
Creates and starts a container from an image.

📌 8. Run container interactively (terminal mode)

     docker run -it ubuntu bash

Purpose:
Opens a Linux terminal inside the container.

📌 9. Stop a container

     docker stop container_id

Purpose:
Stops a running container.

📌 10. Remove a container

     docker rm container_id

Purpose:
Deletes a stopped container.

📌 11. Remove an image

     docker rmi image_name

Purpose:
Deletes a Docker image.

📌 12. View system info

     docker info

Purpose:
Shows system-level Docker configuration.

📌 13. Clean unused data

     docker system prune

Purpose:
Removes unused containers, images, and cache to free space.

📌 14. Force clean everything unused

     docker system prune -a

Purpose:
Removes ALL unused images + containers (more aggressive cleanup).

📌 15. View logs of a container

     docker logs container_id

Purpose:
Shows output/logs of a container.

