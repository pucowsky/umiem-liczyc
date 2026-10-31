# Umiem Liczyć

Strona internetowa stworzona z myślą o nauce i ćwiczeniu umiejętności matematycznych w prosty, przejrzysty i angażujący sposób.

## Opis projektu

Umiem Liczyć to projekt osobisty mający na celu wspieranie nauki matematyki poprzez interaktywne zadania, prosty układ graficzny i przejrzysty proces ćwiczenia. Aplikacja została zaprojektowana tak, aby nauka była bardziej dostępna, uporządkowana i motywująca.

Celem projektu jest nie tylko stworzenie funkcjonalnego narzędzia do ćwiczeń, ale również pokazanie praktycznych umiejętności w obszarze tworzenia aplikacji, projektowania doświadczeń użytkownika oraz rozwiązywania realnych problemów w prostym i czytelnym systemie.

## Dlaczego ten projekt?

Matematyka to obszar, który wymaga regularnej praktyki, zrozumienia oraz pewności siebie. Wiele narzędzi edukacyjnych jest zbyt skomplikowanych, zbyt ubogich lub mało angażujących, dlatego warto tworzyć rozwiązania, które są:
- proste w obsłudze
- czytelne wizualnie
- wspierające naukę krok po kroku
- dostępne dla użytkownika na każdym poziomie zaawansowania

Zadaniem platformy jest:
* umożliwienie szybkiej i wygodnej metody rezerwacji lekcji korepetycji
* zachęcenie użytkowników do systematycznej pracy i wizualizacja małych postępów
* diagnoza powtarzających się schematów błędów
* powtórzenie wiedzy fundamentalnej przed kolejnym zaawansowaniem
* użycie konkretnych modeli przed przejściem do abstrakcji
* dostosowanie do potrzeb użytkownika

## Funkcjonalności

1. Strona główna
   * responsywny układ
   * nawigacja
   * sekcja przedstawiająca markę
   * sekcja bohaterów:
      - odczytywanie z bazy danych i wyświetlanie
      - dodawanie do bazy danych w panelu użytkownika
      - ukrywanie wyświetlania w panelu administratora
      - edytowanie w panelu użytkownika
      - moderacja w panelu administratora
      - limit długości
      - kolejność wyświetlania
      - antyspam
  * sekcja oferty:
      - dynamiczne wyświetlanie cen
  * sekcja kalendarza publicznego:
      - wyświetlanie dostępności nauczycieli
      - przejście do rezerwacji
      - alternatywnie widget calendly
      - subskrypcja kalendarza w urządzeniu zewnętrznym
      - synchronizacja z subskrybowanym kalendarzem w urządzeniu zewnętrznym
  * sekcja nauczycieli
  * sekcja formularza kontaktowego:
      - wysyłka e-maili
      - autoresponder
      - elastyczny szablon
      - numerowane zgłoszenia
      - walidacja danych
      - bezpieczne unikanie tagów html
      - honeypot
      - antyspam
      - rate limit
    * stopka 
2. Ciasteczka
3. Rejestracja
  * logowanie i wylogowywanie
  * hashowanie haseł
  * resetowanie hasła
  * e-mail potwierdzający
4. Interfejs użytkownika
  * Uczeń:
      - ścieżka postępu z kamieniami milowymi, odznaki
      - historia lekcji
      - podgląd kalendarza, propozycje terminów lekcji jednorazowych i regularnych
      - subskrypcja kalendarza w urządzeniu zewnętrznym
  * Rodzic:
      - podgląd postępów ucznia/ów
  * Nauczyciel
  * Administrator:
      - generowanie paragonów na żądanie, elastyczny szablon
      - system płatności
5. Zadanie dnia
  * interaktywna tablica wirtualna
  * passa
6. Minigra detektywistyczna
7. Newsletter

## Struktura

Projekt wykorzystuje elementy modelu MVC.

Cykl życia requestu
```text
Browser -> public/index.php -> config/routes.php -> App\Core\Router
    -> middleware -> controller -> service/model -> PDO Db -> view -> App\Core\Response -> Browser
```

Kontroler frontu definiuje `BASE_PATH`, `APP_PATH` i `CFG_PATH`, wczytuje `Composer`, odczytuje dane środowiskowe `config/.env`, konfiguruje errory i logi, rozpoczyna sesję, rejestruje obiekty fabryczne, wczytuje ścieżki i nadania.

