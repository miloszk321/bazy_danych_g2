
#Bazy danych 3 
Zadanie 1
```sql
#a
CREATE TABLE kreatura AS SELECT * FROM wikingowie.kreatura;
CREATE TABLE zasob AS SELECT * FROM wikingowie.zasob;
CREATE TABLE ekwipunek AS SELECT * FROM wikingowie.ekwipunek;
#2
SELECT * FROM wikingowie.zasob;
#3
SELECT * FROM wikingowie.zasob WHERE rodzaj = 'jedzenie';
#4
SELECT idZasobu, ilosc FROM ekwipunek WHERE idKreatury IN  (1, 3, 5);
```
Zadanie 2
```sql
#1
SELECT * FROM kreatura
WHERE rodzaj <> 'wiedźma' AND udzwig <= 50;
#2
SELECT * FROM zasob
where waga between 2 and 5;
#3
select * from kreatura
where nazwa like '%or%' AND udzwig between 30 and 70;
```
Zadanie 3
```sql
#1
SELECT * FROM zasob
WHERE MONTH(dataPozyskania) IN (7, 8);
#2
select * from zasob
where rodzaj is not null order by waga asc;
#3

