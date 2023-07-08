# Programowanie aplikacji sieciowych
[`back to README.md`](../README.md)
## 58. Mechanizm sesji w zarządzaniu stanem aplikacji sieciowej

**Sesja** — ograniczone czasowo, dwukierunkowe łącze, praktyczna (stosunkowo wysoka) warstwa w protokole TCP/IP, umożliwiająca interaktywną ekspresję i wymianę informacji między dwoma lub większą liczbą urządzeń  komunikacyjnych czy końcowych.

* sesja ustanawiana w określonym momencie, a doprowadzana do końca w innym późniejszym określonym momencie
* ustanowiona sesja może obejmować więcej niż jeden komunikat w każdym kierunku
* sesja zwykle stanowa tz. co najmniej jedna ze stron komunikujących się  musi przechowywać informacje o bieżącym stanie i zapisać informacje o historii sesji, aby móc się komunikować
* ustanowienie sesji jest podstawowym wymogiem do realizacji komunikacji zorientowanej na połączenie
* sesja podstawowym etapem transmisji w trybach komunikacji bezpołączeniowej
* transport komunikacji może być realizowany w ramach protokołów i usług w warstwie aplikacji (HTTP, telnet),  w warstwie sesyjnej (Session Initiation Protocol)lub w warstwie transportowej (sesja TCP) w modelu OSI.

* sesja po stronie serwera
  * mogą być trudne w obsłudze w połączeniu z systemami równoważenia obciążenia/wysokiej dostępności
  * mogą się nie nadawać do użytku w niektórych systemach wbudowanych bez pamięci masowej
  * problem z równoważeniem obciążenia można rozwiązać, używając współużytkowanej pamięci masowej lub stosując wymuszoną komunikację równorzędną między każdym klientem a pojedynczym serwerem w klastrze
* sesja po stronie klienta
  * wykorzystują pliki cookie i techniki kryptograficzne do utrzymania stanu bez przechowywania tak dużej ilości danych na serwerze
  * komunikacja
    * serwer przesyła dane o aktualnym stanie do klienta w postaci pliku cookie. Klient zapisuje plik cookie w pamięci lub na dysku
    * z każdym kolejnym żądaniem klient odsyła plik cookie z powrotem do serwera, a serwer wykorzystuje dane do „zapamiętania” stanu aplikacji dla tego konkretnego klienta i wygenerowania odpowiedniej odpowiedzi
  * Przechowywane przez klienta dane są podatne na modyfikację przez użytkownika, co może prowadzić do nieprawidłowego działania aplikacji, należy zagwarantować
    * poufność danych — tylko serwer powinien być w stanie zinterpretować dane
    * integralność danych — tylko serwer powinien być w stanie modyfikować dane
    * autentyczność danych — nic poza serwerem nie powinno być w stanie inicjować prawidłowych sesji
  
    Aby to osiągnąć sewer musi zaszyfrować dane przed wysłaniem, a ich modyfikacja powinna być uniemożliwiona za pomocą środków kryptograficznych
* pliki cookie mogą być kompresowana i dekompresowane, aby zmniejszyć rozmiar danych przesyłanych między klientem a serwerem
* token sesji HTTP — unikalny identyfikator generowany i wysyłany z serwera do klienta w celu identyfikacji bieżącej sesji interakcji
  * klient zwykle przechowuje i wysyła token jako plik cookie HTTP i/lub wysyła go jako parametr w zapytaniach GET lub POST

***Zarządzanie sesją** — proces śledzenia aktywności użytkownika podczas sesji interakcji z systemem komputerowym. Typowe zadanie zarządzanie sesja obejmują:

* śledzenie, które aplikacje są otwarte i jakie dokumenty zostały otwarte przez poszczególne aplikacje, tak aby można było przywrócić ten sam stan, gdy użytkownik wyloguje się i zaloguje później
* może wymagać ponownego zalogowania się po wygaśnięciu sesji
* przechowanie formacji po stronie serwera między żądaniami HTTP

## 59. Mechanizm gniazd – pojęcie, sposób realizacji i zastosowanie

**Gniazdo** — struktura oprogramowania w węźle sieci komputerowej, która służy jako punkt końcowy do wysyłania i odbierania danych w sieci. Termin gniazdo sieciowe jest najczęściej używany w kontekście zestawu protokołów internetowych i dlatego często jest również określany jako gniazdo internetowe. W tym kontekście gniazdo jest zewnętrznie identyfikowane przez inne hosty na podstawie adresu gniazda, który jest triadą protokołu transportowego, adresu IP i numeru portu.

