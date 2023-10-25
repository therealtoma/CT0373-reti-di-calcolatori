## nv routing
## network layer
mentre il compito del livello data link è quello di mettere in comunicazione un host con il resto degli altri attraverso il canale fisico.
Il livello **network** ha il compito di collegare host che non fanno parte della stessa rete fisica attraverso l'utilizzo di **router**.
![network layer](./assets/06/network-layer.png)
in questa foto i cerchi rappresentano gli **host**, i quadrati sono i **router** si occupano solamente di instradare il traffico.

Il frame del datalink è detto **pacchetto**, che contiene un header, che verrà incapsulato nel payload del frame del livello datalink.

Esistono due tipi:
- **datagram-oriented**: usato attualmente da Internet
- **circuit-oriented**

### datagram oriented
ogni host del livello rete è identificato da un **indirizzo**; per poter inviare un pacchetto ad un host, il mittente deve creare un pacchetto che contiene:
- l'indirizzo dell'host del mittente
- l'indirizzo dell'host del destinatario
- l'informazione che deve essere inviata

i router usano un tipo di comunicazione chiamata **hop-by-hop**, dove un router riceve un pacchetto (non destinato per lui), prende una decisione sul dove inviarlo e lo inoltra al prossimo router.

Le decisioni sono prese in base a una **forwarding table**: una struttura dati che mappa un indirizzo di destinazione con uno (o più indirizzi) destinazione; la tabella viene consultata per ogni pacchetto che viene ricevuto.
2 tipi di errori possono succedere:
- **black holes**: situazione in cui un router riceve un pacchetto ma nella tabella di routing non sa dove inviarlo, il pacchetto viene scartato
- **loops**

Ogni router si occupa di svolgere due funzioni:
- **data plane**: si occupa di instradare i pacchetti, in base al contenuto delle tabelle di routing
- **control plane**: processo che si occupa di creare e mantenere le tabelle di routing. Il modo più semplice per creare le tabelle consiste nel farlo a mano, questa cosa non scala, è necessario trovare un modo per farlo automaticamente. Introduciamo quindi dei pacchetti speciali non contenenti dati, ma informazioni utili per creare le tabelle di routing

All'interno di un contesto privato è possibile che eista un controller dedicato che si occupa di gestire l'intera rete privata; è in grado quindi di configurare le tabelle di routing, questo approccio è detto **centralizzato**.
All'interno di Internet un approccio centralizzato risulta impossibile, per questo si usa l'approccio **distribuito**

### addressing

**flat addressing**
in questo approccio gli indirizzi sono completamente scorrelati tra di loro, infatti sono quelli decisi dal produttore.
- **pro**: non è necessario fare alcun tipo di configurazione
- **contro**: in questo modo la rete non scala. Dato che Internet contiene miliardi di indirizzi, questo significa che ogni forwarding table deve avere miliardi di entry.

**hirerchical addressing**
in questo approccio, gli indirizzi sono divisi in **blocchi**; ai router viene quindi assegnato uno o più blocchi. In questo modo le dimensioni delle forwarding tables sono molto più piccole.
Nel momento in cui un host cambia network, il suo indirizzo cambia di conseguenza (ci si sposta da casa all'università). è fondamentale quindi trovare un modo per:
- un modo per assegnare un indirizzo ad un host che si collega alla rete
- garantire all'host il mantenimento delle connessioni passate nel momento in cui cambia rete