# Ansible - Vault


1. Tworzenie nowego zaszyfrowanego pliku
    - 

    - Polecenie

        - Zostaniesz poproszony o hasło do Vault, a następnie otworzy się edytor, w którym możesz wpisać dane.

        ```
        ansible-vault create nazwa_pliku
        ```

    - Przykład

        ```
        ansible-vault create vars/secret_vars.yml
        ```

2. Edycja zaszyfrowanego pliku
    - 

    - Polecenie

        - Zostaniesz poproszony o hasło do Vault

        ```
        ansible-vault edit nazwa_pliku
        ```

    - Przykład

        ```
        ansible-vault edit vars/secret_vars.yml
        ```

    
3. Szyfrowanie pliku który nie był wcześniej szyfrowany
    - 

    - Polecenie

        - zaszyfruje plik nazwa_pliku - jezeli nie był wcześniej szyfrowany
        ```
        ansible-vault encrypt nazwa_pliku
        ```

    - Przykład

        ```
        ansible-vault encrypt vars/staging_passwords.yml
        ```

4. Odszyfrowywanie pliku 
    - 

    - Polecenie
        ```
        ansible-vault decrypt nazwa_pliku
        ```

    - Przykład
        ```
        ansible-vault decrypt vars/secret_vars.yml
        ```

5. Zmiana hasła do szyfrowanego pliku
    - 

    - Polecenie
        ```
        ansible-vault rekey nazwa_pliku
        ```

    - Przykład
        ```
        ansible-vault rekey vars/secret_vars.yml
        ```

6. Wyświetla zawartość zaszyfrowanego pliku
    - 

    - Polecenie
        ```
        ansible-vault view nazwa_pliku
        ```

    - Przykład
        ```
        ansible-vault view vars/secret_vars.yml
        ```

7. Uruchamianie Playbook'ów z vaultem
    - 

    - uruchomienie z podaniem hasła

    ```
    ansible-playbook playbook.yml --ask-vault-pass
    ```

    - uruchomienie z plikiem z hasłem

    ```
    nsible-playbook playbook.yml --vault-password-file ~/.vault_pass.txt
    ```