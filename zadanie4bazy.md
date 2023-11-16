use infs_klusinskim;
select * from postac;
```sql
#lab 3, zadanie 3
create table izba (
adres_budynku varchar(50) not null,
nazwa_izby varchar(50) not null,
metraz mediumint unsigned,
wlasciciel int,

foreign key (wlasciciel)
references postac(id_postaci) 
);
# on delete lub update -> restrict set null cascade



drop table izba;
alter table izba add column
kolor varchar(30) default 'czarny'
after metraz;
describe izba;
#pkt 3
insert into izba values 
('Kolejowa 23','spiżarnia',10,default,1);
select * from izba;

#dodac klucz głowny do tabeli izba
alter table izba add 
primary key(adres_budynku, nazwa_izby);
```
#4
```sql
create table przetwory (
id_przetworu int primary key,
rok_produkcji smallint default '1654',
id_wykonawcy int,
zawartosc varchar(255),
dodatek varchar(255) default 'papryczka chilli',
id_konsumenta int,
FOREIGN KEY (id_wykonawcy) REFERENCES postac(id_postaci),
FOREIGN KEY (id_konsumenta) REFERENCES postac(id_postaci)

);

select * from przetwory;

insert into przetwory values 
 (1,default,1,'bigos',default,1);
```
# zadanie 5
```sql

 insert into postac values 
 (9,'piotr','1700-11-09','wiking','323');

select * from postac;
create table statek (
nazwa_statku varchar(50) primary key,
rodzaj_statku ENUM('barka', 'pasazerski', 'wojenny') default NULL,
data_wodowania date,
 max_ladownosc INT CHECK (max_ladownosc > 0)
 );
select * from statek;
insert into statek values
('ponton','pasazerski','1700-12-06','10');

alter table postac add column
funkcja varchar(45);
select * from postac;
UPDATE `infs_klusinskim`.`postac` SET `funkcja` = 'kapitan' WHERE (`id_postaci` = '1');
```