Widoki są generowane po stronie serwera z dodatkami JavaScriptu.

Brakuje pipeline, npm build, kolejki zadań, adapterów.

Drzewo katalogów
```bash
umiemliczyc/
|-- app/
|    |-- Controllers/
|    |    |-- Administrator/
|    |    |-- Nauczyciel/
|    |    |-- Rodzic/
|    |    |-- Uczen/ 
|    |    |-- Public/ 
|    |    |-- Auth/ 
|    |    |-- Documents/
|    |    |-- Shared/ 
|    |-- Core/    
|    |    |-- Request.php
|    |    |-- Response.php
|    |    |-- Routes.php
|    |    |-- Database.php
|    |-- Middleware/
|    |    |-- AuthMiddleware.php
|    |    |-- RoleMiddleware.php
|    |    |-- CsrfMiddleware.php
|    |-- Models/
|    |    |-- Dostepnosc.php
|    |    |-- Blog.php
|    |    |-- Heroes.php
|    |    |-- Spotkanie.php
|    |    |-- CyklicznaSeria.php
|    |    |-- ICalToken.php
|    |    |-- RezerwacjaPubliczna.php 
|    |-- Services/
|    |    |-- ZadanieDnia 
|    |    |-- Mailer
|    |    |-- Calendar
|    |    |-- Documents 
|    |    |-- Rendering  
|    |-- Views/
|    |-- config/
|    |    |-- .env
|    |    |-- routes.php
|    |-- database/
|    |    |-- schema/
|-- public/
|    |-- dodatki/
|    |-- .htaccess 
|    |-- index.php 
|-- storage/
|-- vendor/
|-- node_modules/
|-- composer
|-- package.json
|-- ReadMe.md
|-- License
```

## Zestaw technologii

Projekt jest zbudowany z wykorzystaniem nowoczesnych technologii, pozwalających na skalowanie i rozwój oraz utrzymanie stabilnego i czytelnego kodu źródłowego.

- Frontend: HTML / JS
- Style: CSS
- Backend: PHP 8.3
- Baza danych: MariaDb 11.4
- Narzędzia: Git, npm, GitHub Actions, PHPStan, Node.js 18.8.0, Composer 2.8.12, DomPdf 3.1.6, OAuth2 2.9, PHPMailer 7.1, Twig 3.10, fullcalendar 7.1.0, KaTex 0.18.7 

## Testowanie
TBA

[staging.umiemliczyc.pl]

## Plany 

X. Opracowanie badania PISA
  - czym jest, jak wykorzystujemy wyniki do przygotowania lekcji, co oznaczają wyniki w danym roku i jaki jest trend?
X. Testy diagnostyczne
X. Punkty, rabaty
X. SSO, OAuth, wymuszanie https
X. Opracowanie podstawy programowej
X. Poradnik do pracy z dyskalkulią
X. Poradnik do pracy z neuroróżnorodnością
X. Strategie pokonywania postępów uczniów
X. Fiszki z powtórzeniami
X. SEO, GEO
X. LMS
X. Forum dyskusyjne
X. Czatbot:
  - Korepetytor w metodzie sokratejskiej, kieruje do odpowiedzi poprzez zadawanie pytań naprowadzających. Nie podaje gotowego rozwiązania
X. Aplikacja mobilna
X. Ankiety satysfakcji z lekcji i okresowo
X. Sklep
X. Schema.org
X. Laravel / Symphony


## Benchmarking
* [matzoo.pl](https://www.matzoo.pl)
* [zeszyt.online](https://www.zeszyt.online)
* [aleks.com](https://www.aleks.com)
* [prodigygame.com](https://www.prodigygame.com)
* [matific.com](https://www.matific.com)
* [matemaks.pl](https://www.matemaks.pl)
* [mathwise.com](https://www.mathwise.com)
* [matflix.com](https://www.matflix.com)
* [matematykaszkolna.pl](https://www.matematykaszkolna.pl)
* [arkusze.pl](https://www.arkusze.pl)
* [zadania.info](https://www.zadania.info)
* [dzwonek.pl](https://www.dzwonek.pl)
* [matematyka.pl](https://www.matematyka.pl)
* [khanacademy.org](https://www.khanacademy.org)
* [sprelli.com/](https://sprelli.com/)
* [brilliant.org](https://brilliant.org)
