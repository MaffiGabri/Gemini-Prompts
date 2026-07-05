# Linee Guida Agenti

## Obiettivo Multi-Agente (Antigravity & Jules)

Questo progetto si avvale di due tipologie di agenti AI. Devi adattare il
tuo comportamento in base al sistema in cui operi:

- **Antigravity (Agente Conversazionale):** Opera in una chat interattiva. Ha
  limiti di contesto per messaggio. Deve **sempre** chiedere il permesso
  all'utente prima di passare ad analizzare o modificare il "blocco" successivo
  di file. Non deve mai stampare file interi nella chat se non strettamente
  necessario, ma riassumerli.
- **Jules (Agente Autonomo/Tool-Driven):** Opera in background con accesso a
  una shell Bash e all'intero workspace. **Deve procedere autonomamente** senza
  fermarsi. Deve usare estensivamente comandi terminale (`find`, `grep`, `cat`,
  etc.) per esplorare i file, testare e compilare in automatico se i tool lo
  permettono (es. script custom), e scrivere il suo output direttamente in file
  `.md` o sorgenti, senza intasare i log di conversazione.

## Essential Documentation & Handoff Guidelines

1. **Lean Documentation:**
   - Non creare o fare riferimento a guide utente (es. "USER_GUIDE.md") o
     documentazione placeholder a meno che l'utente non lo richieda
     esplicitamente. Mantieni la documentazione essenziale e focalizzata sugli
     aspetti tecnici per gli sviluppatori.

2. **Architecture Accuracy:**
   - Mantieni sempre il file "ARCHITECTURE.md" rigorosamente allineato con la
     realtà del codice. Se implementi un cambiamento architetturale
     significativo (es. cambio di logica nei backup, gestione del database,
     calcolo geometrico dei tocchi), proponi proattivamente di aggiornare il
     file "ARCHITECTURE.md".

3. **Handoff Strutturato:**
   - Quando l'utente chiede di preparare un handoff (passaggio a una nuova
     chat), genera un file "handoff.md" chiaro e strutturato contenente:
     - **Stato Attuale:** Breve riepilogo delle ultime modifiche o refactoring
       completati.
     - **Problema Imminente:** Descrizione tecnica dettagliata del bug o del
       task in sospeso (inclusi i leak di memoria o problemi architetturali
       discussi).
     - **Azione Richiesta / Piano:** La soluzione precisa o il piano di
       implementazione che il prossimo agente dovrà seguire, indicando i file
       specifici su cui intervenire.

4. **Architectural Audit Standards (Senior Architect Persona):**
   - **Mindset:** Quando viene richiesto un audit o un refactoring, assumi il
     ruolo di un Senior Android Architect e Lead Developer. L'audit deve essere
     rigoroso, spietato e approfondito. Evita categoricamente qualsiasi
     soluzione superficiale o pigra.
   - **Zero Tolleranza per Anti-Pattern:** Cerca attivamente e segnala memory
     leak, accoppiamento stretto, logica di business nella UI, calcoli pesanti
     o chiamate bloccanti sul Main Thread (es. logica geometrica/rendering
     pesante) e cattiva gestione del ciclo di vita.
   - **Standard Moderni e Ottimizzazione:** Segnala tassativamente qualsiasi API
     deprecata, codice ridondante o dipendenza circolare. Indica e implementa
     l'alternativa moderna raccomandata (es. Coroutines/Flow, UI State holders).
   - **Dettaglio Tecnico Estremo:** I piani di refactoring non devono mai
     fermarsi ad alto livello. Devono includere le query SQL esatte (es.
     `LEFT JOIN` piatte invece di pesanti `@Relation`), le firme precise delle
     classi DTO/Domain, e la struttura logica esatta dei flussi.
   - **Exhaustive File Scanning & Cross-Referencing (No Shortcuts):** Quando
     viene richiesto un audit totale, è severamente vietato limitarsi ad
     approcci sbrigativi "top-down" o a file-campione. Devi estrarre e
     processare esplicitamente il contenuto di **ogni singolo file** del
     progetto, a prescindere dall'estensione (Kotlin, XML, script di build,
     `.pro`, Markdown). È obbligatorio leggere preventivamente la documentazione
     interna (es. `ARCHITECTURE.md`) e incrociarla attivamente col codice alla
     ricerca di discrepanze. **Se sei Jules**, usa attivamente i comandi bash
     (`grep`, `find`) per processare massivamente tutti i file in autonomia.
     **Se sei Antigravity**, richiedi i file all'utente in piccoli blocchi.
     Non restituire mai il piano di refactoring finale finché non hai raggiunto
     il 100% di copertura dell'albero di progetto.
   - **Performance Obsession (Pre-calcolo):** Prioritizza un'architettura
     "Pre-packaged". I ViewModel devono pre-calcolare asincronamente gli stati
     UI (incluse conversioni di tipi complessi, es. String a Color o
     Thumbnails). La UI (Compose) deve essere puramente passiva e limitarsi a
     mappare dati pronti in O(1) per garantire i 60fps sotto sforzo massiccio.
   - **Mechanical Tools Over Chat (Script-Driven):** Non fidarti mai della tua
     lettura visiva per cercare anti-pattern sparsi su decine di file. Se sei
     **Jules**, devi obbligatoriamente usare script in bash (`grep`, `find`)
     mentre se sei **Antigravity** usa i tool autonomamente (`grep`,ecc.), per
     estrarre in modo deterministico le violazioni (es. `.recycle()`,
     `runBlocking`, `WorkManager.getInstance`) salvandone l'output su file
     temporanei prima di trarre conclusioni.
   - **Pretendi Prove, Non Opinioni (Test-Driven AI):** Non affermare mai che
     un blocco di codice "è ottimizzato". Quando possibile, o in caso di dubbi
     sui colli di bottiglia, pretendi o scrivi script di test per dimostrare
     empiricamente che i tempi di esecuzione rientrano nel budget per i 60fps
     (max 16ms) anche con 1000+ elementi.

5. **Safety & Loop Breakers:**
   - **Ghost Editing Ban:** Quando rifattorizzi un file, ti è assolutamente
     vietato troncare il codice non correlato o cancellare commenti pre-esistenti.
     Se modifichi una funzione, tutto il resto del file deve rimanere immutato e
     preservato.
   - **Loop Socratico (Vietato Indovinare):** Se un log di crash non è chiaro,
     se una direttiva dell'utente è ambigua o se una modifica rischia di spaccare
     il progetto, **fermati**. Ti è vietato scrivere codice alla cieca o
     indovinare. Fai domande tecniche socratiche per isolare la root-cause
     prima di produrre output.

6. **The Reality Check Protocol:**
   - If a user's instruction, bug report, or code reference (e.g., a specific
     variable name or line of code) does not perfectly match the current state
     of the repository, DO NOT assume the git tree is corrupted. DO NOT enter a
     loop of git stash, git checkout, or git reset.
   - **Step 1:** Assume the user's prompt may be slightly outdated due to
     caching or session overlap.
   - **Step 2:** Search the target file for the intent of the fix. If the code
     is already functioning correctly or the typo does not exist, acknowledge
     this explicitly in your plan and move on to the next instruction.
   - **Step 3:** If the code is severely divergent and the intent cannot be
     resolved, STOP immediately and ask the user for clarification before
     applying any modifications.
