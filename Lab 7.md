Zadanie 1
```sql
#1
select avg(waga) from kreatura
where rodzaj='wiking';
```
```sql
#2
select rodzaj, avg(waga), count(waga),
count(*)
from kreatura group by rodzaj;
```
```sql
#3
select 2023 - year(dataUr) as wiek from kreatura;
```
Zadanie 2
```sql
#1
select sum(waga*ilosc) from zasob order by rodzaj;
```
```sql
#2
select avg(waga) from zasob group by nazwa having sum(ilosc)>=4 and sum(waga*ilosc)>10;
```
```sql
#3
SELECT rodzaj, COUNT(DISTINCT nazwa) AS liczbanazw FROM zasob GROUP BY rodzaj HAVING min(liczbanazw) > 1;
```
Zadanie 3
```sql
#1
select k.nazwa,e.idZasobu,z.nazwa from kreatura k inner join ekwipunek e on k.idKreatury=e.idKreatury;
```
```sql
#2
select k.nazwa,e.idZasobu,z.nazwa from kreatura k inner join ekwipunek e on k.idKreatury=e.idKreatury inner join zasob z on
z.idZasobu=e.idZasobu;
```
```sql
#3
select idKreatury from kreatura
where idKreatury not in 
(select distinct idKreatury from ekwipunek
where idKreatury is not null);
```
Zadanie 4
```sql

```
#3
```sql
select concat(k1.nazwa,' - ',k2.nazwa)
from kreatura k1
inner join kreatura k2
where k1.idKreatury - k2.idKreatury = 5;
```
#
