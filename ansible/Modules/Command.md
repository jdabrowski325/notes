# Ansible Modules - Command

1. Opis
    - 

    - Moduł command wykonuje proste polecenie na zdalnym hoście. W przeciwieństwie do modułu [shell](./Shell.md), nie przetwarza potoków (|), przekierowań (>) ani zmiennych środowiskowych.

2. Wykorzystanie
    - 

    - Używaj go do prostych poleceń, które nie wymagają zaawansowanych funkcji shella. Zawsze preferuj dedykowane moduły Ansible (np. [apt](./Apt.md), [service](./Service.md)), jeśli takie istnieją, ponieważ są one bardziej idempotentne i bezpieczne.

3. Przykłady
    - 

    - 1. 
    ```yaml
        - name: Sprawdź zużycie pamięci
            command: free -h
    ```