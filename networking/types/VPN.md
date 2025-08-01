# VPN - Virtual Private Network

1. Opis 
    - 
    - VPN to połączenie pomiędzy dwoma lub więcej komputerami lub urządzeniami które nie są w tej samej prywatnej sieci
    - Tzn: `Tunnel` jest tworzony przez [LAN](./LAN.md "LAN") i [WAN](WAN.md "WAN"), które są uzywane.

2. Szczegóły
    - 
    
    1. Popularne protokoły VPN
        * PPTP (Point-to-Point Tunneling Protocol)

            - Hermetyzuje ramki PPP (Point-to-Point Protocol) w datagramy do transmisji przez sieć opartą na IP.

            - Domyślnie nie szyfruje danych. (Jest przestarzały i niezabezpieczony w dzisiejszych standardach).

        * L2TP/IPSec (Layer Two Tunneling Protocol / Internet Protocol Security)

            - Połączenie protokołu L2TP (łączącego cechy PPTP i technologii L2F firmy Cisco Systems) z IPSec.

            - IPSec jest używany do szyfrowania danych, zapewniając bezpieczeństwo komunikacji.

3. Wizualizacja
    [VPN](../images/protocols/VPN.png "Virtual Private Network")