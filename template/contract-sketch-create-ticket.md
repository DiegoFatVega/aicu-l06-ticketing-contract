# Contratto Iniziale (Contract Sketch) - Create Ticket

## Prima Di Compilare

Un contratto iniziale (contract sketch) e' una descrizione leggera di input, output e risposte attese.

Serve a rendere verificabile `create ticket` prima di chiedere codice all'AI.

Compila solo la superficie minima:

- cosa entra;
- cosa esce;
- cosa viene rifiutato;
- quale errore ti aspetti.

Non trasformarlo in una specifica API completa, uno schema di un database o un piano di una patch.

Quando compili, ogni esempio deve rispondere (almeno) a tre domande:

- perche' questo input e' valido o invalido?
- quale risposta mi aspetto?
- quale parte della issue o del fuori scope giustifica la scelta?

## Request

```txt
Serve creare ticket dal supporto.
```

## Boundary Map

| Superficie | Cosa riguarda | Nota |
| --- | --- | --- |
| UI | title, description | serve all'utente/supporto |
| API / azione | input: title and description, output: ticket creato | flusso necessario |
| Dati | title, description, owner, createdAt | dati minimi per identificare il ticket |
| Verifica | a campi validi creati, creo un ticket visibile |  |

## Action

Per questo slice, `create ticket` significa:

```txt
Compilare almeno due campi testuali per la creazione di un ticket.
```

## Payload Valido

```json
{
  title: "l'app pincoPallino ha smesso di funzionare";
  description: "ogni volta che provo ad entrare, l'applicazione va in crash"
}
```

Perche' e' valido:

- il payload è completo in tutti i campi richiesti

## Risposta Attesa Di Successo

```txt
  Status: 201, "il tuo ticket è stato creato con successo"
```

Campi attesi:

- createdAt è un campo generato
- title e description sono i campi confermati

## Payload Invalido 1

```json
{
  title: "";
  description: ""
}
```

Motivo del rifiuto:

```txt
  Il ticket è vuoto
```

Risposta attesa:

```txt
  output atteso: Compila questi campi
```

## Payload Invalido 2

```json
{
}
```

Motivo del rifiuto:

```txt
[perche' e' invalido]
```

Risposta attesa:

```txt
[status o errore atteso]
```

## Error Model Minimo

| Caso | Motivo | Risposta attesa |
| --- | --- | --- |
| Campo richiesto mancante o vuoto | [motivo] | [errore] |
| Valore fuori contratto | [motivo] | [errore] |

## Non-Goals Confermati

- [cosa resta fuori scope]
- [cosa non chiedere all'AI]
- [cosa rimandare]


