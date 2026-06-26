# Issue: Create ticket with validation

## Request

```txt
Serve creare ticket dal supporto.
```

## Fatti (Facts)

- Siamo in una piccola applicazione js con express
- Non avrai accesso al codice, siamo in fase di planning
- I ticket hanno un ID univoco
- L'applicazione contiene un sistema di autenticazione
- Solo chi è autenticato può aggiungere nuovi ticket
- Abbiamo un Database che collega autori ai ticket inviati e alle note aggiunte in una relazione One to Many


## Assunzioni (Assumptions)

- I ticket non possono essere vuoti quindi una nota con solo spazi non può essere considerata valida.
- I ticket non devono avere meno di 100 caratteri e non possono superare i 3000
- Il ticket deve avere un timestamp e il campo autore (obbiligatorio) che sarà il nome utente 
- In caso di empty-state visualizza un messaggio d'errore e riporta l'utente alla creazione del ticket

## Domande Aperte (Questions)

- È necessario che i ticket abbiano un sistema di priorità? Se sì quanti gradi di priorità ci sono?
- C'è un limite di ticket giornalieri? 


## Decisione (Decision)

Per questo slice, "creare ticket" significa:

```txt
Avere la possibilità di aggiungere un ticket più o meno esteso che abbia una flag che ne qualifichi il grado di priorità
```

## Fuori Scope / Non-Obiettivi (Non-Goals)

- Non creaimo codice
- No Refactoring
- No modifiche a file che non siano prompt-critica-issue.md
- Non modifichiamo la UI 
- Non aggiungiamo funzioni non esplicitate

## Criteri Di Accettazione (Acceptance Criteria)

1. Il ticket che rispetta i parametri assegnati viene visualizzata correttattamente e viene aggiunta al DB con un ID univoco e collegato all'autore e al ticket di appartenza 
2. Il ticket che non rispetta i paramteri non viene aggiunta al DB e si torna sulla creazione del ticket.
3. Il ticket non è visibile se non si è loggati

## Piano Di Verifica Manuale (Manual Test Plan)

- Input: Inserimento di un ticket corretto. Output: Il ticket se rispetta le condizioni, viene visualizzato correttamente e viene inserito nel DB
- Input: Inserimento di un ticket non conforme. Output: Visualizzato messaggio di errore "Ticket non conforme" e reindirizzamento sulla pagina del ticket.
- Input: Accesso al ticket senza autenticazione. Output: Nessuna ticket visibile.

## Note Per L06

- [quale payload andra' chiarito]
- [quale errore andra' chiarito]
- [quale campo dati andra' deciso]
