# Ansible - Troubleshooting


1. Tryb **Verbose**
    - 

    - Pozwala on zobaczyć, co dokładnie dzieje się w tle.

    - **Kiedy używać**: Zawsze, gdy coś nie działa tak, jak powinno, a standardowe wyjście nie dostarcza wystarczających informacji.

    * `ansible-playbook --verbose (lub -v)`: Wyświetla podstawowe informacje o przebiegu zadań.

    * `ansible-playbook -vv`: Dodaje więcej szczegółów, np. o tym, które fakty są zbierane.

    * `ansible-playbook -vvv`: To jest najczęściej używany tryb do debugowania. Wyświetla szczegółowe wyjście z każdego modułu oraz dane wyjściowe z poleceń SSH.

    * `ansible-playbook -vvvv:` Najbardziej szczegółowy tryb. Pokazuje całą komunikację SSH, co jest kluczowe w przypadku problemów z połączeniem.



2. Moduł **ansible.builtin.debug**
    - 

    - Użyj modułu debug, aby wyświetlić wartości zmiennych, faktów, lub wyjścia z poprzednich zadań.

    - Kiedy używać:

        - Gdy chcesz sprawdzić, czy zmienna ma poprawną wartość.

        - Aby zobaczyć, jakie fakty zostały zebrane o hoście.

        - Aby sprawdzić zawartość pliku, który został wgrany za pomocą modułu template.

    - Przykład

    ```yaml

        - name: Check a variable
          ansible.builtin.debug:
            var: my_variable

    ```

3. Moduł **ansible.builtin.shell** i **ansible.builtin.command**
    - 

    - Jeśli twój playbook nie działa, a zadanie korzysta z modułu Ansible (np. ansible.builtin.package), spróbuj wykonać to samo polecenie bezpośrednio na serwerze za pomocą modułu shell lub command. Pomoże to ustalić, czy problem leży po stronie Ansible, czy samej komendy na zdalnej maszynie.

    - Kiedy używać:

        - Gdy moduł Ansible (np. ansible.builtin.apt) zwraca błąd.
        - Aby sprawdzić, czy polecenie działa poprawnie, a błąd nie jest spowodowany specyfiką środowiska (np. brakiem pakietu python3 na serwerze).

    - Przykład
    
    ```yaml

    - name: Test if a command works
      ansible.builtin.shell: apt install nginx -y

    ```

4. Sprawdzanie połączeń **ansible.builtin.ping**
    - 

    - Zawsze zaczynaj od sprawdzenia, czy Ansible jest w stanie połączyć się z docelowym hostem

    - Kiedy używać: Zanim uruchomisz jakikolwiek playbook, upewnij się, że host jest osiągalny.

    - Przykład
    
    ```
    ansible all -m ansible.builtin.ping
    ```

5. Tryb **check** i **diff**
    - 

    - `--check`: Uruchamia playbook w trybie "suchego przebiegu". Ansible przejdzie przez wszystkie zadania, ale nie wprowadzi żadnych zmian na docelowych hostach. Pozwala to na weryfikację logiki playbooka bez ryzyka.

    - `--diff`: Wyświetla różnice w plikach konfiguracyjnych, które zostałyby zmienione. Jest to bardzo przydatne, gdy używasz szablonów

    - Kiedy używać: Zawsze przed wdrożeniem ważnych zmian. check i diff to twoi najlepsi przyjaciele, jeśli chcesz uniknąć niespodzianek na produkcji.

    - Przykład
    ```
    ansible-playbook your_playbook.yml --check --diff
    ```

6. Izolowanie problemów
    - 

    - Jeśli błąd pojawia się w złożonym playbooku, który ma wiele zadań, spróbuj:

        - Ograniczyć playbook do jednego hosta

        ```
        --limit [nazwa_hosta]
        ```

        - Ograniczyć playbook do jednego zadania

        ```
        --tags [nazwa_tagu]
        ```

7. Sprawdzenie syntaxu **YAML**
    - 

    - "Invalid YAML"

    ```
    python -c 'import yaml, sys; yaml.safe_load(sys.stdin)' < your_playbook.yaml
    ```

    ```
    python3 -c 'import yaml, sys; yaml.safe_load(sys.stdin)' < your_playbook.yml
    ```
