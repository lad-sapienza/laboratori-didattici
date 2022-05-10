---
tags:
  - adv
---
# GIS modulo avanzato: preparazione dei dati
[Accesso ai dati](Accesso%20ai%20dati.md) > Dataset `adv`

1. Recuperare da `diva-gis/ITA_adm/ITA_adm1` il solo poligono della regione del Lazio
![Pasted image 20220509114120](img/estrarre-confine-lazio-01.png)
![Pasted image 20220509114302](img/estrarre-confine-lazio-02.png)
3. Recuperare da `diva-gis/ITA_wat/ITA_water_lines_dcw` la rete fluviale entro gli attuali confini della regione Lazio
![Pasted image 20220509114900](img/ritaglia-fiumi.png)
5. Recuperare da `awmc/inlandwater/inland_water_edits` solo i poligoni che si trovano entro gli attuali confini della regione Lazio
![Pasted image 20220509115303](img/ritaglia-acque-interne.png)
7. Recuperare da `awmc/inlandwater/ba_roads` solo le polilinee che si trovano entro gli attuali confini della regione Lazio
8. Recuperare da `pleiades/pleiades-latest.kmz` solo i siti che si trovano entro gli attuali confini della regione Lazio
![Pasted image 20220509115835](img/ritaglia-siti.png)
![Pasted image 20220509120250](img/salvare-siti-gpkg.png)

[< GIS Avanzato - Introduzione](GIS%20Avanzato%20-%20Introduzione.md)
[> Calcolatore dei campi](Calcolatore%20dei%20campi.md)