# n8n-local
n8n eseguito in locale

## 3. Avvio
```bash
docker compose up -d
```

Apri nel browser:
```
http://<IP_DEL_NOTEBOOK>:5678
```
*(Oppure `http://localhost:5678` se sei sullo stesso PC.)*

---

## 4. Backup
- Cartella `n8n_data` (config, credenziali, workflow)
- Cartella `pg_data` (database Postgres)
- Oppure dump:
```bash
docker exec -t n8n_db pg_dump -U n8n -d n8n | gzip > backup_n8n.sql.gz
```

**Importante**: mantieni la stessa `N8N_ENCRYPTION_KEY` per poter decifrare le credenziali dopo un ripristino.

---

## 5. Aggiornamento
```bash
docker compose pull n8n
```
Poi:
```bash
docker compose up -d n8n
```

---

## 6. Note
- Funziona su Docker Desktop (Windows/macOS/Linux)
- Usa percorsi relativi per evitare problemi con WSL2
- Se vuoi una versione con SQLite (ancora più semplice), puoi sostituire Postgres con il volume interno di n8n
