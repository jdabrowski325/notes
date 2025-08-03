# RDS - Amazon **Relational Database Service**

![RDS](../images/services/Arch_Amazon-RDS_32.png "AWS RDS")

1. Opis
    - 

    - Usługa w chmurze, która ułatwia konfigurowanie, obsługę i skalowanie relacyjnej bazy danych.
    - Usługa wspiera popularne silniki baz danych, w tym Amazon Aurora, PostgreSQL, MySQL, MariaDB, Oracle i SQL Server

2. Funkcjonalności
    - 

    - RDS tworzy codzienne kopie zapasowe bazy danych i przechowuje logi transakcji, co umożliwia przywrócenie bazy do dowolnego punktu w czasie.
    - (Multi-AZ) Aby zapewnić wysoką dostępność, można wdrożyć bazę danych w konfiguracji Multi-AZ. AWS automatycznie tworzy replikę w innej strefie dostępności i w przypadku awarii, przełącza ruch na replikę.
    - (Read Replicas) Można tworzyć repliki bazy danych do odczytu, aby zwiększyć wydajność aplikacji, która intensywnie odczytuje dane.
    - RDS zapewnia, że silnik bazy danych jest zawsze aktualny pod względem bezpieczeństwa i stabilności

3. Pricing
    - 

    - [Pricing](https://aws.amazon.com/rds/pricing/)

4. Troubleshooting
    - 

    - [Troubleshooting](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/CHAP_Troubleshooting.html)