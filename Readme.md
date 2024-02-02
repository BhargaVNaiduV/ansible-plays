# Ansible with Lightweight Docker Containers
Testing chnages made in Git bash
This repository provides a setup for practicing Ansible using lightweight Docker containers. The goal is to create a simple environment with an Ansible master and two Ansible hosts.

## Steps to Set Up the Environment

### 1. Create Docker Network

```bash
docker network create ansible_net


Create Ansible Master Container

docker run -itd --name ansible-master --network ansible_net alpine
docker exec -it ansible-master apk add ansible


Create Ansible Host Containers


docker run -itd --name ansible-host1 --network ansible_net alpine
docker run -itd --name ansible-host2 --network ansible_net alpine
docker exec -it ansible-host1 apk add python3
docker exec -it ansible-host2 apk add python3


. Configure SSH in Ansible Master Container

docker exec -it ansible-master ssh-keygen -t rsa
docker exec -it ansible-master ssh-copy-id root@ansible-host1
docker exec -it ansible-master ssh-copy-id root@ansible-host2


Advantages of Using Lightweight Docker Images:

1. Reduced Image Size:
   - Smaller sizes lead to faster download times and reduced storage requirements.

2. Faster Deployment:
   - Smaller images result in faster container deployment, improving application startup time.

3. Resource Efficiency:
   - Lightweight images consume fewer system resources, making them suitable for resource-constrained environments.

4. Security:
   - Minimalistic images have fewer unnecessary components, reducing the potential attack surface and enhancing security.

5. Easier Distribution:
   - Smaller images are quicker to push and pull, simplifying the distribution process, especially in CI/CD pipelines.

6. Optimized Build Times:
   - The use of lightweight base images can significantly speed up the Docker image build process.
