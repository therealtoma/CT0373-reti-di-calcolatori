# public key encryprion
un piccolo ripasso sulla [chiave simmetrica](./10-symmetric-key-cryptography.md).
abbiamo visto che:
- Alice e Bob si scambiano una chiave segreta attraverso un canale sicuro (io vado fisicamente in banca e ottengo la chiave)
- la stessa chiave è usata sia per criptare che per decriptare il messaggio (motivo per cui si chiama chiave simmetrica)

è necessario avere quindi un canale sicuro sul quale scambiarsi la chiave segreta, verrà usato solamente per lo scambio, il resto della comunicazione avviene in un canale non sicuro.
