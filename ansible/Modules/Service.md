# Ansible Modules - Service

1. Opis
    - 

    - Moduł service zarządza usługami systemowymi na zdalnych hostach. Może uruchamiać, zatrzymywać, restartować usługi oraz włączać je przy starcie systemu.

2. Wykorzystanie
    - 

    - Używaj go, aby upewnić się, że usługi działają poprawnie, są restartowane po zmianie konfiguracji lub są wyłączane, jeśli nie są potrzebne.

3. Przykłady
    - 

    - 1. 
    ```yaml

    - name: Restartuj usługę Nginx i włącz ją przy starcie
      service:
        name: nginx
        state: restarted
        enabled: yes

    ```