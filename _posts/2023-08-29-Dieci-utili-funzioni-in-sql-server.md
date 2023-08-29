---
layout: post
title: Una raccolta di utili funzioni in sql server
subtitle: Rendere disponibile una dipendenza in locale senza attingere da Maven Central
#cover-img: /assets/img/path.jpg
#thumbnail-img: /assets/img/thumb.png
#share-img: /assets/img/path.jpg
tags: [Sql, Sql Server, Query]
---

Una raccolta di utili funzioni in sql server che permettono di risolvere le più comuni difficoltà nella generazione di una query.


- CAST()
Questa funzione permette la conversione di un data type in un altro data type
```
SELECT Cast(10 AS VARCHAR); 
```

- COALESCE()
Questa funzione ritorna il primo valore non null da una lista di espressioni
```
SELECT COALESCE(NULL, 'value2', 'value3'); 
```

- NVL()
La funzione NVL sostituisce i valori null con un valore predefinito specificato.
```
SELECT Nvl(NULL, 'default value'); 
```

- CASE
L'espressione case esegue operazioni condizionali in base a un'espressione specificata.
```
SELECT CASE
         WHEN 1 = 1 THEN 'true'
         ELSE 'false'
       END; 
```

- CONVERT()
La funzione convert converte un valore in un tipo di dati specificato.
```
SELECT CONVERT(VARCHAR, 10); 
```

- STRING_SPLIT()
La funzione split divide una stringa in una tabella di sottostringhe.
```
String_split('apple,banana,cherry', ',');
```

- MID()
La funzione mid estrae una sottostringa da una stringa, iniziando da una posizione specificata e con una lunghezza specificata.
```
SELECT Mid('apple', 2, 3); 
```

- DATEADD()
La funzione di aggiunta data aggiunge un numero specificato di intervalli (come giorni, mesi o anni) a una data.
```
SELECT Dateadd(day, 7, '2023-05-05'); 
```

- DATE_FORMAT()
La funzione di formato data riformatta un valore di data in una stringa con un formato specificato.
```
SELECT Date_format('2023-05-05', '%m/%d/%Y'); 
```

- DATEPART()
La funzione della parte della data estrae una parte specifica di una data, ad esempio anno, mese o giorno.
```
SELECT Datepart(year, '2023-05-05'); 
```

- DAYOFWEEK()
La funzione del giorno della settimana restituisce il giorno della settimana per una determinata data.
```
SELECT Dayofweek('2023-05-05'); 
```

-  TRIM()
La funzione trim rimuove gli spazi iniziali e finali da una stringa.
```
SELECT Trim(' banana '); 
```

-  FORMAT()
La funzione format riformatta un valore in un formato di stringa specificato.
```
SELECT Format(12345.6789, '#,##0.00'); 
```

-  REPLACE()
La funzione di sostituzione sostituisce una stringa specificata con un'altra stringa in una determinata espressione.
```
SELECT Replace('banana', 'a', 'e'); 
```