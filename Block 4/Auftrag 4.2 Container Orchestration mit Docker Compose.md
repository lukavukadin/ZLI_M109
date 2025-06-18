# 🐳 Projekt-Dokumentation: Docker Compose mit Flask & Redis


## Ziel des Projekts

Erstellung einer Python-Webanwendung mit Flask und Redis, orchestriert mit Docker Compose.  
Die App zählt, wie oft sie im Browser aufgerufen wurde – der Zähler wird in Redis gespeichert.

---

## Schritt 1 – Projektordner erstellen

```
mkdir ZLI_M109
cd ZLI_M109
```

---

## Schritt 2 – `app.py` erstellen

**Inhalt:**

```import time
import redis
from flask import Flask

app = Flask(__name__)
cache = redis.Redis(host='redis', port=6379)

def get_hit_count():
    retries = 5
    while True:
        try:
            return cache.incr('hits')
        except redis.exceptions.ConnectionError:
            if retries == 0:
                raise
            retries -= 1
            time.sleep(0.5)

@app.route('/')
def hello():
    count = get_hit_count()
    return f'Hello World! I have been seen {count} times.\n'
```


---

## Schritt 3 – `requirements.txt` erstellen

Inhalt:

````
flask
redis
````


---

## Schritt 4 – Dockerfile schreiben

Inhalt:
````
FROM python:3.10-alpine
WORKDIR /code
ENV FLASK_APP=app.py
ENV FLASK_RUN_HOST=0.0.0.0
RUN apk add --no-cache gcc musl-dev linux-headers
COPY requirements.txt requirements.txt
RUN pip install -r requirements.txt
EXPOSE 5000
COPY . .
CMD ["flask", "run", "--debug"]
````


---

## Schritt 5 – `compose.yaml` erstellen

inhalt:

````
services:
  web:
    build: .
    ports:
      - "8000:5000"
    develop:
      watch:
        - action: sync
          path: .
          target: /code
  redis:
    image: "redis:alpine"
````


---

## Schritt 6 – App starten mit Docker Compose

`docker compose up --watch`

---

## Schritt 7 – App im Browser testen

Gehe zu: `http://localhost:8000`

Ergebnis:  `Willkommen! Ich wurde 1 Mal gesehen.`

---

## Schritt 8 – App live aktualisieren (Compose Watch)

Ändere in `app.py` z. B.: `return f'Grüezi! Ich wurde {count} Mal gesehen.\n'`

![[Pasted image 20250618104056.png]]

---

## Schritt 9 – Zusatzbefehle (optional)

|Befehl|Zweck|
|---|---|
|`docker compose ps`|Zeigt laufende Container|
|`docker compose down`|Stoppt alles & löscht Container|
|`docker compose stop`|Stoppt nur (ohne löschen)|
|`docker image ls`|Zeigt deine Docker-Images|

#### 1. Was ist Redis?

**Redis** ist ein **In-Memory Key-Value Store**, der häufig für **Caching**, **Session Management**, **Pub/Sub** und einfache Datenpersistenz verwendet wird.  
In diesem Beispiel speichert Redis den Hit-Counter, also wie oft die Seite aufgerufen wurde.

#### 2. Welche Ports werden genutzt?

| Container | Interner Port | Externer Port (gemappt) | Zweck                         |
| --------- | ------------- | ----------------------- | ----------------------------- |
| Web       | 5000          | 8000                    | Zugriff auf Flask-App via Web |
| Redis     | 6379          | -                       | Kommunikation mit Web-Service |

#### 3. Was ist die Bedeutung von ENV im DOCKERFILE?

 Der Befehl `ENV` wird verwendet, um **Umgebungsvariablen** im Container zu setzen. Diese Variablen können im Container während der Laufzeit verwendet werden.