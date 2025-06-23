# Projektbeschreibung und technische Fragen zur Counter-App

---

## 🧾 Allgemeine Beschreibung

### Frage 1  
**Was ist der Zweck der Applikation? Was kann man damit machen? Wer nutzt sie?**

**Antwort:**  
Die „Counter-App“ ist eine digitale Lösung zur Ablösung papierbasierter Zählprozesse. Sie ermöglicht es den Nutzern, Zählvorgänge zu erstellen, Messungen durchzuführen und Ergebnisse zu speichern. Zielgruppen sind Mitarbeitende in Lagerverwaltung, bei Inventuren oder Veranstaltungen, die regelmäßig Bestände oder Teilnehmerzahlen erfassen.

---

## 🧑‍💻 Technologien und Sprachen

### Frage 2  
**Welche Programmiersprachen oder Abfragesprachen werden verwendet?**  
- **Frontend:** JavaScript  
- **Backend:** JavaScript  
- **Datenbank:** SQL  

### Frage 3  
**Welche Technologien werden verwendet?**  
- **Frontend:** React  
- **Backend:** NodeJS  
- **Datenbank:** Postgres  
- **Container Orchestration:** OpenShift (Kubernetes)

---

## 🔐 Ressourcen und Infrastruktur

### Frage 5  
**Wo befinden sich die Credentials für den Datenbankzugriff?**  
- **Antwort:** `Database` oder `Backend Secret`

### Frage 6  
**Wo steht die URL, unter der das Frontend das Backend erreichen kann?**  
- **Antwort:** `Frontend Deployment`

### Frage 7  
**Welche Resource empfängt externe HTTP-Requests und leitet sie ans Backend weiter?**  
- **Antwort:** `Backend Route`

### Frage 8  
**Welche Resource empfängt externe HTTP-Requests und leitet sie ans Frontend weiter?**  
- **Antwort:** `Frontend Route`

---

## 🔄 Interne Kommunikation

### Frage 9  
**Welche Resource verteilt SQL-Queries an die Datenbank-Pods?**  
- **Antwort:** `Database Service`

### Frage 10  
**Welche Resource verteilt interne HTTP-Requests ans Backend?**  
- **Antwort:** `Backend Service`

### Frage 11  
**Welche Resource verteilt interne HTTP-Requests ans Frontend?**  
- **Antwort:** `Frontend Service`

---

## 🧩 Pod- und Deployment-Verwaltung

### Frage 12  
**Welche Resource verwaltet die Pods des Backends?**  
- **Antwort:** `Backend Deployment`

### Frage 13  
**Welche Resource verwaltet die Pods des Frontends?**  
- **Antwort:** `Frontend Deployment`

---

## 🌐 Netzwerk und Ports

### Frage 14  
**Auf welchem Port empfängt das Backend HTTP-Anfragen?**  
- **Antwort:** `Port 8080`

### Frage 15  
**Auf welchem Port empfängt das Frontend HTTP-Anfragen?**  
- **Antwort:** `Port 3000`

---

## 📄 YAML-Manifest-Vervollständigung

### Frage 16  
**Manifest für das Backend-Deployment:**  
- `kind`: Deployment  
- `matchLabels key`: app  
- `matchLabels value`: counter-backend  
- `DB_USER Secret`: counter-database  
- `DB_NAME Environment Variable`: DB_NAME  

### Frage 17  
**Manifest für die Route des Frontends:**  
- `kind`: Route  
- `to.kind`: Service  
- `insecureEdgeTerminationPolicy`: Redirect  

### Frage 18  
**Manifest für den Frontend-Service:**  
- `kind`: Service  
- `selector key`: app  
- `selector value`: counter-frontend  

---

## 💻 OpenShift CLI Befehle

### Frage 19  

**Alle laufenden Pods anzeigen:**  
```bash
oc get pods
```


### Frage 20  

**Alle YAML-Dateien im aktuellen Verzeichnis in den Cluster laden:**

```
oc apply -f .
```
