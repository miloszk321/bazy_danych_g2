```sql
1.select imie,nazwisko,data_urodzenia from pracownik;
2.SELECT imie,nazwisko,YEAR(NOW()) - YEAR(data_urodzenia) AS wiek FROM pracownik;
3.SELECT d.nazwa, COUNT(id_pracownika) from dzial d inner join pracownik p on d.id_dzialu=p.dzial group by d.nazwa;
4.select k.nazwa_kategori, count(t.id_towaru) from kategoria k inner join towar t on k.id_kategori=t.kategoria group by k.nazwa_kategori;
5.select k.nazwa_kategori, group_concat(t.nazwa_towaru) from kategoria k inner join towar t on k.id_kategori=t.kategoria group by k.nazwa_kategori;
6.select round(avg(pensja),2) from pracownik;
7.select round(avg(pensja),2) from pracownik where (year(now())-year(data_zatrudnienia))>5;
8.select nazwa_towaru,count(towar) from pozycja_zamowienia p inner join towar t on p.towar=t.id_towaru group by nazwa_towaru order by count(towar) desc limit 10;
9.select numer_zamowienia,sum(ilosc*cena) from zamowienie z inner join pozycja_zamowienia p on z.id_zamowienia=p.zamowienie where data_zamowienia between '2017-01-01' and '2017-03-01' group by id_zamowienia;
10.
