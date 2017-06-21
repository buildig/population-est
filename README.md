# population-est

Eesti rahvaarv omavalitsuste lõikes [CSV formaadis](https://github.com/buildig/population-est/blob/master/omavalitsus_rahvaarv.csv). / Estonian population per local governments in [CSV format](https://github.com/buildig/population-est/blob/master/omavalitsus_rahvaarv.csv).

See [releases](https://github.com/buildig/population-est/releases) for snapshot's metadata.

Fields:

- OKOOD - Code of the local government
- ONIMI - Name of the local government
- ONIMI	= 'Aadressita isikud' - People with no fixed address
- ONIMI	= 'Välisriigi aadressiga' - People with foreign address
- MEHED - No. of men
- NAISED - No. of women
- KOKKU - Total

## Population data with EHAK 
```
php -r "readfile('https://github.com/buildig/EHAK/raw/master/geojson/omavalitsus.json');" > omavalitsus.json
mapshaper omavalitsus.json -join omavalitsus_rahvaarv.csv keys=ONIMI,ONIMI
```
