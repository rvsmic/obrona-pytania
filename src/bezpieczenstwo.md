# Bezpieczeństwo systemów informatycznych

[`back to README.md`](../README.md)

## 63. Atrybuty bezpieczeństwa informacji

### Zgodnie z normą **ISO 27001**, atrybuty bezpieczeństwa informacji to (tzw. *CIA triad*):

- **Confidentiality** (poufność) — zapewnienie, dostęp do informacji tylko dla uprawnionych osób, ze względu na zakres obowiązków służbowych lub umowę. Osoby które mają dostęp do informacji, nie mogą jej ujawnić osobom nieuprawnionym. Na przykład, żeby nie została ujawniona konkurencji, lub osobom nieuprawnionym, które nie mają do niej dostępu.
- **Integrity** (integralność) — zapewnienie, że informacja nie została zmieniona przez nieuprawnione osoby, w nieuprawniony sposób. Na przykład, żeby nie została zmieniona przez wirusy, lub przez osoby nieuprawnione, które nie mają do niej dostępu.
- **Availability** (dostępność) — zapewnienie, że informacja jest dostępna dla uprawnionych osób w odpowiednim czasie i określony sposób. Na przykład dla pracowników firmy, którzy muszą mieć dostęp do informacji w celu wykonywania obowiązków służbowych związanych z tymi danymi, w godzinach pracy.

### Dodatkowe atrybuty bezpieczeństwa informacji to:

- **Authenticity** (autentyczność) — zapewnienie, że informacja jest autentyczna, czyli pochodzi od osoby, która jest jej rzeczywistym autorem. Dotyczy to zarówno komunikacji jak i operacji na danych. Chodzi o osoby, procesy, systemy czy instytucje.
- **Accountability** (rozliczalność) — zapewnienie, że da się zweryfikować kto i kiedy wykonał daną operację na danych.
- **Non-repudiation** (niezaprzeczalność) — zapewnienie, że osoba, która uczestniczyła w komunikacji nie może zaprzeczyć, że tego nie robiła. Jest to również ochrona przed *fałszywym* zaprzeczeniem.
- **Reliability** (niezawodność) — zapewnienie, że system jest niezawodny, czyli taki który działa bezbłędnie.
- **Identification** (identyfikacja) — możliwość rozróżnienia użytkowników, np po UID.
- **Authentication** (uwierzytelnianie) — możliwość weryfikacji tożsamości użytkownika, najczęściej opiera się na:
  - co użytkownik wie (hasło, PIN, ...) (knowledge factor)
  - co użytkownik ma (owership factor)
  - kim lub jakim jest użytkownik (inherence factor)
- **Authorization** (autoryzacja) — process przyznawania użytkownikowi dostępu do zasobów systemu, na podstawie jego tożsamości i uprawnień.
- **Access control** (kontrola dostępu) — zapewnienie, że użytkownik ma dostęp tylko do zasobów, do których ma uprawnienia. Jest to również system składający się z urządzeń, aplikacji i procedur, które kontrolują dostęp do zasobów systemu.

## 64. Modele dystrybucji kluczy kryptograficznych

### Są różne modele dystrybucji kluczy kryptograficznych, takie jak:

