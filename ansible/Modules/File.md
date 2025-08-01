# Ansible Modules - File

1. Opis
    - 

    - Moduł file zarządza plikami, katalogami i dowiązaniami symbolicznymi na zdalnych hostach.

2. Wykorzystanie
    - 

    - Używaj go do tworzenia, usuwania, zmiany uprawnień i własności plików lub katalogów. Jest to podstawowy moduł do zarządzania strukturą plików na serwerach.

3. Przykłady
    - 

    - 1. 
    ```yaml

        - name: Utwórz katalog dla strony internetowej
          file:
            path: /var/www/html/mysite
            state: directory
            owner: www-data
            group: www-data
            mode: '0755'

    ```