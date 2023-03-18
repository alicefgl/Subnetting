# Subnetting
Utilizzare le regole di subnetting per creare due sottoreti della stessa dimensione partendo dall'indirizzo 192.168.0.0/24 (su Filius)

Conoscenze teoriche:
Il subnetting è una suddivisione di una rete principale in diverse sottoreti che possono contenere un determinato numero di dispositivi ai quali corrisponde un indirizzo ip, per eseguire il calcolo del subnetting è perciò necessario definire gli intervalli delle combinazioni di indirizzi ip per ogni sottorete e la subnet mask relativa all'insieme.
Questo processo si applica in base a determinate esigenze che costringono quindi chi struttura una rete ad abbandonare le classi di indirizzi, si avranno perciò delle configurazioni classless.

Procedimento:
1) Dato un determinato numero di sottoreti desiderate e la rete principale dalla quale si calcolano i range di ip, si inizia dividendo il numero massimo di dispositivi disponibili in quella rete per il numero di sottoreti. In questo caso la rete data è 192.168.0.0 con subnet 255.255.255.0 , significa che solo l'ultimo ottetto dell'indirizzo ip è dedicato ai dispositivi (host_id), il numero massimo di dispositivi è perciò 256.
Il calcolo è quindi:  256 / 2 = 128   da cui possiamo dedurre che i range di indirizzi corrispondono ad una rete diversa ogni 128 combinazioni.

2)  Dopo aver calcolato il numero di combinazioni per ogni sottorete si può passare a definire i vari range, tenendo conto del fatto che il primo indirizzo disponibile ad ogni sottorete deve identificare la rete mentre l'ultimo è dedicato al broadcast: questi indirizzi non possono essere assegnati ai dispositivi all'interno delle reti.
I range risulteranno essere:
- subnet 1:
  192.168.0.0 -> id_rete
  192.168.0.127 -> id_broadcast
- subnet 2:
  192.168.0.128 -> id_rete
  192.168.0.255 -> id_broadcast
Gli ip compresi nei range sopra riportati possono essere assegnati ai vari dispositivi.
Alcuni indirizzi possono essere dedicati a dei determinati dispositivi come i router (con funzione di gateway), per i quali l'indirizzo ip deve essere costante e perciò duraturo nel tempo. Si sceglie quindi di assegnare a questi dispositivi l'indirizzo massimo disponibile per i dispositivi, oppure il minimo.
Lo stesso procedimento può avvenire anche con dispositivi come un DHCP server o un DNS.

3) L'ultimo passaggio da effettuare per poter configurare i dispositivi della rete è il cacolo della subnet mask, che dipende anch'essa dal numero di subnet desiderate.
Secondo questo esercizio il numero di subnet mask è 2, che è uguale a 2^1 quindi da ciò si può dedurre che la divisione delle varie sottoreti avviene modificando il primo bit, che può assumere solo 2 valori (0 e 1), che è il numero di sottoreti desiderato.
Modificando quindi il primo bit da 0 a 1, si ottiene questa subnet mask: 11111111.11111111.11111111.10000000
Calcolando l'equivalente decimale dell'ultimo ottetto riportato sopra in binario, si ottiene: 10000000 = 2^7 = 128
La subnet mask sarà perciò uguale a 255.255.255.128
