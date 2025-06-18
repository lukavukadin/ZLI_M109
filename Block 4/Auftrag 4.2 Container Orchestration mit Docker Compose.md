# Auftrag 4.2












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