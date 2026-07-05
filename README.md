# Progetto Android: Panoramica e Obiettivi

Questo è il repository principale del nostro progetto Android. L'applicazione è
sviluppata in Kotlin, sfruttando Coroutines e Flow per la gestione delle
operazioni asincrone e dei flussi di dati. Utilizziamo Jetpack Compose per
la costruzione della UI in modo dichiarativo e seguiamo il pattern UDF
(Unidirectional Data Flow) per una gestione dello stato chiara e prevedibile.

L'applicazione è progettata per gestire un carico estremo, con supporto per
oltre 1000 punti di imperfezione, ciascuno associato a immagini e storiografia
su diverse varianti. Le prestazioni sono una priorità assoluta, con vincoli
rigidi per evitare problemi di Out of Memory (OOM) e memory leak.

Per ulteriori dettagli sull'architettura, consulta il file `ARCHITECTURE.md`.
Questo documento rappresenta lo stato attuale (as-is) del codice e viene
aggiornato di pari passo con lo sviluppo.
