



Zadanie 3
```sql
#1
select s.nazwa, ew.sektor
from sektor s
inner join etapy_wyprawy ew on s.id_sektora=ew.sektor
group by s.id_sektora;
```
```sql
#2
select k.nazwa,
if(count(u.id_uczestnika) > 0,
'brał udział w wyprawie',
'niebrał udziału w wyprawie') 
from kreatura k
left join uczestnicy u on u.id_uczestnika=k.idKreatury
group by k.idKreatury;
```
Zadanie 4
```sql
#1
select w.nazwa,sum(length(dziennik)) from wyprawa w inner join etapy_wyprawy e on w.id_wyprawy=e.idWyprawy group by w.nazwa
having sum(length(dziennik)) <400;
```
```sql
#2
select w.nazwa,avg(waga) from wyprawa w inner join uczestnicy u on w.id_wyprawy=u.id_wyprawy
inner join ekwipunek e on u.id_uczestnika=e.idKreatury
inner join zasob z on e.idZasobu=z.idZasobu group by w.nazwa;
```
```sql
