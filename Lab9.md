```sql
1.select imie,nazwisko,data_urodzenia from pracownik;
```
```sql
2.SELECT imie,nazwisko,YEAR(NOW()) - YEAR(data_urodzenia) AS wiek FROM pracownik;
```
```sql
3.SELECT d.nazwa, COUNT(id_pracownika) from dzial d inner join pracownik p on d.id_dzialu=p.dzial group by d.nazwa;
```
```sql
4.select k.nazwa_kategori, count(t.id_towaru) from kategoria k inner join towar t on k.id_kategori=t.kategoria group by k.nazwa_kategori;
```
```sql
5.select k.nazwa_kategori, group_concat(t.nazwa_towaru) from kategoria k inner join towar t on k.id_kategori=t.kategoria group by k.nazwa_kategori;
```
```sql
6.select round(avg(pensja),2) from pracownik;
```
```sql
7.select round(avg(pensja),2) from pracownik where (year(now())-year(data_zatrudnienia))>5;
```
```sql
8.select nazwa_towaru,count(towar) from pozycja_zamowienia p inner join towar t on p.towar=t.id_towaru group by nazwa_towaru order by count(towar) desc limit 10;
```
```sql
9.select numer_zamowienia,sum(ilosc*cena) from zamowienie z inner join pozycja_zamowienia p on z.id_zamowienia=p.zamowienie where data_zamowienia between '2017-01-01' and '2017-03-01' group by id_zamowienia;
```
```sql
10.select pr.imie, pr.nazwisko, sum(pz.ilosc*pz.cena) as suma from zamowienie z inner join pozycja_zamowienia pz on z.id_zamowienia=pz.zamowienie inner join pracownik pr on pr.id_pracownika=z.pracownik_id_pracownika group by z.pracownik_id_pracownika order by suma desc
```
Zadanie 2
```sql
1.select d.nazwa, min(p.pensja), max(p.pensja) 
```
```sql
2.select z.numer_zamowienia, sum(pz.ilosc*pz.cena) as wartosc, z.klient, k.pelna_nazwa from zamowienie z inner join pozycja_zamowienia pz on z.id_zamowienia=pz.zamowienie inner join klient k on k.id_klienta=z.klient group by z.id_zamowienia order by wartosc desc limit 10;
```
```sql
3.
