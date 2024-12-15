# Data ophalen

## Compositie laden
Compositie ophalen met /rest/openehr/v1/ehr/{ehr_id}/composition/{versioned_object_uid}

## AQL

Om alle EHR IDs uit de database op te halen kan men de volgende query gebruiken:
```sql
SELECT e/ehr_id/value
FROM EHR e
```

Om alle composities op te halen die we net hebben gepost met hun respectievelijke EHR IDs kunnen we de volgende query
gebruiken:
```sql
SELECT e/ehr_id/value, c/uid/value 
FROM EHR e 
    CONTAINS COMPOSITION c 
WHERE 
    c/name/value = 'workshop-example'
```

{
"q": "SELECT e/ehr_id/value, c/uid/value FROM EHR e CONTAINS COMPOSITION c WHERE c/name/value = 'workshop-example'"
}

