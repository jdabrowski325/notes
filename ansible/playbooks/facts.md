# Ansible - playbooks facts

1. Opis
    - 

    - To dane, które są automatycznie zbierane o docelowych hostach, na których uruchamiasz playbook. Ansible domyślnie łączy się z maszyną i zbiera całą masę informacji o jej systemie operacyjnym, interfejsach sieciowych, dyskach, zainstalowanych pakietach, pamięci RAM i wielu innych.
    - Pozwalają pisać dynamiczne playbooki, które dostosowują swoje działanie do konkretnego hosta. Zamiast "na sztywno" zakładać, że na wszystkich serwerach masz tę samą wersję systemu operacyjnego, możesz sprawdzić to za pomocą faktów i podjąć odpowiednie kroki.

2. Przykłady
    - 

    - Uzycie facts aby wypisać dane systemowe
    ```yaml
        - name: "Dane systemowe"
            hosts: all
            gather_facts: true

            tasks:
              - name: fakty systemowe
                ansible.builtin.debug:
                msg:
                    - "--- Informacje o hoscie {{ ansible_hostname }} ---"
                    - "Adres IPv4: {{ ansible_default_ipv4.address }}"
                    - "Adres IPv6: {{ ansible_default_ipv6.address | default('Brak adresu IPv6') }}"
                    - "System operacyjny: {{ ansible_distribution }} {{ ansible_distribution_major_version }} ({{ ansible_distribution_version }})"
                    - "Architektura procesora: {{ ansible_architecture }}"
                    - "Model procesora: {{ ansible_processor[1] }}"
                    - "Liczba procesorow: {{ ansible_processor_count }}"
                    - "Calkowita pamiec RAM: {{ (ansible_memtotal_mb / 1024) | round(2) }} GB"
                    - "Dostepna pamiec RAM: {{ (ansible_memfree_mb / 1024) | round(2) }} GB"
                    - "Uzycie RAM: {{ ((ansible_memtotal_mb - ansible_memfree_mb) / ansible_memtotal_mb * 100) | round(2) }} %"
                    - "---"
    ```