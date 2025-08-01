# Ansible .cfg

1. Opis
    - 

    - Plik ansible.cfg to serce konfiguracji Ansible. Pozwala on na dostosowanie działania programu do twoich potrzeb, bez konieczności wprowadzania zmian w każdym poleceniu. Ansible szuka tego pliku w następującej kolejności:

    - 1. Zmienna środowiskowa ANSIBLE_CONFIG
    - 2. Plik ansible.cfg w bieżącym katalogu
    - 3. Plik .ansible.cfg w katalogu domowym (~/)
    - 4. Plik /etc/ansible/ansible.cfg

2. Przykłady
    - 

    - 1. 
    ```cfg

[defaults]

inventory = ./inventory #sciezka do pliku inventory.yaml
remote_user = ansible_user #podstawowe konto
private_key_file = ~/.ssh/ansible_id_rsa #sciezka klucza ssh
host_key_checking = True #sprawdzanie klucza ssh

[privilege_escalation]

become = True #zezwolenie
become_method = su #metoda su 
become_user = root #user którym ma sie stać

    ```