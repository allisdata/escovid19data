# Escovid19data: Capturando datos de COVID-19 por provincias en España

[![GitHub license](https://img.shields.io/badge/License-Creative%20Commons%20Attribution%204.0%20International-blue)](https://github.com/montera34/escovid19data/blob/master/LICENSE.md)
[![GitHub commit](https://img.shields.io/github/last-commit/pcm-dpc/COVID-19)](https://github.com/montera34/escovid19data/commits/master)

## ¿Puedes utilizar los datos? ¿Cómo colaborar?

[Pon link a este repositorio (https://github.com/montera34/escovid19data)](https://github.com/montera34/escovid19data) y llámalo Escovid19data. Liberamos los datos para que hagas con ellos lo que quieras. Si nos citas, mejor, para mantener la trazabilidad de los datos. Nos encantará saber que usas los datos, escríbemos a covid19@montera34.com o tuitea con #escovid19data.
Ver condiciones de [la licencia con que compartimos los datos](https://github.com/montera34/escovid19data/blob/master/LICENSE.md).

Puedes ayudar colaborando actiamente en la recopilación de daos o detectando errores y notificándolos. Puedes ponernos un email, o mejor, [crear un incidencia](https://github.com/montera34/escovid19data/issues). 

## Los datos / The data

**ES**

Los datos se publican en este CSV: [/data/output/covid19-provincias-spain_consolidated.csv](https://github.com/montera34/escovid19data/blob/master/data/output/covid19-provincias-spain_consolidated.csv)

Incluye el código del INE pra las provincias y datos relativos a 100.000 habitantes.
Cuando se indica 'NA' es que no hay datos disponibles.

Los datos descarados de las hoja de cálculo son procesados con este [script de R](https://code.montera34.com:4443/numeroteca/covid19/-/blob/master/analysis/process_spain_provinces_data.R) en otro repositorio. 

Los datos originales usados son almacenados en este directorio: [/data/original/spain](https://code.montera34.com/numeroteca/covid19/-/tree/master/data/original/spain). Puedes acceder a datos más desagregados que ls provinicas, por ejemplo a datos por [islas de Canarias](https://code.montera34.com/numeroteca/covid19/-/tree/master/data/original/spain/canarias) o por [área sanitaria en Galicia](https://code.montera34.com/numeroteca/covid19/-/tree/master/data/original/spain/galicia).

**EN**

Data are published in this CSV file: [/data/output/covid19-provincias-spain_consolidated.csv](https://github.com/montera34/escovid19data/blob/master/data/output/covid19-provincias-spain_consolidated.csv)

It includes now INE code for provinces and data per 100.000 inhabitants.
'NA' is indicated when no data is available.

Downloaded data from the working spreadsheet are processed with this [R script](https://code.montera34.com:4443/numeroteca/covid19/-/blob/master/analysis/process_spain_provinces_data.R) in another repository.

### Variables

Original data:

* `date` Day in yyyy-mm-dd format
* `province` Province
* `ine_code` INE code fro the province
* `ccaa` Comunidad autónoma (region)
* `new_cases` Number of new COVID-19 cases as reported in oficial data
* `activos` Active COVID-19 cases
* `hospitalized` Hospitalized (cumulative). [Ver wiki](https://github.com/montera34/escovid19data/wiki#hospitalizados)
* `intensive_care` UCI (intensive care patiens) (cumulative)
* `deceased` Deaths (cumulative)
* `cases_accumulated` Cases (cumulative)
* `recovered` Recovered (cumulative)
* `poblacion` Inhabitants of the province

Calculated data:

* `daily_cases` Daily cases. Calculated as a difference of cumulative cases reported.
* `daily_cases_avg7` Average daily cases in the last 7 days (rolling average 7 days) 
* `cases_per_cienmil` Cumulative cases per 100,000 inhabitants
* `intensive_care_per_100000` Cumulative cases per 100,000 inhabitants
* `deceassed_per_100000` Cumulative deaths per 100,000 inhabitants
* `daily_deaths` Daily deaths. Calculated as a difference of cumulative deaths reported.
* `daily_deaths_inc` Calculated as the percentage from last day (cumulative)
* `daily_deaths_avg3` Average daily deaths in the last 3 days (rolling average 3 days) 
* `daily_deaths_avg6` Average daily deaths in the last 7 days (rolling average 7 days) 
* `deaths_last_week` Deaths in the last 7 days.

Data sources and comments:

* `source_name` Name of source of information, separated by ;
* `source` Source of information, separated by ;
* `comments` Comments of the data

Structure of CSV:

| "date"       | "province"          | "ine\_code" | "ccaa"                 | "new\_cases" | "activos" | "hospitalized" | "intensive\_care" | "deceased" | "cases\_accumulated" | "recovered" | "poblacion" | "cases\_per\_cienmil" | "intensive\_care\_per\_100000" | "deceassed\_per\_100000" | "daily\_deaths" | "daily\_deaths\_inc" | "daily\_deaths\_avg3" | "daily\_deaths\_avg6" | "source"                                                            | "comments" |
|--------------|---------------------|-------------|------------------------|--------------|-----------|----------------|-------------------|------------|----------------------|-------------|-------------|-----------------------|---------------------------------|--------------------------|-----------------|----------------------|-----------------------|-----------------------|---------------------------------------------------------------------|------------|
| 2020\-03\-27 | "Badajoz"           | 6           | "Extremadura"          | 61           | 352       | 91             | 18                | 10         | 390                  | 27          | 673559      | 57\.9                 | 2\.67                           | 1\.48                    | 2               | 25                   | 2\.3                  | 1\.5                  | "http://www\.juntaex\.es/comunicac\.\.\."                           | ""         |
| 2020\-03\-27 | "Burgos"            | 9           | "Castilla y León"      | 74           | NA        | 243            | 49                | 39         | 604                  | 95          | 356958      | 169\.21               | 13\.73                          | 10\.93                   | 7               | 21\.9                | 5                     | 4\.2                  | "https://analisis\.datosabiertos\.jcyl\.es/pag\.\.\."               | ""         |
| 2020\-03\-27 | "Valencia/València" | 46          | "Comunitat Valenciana" | 239          | NA        | 840            | 140               | 88         | 2027                 | NA          | 2565124     | 79\.02                | 5\.46                           | 3\.43                    | 16              | 22\.2                | 14                    | 12\.2                 | "http://www\.san\.gva\.es/comunica\.\.\.pdf\)"                      | ""         |
| 2020\-03\-28 | "Almería"           | 4           | "Andalucía"            | NA           | 173       | 72             | NA                | 10         | 173                  | NA          | 716820      | 24\.13                | NA                              | 1\.4                     | 2               | 25                   | 1\.7                  | 1\.5                  | "https://www\.juntadeandalucia\.es/organismos/salu\.\.\.3791\.html" | ""         |

                                                                                               | 
### Población por provincias (2019)

Población por provincias del INE:  https://www.ine.es/jaxiT3/Datos.htm?t=2852#!tabs-tabla


## Sobre la iniciativa

Este es un proyecto colaborativo para mejorar los datos sobre COVID-19 en España por provincias.

* [Hoja de cálculo de trabajo](https://docs.google.com/spreadsheets/d/1qxbKnU39yn6yYcNkBqQ0mKnIXmKfPQ4lgpNglpJ9frE/edit#gid=0). Ayúdanos a completarla. Pide acceso. Si detectas errores háznoslo saber.
* Llamamiento inicial para colaborar iniciales para conseguir los datos de [@numeroteca](https://twitter.com/numeroteca/status/1239853592569425920) y [@ProsumidorSoc](https://twitter.com/ProsumidorSoc/status/1240569799056461826).

Contacto: covid19@montera34.com

### ¿Quíen está detrás de esto?

Hay muchas personas que nos habéis ayudado y aportado pistas. Gracias a todas por colaborar. 

Ahora mismo, estamos manteniendo los datos y amadrinando provincias y comunidades autónomas: [@ProsumidorSoc](https://twitter.com/ProsumidorSoc) [@numeroteca](https://twitter.com/numeroteca) [@arivero](https://twitter.com/arivero) [@ManoloYuri](https://twitter.com/ManoloYuri) [@congosto](https://twitter.com/congosto) [@skotperez](https://twitter.com/skotperez) [@allisdata](https://twitter.com/@allisdata) [@acorsin](https://twitter.com/acorsin) [@hhkaos](https://twitter.com/hhkaos) [@belengarcia_8](https://twitter.com/belengarcia_8) [@Tejerauskas](https://twitter.com/Tejerauskas) [@aniol](https://twitter.com/aniol) [@zgzmiki89](https://twitter.com/zgzmiki89) [@mota_santiago](https://twitter.com/mota_santiago) [@nachotronic](https://twitter.com/nachotronic) [@puzzle72](https://twitter.com/@puzzle72) [@montera34](https://twitter.com/@montera34) [@alfonsotwr](https://twitter.com/alfonsotwr) [@lipido](https://twitter.com/lipido) [@danielegrasso](twitter.com/danielegrasso)

Si se nos olvida alguien ¡avísanos!

Cada cual se encarga de una comunidad autónoma o provincia. [Ver sección "Organización" de la hoja de cálculo](https://docs.google.com/spreadsheets/d/1qxbKnU39yn6yYcNkBqQ0mKnIXmKfPQ4lgpNglpJ9frE/edit#gid=179891808).
 
## Visualizaciones y uso de los datos

Mándanos tu análisis o visualización si usas estos datos (covid19@montera34.com):

* [Gráficos y códido de R disponibles](https://lab.montera34.com/covid19/#fallecimientosDiaProvincias) mantenido por [@montera34](https://twitter.com/montera34)).
* [Dashboard interactivo en Tableau con los datos provinciales (en Tableau Public)](https://public.tableau.com/profile/javier.cant.n#!/vizhome/COVIDprov/Historia1?publish=yes) mantenido por [@ProsumidorSoc](https://twitter.com/ProsumidorSoc).
* [La evolución del COVID-19 en España y en el mundo, en gráficos](https://picanumeros.wordpress.com/2020/03/13/la-evolucion-del-covid-19-en-espana-en-graficos/) por [@picanumeros](https://twitter.com/picanumeros)
* [Mapas de afectados por coronavirus en España](https://mapa-de-afectados-por-coronavirus-plataformacovid.hub.arcgis.com/) iniciativa mantenida por voluntarios e impulsada por Esri España.
* [Un dashboard de análisis](https://cultureofinsight.shinyapps.io/covid-19/) mantenido por [@harlesden88](https://twitter.com/harlesden88).
* [Visualización de evolución de múltiples variables en modo cartograma](https://iguacel.github.io/iguacel/#/exp/20) mantenido por [@infoiguacel](https://twitter.com/infoiguacel).

### Prensa

* eldiario: ¿Por qué Canarias resiste al coronavirus y Soria no?  (Raquel Ejerique, Raúl Sánchez) https://www.eldiario.es/sociedad/Canarias-pocos-casos-coronavirus-Segovia_0_1017698330.html
* ABC: Las provincias que mejor y peor llegan para pasar a la siguiente fase de la desescalada (Luís Cano) https://www.abc.es/sociedad/abci-coronavirus-provincias-mejor-y-peor-llegan-para-pasar-siguiente-fase-desescalada-202005051948_noticia.html
* El País: Residencias, UCI y aglomeración: los puntos débiles de cada provincia para enfrentar al virus en la nueva fase Borja Andrino, Daniele Grasso, Kiko Llaneras)  https://elpais.com/sociedad/2020-05-10/residencias-uci-y-aglomeracion-los-puntos-debiles-de-cada-provincia-para-enfrentar-al-virus-en-la-nueva-fase.html
* El País: Lo que inquieta del estudio de prevalencia en España: ¿Un muerto por cada 100 infectados? (Borja Andrino, Daniele Grasso, Kiko Llaneras) https://elpais.com/sociedad/2020-05-13/lo-que-inquieta-del-estudio-de-prevalencia-en-espana-un-muerto-por-cada-100-infectados.html 
* El País: El mapa del riesgo de rebrote en España: consulta la situación de tu provincia (Borja Andrino, Daniele Grasso, Kiko Llaneras, Luís Sevillano, Ignacio Povedano, Fernando Hernández) https://elpais.com/especiales/2020/coronavirus-covid-19/fases-desescalada/riesgo-de-rebrotes/
* El País: Asteriscos, incoherencias y opacidad: 15 problemas de Sanidad con la gestión de datos del coronavirus  (Borja Andrino, Daniele Grasso, Kiko Llaneras) https://elpais.com/sociedad/2020-05-26/asteriscos-incoherencias-y-opacidad-15-problemas-del-ministerio-con-la-gestion-de-datos-del-coronavirus.html

### Artículos científicos

* Briz-Redón, Á., & Serrano-Aroca, Á. (2020). A spatio-temporal analysis for exploring the effect of temperature on COVID-19 early evolution in Spain. Science of The Total Environment, 138811. https://www.sciencedirect.com/science/article/pii/S0048969720323287
* "Effects of mobility and multi-seeding on the propagation of the COVID-19 in Spain" (pre-print) Mattia Mazzoli, David Mateo, Alberto Hernando, Sandro Meloni y Jose Javier Ramasco https://www.medrxiv.org/content/10.1101/2020.05.09.20096339v2
* "Regional correlations of COVID-19 in Spain" (pre-print) por Daniel Oto-Peralías https://osf.io/tjdgw/download

## Fuentes de información y estado de la base de datos

Puedes ver el análisis sobre las fuentes de información en este informe https://lab.montera34.com/covid19-r/reports/informe-escovid19data.html

Se han usado varias fuentes, la mayoría oficiales, algunas periodísicas, que se indican en cada una de los datos por día y provincia en la columna "source".
Puedes leer más información sobre cada [una de las fuentes en este documento](https://docs.google.com/document/d/12wkE0w1kdBHdwkj6AhPc0VnSQHgP_zz5rcVTyqng5y8/edit#).

También puedes encontrar (y contribuir) información actualizada en [la wiki  de este repositorio](https://github.com/montera34/escovid19data/wiki).

A continuación puedes encotnrar información sobre las fuentes de cada comunidad autónoma.

### Comunidades uniprovinciales: Asturias, Baleares, Cantabria, Madrid, Murcia, Navara y La Rioja (Ceuta y Melilla)

**Actualmente**: Se toma la serie histórica del Instituto de Salud Carlos III (https://covid19.isciii.es/resources/serie_historica_acumulados.csv). Se usan para algunas comunidades autónomas uniprovinciales los datos de fallecidos previos al 8 de marzo de 2020 [Datadista](https://github.com/datadista/datasets/tree/master/COVID%2019)

**Pasado**: Se usaba al principio los datos de RTVE, luego se sustituyó por los datos de los PDF del Ministerio de Sanidad que recopila Datadista.

### Andalucía

**Actualmente**: se utiliza [la serie histórica de acumulados](https://www.juntadeandalucia.es/institutodeestadisticaycartografia/badea/operaciones/consulta/anual/38228?CodOper=b3_2314&codConsulta=38228) que publica la Junta de Andalucía. La volcamos manualmente en nuestra hoja de cálculo en la pestaña "[andalucía](https://docs.google.com/spreadsheets/d/1qxbKnU39yn6yYcNkBqQ0mKnIXmKfPQ4lgpNglpJ9frE/edit#gid=1472471361)" y descargamos directamente desde ahí.

Fuente de datos (2020.04.28): Junta de Andalucía 100%.

**Pasado**: Para los primeros días se usaron los datos que ofrecía RTVE en la [visualización hecha con Flourish](https://public.flourish.studio/visualisation/1451263/). Más tarde se usaron las notas de prensa de la Junta de Andalucía ([ver ejemplo](https://www.juntadeandalucia.es/organismos/saludyfamilias/actualidad/noticias/detalle/233232.html) del 13.03.2020).

### Aragón

**Actualmente**: Se utilizan las notas de prensa publicadas en Aragonhoy.net (Gobierno de Aragón): [ejemplo de nota de prensa de 28.04.2020](http://www.aragonhoy.net/index.php/mod.noticias/mem.detalle/area.1379/id.259392). Lo datos se vuelcan en la pestaña común ["provincias" de la hoja de cálculo](https://docs.google.com/spreadsheets/d/1qxbKnU39yn6yYcNkBqQ0mKnIXmKfPQ4lgpNglpJ9frE/edit#gid=0). **Pasado**: Para los primeros días se usaron los datos que ofrecía RTVE en la [visualización hecha con Flourish](https://public.flourish.studio/visualisation/1451263/) y algunos periódicos.

Fuente de datos (2020.04.28): Gobierno de Aragón 66%, RTVE 21%, G. de Aragón y RTVE 8%, Prensa 5%.

### Canarias

**Actualmente**: Se utilizan las notas de prensa publicadas por el Gobierno de Canarias: [ejemplo de nota de prensa de 28.04.2020](https://www3.gobiernodecanarias.org/noticias/la-consejeria-de-sanidad-registra-1887-casos-acumulados-de-coronavirus-covid-19/). Lo datos se vuelcan en la pestaña común ["provincias" de la hoja de cálculo](https://docs.google.com/spreadsheets/d/1qxbKnU39yn6yYcNkBqQ0mKnIXmKfPQ4lgpNglpJ9frE/edit#gid=0) por isla.

Fuente de datos (2020.04.28): Gobierno de Canarias 100%.

### Castilla-La Mancha

**Actualmente**: Se utilizan las notas de prensa publicadas por el Castilla-La Mancha: [ejemplo de nota de prensa de 28.04.2020](https://www.castillalamancha.es/actualidad/notasdeprensa/contin%C3%BAa-la-tendencia-de-m%C3%A1s-altas-epidemiol%C3%B3gicas-y-menos-hospitalizados-en-castilla-la-mancha-en). Lo datos se vuelcan en la pestaña común ["provincias" de la hoja de cálculo](https://docs.google.com/spreadsheets/d/1qxbKnU39yn6yYcNkBqQ0mKnIXmKfPQ4lgpNglpJ9frE/edit#gid=0) por provincia.

Fuente de datos (2020.04.28): Gobierno de Castilla-La Mancha 73%, RTVE 27%.

### Castilla y León

**Actualmente**: Se copia pegan datos de [la página de datos abiertos](https://analisis.datosabiertos.jcyl.es/pages/coronavirus/) de la Junta de Castilla y León en la pestaña común ["provincias" de la hoja de cálculo](https://docs.google.com/spreadsheets/d/1qxbKnU39yn6yYcNkBqQ0mKnIXmKfPQ4lgpNglpJ9frE/edit#gid=0) por provincia.

Fuente de datos (2020.04.28): Junta de Castilla y León: 87%, RTVE 13%.

### Cataluña

**Actualmente**: 

* para los **casos** se usan los datos de [Transparencia de Catalunya](https://analisi.transparenciacatalunya.cat/Salut/Registre-de-test-de-COVID-19-realitzats-a-Cataluny/jj6z-iyrp/data) y se procesan con este script count_catalunya.R. Puedes ver el resultado en [este CSV](https://code.montera34.com:4443/numeroteca/covid19/-/blob/master/data/output/spain/catalunya-cases-evolution-by-province.csv). Se actualiza cada dos o tres días.

Fuente de datos (2020.05.05):  Transparencia de Catalunya 100% 

* para los **fallecidos** se ha volcado manualmente el contenido del [dashboard de Salut de la Generalitat](https://app.powerbi.com/view?r=eyJrIjoiZTkyNTcwNjgtNTQ4Yi00ZTg0LTk1OTctNzM3ZGEzNWE4OTIxIiwidCI6IjNiOTQyN2RjLWQzMGUtNDNiYy04YzA2LWZmNzI1MzY3NmZlYyIsImMiOjh9) en la [pestaña cat_ de la hoja de cálculo](https://docs.google.com/spreadsheets/d/1qxbKnU39yn6yYcNkBqQ0mKnIXmKfPQ4lgpNglpJ9frE/edit#gid=841105696) que está disponible en [este CSV](https://code.montera34.com:4443/numeroteca/covid19/-/blob/master/data/original/spain/catalunya/powerbi.csv). Se actualiza cada dos o tres días.
La pega es que los datos de fallebmimientos, al ser por región sanitaria no coinciden del todo con los límites geográficos de las provincia (ver siguiente tabla):

| PUEBLO /ZONA           | COMARCA REAL      | PROVÍNCIA REAL | RS ASIGNADA       | PROVINCIA RS |
|------------------------|-------------------|----------------|-------------------|--------------|
| Tora I Biosca          | Segarra           | Lleida         | Catalunya Central | Barcelona    |
| Vacarisses I Rellinars | Valles Occidental | Barcelona      | Catalunya Central | Barcelona    |
| Espinelves             | Osona             | Girona         | Catalunya Central | Barcelona    |
| Maresme Nord           | Maresme           | Barcelona      | Girona            | Girona       |
| Viladrau               | Osona             | Girona         | Catalunya Central | Barcelona    |
| Zona Baixa Segarra     | Anoia             | Barcelona      | Camp De Tarragona | Tarragona    |
| Cunit                  | Baix Penedes      | Tarragona      | Barcelona Sud     | Barcelona    |
| Gósol                  | Berguedà          | Lleida         | Catalunya Central | Barcelona    |
| Solsonés               | Solsonés          | Lleida         | Catalunya Central | Barcelona    |

Fuente de datos (2020.05.05):  Salut de Catalunya 100% 

* para otros datos como hospitalizados o cuidados intensivos hay una mezcla de fuentes periodísticas para Girona, Lleida y Tarragona. Falta indicar fuente para un 13%.

**Anteriormente**: los datos de casos y fallecidos para la provincia de Barcelona se calculaban en base al total de Cataluña (de Minsiterio de Sanidad- Datadista) y restando los datos de las otras tres provincias. Para Girona se usaba [este repositorio](https://github.com/nachotronic/covid19/blob/master/casos_girona.csv) mantenido por [@nachotronic](https://twitter.com/nachotronic). Para Lleida el gráfico publicado en [esta noticia de segre.com](https://www.segre.com/es/noticias/lleida/2020/03/24/lleida_suma_morts_positius_coronavirus_sol_dia_102336_1092.html). Para Tarragona múltiples fuentes periodísticas. Barcelona se calculaba restando al total de la comunidad autónoma los datos de las otras tres provincias catalanas.

### Comunidad Valenciana

**Actualmente**: Se utilizan las notas de prensa publicadas por la Generalitat Valenciana: [ejemplo de nota de prensa de 8.04.2020](https://www.gva.es/va/inicio/area_de_prensa/not_detalle_area_prensa?id=853677). Los datos se vuelcan en la pestaña común ["provincias" de la hoja de cálculo](https://docs.google.com/spreadsheets/d/1qxbKnU39yn6yYcNkBqQ0mKnIXmKfPQ4lgpNglpJ9frE/edit#gid=0) por provincia.

Fuente de datos (2020.04.28): Generalitat Valenciana 87%, RTVE 13%

### Extremadura

**Actualmente**: Se utilizan las notas de prensa publicadas por la Junta de Extremdura: [ejemplo de nota de prensa de 8.04.2020](http://www.juntaex.es/comunicacion/noticia?idPub=30056#.Xo29JnJS-Cg). Los datos se vuelcan en la pestaña común ["provincias" de la hoja de cálculo](https://docs.google.com/spreadsheets/d/1qxbKnU39yn6yYcNkBqQ0mKnIXmKfPQ4lgpNglpJ9frE/edit#gid=0) por provincia, previo cálculo, pues en las notas de prensa aparecen por áreas de Salud.

Los datos de personas recuperadas en Extremadura recogen todas las altas, tanto las de pacientes confirmados por PCR como los casos identificados por otras pruebas diagnósticas. 

Desde el 28 de abril, la Junta de Extremadura solo recoge en sus informes los casos confirmados por PCR. Esto produce un escalón a la baja en la serie, puesto que no se han ajustado las cifras de los días anteriores. Desde el 15 de mayo, las notas de prensa dejan de reflejar la cifra total de casos confirmados por área de salud, de modo que pueden producirse algunas diferencias con los datos reflejados en los informes diarios del Ministerio.

Fuente de datos (2020.04.28): Junta de Extremadura 81%, Prensa 10%, Falta Fuente 9%

### Galicia

**Actualmente**: se recopila de prensa. Por completar.

Fuente de datos (2020.04.28):  Prensa 38%, galiciancovid19.info 34%, RTVE 25%, Falta Fuente 3%

### País Vasco- Euskadi

**Actualmente**: se recopila de las notas de prensa publiadas en Irekia, la página de datos abiertos del Gobierno Vasco: [ejemplo de nota de prensa de 29.04.2020](https://www.irekia.euskadi.eus/es/news/61544-actualizacion-datos-covid-euskadig). Los datos se vuelcan en la pestaña común ["provincias" de la hoja de cálculo](https://docs.google.com/spreadsheets/d/1qxbKnU39yn6yYcNkBqQ0mKnIXmKfPQ4lgpNglpJ9frE/edit#gid=0) por provincia.

Fuente de datos (2020.04.28):  Osakidetza 61%, Gobierno de Euskadi 28%, RTVE 9%, Irekia 2%

## Cómo funciona el proceso de obtención y publicación de los datos

Cada madrina, reponsable de conseguir los datos, de una comunidad autónoma o provincia sube los datos a una hoja de cálculo común.
Los datos se descargan en este CSV: `data/original/covid19_spain_provincias.csv` para ser procesador con el [R script](https://code.montera34.com:4443/numeroteca/covid19/-/blob/master/analysis/process_spain_provinces_data.R) y se genera el CSV listo para usarse [/data/output/covid19-provincias-spain_consolidated.csv](https://github.com/montera34/escovid19data/-/blob/master/data/output//covid19-provincias-spain_consolidated.csv).

No todos los datos están disponibles en la hoja de cálculo compartida, como se indica en algunas comunidades se obtiene directamente de la fuente.

El proyecto tiene un grupo de Telegram con el que nos coordinamos. Escribe a covid19@montera34.com para apuntarte y saber más.
