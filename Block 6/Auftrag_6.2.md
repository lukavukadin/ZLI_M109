# ✅ Auftrag 6.2 – HTML-Seite auf OpenShift deployen

## 📌 Ziel

Eine eigene HTML-Seite mit Docker containerisieren, auf **GitHub Container Registry (GHCR)** pushen und in **OpenShift** via **Route** öffentlich verfügbar machen.

---

## 📁 Projektstruktur

plaintext

KopierenBearbeiten

`html-openshift-app/ ├── index.html ├── dockerfile.nginx ├── deployment.yaml ├── service.yaml └── route.yaml`

---

## ⚙️ Docker: Build und Push

### 🐳 Dockerfile (`dockerfile.nginx`)

Dockerfile

KopierenBearbeiten

`FROM nginxinc/nginx-unprivileged COPY index.html /usr/share/nginx/html/index.html`

### 🔨 Build

bash

KopierenBearbeiten

`docker build -t ghcr.io/lukavukadin/html-openshift-app:v2 -f dockerfile.nginx .`

### 🚀 Push

bash

KopierenBearbeiten

`docker push ghcr.io/lukavukadin/html-openshift-app:v2`

---

## 🔐 GHCR Zugriff mit Secret

Da GHCR-Images standardmäßig **privat** sind, wird ein **`imagePullSecret`** benötigt.

### 🛡️ Secret erstellen

bash

KopierenBearbeiten

`oc create secret docker-registry ghcr-secret \   --docker-server=ghcr.io \   --docker-username=lukavukadin \   --docker-password=<GITHUB_TOKEN> \   --docker-email=none@example.com`

> ⚠️ **Hinweis:** Dein GitHub Token braucht mindestens die Berechtigung `read:packages`.

---

## 🛠️ OpenShift Konfigurationen

### 📄 `deployment.yaml`

yaml

KopierenBearbeiten

`apiVersion: apps/v1 kind: Deployment metadata:   name: html-openshift-app   labels:     app: html-openshift-app spec:   replicas: 1   selector:     matchLabels:       app: html-openshift-app   template:     metadata:       labels:         app: html-openshift-app     spec:       containers:         - name: html-openshift-app           image: ghcr.io/lukavukadin/html-openshift-app:v2           ports:             - containerPort: 8080           imagePullPolicy: Always       imagePullSecrets:         - name: ghcr-secret`

bash

KopierenBearbeiten

`oc apply -f deployment.yaml`

---

### 📄 `service.yaml`

yaml

KopierenBearbeiten

`apiVersion: v1 kind: Service metadata:   name: html-openshift-app   labels:     app: html-openshift-app spec:   ports:     - name: http       protocol: TCP       port: 8080       targetPort: 8080   selector:     app: html-openshift-app`

bash

KopierenBearbeiten

`oc apply -f service.yaml`

---

### 🌐 `route.yaml`

yaml

KopierenBearbeiten

`apiVersion: route.openshift.io/v1 kind: Route metadata:   name: html-openshift-app   labels:     app: html-openshift-app spec:   to:     kind: Service     name: html-openshift-app   port:     targetPort: http   tls:     termination: edge     insecureEdgeTerminationPolicy: Redirect`

bash

KopierenBearbeiten

`oc apply -f route.yaml`

---

## ✅ Kontrolle

### 🔍 Pods prüfen

bash

KopierenBearbeiten

`oc get pods # → STATUS: Running`

### 🔗 Route anzeigen

bash

KopierenBearbeiten

`oc get routes # → Liefert dir die öffentliche URL zur App`

---

## 🌍 Ergebnis im Browser

Beispiel-Link:

arduino

KopierenBearbeiten

`https://html-openshift-app-254201-zlic-lvukadin1.apps.exoscale-ch-gva-2-0.appuio.cloud`

**Inhalt der Seite:**

KopierenBearbeiten

`Willkommen! ZLI GOATED`