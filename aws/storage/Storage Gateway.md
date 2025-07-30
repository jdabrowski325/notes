# Storage Gateway - Amazon **Storage Gateway**

![Storage Gateway](../images/services/Arch_AWS-Storage-Gateway_32.png "AWS Storage Gateway")

1. Opis
    - 

    - Hybrydowa usługa przechowywania danych, która łączy lokalną infrastrukture z chmurową AWS
    - Umozliwia **bezpieczne** i **efektywne** przeszyłanie danych między aplikacjami a pamiecią masową AWS

2. Funkcjonalności
    - 

    - Pozwala lokalnym aplikacjom bezproblemowo korzystać z usług przechowywania AWS, takich jak [Amazon S3](S3.md "AWS S3") czy [Amazon EBS](EBS.md "AWS EBS")
    - Pozwala na uzywanie róznych typów *gateway*'ów do róznych uzyć:
        * Tape
        * S3 File
        * Amazon FSx File
        * Volume
    - Gateway przechowuje często uzywane pliki lokalne (zmniejszenie opóźnienia) jednocześnie zarządzając przesyłaniem danych do chmury
    - Wszyskie dane sa szyfrowane oraz zintegrowane z [Amazon IAM](../security/IAM.md "AWS IAM")


3. Pricing
    - 

    - [Pricing](https://aws.amazon.com/storagegateway/pricing/)

4. Troubleshooting
    - 

    - [Troubleshooting](https://docs.aws.amazon.com/filegateway/latest/filefsxw/troubleshooting-gateway-issues.html)