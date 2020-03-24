
# Daily number of COVID-19 tests by country – time-series

Currently coveres (most of) Europe up until the 23. March 2020. I was unable to find official numbers for: BE, IE, NL, ES, CH, DE, MT. Note differences in the reported units:

* __Number of people tested:__ SE, NO, DK, UK, LV, SI, PT.
* __Number of samples tested:__ AT, FI, IS,FR, HR, CZ, EE, HU, IE, LT, PL, RO, SK, IT.

For other countries, see the list of [coronavirus testing data sources](https://ourworldindata.org/coronavirus-testing-source-data) compiled by _Our World in Data_ (Esteban Ortiz-Ospina).

This data will be added to Wikidata to ease collaboration and updating. To extract data from Wikidata use the following [query](https://query.wikidata.org/):

```SPARQL
SELECT ?item ?itemLabel ?dates ?caseNo ?deathNo ?testNo ?countryLabel WHERE {
  ?item wdt:P361 wd:Q83741704.
  OPTIONAL { ?item wdt:P17 ?country. }
  ?item p:P1603 ?cases.
  ?cases ps:P1603 ?caseNo;
    pq:P585 ?dates.
  OPTIONAL {
    ?item p:P1120 ?deaths.
    ?deaths pq:P585 ?dates;
      ps:P1120 ?deathNo.
  }
  OPTIONAL { 
    ?item p:P1114 ?test. 
    ?test pq:P805 wd:Q86901049.
    ?test pq:P585 ?dates;
      ps:P1114 ?testNo
  }
  SERVICE wikibase:label { bd:serviceParam wikibase:language "[AUTO_LANGUAGE],en". }
}
ORDER BY (?country) (?dates)
```



