## link state routing
mentre il distance vector routing è un algoritmo distribuito, il distance vector routing consiste nell'invio di messaggi per poter per consentire ai router di conoscere la topologia della rete

alcune **assunzioni**:
- la rete è rappresentata come un **grafo** nel quale i router sono i nodi e i link sono gli archi
- ad ogni link è assegnato un **peso**: il *migliore* e il *peggiore*
- l'algoritmo quindi sceglie il percorso con il peso minore basandosi su una serie di funzioni; diversi sono i modi per calcolare i pesi:
  - pesi *unitari*, identici per tutti i link
  - pesi *proporzionali* alla distanza (ritardo di propagazione), il percorso più rapido è calcolato in base al ritardo di propagazione
  - $\frac{C}{link - capacity}$, dove $C$ è una costante. Maggiore è la capacità del link e minore sarà il suo peso.

#### funzionamento
- ogni router ha il proprio indirizzo
- periodicamente i router inviano un pacchetto (`HELLO` packet) ogni `N` secondi su tutte le interfacce al quale è connesso
- durante questo processo, il router è in grado di capire a chi è connesso
- questi messaggi sono utili a capire se un router non è più disponibile (se dopo `k x N` secondi non si riceve un messaggio da un router, si può assumere che sia offline)

#### messaggi LSP
quando un router è a conoscenza dei suoi vicini, deve costruire un **pacchetto LST** per informare i router della rete; un pacchetto contiene:
- `LSP.Router`: indica l'indirizzo del mittente del pacchetto
- `LSP.age`: tempo di vita rimasto al pacchetto
- `LSP.seq`: il sequence number del pacchetto, incrementato ad ogni step
- `LSP.Links[]` lista dei link vicini
  - `LSP.Link[i].Id`: l'id del vicino
  - `LSP.Link[i].cost`: costo del link