# public key encryprion
un piccolo ripasso sulla [chiave simmetrica](./10-symmetric-key-cryptography.md).
abbiamo visto che:
- Alice e Bob si scambiano una chiave segreta attraverso un canale sicuro (io vado fisicamente in banca e ottengo la chiave)
- la stessa chiave è usata sia per criptare che per decriptare il messaggio (motivo per cui si chiama chiave simmetrica)

è necessario avere quindi un canale sicuro sul quale scambiarsi la chiave segreta, verrà usato solamente per lo scambio, il resto della comunicazione avviene in un canale non sicuro.

#### principi chiave pubblica
il principio alla base della chiave pubblica è permettere ad Alice e Bob di poter comunicare in modo sicuro senza doversi scambiare nessuna informazione sensibile.
esistono molti algoritmi per assolvere a questo scopo, i più famosi sono:
- **Diffie-Halleman** Key exchange
- **RSA** public key encryption
- **Elliptic curve** encryption (non viene trattata all'interno del corso)

