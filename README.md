# Skript Workshop Kubernetes

## 1. Vorraussetzungen

[Vorraussetzungen des Docker Workshops](https://github.com/SMehren/docker-workshop/blob/main/README.md#1-vorraussetzungen)

### 1.1 Windows

[kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl-windows/)

### 1.2 Mac

[kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl-macos/)

## 2. Installation

### 2.1 Windows

WSL Ausführen

```sh
wsl
```

In WSL k3d installieren

```sh
curl -s https://raw.githubusercontent.com/k3d-io/k3d/main/install.sh | bash
```

oder

```sh
wget -q -O - https://raw.githubusercontent.com/k3d-io/k3d/main/install.sh | bash
```

### 2.2 Mac

```sh
curl -s https://raw.githubusercontent.com/k3d-io/k3d/main/install.sh | bash
```

oder

```sh
wget -q -O - https://raw.githubusercontent.com/k3d-io/k3d/main/install.sh | bash
```

## 3. Cluster Setup

(Für Windows alle Commands in WSL ausführen)

Docker Desktop ausführen

```sh
k3d cluster create <mycluster>
```

```sh
kubectl get nodes
```

## 5. [Workshop](https://kubernetes.io/docs/tutorials/kubernetes-basics/)

### 5.1

## 6. Abschluss- / Bonusaufgaben

TODO
