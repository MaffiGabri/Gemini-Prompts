# Aggiornamento Documentazione

Task: Analizzare l'attuale base di codice per aggiornare e allineare la
documentazione (`README.md` e i file di documentazione dell'architettura).

Contesto e Filosofia:
Attualmente, il `README.md` e i file di architettura sono obsoleti e
vengono erroneamente trattati come una "bibbia" rigida o una specifica.
Dobbiamo passare a un approccio di "Living Documentation". L'effettiva
implementazione nel codice è l'UNICA Singola Fonte di Verità (SSOT).

Istruzioni:

1. Analizza l'intera base di codice per comprendere lo stato attuale e
   reale del progetto, la sua architettura effettiva, le dipendenze, il
   flusso di dati e le funzionalità implementate. **Se sei Jules (agente
   bash), usa i comandi per esplorare massivamente i file. Se sei
   Antigravity (chat), chiedi all'utente di caricare o mostrare i file
   salienti.**
2. Revisiona il `README.md` esistente e qualsiasi file di architettura (es.
   `ARCHITECTURE.md` o simili nelle sottocartelle).
3. Identifica le discrepanze in cui la documentazione descrive
   funzionalità pianificate, strutture deprecate o obiettivi
   aspirazionali che NON corrispondono al codice attuale.
4. Crea un piano strutturato per l'aggiornamento della documentazione. Invece
   di riscrivere tutto in un singolo passaggio, dividi il lavoro in step
   incrementali (es. un file o una sezione alla volta) da far approvare.
5. Riscrivi e aggiorna i file in modo incrementale affinché riflettano
   strettamente lo **stato dell'arte (as-is)** della base di codice attuale.
   Rimuovi o etichetta chiaramente le funzionalità "future/todo" in
   modo che non vengano confuse con le implementazioni attuali.
6. Aggiungi una breve nota nell'introduzione della documentazione
   architetturale per precisare che si tratta di un documento vivo, in
   continua evoluzione, che riflette l'implementazione effettiva e non
   una specifica rigida calata dall'alto.

**Se sei Jules**, scrivi direttamente le modifiche nei file `README.md` e
`ARCHITECTURE.md` procedendo in modo iterativo. **Se sei Antigravity**,
fornisci i testi aggiornati all'interno della chat chiedendo all'utente di
incollarli, procedendo un blocco alla volta.
