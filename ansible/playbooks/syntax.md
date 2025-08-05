# Ansible - playbooks Syntax

- Syntaxy do uzycia w playbook'ach

1. Loops
    - 

    - aby uzywac petle trzeba korzystac z jinja2

    - Przykład

    ```conf

    # templates/server.conf.j2

    {% for host in groups['web_servers'] %}
      server {{ hostvars[host]['ansible_default_ipv4']['address'] }}:80;
    {% endfor %}

    ```

2. Warunki if, else
  - 

  - aby uzywac warunki trzeba korzystac z jinja2

  ```yaml

  my_var: >-
  {%- if ansible_distribution == 'Ubuntu' -%}
    'param for ubuntu'
  {%- elif ansible_distribution == 'Debian' -%}
    'params for debian'
  {%- else -%}
    'what else'
  {%- endif -%}


  ```

3. When
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

4. Register
    - 

    - `Register` - Zapisanie pełnego wyniku wykonania zadania do zmiennej. Pozwala na użycie tych danych w kolejnych zadaniach.

    - Przykład

    ```yaml
        - name: Sprawdz status uslugi
          ansible.builtin.command: systemctl is-active nginx
          register: status_nginx
          ignore_errors: true
    ```

5. Register i When
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

6. Async
  - 

  - Uruchamianie długo trwających zadań w tle, bez blokowania reszty playbooka. Ansible uruchamia zadanie i nie czeka na jego zakończenie. Zamiast tego sprawdza status zadania co jakiś czas.

  - `async` i `poll`

  - Przykład

  ```yaml

    - name: Uruchomienie skryptu, ktory trwa dlugo i sprawdzenie statusu po 15 sekundach
      ansible.builtin.shell: /opt/long_running_script.sh
      async: 300
      poll: 15

  ```

7. Serial
  - 

  - Wykonywanie zadań na serwerach w określonej kolejności, w małych, kontrolowanych grupach. Zamiast wykonywać zadania na wszystkich hostach jednocześnie, możesz robić to partiami.

  - Przykład

  ```yaml
    - name: Wdrozenie na serwerach w partiach po 3
    hosts: serwery_www
    serial: 3
    tasks:
      - name: Wlacz tryb konserwacji
        ansible.builtin.command: /usr/local/bin/maintenance_mode_on.sh
        delegate_to: "{{ item }}"
        loop: "{{ groups['load_balancers'] }}"

      - name: Zaktualizuj i zrestartuj serwer
        ansible.builtin.package:
          name: httpd
          state: latest
        notify: Restart httpd

      - name: Wylacz tryb konserwacji
        ansible.builtin.command: /usr/local/bin/maintenance_mode_off.sh
        delegate_to: "{{ item }}"
        loop: "{{ groups['load_balancers'] }}"

    handlers:
      - name: Restart httpd
        ansible.builtin.service:
          name: httpd
          state: restarted
  ```

8. Parallel
    - 

    - Wykonywanie zadań na wszystkich serwerach w tym samym czasie. Jest to domyślne zachowanie Ansible.

    - Przykład

    ```yaml
      - name: Domyślna aktualizacja na wszystkich serwerach jednoczesnie
        hosts: serwery_www
        tasks:
          - name: Zaktualizuj wszystkie pakiety
            ansible.builtin.apt:
              update_cache: yes
              upgrade: dist
    ```

9. Task Delegation
  - 

  - Pozwala na wykonywanie zadania na innym hoście niż ten, na którym aktualnie pracuje Ansible. Jest to niezwykle przydatne w scenariuszach, gdzie potrzebujesz kontrolować infrastrukturę z centralnego punktu

  - Przykład

  ```yaml

  - name: Take web server out of load balancer pool
    ansible.builtin.command: /usr/local/bin/lb_api --remove-server={{ inventory_hostname }}
    delegate_to: lb_server

  ```

10. Blocks
  - 

  - Grupowanie zadań. Bloki pozwalają na logiczne łączenie ze sobą powiązanych zadań, co zwiększa czytelność i ułatwia zarządzanie. Co ważniejsze, bloki są używane w połączeniu z dyrektywami rescue i always, które umożliwiają obsługę błędów.

  - Przykład

  ```yaml

  - name: A playbook with blocks
  hosts: all
  tasks:
    - name: Start of the playbook
      ansible.builtin.debug:
        msg: "Starting tasks..."
    
    - block:
        - name: First task in the block
          ansible.builtin.command: /usr/bin/echo "This is inside a block"
        
        - name: Second task in the block
          ansible.builtin.command: /usr/bin/echo "Another task"
      rescue:
        - name: Handle error
          ansible.builtin.debug:
            msg: "An error occurred in the block. Handling it now."

  ```

11. Magic vars
  - 

  - Specjalne zmienne, które są automatycznie tworzone i zarządzane przez Ansible. Zawierają one przydatne informacje o aktualnym stanie hosta, playbooka lub środowiska.

  - Przykłady

    1. `hostvars`
      - Słownik, który zawiera wszystkie zmienne i fakty dla każdego hosta w twoim inwentarzu. Umożliwia dostęp do danych z innych hostów.

      ```yaml

      - name: Get IP of a different host
          ansible.builtin.debug:
            msg: "The IP of another_host is {{ hostvars['another_host'].ansible_default_ipv4.address }}"

      ```

    2. `inventory_hostname`
      - Nazwa hosta, na którym aktualnie wykonywane jest zadanie.

      ```yaml

      - name: Display my hostname
        ansible.builtin.debug:
          msg: "My hostname is {{ inventory_hostname }}"

      ```

    3. `group_names`
      - Lista grup, do których należy dany host.

      ```yaml

      - name: Check my groups
        ansible.builtin.debug:
          msg: "I am in groups: {{ group_names }}"

      ```

    4. `ansible_play_hosts`
      - Lista hostów, które są częścią bieżącego przebiegu playbooka.

    5. `ansible_play_batch`
      - Lista hostów, na których zadanie jest aktualnie wykonywane (szczególnie przydatne z serial).