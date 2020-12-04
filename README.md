# CLICH4
_Procedure per l'elaborazione e la visualizzazione dei dati climatici di 5 serie storiche_

L'obbiettivo è quello di caratterizzare il clima di 5 grandi città della Lombardia attraverso la disamina di serie termometriche e pluviometriche storiche.
Le stazioni scelte sono:
- Milano (disponibile dal 1901 al 2020) - Stazione in uso "Milano Brera"
- Brescia (disponibile dal 1951 al 2015) - Stazione in uso "Brescia ITAS Pastori"
- Sondrio (disponibile dal 1951 al 2015) - Stazione in uso "Sondrio Fojanini"
- Mantova (disponibile dal 1901 al 2015) - Stazione in uso "Mantova Lunetta"
- Pavia (disponibile dal 1950 al 2015) - Stazione in uso "Pavia Ponte Ticino"

Per ognuna di queste stazioni sono definiti i parametri giornalieri (registrati in modalità 9-9) di:
- Temperatura minima (tempMin)
- Temperatura massima (tempMax)
- Precipitazione cumulata (prec)

## Funzionamento script
I dati delle cinque serie storiche sono contenuti all'interno di altrettanti files denominati es: "milano_clima.nc", quest'ultimi elaborati da diversi script che si occupano di produrre le elaborazioni citate nel paragrafo successivo e visionabili negli esempi di questa repository. L'elenco degli script è visionabile nel file pdf riassuntivo [Documentazione CLICH](https://github.com/ARPASMR/CLICH4/blob/master/Documentazione%20processi%20di%20clich%20-%20Clima%20Lombardia.pdf)

## Utilizzo degli script
Le procedure allo stato attuale (04/12/2020) non vengono eseguite in automatico, ma possono essere fatte funzionare "manualmente" attraverso l'accesso al server di GAGLIARDO (10.10.0.15). 
Gli script principali disponibili sono due, si trovano entrambi nella directory _/home/meteo/bin_ e sono chiamati:
1) cdo_clima.sh
2) cdo_alldays.sh

N.B. Solo la stazione di Milano viene aggiornata con i nuovi dati ogni giorno (entro le ore 10:00). I dettagli degli aggiornamenti sono in capo ad Antioco Vargiu (a.vargiu@arpalombardia.it).

### Esempio script n°1:
```
[meteo@arpav-gagliardo bin]$ ./cdo_clima.sh

* Inizio PROCEDURA cdo_clima.sh per calcolo indicatori del clima *
* Le città presenti sono: Brescia, Mantova, Milano, Pavia e Sondrio *
* ATTENZIONE! Leggi di seguito da quando sono disponibili le stazioni *
* Milano disponibile dal 1901 al 2020 *
* Brescia disponibile dal 1951 al 2015 *
* Sondrio disponibile dal 1951 al 2015 *
* Mantova disponibile dal 1901 al 2015 *
* Pavia disponibile dal 1950 al 2015 *
*
*******************************************************************************
Seleziona stazione e periodo di riferimento con modalità: città annoinizio annofine
milano 1901 2020
```
Lo script produrrà in automatico otto immagini, reperibili su Gagliardo nella seguente cartella _/home/meteo/clich/output_ e che descrivono il clima di riferimento per il periodo scelto. Per i dettagli vi invito a consultare il file riassuntivo in [Documentazione CLICH](https://github.com/ARPASMR/CLICH4/blob/master/Documentazione%20processi%20di%20clich%20-%20Clima%20Lombardia.pdf) e a consultare la cartella esempi_script_1 presente in questa repository.

### Esempio script n°2:
```
[meteo@arpav-gagliardo bin]$ ./cdo_alldays.sh

* Inizio PROCEDURA cdo_alldays.sh per visualizzazione temp e prec anno in corso e passati *
* Le città presenti sono: Brescia, Mantova, Milano, Pavia e Sondrio *
* ATTENZIONE! Leggi di seguito da quando sono disponibili le stazioni *
* Milano disponibile dal 1901 al 2020 *
* Brescia disponibile dal 1951 al 2015 *
* Sondrio disponibile dal 1951 al 2015 *
* Mantova disponibile dal 1901 al 2015 *
* Pavia disponibile dal 1950 al 2015 *
*
*******************************************************************************
Scegli la città di cui vuoi visualizzare il clima e l'anno
milano 2020
```
Lo script produrrà in automatico 5 immagini, reperibili su Gagliardo nella seguente cartella _/home/meteo/clich/output_ e che descrivono l'evoluzione dei parametri meteo per l'anno scelto con le rispettive anomalie. Per i dettagli vi invito a consultare il file pdf riassuntivo [Documentazione CLICH](https://github.com/ARPASMR/CLICH4/blob/master/Documentazione%20processi%20di%20clich%20-%20Clima%20Lombardia.pdf) e a consultare la cartella esempi_script_2 presente in questa repository.

## Immagini presenti su GHOST
Attualmente, per consultazione, sono presenti su GHOST (10.10.0.14) alcuni output significativi per il clima di riferimento di ognuna delle cinque città. I dati sono consultabili nel link di seguito: [http://10.10.0.14/clima/RIFERIMENTO/](http://10.10.0.14/clima/RIFERIMENTO/)
La pagina web è stata costruita da Maria Ranci (m.ranci@arpalombardia.it)

## Avvertenze e nuovi sviluppi

_AVVERTENZE_

Lo script cdo_alldays.sh produce una tabella contenente le classifiche aggiornate di ogni mese rispetto a tutto il clima della serie storica per quel singolo mese (es. maggio 2020 è il 4° più caldo e il 116° più freddo). Dal punto di vista operativo la classifica viene stilata sulla base di una matrice di dati che viene prodotta da cdo_clima.sh. 
Di conseguenza, nel caso di analisi "operativa" (es. Milano nell'anno in corso) è necessario prima far "girare" lo script cdo_clima.sh per l'intera serie storica (es. milano 1901 2020), poi rinominare i file _Matrice_Tmin_mean_clima_ordinata_milano.csv_ e _Matrice_Tmax_mean_clima_ordinata_milano.csv_ presenti in _/home/meteo/clich/input_ aggiungendo il suffisso _fixed_ (es. _Matrice_Tmin_mean_clima_ordinata_milano_fixed.csv_)

_SVILUPPI_

Le successive fasi di sviluppo potrebbero comprendere:
- "Pulizia" delle serie storiche di Pavia, Brescia, Sondrio e Mantova con riempimento dati mancanti.
- Completamento delle 4 serie restanti (dal 2015 al 2020) e aggiornamento automatico delle procedure (come per Milano)
- Correzione e semplificazione della procedura sopramenzionata nelle avvertenze
- Nuovi script di elaborazione dati e produzione output
