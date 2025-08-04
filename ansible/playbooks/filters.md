# Ansible - playbooks filter

1. Opis
    - 

    - Filtry w Ansible to nic innego jak narzędzia do manipulowania danymi. Pozwalają one na przekształcanie, modyfikowanie, selekcjonowanie lub formatowanie zmiennych i faktów, tak aby pasowały do twoich potrzeb.

        - Matematyczne:
            - round - Zaokrągla liczbę.
            - int - Konwertuje wartość na liczbę całkowitą.
            - float - Konwertuje wartość na liczbę zmiennoprzecinkową.
        
        - Tekstowe
            - lower - Zmienia tekst na małe litery.
            - upper - Zmienia tekst na wielkie litery.
            - replace - Zamienia jedną część tekstu na inną.

        - Listowe (filtrowanie)
            - map - Stosuje filtr do każdego elementu na liście.
            - sort - Sortuje listę.
            - unique - Usuwa duplikaty z listy.
            - json_query - Używa składni JSONPath do wyciągania danych

        - Testowe
            - defined - Sprawdza, czy zmienna jest zdefiniowana.
            - list - Sprawdza, czy zmienna jest listą.
            - ipv4 - Sprawdza, czy wartość jest poprawnym adresem IPv4.