Termin gniazdo jest również używany w odniesieniu do punktu końcowego oprogramowania wewnętrznej komunikacji między procesami (IPC), która często korzysta z tego samego interfejsu API co gniazdo sieciowe

* Struktura i właściwości gniazda są definiowane przez interfejs programowania aplikacji (API) dla architektury sieciowej
* Gniazda są tworzone tylko podczas życia procesu aplikacji działającej w węźle
* Wykorzystywane jest przez aplikacje do komunikowania się przez sieć w ramach komunikacji międzyprocesowej
* Posiada 3 główne właściwości:
  * typ gniazda identyfikujący protokół wymiany danych
  * lokalny adres gniazda (np. IP czy Ethernet)
  * opcjonalny lokalny numer portu identyfikujący proces, który wymienia dane przez gniazdo (jeśli typ gniazda pozwala używać portów)
  * dodatkowo może na czas trwania połączenia przechowywać adres zdalnego gniazda i numer portu identyfikujący zdalny proces (jeśli typ gniazda pozwala używać portów)
* Adres IP wyznacza węzeł w sieci, numer portu określa proces w węźle ("typu usługi"), a typ gniazda determinuje sposób wymiany danych.

### Realizacja

* Stos protokołów zwykle dostarczonych przez system operacyjny, będący zestawem usług, umożliwia komunikację przez sieć. System operacyjny przekazuje ładunek nadchodzących pakietów IP do odpowiedniej aplikacji przez wyodrębnienie informacji o adresie gniazda z nagłówków IP i protokołów transportowych oraz usunięcie nagłówków z danych aplikacji.
* Interfejs programowania aplikacji (API) dla stosu protokołów sieciowych tworzy uchwyt dla każdego gniazda utworzonego przez aplikację, powszechnie nazywany deskryptorem gniazda.
* W systemach operacyjnych typu Unix ten deskryptor jest rodzajem deskryptora pliku.
* Jest on przechowywany przez proces aplikacji do wykorzystania przy każdej operacji odczytu i zapisu w kanale komunikacyjnym.
* W momencie tworzenia za pomocą interfejsu API gniazdo sieciowe jest powiązane z kombinacją typu protokołu sieciowego, który ma być używany do transmisji, adresu sieciowego hosta i numeru portu.
* W systemach typu Unix obsługa gniazd jest implementowana w jądrze, a wykonywanie na nich operacji umożliwiają funkcje systemowe podobne do tych, jakich używa się w stosunku do plików.

### Zastosowanie

* do trwałych połączeń do komunikacji między dwoma węzłami
* mogą uczestniczyć w komunikacji bezpołączeniowej i multicast
* termin gniazdo sieciowe zwykle odnosi się do używania z protokołem internetowym (IP)

## 60. Metody obsługi wielu klientów równolegle w aplikacjach sieciowych

### Wątki

* wątki realizowane w ramach jednego procesu (programu), mające własny stos, zestaw rejestrów,licznik rozkazów, indywidualne dane, zmienne lokalne, i informację o stanie ale wspólną przestrzeń adresową, ogólną obsługę sygnałów, pamięć wirtualną, dane oraz wejście-wyjście w obrębie danego procesu
* w wielowątkowym procesie każdy wątek wykonuje się odzielnie i asynchronicznie
* wielowątkowe serwery 
  * mogą obsługiwać wiele połaczeń równolegle
  * każde połączenie jest obsługiwane przez osobny wątek
  * schemat działania
    * tworzenie gniazda, prrzypisanie mu adresu IP i portu
    * uruchomienie pętli nieskończonej, w której
      * akceptowane połączenia od serwera
      * w przypadku połączenie, tworzony nowy wątek, który obsługuje połączenie
 



### Gniazda nieblokujące i monitorowanie zdarzeń

