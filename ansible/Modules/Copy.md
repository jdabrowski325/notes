# Ansible Modules - Copy

1. Opis
    - 

    - Moduł copy kopiuje pliki z hosta kontrolującego Ansible do hostów zdalnych.

2. Wykorzystanie
    - 

    - Idealny do dystrybucji plików konfiguracyjnych, skryptów lub innych zasobów statycznych, które muszą być identyczne na wielu maszynach.

3. Przykłady
    - 

    - 1. 
    ```yaml

        - name: Skopiuj plik konfiguracyjny Nginx
          copy:
            src: files/nginx.conf
            dest: /etc/nginx/nginx.conf
            owner: root
            group: root
            mode: '0644'

    ```