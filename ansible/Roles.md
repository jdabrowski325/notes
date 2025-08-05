# Ansible - Roles


1. Tworzenie roli
    - 

    - Polecenie

    ```
    ansible-galaxy init nazwa_roli
    ```

    - Struktura

    ```
    nazwa_roli/
        ├── defaults/
        │   └── main.yml
        ├── handlers/
        │   └── main.yml
        ├── meta/
        │   └── main.yml
        ├── tasks/
        │   └── main.yml
        ├── templates/
        ├── tests/
        │   ├── inventory
        │   └── test.yml
        └── vars/
            └── main.yml

    ```

2. Pobieranie gotowych roli
    - 

    - Polecenie

    ```
    ansible galaxy install nazwa_roli_galaxy
    ```

    - Polecenie na instalowanie roli z pliku

    ```
    ansible galaxy install -r role.yml
    ```

3. Uzywanie roli w playbooku
    - 

    - Przykład

    ```yaml

    - name: Użycie roli w playbooku
        hosts: serwery_www
        roles:
          - nazwa_twojej_roli

    ```

4. Sprawdzenie dostepności ról
    - 

    - Polecenie

    ```
    ansible-galaxy list
    ```