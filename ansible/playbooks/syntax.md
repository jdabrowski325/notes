# Ansible - playbooks Syntax

- Syntaxy do uzycia w playbook'ach

1. Loops
    - 

    - 

2. When
    - 

    - `when` - działa jak if - ale zawsze zwraca wartosc true/false

    - Przykład
        ```yaml

            - name: Zainstaluj pakiet tylko na Ubuntu
              ansible.builtin.package:
                name: nginx
                state: present
              when: ansible_distribution == 'Ubuntu'

            - name: Zainstaluj pakiet tylko na CentOS
              ansible.builtin.package:
                name: httpd
                state: present
              when: ansible_distribution == 'CentOS'

        ```

3. Register
    - 

    - `Register` - Zapisanie pełnego wyniku wykonania zadania do zmiennej. Pozwala na użycie tych danych w kolejnych zadaniach.

    - Przykład
    ```yaml
        - name: Sprawdz status uslugi
          ansible.builtin.command: systemctl is-active nginx
          register: status_nginx
          ignore_errors: true
    ```

4. Register i When
    - 

    - Wykonywanie zadań na podstawie wyniku poprzednich. To jeden z najpotężniejszych wzorców w Ansible.

    - Przykład
    ```yaml
    
    - name: Sprawdz status uslugi
      ansible.builtin.command: systemctl is-active nginx
      register: status_nginx
      ignore_errors: true

    - name: Uruchom usluge tylko jesli jest wylaczona
      ansible.builtin.service:
        name: nginx
        state: started
      when: status_nginx.rc != 0

    ```