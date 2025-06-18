**1. Warum braucht man Container-Orchestrierung?**  
Damit man viele Container automatisch verwalten kann – z. B. starten, stoppen, überwachen oder bei Problemen neu starten. Das spart Aufwand und sorgt für stabile Abläufe, besonders bei großen Anwendungen.

---

**2. Wie funktioniert Container-Orchestrierung?**  
Ein Orchestrierungstool kümmert sich automatisch darum, wo und wie Container laufen. Es verteilt sie sinnvoll auf Server, überwacht ihren Zustand und skaliert sie bei Bedarf hoch oder runter – alles nach definierten Regeln.

---

**3. Welche Container-Orchestrierung Technologien kennen Sie?**

- **Kubernetes** (am weitesten verbreitet)
    
- **Docker Swarm** (einfacher, aber weniger mächtig)
    
- **Apache Mesos** (für sehr große, komplexe Systeme)
    

---

**4. Was versteht man unter horizontaler Skalierung im Kontext von Cloud-Anwendungen?**  
Man startet einfach **mehrere Instanzen** einer Anwendung, um die Last zu verteilen – statt einem großen Server nutzt man viele kleinere. Ideal für hohe Verfügbarkeit und bessere Performance.

---

**5. Was gibt es für Deployment Strategien?**

- **Blue-Green Deployment:** Zwei Versionen, man schaltet einfach um
    
- **Canary Release:** Neue Version wird nur für wenige Nutzer freigegeben
    
- **Rolling Update:** Schrittweise Aktualisierung, ohne Downtime
    
- **Recreate:** Alte Version wird gestoppt, dann neue gestartet (kurze Downtime)