* umożliwiają nieblokujące (asynchroniczne) operacje wejścia/wyjścia
* operacja nie blokuje wątku (jej wywołanie wraca natychmiast) i może przekazać mniej bajtów danych niż było wymagane lub nawet wcale
* operacja kończy się natychmiast
* połączenie nie blokuje wątku, wynik zwracany jest natychmiast i wskazuje na to, czy połączono się z serwerem czy nie
* przy czytaniu wątek nie jest blokowany jeśli nie ma danych, gdy nie ma danych w buforze to zwracany jest błąd, który nie wstrzymuje działania programu
* można w pętli odpytywać czy są dane do odczytu, jeśli nie to można wykonać inne operacje
* możliwe multipleksowanie, czyli obsługiwanie wielu kanałów przez jeden wątek
* każda operacja asynchroniczna kończy się zmienieniem stanu gniazda
* funkcje monitorujące operacje asynchroniczne np. `select()` — funkcja z rodziny monitorujących zniór desktyptorów WE/WY (tutaj gniazd), którą można wykorzystać do synchronizacji wielu operacji wykonywanych w tle (asynchronicznych)



## 61. Pocztowe protokoły warstwy aplikacji

### SMTP, SMTPS i ESMTP

**SMTP** (Simple Mail Transfer Protocol) —  protokół komunikacyjny opisujący sposób przekazywania poczty elektronicznej w Internecie. Używa portu 25.

* protokół tekstowy
* określa się co najmniej jednego odbiorcę wiadomości (w większości przypadków weryfikowane jest jego istnienie), a następnie przekazuje treść wiadomości
* brak mechanizmu weryfikacji nadawcy — ułatwia rozpowszechnianie spamu i wirusów komputerowych
  * stworzono rozszerzenie SMTP-AUTH — klient może zalogować się przy użyciu dowolnej metody uwierzytelniania obsługiwanej przez serwer; używany głównie przez serwery przesyłania, gdzie uwierzytelnianie jest obowiązkowe
  * nadawca może "udawać" serwer
* stworzony był w oparciu o czysty tekst ASCII — nie radził sobie dobrze z plikami binarnymi, aby je kodować stworzono np. standard MIME (Multipurpose Internet Mail Extensions, dwuczęściowy identyfikator formatu plików i formatu treści przesyłanych w Internecie)
* ESMTP (Extended Simple Mail Transfer Protocol) jest rozszerzeniem protokołu SMTP
  * ustanowił ogólną strukturę dla wszystkich istniejących i przyszłych rozszerzeń, których celem było dodanie funkcji, których brakowało w oryginalnym SMTP
  * definiuje spójne i łatwe w zarządzaniu środki, za pomocą których można identyfikować klientów i serwery ESMTP, a serwery mogą wskazywać obsługiwane rozszerzenia
  * użytkownicy mogą ręcznie określić z góry maksymalny rozmiar akceptowany przez serwery ESMTP
  * ma maksymalny rozmiar wiadomości, który może być przesłany
  * 
### POP3

**Post Office Protocol** (POP) — protokół internetowy z warstwy aplikacji pozwalający na odbiór poczty elektronicznej ze zdalnego serwera do lokalnego komputera poprzez połączenie TCP/IP. Używa portu 110 (z SSL portu 995).

Wcześniejsze wersje POP, POP2 zastąpione całkowicie przez POP3.

**POP3**:

* umożliwia jedynie pobieranie i kasowanie poczty
* po połączeniu z siecią, użytkownik może pobrać pocztę z serwera na swój komputer za pomocą protokołu POP3
* połączenie realizowane tylko gdu użytkownik pobiera pocztę, nie może zostać uśpione
* każdy list musi być pobierany razem z załącznikami i żadnej jego części nie można w łatwy sposób pominąć (komenda `top` pozwala określić przesyłaną liczbę linii od początku wiadomości)
* wszystkie maile do jednej skrzynki — nie da się utworzyć kilku
* serwer POP3 nie potrafi sam przeszukiwać czekających w kolejce wiadomości
* komunikacja może być zaszyfrowana SSL
* hasło przesyłane otwartym tekstem, o ile nie korzysta się z opcjonalnej komendy protokołu POP3, APOP
* protokół tekstowy
* komunikacja za pomocą czteroliterowych poleceń

### IMAP

**IMAP** (ang. Internet Message Access Protocol) – internetowy protokół pocztowy zaprojektowany jako następca POP3. Protokół TCP oraz port 143.

**IMAP**:

