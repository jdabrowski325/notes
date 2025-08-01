# HTTP - Hypertext Transfer Protocol

1. Port
    * 80

2. Warstwa OSI
    * 7 (aplikacji)


3. Szczegóły
    - 
    - HTTP działa na Warstwie Aplikacji (Warstwa 7) modelu OSI, tak samo jak HTTPS, ale bez dodatkowej warstwy bezpieczeństwa TLS/SSL.

    - polaczenie na strone: 
        - Przeglądarka nawiązuje połączenie TCP z serwerem na porcie 80.
        - Po nawiązaniu połączenia TCP, przeglądarka wysyła żądanie HTTP (np. GET /index.html HTTP/1.1) do serwera.
        - Serwer przetwarza żądanie i wysyła odpowiedź HTTP, zawierającą status odpowiedzi i zawartość żądanego zasobu (np. kod HTML strony).
        - Przeglądarka odbiera odpowiedź i wyświetla zawartość użytkownikowi.

    - Headers (Nagłówki)
        - Request header
            - Contain more information about the resource to be fetched, or about the client requesting the resource.

            - GET /home.html HTTP/1.1
            - User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10.9; rv:50.0) Gecko/20100101 Firefox/50.0
            - Host: developer.mozilla.org
            - Accept: text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8
            - Accept-Language: en-US,en;q=0.5
            - Accept-Encoding: gzip, deflate, br
            - Referer: https://developer.mozilla.org/testpage.html
            - Connection: keep-alive
            - Upgrade-Insecure-Requests: 1
            - If-Modified-Since: Mon, 18 Jul 2016 02:36:04 GMT
            - If-None-Match: "c561c68d0ba92bbeb8b0fff2a9199f722e3a621a"
            - Cache-Control: max-age=0

        - Response header
            - Hold additional information about the response, like its location or about the server providing it.

            - 200 OK
            - Access-Control-Allow-Origin: *
            - Connection: Keep-Alive
            - Content-Encoding: gzip
            - Content-Type: text/html; charset=utf-8
            - Date: Mon, 18 Jul 2016 16:06:00 GMT
            - ETag: "c561c68d0ba92bbeb8b0f612a9199f722e3a621a"
            - Keep-Alive: timeout=5, max=997
            - Last-Modified: Mon, 18 Jul 2016 02:36:04 GMT
            - Server: Apache
            - Set-Cookie: my-key=my value; expires=Mon, 17-Jul-2017 16:06:00 GMT; Max-Age=31449600; Path=/; secure
            - Transfer-Encoding: chunked
            - Vary: Cookie, Accept-Encoding
            - X-Backend-Server: developer2.webapp.scl3.mozilla.com
            - X-Cache-Info: not cacheable; meta data too large
            - X-kuma-revision: 1085259
            - x-frame-options: DENY

        - Representation header
            - Contain information about the body of the resource, like its MIME type, or encoding/compression applied.

            - Content-Length
            - Content-Range
            - Content-Type
            - Content-Encoding
            - Content-Location
            - Content-Language

        - Payload header
            - Contain representation-independent information about payload data, including content length and the encoding used for transport.

            - Content-Length
            - Content-Range
            - Trailer
            - Transfer-Encoding