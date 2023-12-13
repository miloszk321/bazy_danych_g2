# Zadania lab_04
## Zadanie 1
#1
```sql
 create table postac (
    -> id_postaci int auto_increment primary key,
    -> nazwa VARCHAR(40),
    -> data_ur date
    -> rodzaj enum('wiking','ptak','kobieta'),
    -> wiek int unsigned);
#2
insert into postac values(default, 'Bjorn','1700-01-01','wiking',323);
insert into postac values(default, 'Drozd','1893','Ptak',130);
insert into postac values(default, 'Tesciowa','1000-01-01','kobieta',2000);
#3
Update postac
set wiek=88
where id_postaci=3;
```
Zadanie 2
```sql
#1
create table walizka(
    -> id_walizki int primary key auto_increment,
    -> pojemnosc int unsigned,
    -> kolor enum('rozowy','czerwony','teczowy','zolty'),
    -> id_wlasciciela int,
    -> foreign key(id_wlasciciela) references postac(id_postaci) on delete cascade);
#2
alter table walizka alter column kolor set default 'różowy';
#3
insert into walizka values(default,100,'tęczowy',1);
insert into walizka values(default,50,default,3);
```
Zadanie 3
```sql
#1
create table izba (
adres_budynku varchar(50) not null,
nazwa_izby varchar(50) not null,
metraz mediumint unsigned,
wlasciciel int,

foreign key (wlasciciel)
references postac(id_postaci) 
);
#2
alter table izba add column
kolor varchar(30) default 'czarny'
after metraz;
#3
insert into izba values 
('Kolejowa 23','spiżarnia',10,default,1);
select * from izba;
Zadanie 4
#1
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
#2
insert into przetwory values 
 (1,default,1,'bigos',default,1);
Zadanie  5
#1
insert into postac values 
 (9,'piotr','1700-11-09','wiking','323');
insert into postac values 
 (10,'Marek','1702-11-09','wiking','321');
insert into postac values 
 (11,'Daniel','1701-11-09','wiking','322');
insert into postac values 
 (12,'Marian','1715-11-09','wiking','308');
#2
create table statek (
nazwa_statku varchar(50) primary key,
rodzaj_statku ENUM('barka', 'pasazerski', 'wojenny') default NULL,
data_wodowania date,
 max_ladownosc INT CHECK (max_ladownosc > 0)
 );
#3
insert into statek values
('ponton','pasazerski','1700-12-06','10');
select * from statek;
insert into statek values
('kajak','wojenny','1705-12-06','10');
#4
alter table postac add column
funkcja varchar(45);
#5
UPDATE postac SET funkcja = 'kapitan' WHERE (`id_postaci` = '1');
#6
alter table postac add column statek varchar(50) 
alter table postac add foreign key(statek) references statek(nazwa_statku)
#7
update postac set statek='kajak' where rodzaj='wiking'
update postac set statek='ponton' where rodzaj='ptak'
#8
delete from izba where nazwa_izby='spiżarnia'
#9
drop table izba


