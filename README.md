# SQL-MieszalniaFarb

## Opis problemu: 
Projekt przedstawia relacyjną bazę danych zaprojektowaną dla punktu produkcyjno-sprzedażowego farb. System wspiera pełny proces biznesowy: od zarządzania surowcami (bazy i pigmenty), przez definiowanie złożonych receptur, aż po obsługę zamówień klientów i monitorowanie wydajności pracowników.

## Funkcje:
- kontrola zgodności zamówień
- przeglądanie receptur i zamówień przez pracowników
- możliwość dodawania, edytowania i usuwania receptur przez kierownika
- zmiana statusu zamówień (w realizacji/zakończone)
- dostęp doradcy klienta do informacji o kliencie i jego zamówieniach
- każda receptura będzie się składała z bazy oraz wielu pigmentów
  
## Zastosowane narzędzia: 
- Język: SQL/ PL/SQL
- DBMS: Oracle Database
- Narzędzia: Oracle SQL Developer

## Struktura baz danych:
1. BAZY_FARB: Katalog dostępnych baz (akrylowe, lateksowe, olejne) wraz z ich kosztem i pojemnością.
2. PIGMENTY: Baza barwników identyfikowanych przez kody kolorów i wartości HEX.
3. RECEPTURY: Definicje kolorów gotowych, określające wymaganą ilość bazy.
4. RECEPTURA_PIGMENTY: Tabela łącząca wiele-do-wielu, określająca gramaturę poszczególnych pigmentów w danej recepturze.
5. KLIENCI: Rejestr danych kontaktowych i adresowych klientów.
6. PRACOWNICY: Dane personelu z podziałem na stanowiska (Manager, Doradca, Technolog, Pracownik).
7. ZAMOWIENIA: Centralna tabela procesowa łącząca wszystkie aspekty systemu.
W celu optymalizacji wydajności zaimplementowano indeksy na kluczowych kolumnach: NAZWISKO klienta, BAZA_ID w recepturach oraz identyfikatorach w zamówieniach.

## Przykładowe Raporty
W pliku `raporty.sql` znajdują się zapytania:
Raport 1 - pokazuje listę wszystkich zamówień wraz z datą, klientem, ilością litrów i statusem, posortowaną od najnowszych.
Raport 2 - przedstawia pracowników oraz liczbę przypisanych im zamówień, uporządkowaną malejąco według liczby realizacji.
Raport 3 - pokazuje dla każdej receptury łączną ilość sprzedanych litrów oraz całkowity koszt produkcji zrealizowanych zamówień.
Raport 4 - przedstawia aktywnych pracowników wraz z liczbą obsłużonych zamówień, liczbą unikalnych klientów i średnią ilością litrów na zamówienie.
Raport 5 - pokazuje stan magazynowy baz farb, ile litrów jest zarezerwowanych w bieżących zamówieniach oraz ostrzeżenie o poziomie zapasów.
Raport 6 - przedstawia zużycie pigmentów, czyli w ilu recepturach występują oraz ile gramów łącznie zużyto w zrealizowanych zamówieniach.


## Jak uruchomić projekt
- Uruchom skrypt `createTable.sql`, aby utworzyć strukturę tabel i indeksów.
- Załaduj dane testowe za pomocą `insertInto.sql` (zawiera ponad 60 rekordów klientów i liczne zamówienia).
- Wykorzystaj `raporty.sql` do generowania analiz biznesowych.
