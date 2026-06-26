# Issue: Create ticket with validation

## Request

```txt
Serve creare ticket dal supporto.
```

## Fatti (Facts)

- Siamo in una piccola applicazione js con express.
- Non avrai accesso al codice, siamo in fase di planning.
- L'applicazione contiene un sistema di autenticazione.
- Solo chi è autenticato può creare dei ticket.
- Esiste un DB relazionale che collega autori ai ticket inviati e alle note aggiunte (1 to many).

## Assunzioni (Assumptions)

- Le note non possono contenere solo spazi vuoti.
- Le note non devono avere minimo 100 caratteri.
- Le note non possono superare i 3000 caratteri.
- Le note saranno visualizzate nella stessa pagina del ticket.
- Un ticket può avere più note.
- La nota deve avere obbligatoriamente timestamp e il campo autore (NomeUtente).
- Le note potranno essere visualizzate solo da chi avrà il ruolo denominato "Supporto tecnico", dall'"Admin" e dall'autore stesso della nota.
- In caso di empty-state, visualizza un messaggio di errore e riporta l'utente alla creazione della nota.

## Domande Aperte (Questions)

- E' necessario che i ticket abbiano un sistema di priorità? se la risposta è si, quanti gradi di priorità ci sono?.
- C'è un limite di ticket giornalieri?.
- Possono esserci allegati nel ticket? di quanto è la dimensione massima? quali sono le estensioni dei file accettati e quali non?.

## Decisione (Decision)

Per questo slice, "creare ticket" significa:

```txt
Avere la possibilità di aggiungere una nota più o meno estesa che abbia una flag che ne qualifichi il grado di priorità.
```

## Fuori Scope / Non-Obiettivi (Non-Goals)

- Non creiamo codice.
- No refactoring.
- No modifiche a file che non siano prompt-critica-issue.md.
- Non modificare la UI.
- Non aggiungiamo funzioni oltre a quelle esplicitate.
  
## Criteri Di Accettazione (Acceptance Criteria).

1. La nota che rispetta i parametri assegnati viene visualizzata correttamente e la nota viene aggiunta al database, e deve avere un id univoco e collegato con l'autore e al ticket di appartenenza.
2. La nota che non rispetta i parametri non viene aggiunta al DB e la pagina di rimanda alla pagina dei ticket.
3. La nota non è visibile se non sei loggato

## Piano Di Verifica Manuale (Manual Test Plan)

- Input: Inserimento di una nota corretta. Output: La nota che rispetta i parametri viene visualizzata correttamente e viene inserita nel DB.
- Input: inserimento di una nota non conforme. Output: messaggio di errore e renderizzamento sulla pagina dei ticket
- Input: accesso al ticket senza autenticazione. Output: nessuna nota visibile.
- 
## Note Per L06

- [quale payload andra' chiarito]
- [quale errore andra' chiarito]
- [quale campo dati andra' deciso]
