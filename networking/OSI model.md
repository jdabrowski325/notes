# OSI model layers


* Model OSI to sposób na zrozumienie, jak komputery komunikują się w sieci, podzielony na siedem warstw.

1. Warstwa Fizyczna (Physical)
    - 

    - Odpowiada za fizyczne przesyłanie danych, czyli impulsy elektryczne lub świetlne przez kable.
    - Definiuje typy kabli i złączy, np. porty USB czy kable Ethernet.

2. Warstwa Łącza Danych (Data Link)
    - 
        
    - Zapewnia niezawodny transfer danych między bezpośrednio połączonymi urządzeniami w sieci lokalnej.
    - Obsługuje adresy fizyczne (MAC) i wykrywa błędy w transmisji.

3. Warstwa Sieci (Network)
    - 

    - Odpowiada za routowanie danych (pakietów) między różnymi sieciami, np. przez Internet.
    - Używa adresów IP do znajdowania najlepszej ścieżki do celu.

4. Warstwa Transportu (Transport)
    - 

    - Zapewnia niezawodną komunikację "od końca do końca" między dwoma programami.
    - Dzieli dane na mniejsze części i kontroluje przepływ, np. za pomocą protokołu TCP.

5. Warstwa Sesji (Session)
    - 

    - Zarządza sesjami komunikacji między aplikacjami, czyli kiedy i jak długo dane są wymieniane.
    - Pomaga w wznawianiu przerwanych połączeń.

6. Warstwa Prezentacji (Presentation)
    - 

    - Tłumaczy dane na format zrozumiały dla aplikacji, np. szyfruje lub kompresuje informacje.
    - Dba o to, żeby dane były w odpowiedniej składni dla odbiorcy.

7. Warstwa Aplikacji (Application)
    - 

    - Jest najbliżej użytkownika i umożliwia programom dostęp do usług sieciowych.
    - Są tu protokoły do przeglądania stron (HTTP), wysyłania e-maili (SMTP) czy przesyłania plików (FTP).