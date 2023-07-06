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