* umożliwia zarządzanie wieloma folderami pocztowymi
* umożliwia pobieranie i operowanie na listach znajdujących się na zdalnym serwerze
* pozwalają na pobieranie nagłówków wiadomości bez pobierania całej treści
* pozwala na dwa tryby działania: połączeniowy i bezpołączeniowy
* klient często utrzymuje połączenie dopóki interfejs użytkownika uruchomiony
* umożliwia połączenie wielu klientów naraz
* wiadomości mogą być wysyłane bezpośrednio do użytkownika bez konieczności odpytywania serwera
* w protokole IMAP fragmenty wiadomości elektronicznej są opisane za pomocą standardu MIME 
* system flag określających status wiadomości (flagi zapisywane na serwerze)
* niektóre serwery IMAP pozwalają na tagowanie wiadomości
* przeszukiwanie skrzynki pocztowej po stronie serwera — nie ma konieczności pobrania wszystkich wiadomości

## 62. Porównanie HTTP i WebSocket

### HTTP

**HTTP** (ang. Hypertext Transfer Protocol) — protokół komunikacyjny między klientem a serwerem w siecie WWW. Używa portu 80 i 443 (szyfrowane) TCP.

* zlokalizowany na 7 warstwie modelu OSI  (aplikacyjnej) i zależy od protokołu TCP na 4 warstwie (transportowej)
* działa w półdupleksie (informacje są przesyłane i odbierane naprzemiennie)
* określa formę żądań klienta (tj. np. przeglądarki www) dotyczących danych i formę odpowiedzi serwera
* protokół bezstanowy — nie zapamiętuje poprzednich żądań klienta
  * ten problem rozwiązywane za pomocą ciasteczek, sesji po stronie serywera, ukryte parametry, parametry w adresie URL
* do przesyłania zasobów (plików, pliów HTML, graficznych, wyników zapytań itd.)
* protokół tekstowy
* protokół typu *zapytanie-odpowiedź* — zapytanie od klienta zawierające informacje o żądanym zasobie, odpowiedź od serwera z treścią zasobu lub informacją o błędzie
* zapytanie składa się z:
  * linii początkowowej zakończonej znakami CRLF
  * 0 lub więcej nagłówków zakończonych znakami CRLF (nagłówek to właściwość zapytaniai odpowiedzi przesyłane wraz z samą wiadomością)
  * pustego wiersza (czyli CRLF)
  * opcjonalego ciała zapytania
* zapytanie zawsze kończy się znakami CRLF
* odpowiedz HTTO nie określa końca odpowiedzi, ale serwer musi zamknąć połączenie TCP po wysłaniu odpowiedzi — trzeba parsować nagłówek `Content-Length` lub `Transfer-Encoding`
* ogólny format **żądania**:
  
  `Method Request-URI HTTP-Version \r\n`

  `HEADER1: VALUE1 \r\n`
  
  `HEADER2: VALUE2 \r\n`

  `...`
  
  `HEADERX: VALUEX \r\n`
  
  `\r\n`
  
  `BODY\r\n`
  * `METHOD` — metoda żądania, np. 
    * `GET` — pobranie zasobu wskazanego przez Request-URI
    * `HEAD` — pobiera informacje o zasobie, stosowane do sprawdzania dostępności zasobu
    * `PUT` — przyjęcie danych przesyłanych od klienta do serwera, najczęściej aby zaktualizować wartośćzasobu
    * `POST` — przyjęcie danych przesyłanych od klienta do serwera (np. wysyłanie zawartości formula-rzy)
    * `DELETE` — żądanie usunięcia zasobu
    * `OPTIONS` — informacje o opcjach i wymaganiach dotyczących zasobu
    * `TRACE` — diagnostyka, analiza kanału komunikacyjnego
    * `CONNECT` — żądanie przeznaczone dla serwerów pośredniczących pełniących funkcje tunelowania
    * `PATCH` — aktualizacja części zasobu (np. jednego pola).
  * `URI` — ścieżka do zasobu, np. `/index.html`
  * `HTTP-Version` — wersja protokołu np. `HTTP/1.1`
* ogólny format **odpowiedzi** HTTP
    
    `HTTP-Version Status-Code Reason-Phrase \r\n`
    
    `HEADER1: VALUE1 \r\n`
    
    `HEADER2: VALUE2 \r\n`
    
    `...`
    
    `HEADERX: VALUEX \r\n`
    
    `\r\n`
    
    `BODY\r\n`
    * `HTTP-Version` — wersja protokołu np. `HTTP/1.1`
    * `Status-Code` — kod statusu odpowiedzi
      * `1xx` — kody informacyjne
      * `2xx` — kody powodzenia
      * `3xx` — kody przekierowania
      * `4xx` — kod błądu aplikacji klienta
      * `5xx` — kod błądu serwera
    * `Reason-Phrase` — wiadomość powiązana z danym kodem odpowiedzi, krótki opis kodu statusu, np. `OK`, `Not Found`, `Internal Server Error`
