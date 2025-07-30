# File Cache - Amazon **File Cache**

![File Cache](../images/services/Arch_Amazon-File-Cache_32.png "AWS File Cache")

1. Opis
    - 

    - Usługa, która zapewnia szybką, tymczasową pamięć podręczną dla danych plików, niezależnie od tego, czy są przechowywane lokalnie, w [Amazon S3](S3.md "AWS S3"), czy w innych systemach plików AWS (np. [FSx](FSx.md "AWS FSx")).
    - Jest zaprojektowana, aby przyspieszyć obciążenia wymagające dużej przepustowości i niskich opóźnień, takie jak uczenie maszynowe, rendering mediów i analityka danych.

2. Funkcjonalności
    - 

    - Zapewnia sub-milisekundowe opóźnienia, setki GB/s przepustowości i miliony **IOPS** **(Operacje wejścia-wyjścia na sekundę)**
    - Automatycznie ładuje dane do pamięci podręcznej w miarę ich potrzeby (lazy-loading) lub umożliwia wstępne ładowanie (pre-loading) danych przed rozpoczęciem pracy
    - Dane w pamięci podręcznej są szyfrowane w spoczynku i w transporcie, a usługa jest zintegrowana z AWS IAM dla kontroli dostępu.
    - Umożliwia dostęp do danych z wielu lokalizacji (lokalnych serwerów NFS, [Amazon S3](S3.md "AWS S3"), [FSx](FSx.md "AWS Fsx")) za pomocą jednego punktu dostepu

3. Pricing
    - 

    - [Pricing](https://aws.amazon.com/filecache/pricing/)


4. Troubleshooting
    - 

    - [Troubleshooting](https://docs.aws.amazon.com/fsx/latest/FileCacheGuide/troubleshooting.html)