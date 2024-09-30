# Learn to use Kubernetes, Docker, Minikube and Kubectl

## Launch your AWS instance with following preferences:
- Ubuntu OS
- t2.xlarge (16GB ram)
- 50 GB storage
- HTTP/HTTPS and All traffic (anywhere) enabled

### Now open your instance in PuTTY and follow the following commands.

## Installing Docker, Minikube and Kubectl

### 1. Install Docker:

```bash
curl -sL https://github.com/ShubhamTatvamasi/docker-install/raw/master/docker-install.sh | bash
```

- Use the following commands:

```bash
sudo usermod -aG docker $USER
```

- ↑ The command `sudo usermod -aG docker $USER` is used to add the current user to the docker group.


```bash
newgrp docker
```
- ↑ The `newgrp docker` command is used to switch the current group of the active shell to the docker group without having to log out and log back in.


### 2. Installing Kubectl:

```bash
sudo snap install kubectl --classic
```

- Check Kubectl version:

```bash
kubectl version --client
```

### 3. Installing Minikube:

```bash
curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
```

```bash
sudo install minikube-linux-amd64 /usr/local/bin/minikube
```

- Check Minikube version:

```bash
minikube version
```

## Now that we have Minikube installed, let’s start a Minikube cluster using the Docker driver:

```bash
minikube start --driver=docker
```

- Check Minikube status:
```bash
minikube status
```

```bash
kubectl cluster-info
```

```bash
kubectl config view
```

```bash
kubectl get nodes
```

```bash
kubectl get pods
```

```bash
minikube dashboard
```
<br>

## Let’s deploy a simple Nginx web server using kubectl:

```bash
kubectl create deployment nginx-web --image=nginx
```

```bash
kubectl expose deployment nginx-web --type NodePort --port=80
```

```bash
kubectl get deployment,pod,svc
```

## Managing Minikube Addons

```bash
minikube addons list
```

```bash
minikube addons enable dashboard
```

```bash
minikube addons enable ingress
```

- The following command will give you a link for your dashboard:

```bash
minikube dashboard --url
```

```bash
kubectl proxy --address='0.0.0.0' --disable-filter=true &
```

```bash
http://server_ip:8001/api/v1/namespaces/kubernetes-dashboard/services/http:kubernetes-dashboard:/proxy/
```
- ↑ In your browser replace `server_ip` with public ip
