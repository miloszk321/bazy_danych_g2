Zadanie 1
```sql
#1
delete from postac
where nazwa<>'Bjorn'
and rodzaj='wiking'
order by data_ur asc limit 2;
```
```sql
#2
alter table statek
drop foreign key statek_ibfk_1;
alter table przetwory
drop foreign key przetwory_ibfk_2;
alter table walizka
drop foreign key walizka_ibfk_1;
alter table postac modify id_postaci int;
alter table postac drop primary key;
```
Zadanie 2
```sql
#1
alter table postac
add column pesel char(11) first;
update postac set pesel='6543674832' + id_postaci;
alter table postac add primary key(pesel);
```
```sql
#2
alter table postac modify 
rodzaj enum('wiking', 'ptak', 'kobieta', 'syrena');
```
```sql
#3
insert into postac values
(67893245681,10,'Gertruda Nieszczera','1893-11-03','syrena','130', null);
```
Zadanie 3
```sql
#1
update postac set statek='kajak'
where nazwa like '%a%';
```
```sql
#2
update statek set max_ladownosc=max_ladownosc * 0.7
where year(data_wodowania) between 1600 and 2000;
```
```sql
#3
alter table postac add check(wiek < 1000);
```
Zadanie 4
```sql
#1
alter table postac modify 
rodzaj enum('wiking', 'ptak', 'kobieta', 'syrena','waz');
insert into postac values 
(67893245684,11,'Loko','1900-11-03','waz','223', null,null);
```
```sql
#2
create table marynarz like postac;
insert into marynarz select * from postac where statek_nazwa is not null;
```
```sql
#3
alter table marynarz add foreign key(statek) references statek(statek_nazwa);
```
Zadanie 5
```sql
#1
update postac set statek=null;
```
```sql
#2
delete from postac where rodzaj='wiking' and nazwa<>'Bjorn' limit 1;
```
```sql
#3
alter table postac drop foreign key postac_ibfk_1;
alter table marynarz drop foreign key marynarz_ibfk_1;
delete from statek;
```
```sql
#4
drop table statek;
```
```sql
#5
create table zwierz(
id int primary key auto_increment,
nazwa varchar(50),
wiek int);
```
```sql
#6
insert into zwierz(nazwa,wiek) select nazwa,wiek from postac where rodzaj='ptak' or rodzaj='wąż';
```
