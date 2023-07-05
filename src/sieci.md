# Sieci komputerowe

[`back to README.md`](../README.md)

## 9. Protokoły TCP i UDP – porównanie i zastosowanie

### UDP

**UDP (User Datagram Protocol — *protokół pakietów użytkownika*)** — jeden z protokołów internetowych. Jest stosowany w **warstwie transportowej**. Jest to protokół bezpołączeniowy, więc nie ma narzutu na nawiązywanie połączenia i śledzenie sesji (w przeciwieństwie do TCP). Nie ma też mechanizmów kontroli przepływu i retransmisji.

Jest dzięki temu prostszy i szybszy od TCP, ale mniej niezawodny.

Najczęściej stosowany jest do przesyłania danych w czasie rzeczywistym, np. w transmisji strumieniowej (np. wideo, audio) czy do gier sieciowych. Korzysta z niego np. protokół DNS czy VoIP

UDP wspiera również **multicast** (wysyłanie do wielu odbiorców jednocześnie).

### TCP

**TCP (Transmission Control Protocol — *protokół kontroli transmisji*)** — jeden z protokołów internetowych. Jest stosowanym **warstwie transportowej**. Jest to protokół połączeniowy, więc wymaga nawiązania połączenia i śledzenia sesji (w przeciwieństwie do UDP). Ma też mechanizmy kontroli przepływu i retransmisji. Gwarantuje dostarczenie danych w kolejności, w jakiej zostały wysłane. Wszystkie dane muszą być dostarczone, a jeśli nie zostaną, to połączenie zostanie zerwane. Stosuje się tez sumy kontrolne (CRC) do sprawdzania poprawności danych i ich integralności. Stosuje się również potwierdzenia odbioru danych.

Jest to protokół *klient-serwer*

Jest dzięki temu bardziej niezawodny, ale mniej prosty i wolniejszy od UDP.

#### Nawiązywanie połączenia

1. Klient wysyła pakiet `SYN` do serwera
2. Serwer odpowiada pakietem `SYN-ACK`
3. Klient odpowiada pakietem `ACK`

