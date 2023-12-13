
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
