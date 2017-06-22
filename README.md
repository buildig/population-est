# population-est

Eesti rahvaarv omavalitsuste lõikes [CSV formaadis](https://github.com/buildig/population-est/blob/master/omavalitsus_rahvaarv.csv). / Estonian population per local governments in [CSV format](https://github.com/buildig/population-est/blob/master/omavalitsus_rahvaarv.csv).

See [releases](https://github.com/buildig/population-est/releases) for snapshot's metadata.

Fields:

- OKOOD - Code of the local government
- ONIMI - Name of the local government
- ONIMI	= 'Aadressita isikud' - People with no fixed address
- ONIMI	= 'Välisriigi aadressiga' - People with foreign address
- MNIMI
- MKOOD
- AREA - area in m2
- MEHED - No. of men
- NAISED - No. of women
- KOKKU - Total
- DENSITY - KOKKU / AREA (km2)

## Population data combined with EHAK 
```
php -r "readfile('https://github.com/buildig/EHAK/raw/master/geojson/omavalitsus.json');" > omavalitsus.json
mapshaper omavalitsus.json -join rahvaarv.csv keys=ONIMI,ONIMI -each 'DENSITY=((KOKKU/(AREA/1000000)).toFixed(2))/1' -o omavalitsus_rahvaarv.json
mapshaper omavalitsus.json -join rahvaarv.csv keys=ONIMI,ONIMI -each 'DENSITY=((KOKKU/(AREA/1000000)).toFixed(2))/1' -o omavalitsus_rahvaarv.csv
```