- **Oparty o klucz publiczny** — klucz publiczny jest dostępny dla wszystkich, a klucz prywatny jest znany tylko właścicielowi. W tym modelu, klucz publiczny jest używany do szyfrowania, a klucz prywatny do deszyfrowania.

    ![Public Key Cryptography](https://upload.wikimedia.org/wikipedia/commons/thumb/1/11/Asymmetric_cryptography_-_step_2.svg/800px-Asymmetric_cryptography_-_step_2.svg.png)

- **Oparty o protokół Diffiego-Hellmana** — klucz jest ustalany wspólnie przez dwie strony, które nie muszą się znać, na podstawie wybranych przez siebie publicznych parametrów (np. modulo liczby pierwszej) i na obliczeniach matematycznych (liczba pierwsza jest tajna, a operacja na niej nie). Prowadzi to do wygenerowania wspólnego klucza, który jest znany tylko tym dwóm stronom. Zaletą tego rozwiązania jest odporność na podsłuchiwanie
  
    ![Diffie-Hellman Key Exchange](https://upload.wikimedia.org/wikipedia/commons/a/a9/Diffie-Hellman_Key_Exchange.png)

- **Oparty o zaufaną stronę trzecią (TTP)** — zaufana trzecia strona to strona, która jest zaufana przez dwie strony, które chcą się wymieniać kluczami. Zaufana trzecia strona przechowuje klucz każdej ze stron, który został jej przekazany, np osobiście. Zostaje on udostępniony stronom komunikacji gdy każda ze stron ufa 3 stronie. Wadą tego rozwiązania jest to, że zaufana trzecia strona musi być dostępna, aby dwie strony mogły się wymieniać kluczami. Zaufanie oznacza tutaj, że trzecia strona może reprezentować interesy danej strony. Model ten jest używany w PKI (Public Key Infrastructure), gdzie zaufana trzecia strona jest CA (Certificate Authority).

Inne pojęcia:

- **PKI (Public Key Infrastructure)** jest to zbiór polityk, procedur i systemów komputerowych, niezbędnych do uwierzytelniania, szyfrowania, integralności i niezaprzeczalnosc. Jest to pewnego rodzaju *kryptosystem*, w skład którego wchodzą:
  - **CA** — urzędy certyfikacji, które wydają certyfikaty cyfrowe, które zawierają klucz publiczny i dane użytkownika, również certyfikuje inne CA
  - **RA** — urzędy rejestracji, które weryfikują tożsamość użytkownika i zbiera wnioski o certyfikaty
  - **użytkownicy** — osoby/systemy, które chcą uzyskać certyfikat cyfrowy
    ![PKI schemat](<https://upload.wikimedia.org/wikipedia/commons/thumb/3/34/Public-Key-Infrastructure.svg/1024px-Public-Key-Infrastructure.svg.png?1688420296540>)
  System ten jest używany w protokołach takich jak:
  - SSL/TLS
  - SSH
  - S/MIME

- **Web of Trust (sieć zaufania)** — zdecentralizowana metoda uwierzytelniania osób i kluczy publicznych. Każdy użytkownik może podpisać klucz publiczny innego użytkownika, aby potwierdzić jego autentyczność. W ten sposób, każdy użytkownik może zweryfikować klucz publiczny innego użytkownika, jeśli ma podpis od innego użytkownika, któremu ufa. Siłą zaufania do danego użytkownika jest suma zaufania do wszystkich użytkowników, którzy podpisali jego klucz publiczny.
  
    ![Web of Trust](https://upload.wikimedia.org/wikipedia/commons/thumb/4/4e/Web_of_Trust-en.svg/800px-Web_of_Trust-en.svg.png)

## 65. Rodzaje zagrożeń oraz ochrona aplikacji sieciowych

### Zagrożenia, ataki, złośliwe oprogramowanie

- Adware — reklama połączona z oprogramowaniem, czasami niechciana.
- Attack kit — zestaw narzędzi do ataków, np. na stronę internetową. na przykład do generowania Malware.
- Auto—rooter — złośliwe oprogramowanie, które automatycznie atakuje inne komputery.
- Backdoor — ukryte wejście do systemu, które pozwala na obejście zabezpieczeń.
- Downloader — złośliwe oprogramowanie, które pobiera i instaluje inne złośliwe oprogramowanie.
- Drive-by-download — atak z użyciem kodu na opanowanej stronie internetowej, który automatycznie pobiera i instaluje złośliwe oprogramowanie, podczas gdy użytkownik przegląda stronę.
- Exploit — kod, który wykorzystuje konkretną podatność w oprogramowaniu/systemie, aby uzyskać dostęp do systemu.
- Keylogger — złośliwe oprogramowanie, które rejestruje wszystkie naciśnięte klawisze, w celu uzyskania poufnych informacji, takich jak hasła.
- Flooders — złośliwe oprogramowanie, które wysyła duże ilości danych do serwera, aby go przeciążyć (DoS/DDoS — (Distributed) Denial of Service).
- Logic-bomb — złośliwe oprogramowanie, które jest aktywowane w określonym czasie lub po spełnieniu określonych warunków. Zostaje wstawiony do malware.
- Macro virus — złośliwe oprogramowanie, które jest napisane w języku makr, takim jak VBA (Visual Basic for Applications). Zostaje wstawiony do dokumentów. Uaktywnia się po otwarciu dokumentu.
- Mobile code — oprogramowanie które może działać na wielu platformach, np ARM, x86, ...
- Rootkit — Zestaw narzędzi, które pozwalają na dostęp do komputera/systemu, zazwyczaj pozwalają na ukrycie obecności złośliwego oprogramowania na komputerze (od Root — korzeń)
- Spyware — złośliwe oprogramowanie, które zbiera informacje o użytkowniku, takie jak hasła, adresy e-mail, odwiedzone strony internetowe, itp.
- Trojan — złośliwe oprogramowanie, które wygląda na nieszkodliwe (nawet jest przydatne), ale w rzeczywistości może być złośliwe.
- Virus — złośliwe oprogramowanie, które może się replikować i rozprzestrzeniać, zazwyczaj poprzez podłączenie zainfekowanego urządzenia do innego urządzenia (USB, ...).
- Worm — złośliwe oprogramowanie, które może się replikować i rozprzestrzeniać, zazwyczaj poprzez sieć (np. mail).
- Zombie — komputer, który został zainfekowany przez złośliwe oprogramowanie, które pozwala na zdalne sterowanie komputerem przez atakującego, na przykład w celu przeprowadzenia ataku DDoS.

### W celu ochrony aplikacji sieciowych, można:

- Używać HTTPS zamiast HTTP, aby zapewnić poufność i integralność danych.
- autoryzować użytkowników, aby zapewnić poufność i integralność danych.
- sesje użytkowników, aby zapewnić poufność i integralność danych.
- walidaować dane, aby zapobiec atakom typu SQL injection, XSS, ...
- ograniczać dostęp do zasobów
- firewall do zapobiegania atakom typu DoS/DDoS
- ograniczenie limitu zapytań do serwera, aby zapobiec atakom typu brute-force na hasła
- monitorowanie
- skanowanie przed wirusami
- detakcja włamań

## 66. Charakterystyka kryptografii symetrycznej oraz asymetrycznej

### Kryptografia symetryczna

Kryptografia symetryczna to kryptografia, w której do szyfrowania i deszyfrowania używany jest ten sam klucz. Jest to szybsze niż kryptografia asymetryczna, ale wymaga bezpiecznego kanału do przekazania klucza. Przykłady algorytmów to DES, 3DES, AES, Blowfish, Twofish, RC4, RC5, RC6, IDEA, CAST5, CAST6, SEED, ...

![Symmetric Cryptography](https://upload.wikimedia.org/wikipedia/commons/thumb/2/27/Symmetric_key_encryption.svg/800px-Symmetric_key_encryption.svg.png)

Wyróżniamy dwa rodzaje algorytmów:

- algorytmy strumieniowe — szyfruje pojedyncze bity, np. RC4, A5/1, ...
- algorytmy blokowe — szyfruje bloki bitów, np. DES, 3DES, AES, Blowfish, Twofish, RC5, RC6, IDEA, CAST5, CAST6, SEED, ...

### Kryptografia asymetryczna

Kryptografia asymetryczna to kryptografia, w której do szyfrowania i deszyfrowania używane są dwa różne klucze, klucz publiczny i klucz prywatny. Klucz publiczny jest dostępny dla wszystkich, a klucz prywatny jest znany tylko właścicielowi. Jest to wolniejsze niż kryptografia symetryczna, ale nie wymaga bezpiecznego kanału do przekazania klucza. Przykłady algorytmów to RSA, DSA, ElGamal, ECC, ...

![Asymmetric Cryptography](https://upload.wikimedia.org/wikipedia/commons/thumb/1/11/Asymmetric_cryptography_-_step_2.svg/800px-Asymmetric_cryptography_-_step_2.svg.png)

Klucz publiczny jest używany do szyfrowania, a klucz prywatny do deszyfrowania. Tylko w przypadku podpisu cyfrowego, klucz publiczny jest używany do weryfikacji, a klucz prywatny do podpisania.

Klucz publiczny jest wygenerowany na podstawie klucza prywatnego, ale nie jest możliwe wygenerowanie klucza prywatnego na podstawie klucza publicznego.

Metoda ta polega na operacjach matematycznych, które są łatwe do wykonania w jedną stronę, ale trudne do wykonania w drugą stronę. Przykładem takiej operacji jest mnożenie dużych liczb pierwszych. Polega również na wykorzystaniu liczb pierwszych, które są łatwe do wygenerowania, ale trudne do rozłożenia na czynniki pierwsze.
