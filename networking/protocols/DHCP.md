# DHCP - Dynamic Host Configuration Protocol

1. Opis
    - 

    - Jest protokołem po stronie klienta i servera, który konfiguruje urządzenia aby dostawały odpowiednie adresy IP

2. Szczegóły
    - 

    1. Porty
        - 67 -> DHCP server
        - 68 -> DHCP client

    2. DORA
        - DHCP uzywa 4 krokowego systemu nazywanego DORA
            * Discorvery
                - Klient wysyła "broadcast" na sieci aby znaleźć DHCP server

            * Offer
                - DHCP server wysyła "unicast" do klienta oferując adres IP

            * Request
                - Klient wysyła "broadcast" do wszystkich sewerów o swoim nowym IP

            * Acknowledge
                - DHCP server wysyła ostateczny "unicast" zawierający informacje o adresie IP który bedzie miał klient

    3. Po co?
        - Dzieki DHCP konfiguruje hosta tzn:
            - Adres IP
            - Adres Rutera
            - Maska podsieci
        - Bez DHCP trzeba to zrobić ręcznie lub mozna uzyc `bootp`