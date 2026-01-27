---
tags:
  - other-formats
---
## Introduzione a WMS e WFS
- ℹ️ [https://en.wikipedia.org/wiki/Web_Map_Service](https://en.wikipedia.org/wiki/Web_Map_Service)
- ℹ️ [https://en.wikipedia.org/wiki/Web_Feature_Service](https://en.wikipedia.org/wiki/Web_Feature_Service)
## Caricamento WMS

Per questo esercizio useremo i dati del **Geoportale Nazionale** a cura del Ministero dell’Ambiente e della Sicurezza Energetica, elencati alla pagina: [https://gn.mase.gov.it/portale/servizio-di-consultazione-wms](https://gn.mase.gov.it/portale/servizio-di-consultazione-wms)

1. Carico Bing Satellite attraverso QuickMap Services
2. Zoom su Roma
3. Menu `Layer > Gestore delle Sorgenti Dati` (`CTRL/CMD + L`)
4. `WMS/WMTS` > Nuovo
	1. Nome: GN: Geologica
	2. URL: http://wms.pcn.minambiente.it/ogc?map=/ms_ogc/WMS_v1.3/Vettoriali/Carta_geologica.map
5. `Connetti` per acquisire la lista dei servizi disponibili
6. Selezionare il primo e `Aggiungi`

## Caricamento WFS

Anche per questo esercizio useremo i dati del **Geoportale Nazionale** a cura del Ministero dell’Ambiente e della Sicurezza Energetica, elencati alla pagina: 
[https://gn.mase.gov.it/portale/wfs](https://gn.mase.gov.it/portale/wfs)

1. Carico Bing Satellite attraverso QuickMap Services
2. Zoom su Roma
3. Menu `Layer > Gestore delle Sorgenti Dati` (`CTRL/CMD + L`)
4. `WFS` > Nuovo
	1. Nome: GN: Geologica
	2. URL: [http://wms.pcn.minambiente.it/ogc?map=/ms_ogc/WMS_v1.3/Vettoriali/Carta_geologica.map](http://wms.pcn.minambiente.it/ogc?map=/ms_ogc/wfs/Carta_geologica.map)
5. `Connetti` per acquisire la lista dei servizi disponibili
6. Selezionare il primo e `Aggiungi`


**A differenza dei tiles raster, la [Simbologia](Simbologia.md) di quelli vettoriali può essere modificata**