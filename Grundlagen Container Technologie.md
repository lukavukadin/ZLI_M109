
### ✅ **Was ist Container-Technologie oder Container-Virtualisierung?**

- Leichtgewichtige Virtualisierung auf Betriebssystemebene
    
- Mehrere isolierte Anwendungen (Container) laufen auf demselben Kernel
    
- Container enthalten alle nötigen Abhängigkeiten (Code, Bibliotheken usw.)
    
- Beliebte Plattform: **Docker**
    

---

### ✅ **Vor- und Nachteile der Container-Technologie zu virtuellen Servern (VM)**

**Vorteile:**

- **Schnellere Bereitstellung**
    
- **Geringerer Ressourcenverbrauch**
    
- **Bessere Portabilität** (läuft überall, wo Docker/Container Engine läuft)
    
- **Skalierbarkeit** (ideal für Microservices und Cloud-Umgebungen)
    

**Nachteile:**

- **Geringere Isolation** (teilen denselben Kernel)
    
- **Sicherheitsrisiken** bei falscher Konfiguration
    
- **Komplexere Orchestrierung** bei vielen Containern (z. B. Kubernetes notwendig)
    

---

### ✅ **Produkte im Zusammenhang mit virtuellen Servern und Containern**

**Virtuelle Server (VM):**

- VMware vSphere
    
- Microsoft Hyper-V
    
- Oracle VirtualBox
    
- KVM (Kernel-based Virtual Machine)
    

**Container-Technologie:**

- Docker
    
- Podman
    
- Kubernetes (Orchestrierung)
    
- OpenShift
    
- Docker Compose
    

---

### ✅ **Unterschiede zwischen VM und Container in Bezug auf …**

|Aspekt|Virtuelle Maschine (VM)|Container|
|---|---|---|
|**Bereitstellung**|Minuten bis Stunden|Sekunden|
|**Speicherplatz**|Groß (inkl. ganzes OS)|Klein (nur App + Abhängigkeiten)|
|**Portabilität**|Eingeschränkt (hardwareabhängig)|Hoch (plattformunabhängig)|
|**Effizienz**|Ressourcenintensiver|Leichtgewichtig, effizienter|
|**OS (Kernel)**|Jedes VM hat eigenes Betriebssystem|Gemeinsamer Kernel des Host-Systems|

---

### ✅ **Können virtuelle Server immer durch Container ersetzt werden?**

- **Nein**, nicht immer geeignet
    
    - Wenn vollständige Isolation erforderlich ist
        
    - Wenn unterschiedliche Betriebssysteme nötig sind
        
    - Wenn ältere monolithische Anwendungen laufen
        

---

### ✅ **Unterschied: Self-Managed vs. Fully Managed**

| Merkmal          | Self-Managed                         | Fully Managed                     |
| ---------------- | ------------------------------------ | --------------------------------- |
| **Verwaltung**   | Nutzer ist selbst verantwortlich     | Provider übernimmt die Verwaltung |
| **Flexibilität** | Höher, mehr Kontrolle                | Weniger Kontrolle, standardisiert |
| **Wartung**      | Selbst Updates, Backups usw.         | Automatisch vom Anbieter          |
| **Komplexität**  | Höher, mehr technisches Wissen nötig | Einfach, oft über Weboberfläche   |
| **Kosten**       | Günstiger, aber zeitaufwändiger      | Teurer, aber zeitsparend          |
|                  |                                      |                                   |