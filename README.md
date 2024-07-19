# W11D4: Scansioni NMAP su Windows 7 in Rete Esterna e Interna

Questo repository contiene i risultati di otto scansioni NMAP eseguite su una macchina Windows 7, con l'obiettivo di confrontare i risultati delle scansioni effettuate in una rete esterna (WAN) e in una rete interna (LAN).

## Struttura del Repository

- **Scansioni WAN:** Contiene i file .xml delle scansioni effettuate quando la macchina Windows 7 era su una rete esterna.
- **Scansioni LAN:** Contiene i file .xml delle scansioni effettuate quando la macchina Windows 7 era su una rete interna.
- **Comparazioni:** Contiene i file di comparazione generati con `ndiff`, che mettono a confronto i risultati delle stesse scansioni effettuate in rete locale e in rete esterna.

## Tipi di Scansioni Eseguite

1. **sS (SYN Scan):** Questa scansione invia pacchetti SYN per determinare lo stato delle porte (aperta, chiusa, filtrata).
2. **sT (TCP Connect Scan):** Questa scansione utilizza la chiamata di sistema connect() del sistema operativo per completare la connessione TCP.
3. **sV (Service Version Detection):** Questa scansione tenta di determinare le versioni dei servizi in esecuzione sulle porte aperte.
4. **O (OS Detection):** Questa scansione tenta di identificare il sistema operativo della macchina target.

## Procedura di Scansione

1. **Scansioni WAN:**
   - La macchina Windows 7 aveva un indirizzo IPv4 esterno `192.168.100.102`.
   - L'accesso alla macchina è stato ottenuto tramite un gateway pfSense.
   - Sono state impostate regole firewall su Windows 7 per permettere le connessioni in entrata.

2. **Scansioni LAN:**
   - La macchina Windows 7 è stata spostata sulla stessa rete di Kali, con un indirizzo IPv4 `192.168.50.102`.
   - Le scansioni sono state rieseguite in questa configurazione di rete interna.

## Differenze tra Rete Locale e Rete Esterna

### MAC Address
- Nella scansione in rete locale, è visibile l'indirizzo MAC della macchina target.
- Nella scansione in rete esterna, l'indirizzo MAC non è disponibile.

### RTT (Round-Trip Time)
Il tempo di round-trip (RTT) rappresenta il tempo necessario per un pacchetto di viaggiare dal mittente al destinatario e tornare indietro.

- **SRTT (Smoothed Round-Trip Time):** È una stima del RTT media, calcolata utilizzando un algoritmo di smoothing per ridurre l'impatto delle variazioni temporanee nel tempo di risposta.
- **RTTVAR (Round-Trip Time Variation):** È una misura della variazione del RTT, utilizzata per calcolare i timeout di ritrasmissione.

Nelle scansioni in rete locale:
- Il tempo di vita dei pacchetti (`TTL`) è inferiore.
- I valori di `srtt` e `rttvar` sono generalmente minori, indicando tempi di risposta più veloci e meno variabilità nei tempi di risposta.

## Come Utilizzare Questo Repository

1. **Clona il repository:**
   ```bash
   git clone https://github.com/TheWatchMakerXI/W11D4.git
   ```

2. **Esplora le scansioni:**
   - Naviga nelle cartelle `Scansioni WAN` e `Scansioni LAN` per visualizzare i file .xml delle scansioni.
   - Apri i file di comparazione nella cartella `Comparazioni` per vedere le differenze tra le scansioni in rete locale e in rete esterna.

3. **Visualizza i risultati:**
   - Puoi utilizzare strumenti come `ndiff` per ulteriori comparazioni.
   - Utilizza strumenti di visualizzazione XML per esaminare i dettagli delle scansioni.

## Note Finali

Questi risultati evidenziano le differenze significative tra l'esecuzione di scansioni NMAP su una rete locale rispetto a una rete esterna. La disponibilità dell'indirizzo MAC e i tempi di risposta più rapidi in una rete locale possono fornire maggiori dettagli e precisione nelle scansioni. Tuttavia, le scansioni su reti esterne sono essenziali per valutare la sicurezza e la visibilità dei servizi esposti.

---

Sentiti libero di personalizzare ulteriormente il README in base alle tue esigenze o di includere eventuali informazioni aggiuntive che ritieni utili.
