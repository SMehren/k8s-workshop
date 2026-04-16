# Skript Workshop Kubernetes

## 1. Vorraussetzungen

[Vorraussetzungen des Docker Workshops](https://github.com/SMehren/docker-workshop/blob/main/README.md#1-vorraussetzungen)

### 1.1 Windows

[kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl-windows/)

### 1.2 Mac

[kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl-macos/)

## 2. Installation [k3d](https://k3d.io/stable/)

### 2.1 Windows

#### 2.1.1 Über das Install Skript (Empfohlen)

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

#### 2.1.2 Mit [Chocolatey](https://chocolatey.org/install)

```sh
choco install k3d
```

### 2.2 Mac

#### 2.2.1 Über das Install Skript (Empfohlen)

```sh
curl -s https://raw.githubusercontent.com/k3d-io/k3d/main/install.sh | bash
```

oder

```sh
wget -q -O - https://raw.githubusercontent.com/k3d-io/k3d/main/install.sh | bash
```

#### 2.2.2 Mit [Homebrew](https://brew.sh/)

```sh
brew install k3d
```

## 3. [Workshop](https://kubernetes.io/docs/tutorials/kubernetes-basics/)

### 3.1 Cluster Setup

(Für Windows alle Commands in WSL ausführen)

Docker Desktop ausführen

```sh
k3d cluster create <mycluster>
```

```sh
kubectl get nodes
```

### 3.2 [Eine App Deployen - kubectl und Deployments](https://kubernetes.io/docs/tutorials/kubernetes-basics/deploy-app/deploy-intro/)

### 3.3 [Das Deployment inspizieren - Pods und Nodes](https://kubernetes.io/docs/tutorials/kubernetes-basics/explore/explore-intro/)

### 3.4 [Die App im lokalen Netzwerk veröffentlichen - Netzwerke, Services und Label](https://kubernetes.io/docs/tutorials/kubernetes-basics/expose/expose-intro/)

Hinweis: Da k3d kein wirkliches Cluster aus mehreren Maschinen erstellt und Docker Container vom Host-Netzwerk abgeschottet sind, muss man gewünschte Ports extra freigeben.

Dazu gibt es von k3d eine extra [Anleitung](https://k3d.io/stable/usage/exposing_services/).

Um kein neues Cluster erzeugen zu müssen kann man folgenden Command ausführen um die gewünschten Ports für das Cluster auf dem Host freizugeben:

```sh
k3d node edit k3d-<mycluster>-serverlb --port-add <HostPort>:<ContainerPort>
```

Beispiel

```sh
k3d node edit k3d-mycluster-serverlb --port-add 8080:80
```

### 3.5 [Die App Skalieren - Skalierung und Load Balancing](https://kubernetes.io/docs/tutorials/kubernetes-basics/scale/scale-intro/)

### 3.6 [Die Applikation updaten - Rolling Updates](https://kubernetes.io/docs/tutorials/kubernetes-basics/update/update-intro/)

### 3.7 Bonusaufgaben

Für die Bonusaufgaben ist meist ein Cluster mit mindestens zwei Worker-Nodes (Agents) gefordert.

Um das zu verwirklichen könnt ihr entweder in die Dokumentation von [k3d](https://k3d.io/stable/) schauen, oder ihr folgt der Anleitung.

Zuerst das alte Cluster entfernen

```sh
k3d cluster delete <mycluster>
```

Und dann ein neues HA-Cluster mit 2 Agents starten

```sh
k3d cluster create <mycluster> --servers 3 --agents 2
```

- [PHP Guestbook Applikation mit Redis deployen - Stateless Applications](https://kubernetes.io/docs/tutorials/stateless-application/guestbook/)
- [MySQL und Wordpress mit Persistent Volumes deployen - Stateful Applications](https://kubernetes.io/docs/tutorials/stateful-application/mysql-wordpress-persistent-volume/)
