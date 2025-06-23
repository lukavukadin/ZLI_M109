# Test_2 – Lösungen

  
---
 

**Gegeben ist folgendes Szenario:**  

Sie konnten alle Teile der Applikation auf OpenShift deployen. In der Webkonsole wird sehen Sie aber, dass etwas nicht stimmt.

  

- Fehlerursache – `oc logs` oder Webkonsole zur Fehlersuche  

- ContainerPort ≠ Service-Port ist häufige Ursache  

- `BACKEND_URL` muss erreichbar sein  

- Fehler finden –> Falscher Port im Service oder Route  

- **Lösung –> Deployment-Config, Env setzen, Logs fixen, Image prüfen**

  

---


**Gegeben ist folgendes Szenario:**  

Sie konnten alle Teile der Applikation auf OpenShift deployen. Beim Zugriff auf das Frontend erhalten Sie die folgende Fehlermeldung.

  

- Fehlerursache –> Frontend verweist auf `localhost`, was im Cluster nicht auf das Backend zeigt  

- Fehler finden –> Netzwerk-Tab in DevTools → falsche URL → lokale Adresse  

- **Lösung –>`BACKEND_URL` korrekt setzen im Deployment des Frontends**

  

---


**Die Applikation ist ein voller Erfolg und die Nutzerzahlen steigen schnell.**  

Wie könnte man dem Ansturm schnell gerecht werden?  
Welche Kubernetes Ressource können Sie einsetzen?

  

- **`HorizontalPodAutoscaler` → Kubernetes Ressource**  

- Er sorgt dynamisch für ausreichend Rechenleistung, ohne dass du manuell eingreifen musst.

  

---


**Wie können mit der Commandline alle laufenden Pods angezeigt werden?**

  

- `kubectl get pods`

  

---


**Wie können mit der Commandline alle laufenden Pods angezeigt werden?**

  

- `kubectl apply -f .`

  

---


**Vervollständigen Sie das Manifest für den Service des Frontends**

  

```yaml

kind: Service

selector:

  app: counter-frontend

```

  

---


**Vervollständigen Sie das Manifest für das Route des Frontends**

  

```yaml

kind: Route

to:

  kind: Service

insecureEdgeTerminationPolicy: Redirect

```

  

---

  
**Vervollständigen Sie das Manifest für das Deployment des Backends**

  

```yaml

kind: Deployment

matchLabels:

  app: counter-backend

name: counter-backend

env:

  - name: DB_NAME

```

  

---

**Das Frontend kann von außen via HTTP angesprochen werden.**  

Auf welchem Port kommen die HTTP Anfragen im Container an?

  

- port 80

  

---

**Das Backend kann von außen via HTTP angesprochen werden.**  

Auf welchem Port kommen die HTTP Anfragen im Container an?

  

- port 3000

  

---

**Wählen Sie die Resource aus, welche die HTTP Requests von innerhalb des Clusters an die Pods des Frontends verteilt.**

  

- Frontend Service

  

---

**Wählen Sie die Resource aus, welche die HTTP Requests innerhalb des Clusters an die Pods des Backends verteilt.**

  

- Backend Service

  

---

**Wählen Sie die Resource aus, welche die SQL Queries von innerhalb des Clusters an die Pods der Datenbank verteilt.**

  

- Database Service

  

---


**Wählen Sie die Resource aus, welche die Pods des Frontends verwaltet**

  

- Frontend Deployment

  

---


**Wählen Sie die Resource aus, welche die Pods des Backends verwaltet**

  

- Backend Deployment

  

---
 

**Wählen Sie die Resource aus, welche die HTTP Requests von außerhalb des Clusters (z. B. vom User) entgegen nimmt und im Cluster ans Frontend weitergibt.**

  

- Frontend Route

  

---


**Wählen Sie die Resource aus, welche die HTTP Requests von außerhalb des Clusters (z. B. vom User) entgegennimmt und im Cluster ans Backend weitergibt.**

  

- Backend Route

  

---


**Wählen Sie die Resource aus, welche die Information enthält, unter welchem externen URL das Frontend das Backend erreichen kann**

  

- Frontend Deployment

  

---


**Wählen Sie die Resource aus, welche die Credentials für den Zugriff auf die Datenbank beinhaltet, z. B. damit das Backend auf die Datenbank zugreifen kann.**

  

- database Secret

  

---


**Ordnen Sie zu, welche Technologie am jeweiligen Ort eingesetzt wird:**

  

- Frontend: React  

- Backend: NodeJS  

- Datenbank: Postgres  

- Container Orchestration: OpenShift (Kubernetes)

  

---


**Ordnen Sie zu, welche Programmier- bzw. Abfragesprache am jeweiligen Ort eingesetzt wird:**

  
- JavaScript  

- JavaScript  

- SQL

  

---


**Beschreiben Sie in mindestens 3 Sätzen, welchen Zweck die Applikation verfolgt, was man damit genau machen kann und wer die Nutzer sein könnten.**


- Applikation zählt Ereignisse oder Aktionen und zeigt die Zählung in Echtzeit an.  

- Nutzer können die Zählung starten oder zurücksetzen.  

- Sie eignet sich für Veranstaltungen, Konferenzen oder Organisationen, die Zählungen durchführen müssen.

  

---

**Bringen Sie die Tiers in die Reihenfolge, in welcher der HTTP-Request bei den einzelnen Teilen der Applikation «ankommt»:**

  

1. Browser  

2. Frontend  

3. Backend  

4. Datenbank