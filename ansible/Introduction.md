# Introduction - Ansible

[git](https://github.com/spurin/diveintoansible)

- narzędzie do automatyzacji, które upraszcza zarządzanie konfiguracją, wdrażanie aplikacji i wykonywanie powtarzalnych zadań.

1. Core Concept
    - 

    - Idempotency
        - wielokrotne uruchomienie tego samego zadania zawsze prowadzi do tego samego pożądanego stanu końcowego.

    - Agentless
        - nie wymaga instalowania żadnego dodatkowego oprogramowania na zarządzanych maszynach, używając do komunikacji standardowego protokołu SSH.

    - Declarative
        - Opisujesz docelowy stan systemu, a Ansible sam dba o to, jak go osiągnąć.

2. Core Components
    - 

    - Control Node
        - To maszyna, z której uruchamiasz Ansible, wydając polecenia do innych maszyn.

    - Managed Nodes
        - Są to serwery, które automatyzujesz za pomocą Ansible.

    - Inventory
        - Jest to lista wszystkich maszyn, którymi chcesz zarządzać, często zorganizowanych w grupy.

    - Playbooks
        - To pliki YAML, JSON, ini które definiują listę zadań do wykonania na określonych maszynach.

    - Tasks
        - To pojedyncze akcje, które Ansible ma wykonać, takie jak instalacja pakietu czy kopiowanie pliku.

    - Modules
        - Są to małe programy, których Ansible używa do wykonywania konkretnych zadań.

    - Roles
        - Stanowią ustrukturyzowany sposób na organizowanie playbooków i powiązanych z nimi plików, co ułatwia ponowne użycie kodu.