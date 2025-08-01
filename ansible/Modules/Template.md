# Ansible Modules - Template

1. Opis
    - 

    - Moduł template używa silnika szablonów Jinja2 do generowania plików na hoście zdalnym. Pozwala to na tworzenie dynamicznych plików konfiguracyjnych z użyciem zmiennych.

2. Wykorzystanie
    - 

    - Używaj go, gdy plik konfiguracyjny musi zawierać unikalne wartości dla każdego hosta, np. adres IP, nazwa hosta lub inne zmienne z inventory.

3. Przykłady
    - 

    - 1. 
    ```yaml

    - name: Utwórz plik motd z szablonu
      template:
        src: templates/motd.j2
        dest: /etc/motd
        owner: root
        group: root
        mode: '0644'

    ```

    ```jd2
    Welcome to {{ ansible_hostname }}!
    
    This system is running {{ ansible_os_family }} {{ ansible_distribution_major_version }}.
    ```