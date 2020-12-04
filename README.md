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

## Utilizzo degli script
Le procedure allo stato attuale (04/12/2020) non vengono eseguite in automatico, ma possono essere fatte funzionare "manualmente" attraverso l'accesso al server di GAGLIARDO (10.10.0.15). 
Gli script principali disponibili sono due, si trovano entrambi nella directory _/home/meteo/bin_ e sono chiamati:
1) cdo_clima.sh
2) cdo_alldays.sh

N.B. Solo la stazione di Milano viene aggiornata con i nuovi dati ogni giorno (entro le ore 10:00). I dettagli degli aggiornamenti sono in capo ad Antioco Vargiu.

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
Lo script produrrà in automatico otto immagini, reperibili su Gagliardo nella seguente cartella _/home/meteo/clich/output_ e che descrivono il clima di riferimento per il periodo scelto. Per i dettagli vi invito a consultare il file pdf riassuntivo e a consultare la cartella esempi_script_1 presente in questa repository.

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
Lo script produrrà in automatico 5 immagini, reperibili su Gagliardo nella seguente cartella _/home/meteo/clich/output_ e che descrivono l'evoluzione dei parametri meteo per l'anno scelto con le rispettive anomalie. Per i dettagli vi invito a consultare il file pdf riassuntivo e a consultare la cartella esempi_script_2 presente in questa repository.
