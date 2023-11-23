use infs_klusinskim;
select * from postac;

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
# pkt 2
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

# zadanie 5


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
#5


alter table postac change
id_postaci id_postaci int;
alter table postac modify
id_postaci int;
alter table statek
drop foreign key statek_ibfk_1;
show create table postac;
alter table przetwory
drop foreign key przetwory_ibfk_2;

alter table postac
add column pesel char(11) first;
desc postac;
select * from postac;
update postac set pesel='6543674832' + id_postaci;
#mamy unikalne wartosci kolumnie pesel
# mozemy wiec dodac klucz glowny
alter table postac add primary key(pesel);
#zadanie 2 pkt 2
alter table postac modify 
rodzaj enum('wiking', 'ptak', 'kobieta', 'syrena');
#pkt 3
select * from postac;
insert into postac values
(67893245681,10,'Gertruda Nieszczera','1893-11-03','syrena','130', null);
#zadanie 3
where nazwa like 'd%';
# % dowolny ciag znakow
# _ - dokladnie jeden znak
select nazwa from statek;
where nazwa regexp '^[a-f]{2}=[0-9]{3}';
update postac set statek='kajak'
where nazwa like '%a%';
select * from statek;
where data_wodowania >= '1700-12-06'
and data_wodowania <= '1700-12-09';
where data_wodowania between '1700-12-06'
and '1700-12-09';
update statek set max_ladownosc=max_ladownosc * 0.7
where year(data_wodowania) between 1600 and 2000;
alter table postac add check(wiek < 1000);
update postac set wiek=2000 where nazwa='Bjorn';
#zadanie 4
alter table postac modify 
rodzaj enum('wiking', 'ptak', 'kobieta', 'syrena','waz');
insert into postac values 
(67893245684,11,'Loko','1900-11-03','waz','223', null,null);
#pkt b
create table marynarz like postac;
desc marynarz;
insert into marynarz select * from postac
where statek_nazwa is not null;

create table marynarz2 as select * from postac
where statek_nazwa is not null;

select * from marynarz;

#zadanie 5

INSERT INTO marynarz
select * from postac
WHERE statek_nazwa IS NOT NULL;
