# Architettura del Progetto Android

*Nota Introduttiva: Questo è un documento vivo ed in continua evoluzione che
riflette l'implementazione effettiva (as-is) del codice, e non una specifica
rigida calata dall'alto.*

Questo progetto adotta un'architettura moderna per applicazioni Android, basata
su Kotlin e sulle best practices raccomandate da Google. L'obiettivo principale
è garantire prestazioni ottimali anche in scenari di carico estremo.

## Stack Tecnologico

- **Linguaggio**: Kotlin.
- **UI**: Jetpack Compose. La UI deve essere passiva e reattiva, limitandosi a
  osservare e mappare i dati pronti per il rendering.
- **Asincronia**: Coroutines e Flow per gestire in modo efficiente le operazioni
  concorrenti.
- **Pattern Architetturale**: UDF (Unidirectional Data Flow) con l'utilizzo di
  ViewModel per la gestione degli stati UI.

## Vincoli di Performance

L'applicazione deve supportare scenari complessi con oltre 1000 punti di
imperfezione. Pertanto, l'architettura è soggetta a vincoli stringenti:

- **Prevenzione OOM (Out Of Memory)**: È fondamentale una gestione rigorosa
  della memoria. Le immagini e le risorse pesanti devono essere gestite in
  modo oculato, utilizzando paginazione o meccanismi di caching efficienti.
- **Prevenzione Memory Leak**: I riferimenti al ciclo di vita devono essere
  gestiti con attenzione. Non tolleriamo memory leak che possano degradare
  le prestazioni o causare crash.
- **Ottimizzazione UI**: La renderizzazione in Compose deve evitare sprechi.
  Tutti i calcoli complessi devono essere pre-calcolati dai ViewModel in
  background, in modo che la UI possa elaborarli in tempo costante O(1).
