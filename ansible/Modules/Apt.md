# Ansible Modules - Apt

1. Opis
    - 

    - Moduł apt zarządza pakietami w systemach operacyjnych opartych na Debianie/Ubuntu. Służy do instalowania, usuwania, aktualizowania i zarządzania pakietami.

2. Wykorzystanie
    - 

    - Używaj tego modułu w playbookach, aby zapewnić, że wymagane pakiety są zainstalowane lub usunięte. Jest to podstawowy moduł do zarządzania oprogramowaniem na hostach z systemem Debian/Ubuntu.

3. Przykłady
    - 

    - 1. 
    ```yaml

    - name: Upewnij się, że nginx jest zainstalowany i w najnowszej wersji
      apt:
        name: nginx
        state: latest

    ```