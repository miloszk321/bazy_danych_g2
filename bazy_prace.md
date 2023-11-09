# Zadania lab_04
## Zadanie 1


```sql
 create table postac (
    -> id_postaci int auto_increment primary key,
    -> nazwa VARCHAR(40),
    -> data_ur date
    -> rodzaj enum('wiking','ptak','kobieta'),
    -> wiek int unsigned);
```sql


create table walizka(
    -> id_walizki int primary key auto_increment,
    -> pojemnosc int unsigned,
    -> kolor enum('rozowy','czerwony','teczowy','zolty'),
    -> id_wlasciciela int,
    -> foreign key(id_wlasciciela) references postac(id_postaci) on delete cascade);
``` 



