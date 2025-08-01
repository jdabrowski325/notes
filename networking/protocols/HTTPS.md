# HTTPS - Hypertext Transfer Protocol Secure

1. Port:
    * 443

2. Warstwa OSI
    * 7 (aplikacji)

3. Działanie
    - 
    - W przeciwieństwie do HTTP, HTTPS dodaje dodatkową warstwę bezpieczeństwa, która operuje poniżej Warstwy Aplikacji, ale powyżej Warstwy Transportowej. Tą warstwą jest TLS (Transport Layer Security), a wcześniej jego poprzednik, SSL (Secure Sockets Layer).

    * TLS Handshake
        1. Klient wysyła komunikat "Client Hello" z informacjami o wspieranych wersjach TLS i algorytmach szyfrowania.

        2. Serwer odpowiada "Server Hello", wybierając wersję TLS i algorytm szyfrowania, oraz wysyła swój certyfikat cyfrowy.

        3. Klient weryfikuje certyfikat serwera. Jeśli jest ważny i zaufany, klient generuje "premaster secret" (tajny klucz wstępny), szyfruje go kluczem publicznym serwera (z certyfikatu) i wysyła do serwera.

        4. Serwer deszyfruje "premaster secret" swoim kluczem prywatnym.

        5. Z "premaster secret" i innych danych obie strony generują wspólny "klucz sesji".

        6. Obie strony wysyłają do siebie zaszyfrowane komunikaty potwierdzające zakończenie uścisku dłoni.

    - Po pomyślnym `TLS handshake`'u, wszystkie dalsze komunikaty HTTP (żądania i odpowiedzi) są szyfrowane za pomocą uzgodnionego klucza sesji.

    - Zaszyfrowane dane są przesyłane przez TCP na porcie 443 do i od serwera.

    - Po odebraniu, dane są deszyfrowane przez drugą stronę.

4. Headers (Nagłówki)
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