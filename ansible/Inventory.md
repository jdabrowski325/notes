# Ansible inventory

1. Opis
    -   

    - Inventory to plik, który definiuje listę hostów (serwerów), którymi zarządza Ansible. Może to być statyczny plik w formacie INI lub YAML, lub dynamiczny skrypt, który generuje listę hostów na żądanie.

    - Domyślnie, inventory ma format INI, ale format YAML jest również często używany i bardziej czytelny.

2. Przykłady
    - 

    - 1. 
    ```yaml
    all:
      children:
        webservers:
          hosts:
            web1.example.com:
            web2.example.com:
        databases:
          hosts:
            db1.example.com:
            db2.example.com:
        vars:
          ansible_user: ansible_user
          ansible_ssh_private_key_file: ~/.ssh/id_rsa
    ```