# Ansible Modules - User

1. Opis
    - 

    - Moduł user zarządza kontami użytkowników na zdalnych hostach. Pozwala na tworzenie, usuwanie, modyfikowanie haseł i dodawanie do grup.

2. Wykorzystanie
    - 

    - Idealny do automatycznego tworzenia kont administracyjnych lub kont dla aplikacji, zapewniając spójną konfigurację użytkowników na wszystkich serwerach.

3. Przykłady
    - 

    - 1. 
    ```yaml

    - name: Stwórz nowego użytkownika i dodaj go do grupy docker
      user:
        name: johndoe
        state: present
        groups: docker

    ```