* przykład komunikacji
  * żądanie
  `GET /index.html HTTP/1.1`

  `HOST: 212.182.24.27`
  * odpowiedź
  `HTTP/1.1 200 OK`
  
  `Date: Thu, 13 Apr 2017 14:25:38 GMT`
  
  `Server: Apache/2.4.18 (Ubuntu)`
  
  `Last-Modified: Thu, 13 Apr 2017 13:57:13 GMT`
  
  `ETag: "2c39-54d0cb3af4405"`
  
  `Accept-Ranges: bytes`
  
  `Content-Length: 11321`
  
  `Vary: Accept-Encoding`
  
  `Content-Type: text/html`
  
  ``
  
  `<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN"`
  
  `"http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">`
  
  `<html xmlns="http://www.w3.org/1999/xhtml">`
  
    `<head>`
    
      `<meta http-equiv="Content-Type" content="text/html; charset=UTF-8" />`
      
      `<title>Apache2 Ubuntu Default Page: It works</title>`
      
    `</head>`
    
    `<body>`
    
    `...`
    
    `</body>`

  `</html>`

### WebSocket

**WebSocket** – jest protokołem komunikacyjnym, zapewniającym dwukierunkowy kanał wymiany danych poprzez pojedyncze połączenie TCP. Zaprojektowany do działania na portach 80 i 443 (zabezpieczone) przypisanych fo HTTP. Ma wspierać działania proxy i pośredników.

* zlokalizowany na 7 warstwie modelu OSI  (aplikacyjnej) i zależy od protokołu TCP na 4 warstwie (transportowej)
* działa w duplexie (przesyłanie w dwóch kierunkach jednocześnie) — zmiejsza opóźnienia i obciążenie sieci
* niższe obciążenie serwera niż w przypadku HTTP, ułatwiając przy tym przesyłanie danych w czasie rzeczywistym dzięki zapewnieniu znormalizowanego sposobu wysyłania przez serwer treści do klienta bez uprzedniego żądania klienta i umożliwienia przesyłania komunikatów tam i z powrotem przy zachowaniu aktywnego połączenia
* umożliwia przesyłanie wiadomości na wierzchu protokołu TCP
* każda komenda w żądaniu i odpowiedzi jest zakończona znakami CRLF (tak jak w HTTP)
* komunikacja
  * klient wysyła do serwera żądanie inincjalizujące (*handshahe*) wykorzystując HTTP
    * ze względu na kompatybilność z serwerami WWW niemal identyczne jak zapytanie HTTP, format odpowiedzi serwera zgodny z odpowiedzią HTTP
    * żadanie klienta
  
    `GET /chat HTTP/1.1`

    `Host: server.example.com`
    
    `Upgrade: websocket`

    `Connection: Upgrade`
    
    `Sec-WebSocket-Key: x3JJHMbDL1EzLkh9GBhXDw==`
    
    `Sec-WebSocket-Protocol: chat, superchat`
    
    `Sec-WebSocket-Version: 13`
    
    `Origin: http://example.com`

    * odpowiedź serwera

    `HTTP/1.1 101 Switching Protocols`

    `Upgrade: websocket`

    `Connection: Upgrade`

    `Sec-WebSocket-Accept: HSmrc0sMlYUkAGmm5OPpG2HaGWk=`

    `Sec-WebSocket-Protocol: chat`
  * po zestawieniu połączenia, obie strony mogą wymieniać się danymi w dowolnym momencie, wysyłając
pakiet danych (inaczej niż w protokole HTTP, gdzie komunikacja wyglądała w ten sposób, iż na każde żądanie wysyłana była odpowiedź)
    * dalsza komunikacja ta odbywa się poprzez socket TCP z pominięciem protokołu HTTP
    * wiadomości muszą być przesyłane w specjalnie sformatowanych ramkach
* rozwiązanie czasu rzeczywistego — nie trzeba ręcznie odpytawać w przeciwieństwie do HTTP
* tworzy po stronie klienta socker, który poprzez adres IP i nr portu utrzymuje obustronny kanał z serwerem
* ws (Web Servieces) dla połączeń nieszyfrowanych i wss (Web Secure Servieces) dla połączeń szyfrowanych

Komunikacja WebSocket
![komunikacja websocket](/src/img/pas/websocket.png)