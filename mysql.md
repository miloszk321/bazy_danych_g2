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
