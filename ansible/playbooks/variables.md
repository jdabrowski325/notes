# Anisbile - playbooks variables

1. Opis
    - 
    
    - Zmienne w Ansible pozwalają na wielokrotne wykorzystanie wartości w playbookach, rolach, a nawet w plikach konfiguracyjnych. Zamiast "na sztywno" wpisywać te same wartości w wielu miejscach, możesz zdefiniować je raz jako zmienną i odwoływać się do niej, gdy będzie to potrzebne.

1. Przykłady
    - 

    - Jeden playbook z zmiennymi i taskiem
    ```yaml
        - name: Uruchomienie prostej usługi
        hosts: serwery_www
        vars:
            port: 8080
            service_name: nginx
        tasks:
            - name: Upewnij sie, ze usluga jest uruchomiona
            ansible.builtin.service:
                name: "{{ service_name }}"
                state: started
    ```
    - playbook z taskiem i osobnym plikiem na zmienne
    * playbook.yaml
    ```yaml
        - name: Przyklad z plikiem zmiennych
            hosts: serwery_www
            vars_files:
                - vars/aplikacja.yml
            tasks:
                - name: Wyswietl port aplikacji
                ansible.builtin.debug:
                    msg: "Port aplikacji to {{ port }}"
    ```
    * vars.yaml
    ```yaml
    port: 80
    username: ansible
    ```
