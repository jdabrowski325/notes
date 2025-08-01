# Ansible Modules - Setup

1. Opis
    - 

    - Moduł setup zbiera fakty (ang. facts) o systemie na zdalnym hoście. Fakty to zmienne systemowe takie jak:
        * adresy IP,
        * wersja systemu operacyjnego,
        * informacje o sprzęcie (RAM, procesor),
        * zainstalowane pakiety,

    - Te fakty są następnie dostępne jako zmienne w playbookach Ansible. Moduł setup jest automatycznie uruchamiany na początku każdego playbooka, chyba że jawnie go wyłączysz **(opcja gather_facts: false)**.

2. Wykorzystanie
    - 

    - Używanie zebranych faktów pozwala pisać dynamiczne i uniwersalne playbooki, które dostosowują się do środowiska, w którym są uruchamiane. Zamiast "na sztywno" definiować ścieżki czy nazwy interfejsów sieciowych, możesz użyć zmiennych takich jak ansible_distribution czy ansible_default_ipv4.address.

3. Przykłady
    - 

    - 1. 
    ```yaml

        - name: Wyświetl fakty o hoście
            hosts: all
            tasks:
                - name: Pokaż wersję systemu operacyjnego
                debug:
                    msg: "Host {{ ansible_hostname }} jest w wersji {{ ansible_distribution }} {{ ansible_distribution_major_version }}."
                
                - name: Pokaż domyślny adres IP
                debug:
                    msg: "Domyślny adres IP to {{ ansible_default_ipv4.address }}."

    ```