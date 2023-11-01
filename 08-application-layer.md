# livello applicazione
le applicazioni sono diverse le une dalle altre, è perciò complicato definire uno standard che funziona per tutti.
Generalmente la comunicazione avviene in modo **request/response**, che varia da applicazione a applicazione.
Un protocollo a livello applicazione deve quindi definire la sintassio e il modo in cui le informazioni sono richieste.

#### scambio di testo
solitamente il testo è codificato in **ASCII**, se necessario in **UTF-8**. questi standard si occupano di convertire i caratteri in codice binario.

#### scambio di dati binari
oltre a scambiare testo, è necessario un modo per inviare informazioni binarie (per esempio un'immagine all'interno di una mail).
Sono state adottate due metodologie:
- **big-endian**: il byte più significativo precede quello meno significativo
- **little-endian**: il byte meno significativo precede quello più significativo

All'interno di Internet ormai viene usato **big-endian**