![Nawiązywanie połączenia](<https://upload.wikimedia.org/wikipedia/commons/thumb/9/9a/Tcp_normal.svg/2560px-Tcp_normal.svg.png>)

#### Zerwanie połączenia

1. Klient wysyła pakiet `FIN` do serwera
2. Serwer odpowiada pakietem `ACK`
3. Połączenie zostaje zamknięte

#### Stany połączenia

1. `CLOSED` — połączenie nie jest nawiązane
2. `LISTEN` — serwer nasłuchuje na połączenia przychodzące
3. `SYN-SENT` — klient wysłał pakiet `SYN`
4. `SYN-RECEIVED` — serwer wysłał pakiet `SYN-ACK`
5. `ESTABLISHED` — połączenie zostało nawiązane
6. `FIN-WAIT-1` — klient wysłał pakiet `FIN`
7. `FIN-WAIT-2` — serwer wysłał pakiet `ACK`
8. `CLOSE-WAIT` — serwer wysłał pakiet `FIN`
9. `LAST-ACK` — klient wysłał pakiet `ACK`
10. `TIME-WAIT` — połączenie zostało zamknięte
11. `CLOSING` — klient wysłał pakiet `FIN` i `ACK` jednocześnie

Oba protokoły są stosowane w **warstwie transportowej** modelu TCP/IP. Używają również portów, aby przekazać dane do odpowiednich aplikacji i identyfikować je.

## 10. Adresowanie w warstwie Internetu modelu TCP/IP

### IPv4

**Adres IPv4** — adres w sieci internetowej, który identyfikuje urządzenie sieciowe. Składa się z 32 bitów, które są zapisywane w postaci czterech liczb dziesiętnych oddzielonych kropkami. Każda liczba dziesiętna jest zapisana w postaci liczby binarnej (8 bitów). Do adresowania używa się również **maski podsieci**. Jest to 32-bitowa liczba binarna, która określa, które bity adresu IP są częścią adresu sieci, a które częścią adresu hosta.

### IPv6

**Adres IPv6** — adres w sieci internetowej, który identyfikuje urządzenie sieciowe. Składa się z 128 bitów, które są zapisywane w postaci ośmiu liczb szesnastkowych oddzielonych dwukropkami. Każda liczba szesnastkowa jest zapisana w postaci liczby binarnej (16 bitów). Do adresowania używa się również **maski podsieci**. Jest to 128-bitowa liczba binarna, która określa, które bity adresu IP są częścią adresu sieci, a które częścią adresu hosta. Dodatkowo, adres IPv6 może zawierać **prefiks** (określa, czy adres jest globalny, lokalny czy unikalny) oraz **identyfikator interfejsu** (określa, który interfejs sieciowy jest używany).

> Adresy MAC (adres fizyczny) są stosowane w warstwie niżej, to jest w warstwie **dostępu do sieci** modelu TCP/IP.

## 11. Porównanie zadań przełącznika (switcha) i routera

### Przełącznik

**Przełącznik (switch)** — urządzenie sieciowe, które przekazuje dane w sieci komputerowej. Przekazuje dane do odpowiednich urządzeń na podstawie adresu MAC. Działa w warstwie 2 modelu OSI (warstwa łącza danych). Przełącznik analizuje adresy MAC w ramkach Ethernet, a następnie przekazuje ramki do odpowiednich urządzeń. Minimalizuje to liczbę kolizji i niepotrzebny ruch w sieci. Adresy MAC są zapisywane w pamięci przełącznika w tabeli adresów MAC.
Stosuje się go w sieciach LAN.

### Router

**Router** — urządzenie sieciowe, które przekazuje dane w sieci komputerowej. Przekazuje dane do odpowiednich urządzeń na podstawie adresu IP. Działa w warstwie 3 modelu OSI (warstwa sieci). Router analizuje adresy IP w pakietach IP, a następnie przekazuje pakiety do odpowiednich urządzeń. Router przesyła pakiety w jak najbardziej optymalny sposób, biorąc pod uwagę np. obciążenie sieci. Adresy IP są zapisywane w pamięci routera w tabeli trasowania. Stosuje się go na styku dwóch sieci, na przykład w sieciach LAN i WAN.

## 12. Porównanie modelu OSI i TCP/IP

### Model OSI

**Model OSI** — model warstwowy, który opisuje komunikację w sieciach komputerowych. Składa się z 7 warstw, które są zorganizowane w stos. Każda warstwa odpowiada za inne zadania. Każda warstwa komunikuje się tylko z warstwami sąsiadującymi. Każda warstwa ma swoje własne protokoły. Model OSI jest modelem teoretycznym, który nie jest stosowany w praktyce.

![Model OSI](<https://upload.wikimedia.org/wikipedia/commons/thumb/2/2b/Osi-model.png/2560px-Osi-model.png>)

![Model2](https://upload.wikimedia.org/wikipedia/commons/thumb/5/56/Kapsu%C5%82kowanie_danych_wg_modelu_odniesienia_OSI.svg/1280px-Kapsu%C5%82kowanie_danych_wg_modelu_odniesienia_OSI.svg.png)

Warstwy modelu OSI:

1. **fizyczna** — określa sposób transmisji danych (np. przewody, światłowody, fale radiowe)
2. **łącza danych** —  operuje na ramkach danych, które są przesyłane między węzłami sieci. Używa adresów MAC. Zapewnia kontrolę błędów i przepływ danych. Urządzeniem tej warstwy jest bridge i switch. Ma dwie podwarstwy:
   1. **MAC** — określa sposób dostępu do medium transmisyjnego (np. CSMA/CD) (niższa)
   2. **LLC** — określa sposób przesyłania danych (np. LLC1, LLC2) (wyższa)
3. **sieciowa** — określa sposób przesyłania pakietów między węzłami sieci. Używa adresów IP. Zapewnia trasowanie i adresowanie. Protokoły: IP, ICMP, ARP. Urządzeniem tej warstwy jest router.
4. **transportowa** — zapewnia całościowe połączenie, składa dane w strumień. Używa portów. Zapewnia kontrolę przepływu i błędów. Protokoły: TCP, UDP.
5. **sesji** — określa sposób nawiązywania, utrzymywania i zrywania sesji między aplikacjami. Synchronizuje różne aplikacje. Protokoły: NetBIOS, SAP, PPTP, SOCKS, L2TP, SSH, TLS, SSL, RPC, ASP, AFP, SCP, SIP, SDP, RTP, RTCP, XMPP, H.323.
6. **prezentacji** — określa sposób reprezentacji danych, przetwarza dane do postaci kanonicznej (gdy przetwarza w dół stosu). Odpowiada za kodowanie i konwersję danych. Obsługuje także rzeczy MPEG, JPG, GIF
7. **aplikacji** — zajmuje się specyfikacją interfejsu, który wykorzystują aplikacje do przesyłania danych do sieci.

Warstwy 5-7 są warstwami **usługowymi**.

### TCP/IP

**TCP/IP** — model warstwowy, który opisuje komunikację w sieciach komputerowych. Składa się z 4 warstw, które są zorganizowane w stos. Każda warstwa odpowiada za inne zadania. Każda warstwa komunikuje się tylko z warstwami sąsiadującymi. Każda warstwa ma swoje własne protokoły. Model TCP/IP jest modelem praktycznym, który jest stosowany w praktyce. Każdy nowoczesny system operacyjny implementuje model TCP/IP.

![Model TCP/IP](https://upload.wikimedia.org/wikipedia/commons/thumb/3/3b/UDP_encapsulation.svg/1280px-UDP_encapsulation.svg.png)

1. **dostępu do sieci/fizyczna** — określa sposób transmisji danych (np. przewody, światłowody, fale radiowe) i połączenia między urządzeniami. MAC
2. **internetowa** — określa sposób przesyłania pakietów między węzłami sieci. Używa adresów IP. Zapewnia trasowanie i adresowanie. Protokoły: IP, ICMP, ARP. Urządzeniem tej warstwy jest router.
3. **transportowa** — zapewnia całościowe połączenie, składa dane w strumień. Używa portów. Zapewnia kontrolę przepływu i błędów. Protokoły: TCP, UDP.
4. **aplikacji** — użyteczne dla człowieka aplikacje

## 13. Mechanizm enkapsulacji w modelu OSI

**Enkapsulacja** — proces dodawania nagłówków i/lub stopek do danych. Każda warstwa modelu OSI dodaje własny nagłówek i/lub stopkę. Nagłówek zawiera informacje, które są potrzebne do przetworzenia danych. Stopka zawiera informacje, które są potrzebne do przetworzenia danych. Enkapsulacja jest wykonywana w kolejności od warstwy aplikacji do warstwy fizycznej. Enkapsulacja jest wykonywana przez każdą warstwę modelu OSI.

![Enkapsulacja](https://upload.wikimedia.org/wikipedia/commons/thumb/5/56/Kapsu%C5%82kowanie_danych_wg_modelu_odniesienia_OSI.svg/1280px-Kapsu%C5%82kowanie_danych_wg_modelu_odniesienia_OSI.svg.png)

1. **fizyczna** — bity/elektrony
2. **łącza danych** — ramki/adresy MAC, np Ethernet
3. **sieciowa** — pakiety/adresy IP
4. **transportowa** — segmenty/datagramy/porty TCP/UDP
5. **sesji** — dane
6. **prezentacji** — dane
7. **aplikacji** — dane
