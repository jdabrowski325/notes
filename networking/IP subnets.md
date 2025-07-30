# Subnetting

1. Definicja (eli5)
    `Subnetting to tak, jakbyś ten duży worek z adresami pocztowymi podzielił na mniejsze, tematyczne woreczki. Zamiast mieć jeden wielki bałagan, masz woreczki na listy do salonu, do kuchni, do sypialni itd. W świecie komputerów, te "woreczki" to podsieci`

2. Przykład
    - 

    - firma z adresem `192.168.1.0/24` - 256 adresów ip. Trzeba podzielić firme na 3 sektory:
        * Marketing -> 50 komputerów
        * Sprzedaz -> 30 komputerów
        * IT -> 10 komputerów

    1. Krok 1
        - Liczby adresów w podsieciach zawsze są potęgami 2 (2, 4, 8, 16, 32, 64, 128 itd.)
        - Najbliższa potęga 2, która jest większa lub równa 50, to 64.

    2. Krok 2
        - Żeby mieć 64 adresy, potrzebujemy pożyczyć sobie bity z części hosta (tej, która określa konkretny komputer). W oryginalnej sieci /24, ostatnie 8 bitów to hosty (28=256 adresów). Żeby mieć 64 adresy, potrzebujemy 26=64 adresów, więc zostawiamy 6 bitów dla hostów. To oznacza, że pożyczamy 2 bity (8−6=2) dla sieci.
        - Nasza nowa maska podsieci to /26 (24 + 2 = 26).

        1. Marketing
            - Sieć: 192.168.1.0/26 (adresy od 192.168.1.0 do 192.168.1.63)
            - Liczba dostępnych adresów dla komputerów: 62 (bo 0 to adres sieci, a 63 to adres rozgłoszeniowy, ich nie używasz dla komputerów).

        2. Sprzedaz
            - Teraz zaczynamy kolejny woreczek od następnego wolnego adresu, czyli 192.168.1.64
            - Potrzebuje 30 komputerów. Najbliższa potęga 2 to 32 (25). Więc zostawiamy 5 bitów dla hostów. To oznacza, że pożyczamy 3 bity (8−5=3).
            - Nasza nowa maska podsieci to /27 (24 + 3 = 27).

            - Sieć: 192.168.1.64/27 (adresy od 192.168.1.64 do 192.168.1.95)
            - Liczba dostępnych adresów dla komputerów: 30.

        3. IT
            - Zaczynamy od następnego wolnego adresu, czyli 192.168.1.96
            - Potrzebuje 10 komputerów. Najbliższa potęga 2 to 16 (24). Więc zostawiamy 4 bity dla hostów. To oznacza, że pożyczamy 4 bity (8−4=4).
            - Nasza nowa maska podsieci to /28 (24 + 4 = 28).
            - Sieć: 192.168.1.96/28 (adresy od 192.168.1.96 do 192.168.1.111)
            - Liczba dostępnych adresów dla komputerów: 14.