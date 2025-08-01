# Ansible Modules - Shell

1. Opis
    - 

    - Moduł shell wykonuje polecenie za pomocą powłoki systemowej (shell). Pozwala to na użycie potoków, przekierowań i zmiennych środowiskowych.

2. Wykorzystanie
    - 

    - Używaj go, gdy potrzebujesz wykonać bardziej złożone polecenie shella, które nie może być wykonane za pomocą modułu [command](./Command.md). Pamiętaj, że zawsze, gdy to możliwe, lepiej jest używać dedykowanych modułów Ansible.

3. Przykłady
    - 

    - 1. 
    ```yaml

        - name: Znajdź proces Nginx
            shell: "ps aux | grep nginx | awk '{print $2}'"

    ```