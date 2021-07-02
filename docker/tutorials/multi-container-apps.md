---
title: 'Samouczek platformy Docker — część 6: aplikacje z wieloma kontenerami'
description: Jak skonfigurować sieć między kontenerami i dodać kontener dla bazy danych MySQL.
ms.date: 08/04/2020
author: nebuk89
ms.author: ghogen
manager: jmartens
ms.topic: conceptual
ms.workload:
- azure
ms.openlocfilehash: d23d1f5d94729741630ee76263fd5b32041e9cfd
ms.sourcegitcommit: 8b75524dc544e34d09ef428c3ebbc9b09f14982d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/02/2021
ms.locfileid: "113222919"
---
# <a name="multi-container-apps"></a>Aplikacje z wieloma kontenerami

Do tej chwili pracujesz z aplikacjami z jednym kontenerem. Teraz jednak dodasz program MySQL do stosu aplikacji. Często pojawia się następujące pytanie: "Gdzie będzie działać program MySQL? Zainstaluj go w tym samym kontenerze lub uruchom go oddzielnie?". Ogólnie rzecz biorąc, **każdy kontener powinien wykonać jedną rzecz i zrobić to dobrze.** Z kilku powodów:

- Istnieje dobra szansa, że trzeba będzie skalować interfejsy API i frontonie inaczej niż bazy danych
- Oddzielne kontenery umożliwiają izolowanie wersji i aktualizacji wersji
- Chociaż możesz używać kontenera dla bazy danych lokalnie, możesz użyć usługi zarządzanej dla bazy danych w środowisku produkcyjnym. Nie chcesz wtedy dostarczać aparatu bazy danych wraz z aplikacją.
- Uruchomienie wielu procesów wymaga menedżera procesów (kontener uruchamia tylko jeden proces), co zwiększa złożoność uruchamiania/zamykania kontenera.

Jest też więcej powodów. Dlatego zaktualizuj aplikację, aby działała w ten sposób:

![Aplikacja Todo połączona z kontenerem MySQL](media/multi-app-architecture.png)

## <a name="container-networking"></a>Sieć kontenerów

Należy pamiętać, że kontenery są domyślnie uruchamiane w izolacji i nie mają żadnych informacji o innych procesach lub kontenerach na tym samym komputerze. Jak więc zezwolić jedneowi kontenerowi na rozmowę z innym? Odpowiedzią jest **sieć**. Teraz nie musisz być inżynierem sieci (hooray!). Po prostu zapamiętaj tę regułę...

> [!NOTE]
> Jeśli dwa kontenery znajdują się w tej samej sieci, mogą ze sobą rozmawiać. Jeśli tak nie jest, nie mogą.

## <a name="start-mysql"></a>Uruchamianie programu MySQL

Kontener można umieścić w sieci na dwa sposoby: przypisać go na początku lub połączyć z istniejącym kontenerem. Na razie najpierw utworzysz sieć i dołączysz kontener MySQL podczas uruchamiania.

1. Utwórz sieć.

    ```bash
    docker network create todo-app
    ```

1. Uruchom kontener MySQL i dołącz go do sieci. Zdefiniujemy również kilka zmiennych środowiskowych, których baza danych użyje do zainicjowania bazy danych (zobacz sekcję "Zmienne środowiskowe" na liście [mySQL Docker Hub](https://hub.docker.com/_/mysql/)) (zastąp znaki znakiem w ciągu ` \ ` `` ` `` Windows PowerShell).

    ```bash
    docker run -d \
        --network todo-app --network-alias mysql \
        -v todo-mysql-data:/var/lib/mysql \
        -e MYSQL_ROOT_PASSWORD=secret \
        -e MYSQL_DATABASE=todos \
        mysql:5.7
    ```

    Zobaczysz również, że określono `--network-alias` flagę . Wrócimy do tego za chwilę.

    > [!TIP]
    > Zauważysz, że w tym miejscu używasz nazwy woluminu i dzieje się to w miejscu , w którym `todo-mysql-data` `/var/lib/mysql` mySQL przechowuje swoje dane. Jednak nigdy nie uruchomiono `docker volume create` polecenia . Docker rozpoznaje, że chcesz użyć nazwanego woluminu, i tworzy go automatycznie.

1. Aby upewnić się, że baza danych jest uruchomiona, połącz się z bazą danych i sprawdź, czy nawiąże połączenie.

    ```bash
    docker exec -it <mysql-container-id> mysql -p
    ```

    Gdy pojawi się monit o hasło, wpisz wpis **tajny**. W powłoki MySQL wyświetl listę baz danych i sprawdź, czy baza danych jest `todos` wyświetlona.

    ```cli
    mysql> SHOW DATABASES;
    ```

    Wyświetlone dane wyjściowe powinny wyglądać mniej więcej tak:

    ```plaintext
    +--------------------+
    | Database           |
    +--------------------+
    | information_schema |
    | mysql              |
    | performance_schema |
    | sys                |
    | todos              |
    +--------------------+
    5 rows in set (0.00 sec)
    ```

    Brawo! Masz bazę `todos` danych i jest ona gotowa do użycia.

## <a name="connect-to-mysql"></a>Połączenie do mySQL

Teraz, gdy wiesz, że program MySQL jest uruchomiony i działa, użyjmy go! Ale pytanie brzmi... Jak? Jeśli uruchamiasz inny kontener w tej samej sieci, jak znaleźć kontener (pamiętaj, że każdy kontener ma własny adres IP)?

Aby to ustalić, użyjemy kontenera do rozwiązywania problemów z siecią, [który](https://github.com/nicolaka/netshoot) jest dostarczany z mnóstwem narzędzi przydatnych do rozwiązywania lub debugowania problemów z siecią. 

1. Uruchom nowy kontener przy użyciu `nicolaka/netshoot` obrazu. Pamiętaj, aby połączyć ją z tę samą siecią.

    ```bash
    docker run -it --network todo-app nicolaka/netshoot
    ```

1. Wewnątrz kontenera użyj polecenia `dig` , które jest przydatnym narzędziem DNS. Odszukaj adres IP dla nazwy hosta `mysql` .

    ```bash
    dig mysql
    ```

    Otrzymasz dane wyjściowe podobne do tych...

    ```text
    ; <<>> DiG 9.14.1 <<>> mysql
    ;; global options: +cmd
    ;; Got answer:
    ;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 32162
    ;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 0

    ;; QUESTION SECTION:
    ;mysql.             IN  A

    ;; ANSWER SECTION:
    mysql.          600 IN  A   172.23.0.2

    ;; Query time: 0 msec
    ;; SERVER: 127.0.0.11#53(127.0.0.11)
    ;; WHEN: Tue Oct 01 23:47:24 UTC 2019
    ;; MSG SIZE  rcvd: 44
    ```

    W sekcji "ANSWER SECTION" (SEKCJA ODPOWIEDZI) zostanie wyświetlony rekord dla adresu , który jest rozpoznany jako `A` `mysql` `172.23.0.2` (twój adres IP najprawdopodobniej będzie miał inną wartość). Chociaż zazwyczaj nie jest prawidłową nazwą hosta, platformie Docker udało się ją rozpoznać na adres IP kontenera, który miał alias sieciowy (pamiętasz flagę użytą `mysql` `--network-alias` wcześniej?).

    Oznacza to, że... Aplikacja po prostu musi połączyć się z hostem o nazwie `mysql` i będzie rozmawiała z bazą danych. Nie jest to znacznie prostsze!

## <a name="run-your-app-with-mysql"></a>Uruchamianie aplikacji za pomocą usługi MySQL

Aplikacja z todo obsługuje ustawienie kilku zmiennych środowiskowych w celu określenia ustawień połączenia mySQL. Są to:

- `MYSQL_HOST` — nazwa hosta uruchomionego serwera MySQL
- `MYSQL_USER` — nazwa użytkownika do użycia dla połączenia
- `MYSQL_PASSWORD` — hasło do połączenia
- `MYSQL_DB` — baza danych do użycia po na połączeniu

> [!WARNING]
> **Ustawianie ustawień Ustawienia za pomocą zmiennych środowiskowych** Mimo że ustawianie ustawień połączenia przy użyciu zmiennych środowiskowych jest ogólnie dobre dla procesów programistyczych, zdecydowanie nie zaleca się uruchamiania aplikacji w środowisku produkcyjnym. Aby zrozumieć, dlaczego nie należy używać zmiennych środowiskowych dla [tajnych danych, zobacz](https://diogomonica.com/2017/03/27/why-you-shouldnt-use-env-variables-for-secret-data/)dlaczego nie należy używać zmiennych.
> Bezpieczniejszym mechanizmem jest użycie obsługi kluczy tajnych zapewnianych przez platformę orkiestracji kontenerów. W większości przypadków te wpisy tajne są instalowane jako pliki w uruchomionym kontenerze. Zobaczysz, że wiele aplikacji (w tym obraz MySQL i aplikacja todo) obsługuje również vars env z sufiksem, aby wskazać plik `_FILE` zawierający plik.
> Na przykład ustawienie var spowoduje, że aplikacja będzie używać zawartości przywoływanych `MYSQL_PASSWORD_FILE` plików jako hasła połączenia. Docker nie robi niczego, aby obsługiwać te vars env. Aplikacja musi wiedzieć, aby poszukać zmiennej i pobrać zawartość pliku.

Po objaśnionej pracy uruchom kontener gotowy do tworzenia.

1. Określ każdą z powyższych zmiennych środowiskowych i połącz kontener z siecią aplikacji (zastąp znaki w ` \ ` `` ` `` Windows PowerShell).

    ```bash hl_lines="3 4 5 6 7"
    docker run -dp 3000:3000 \
      -w /app -v ${PWD}:/app \
      --network todo-app \
      -e MYSQL_HOST=mysql \
      -e MYSQL_USER=root \
      -e MYSQL_PASSWORD=secret \
      -e MYSQL_DB=todos \
      node:12-alpine \
      sh -c "yarn install && yarn run dev"
    ```

1. Jeśli przyjrzysz się dziennikom kontenera ( ), powinien zostać wyświetlony komunikat informujący, że korzysta on z bazy danych `docker logs <container-id>` MySQL.

    ```plaintext hl_lines="7"
    # Previous log messages omitted
    $ nodemon src/index.js
    [nodemon] 1.19.2
    [nodemon] to restart at any time, enter `rs`
    [nodemon] watching dir(s): *.*
    [nodemon] starting `node src/index.js`
    Connected to mysql db at host mysql
    Listening on port 3000
    ```

1. Otwórz aplikację w przeglądarce i dodaj kilka elementów do listy zadań do oddawania.

1. Połączenie do bazy danych MySQL i udowodnij, że elementy są zapisywane w bazie danych. Pamiętaj, że hasło jest **tajne.**

    ```bash
    docker exec -ti <mysql-container-id> mysql -p todos
    ```

    W powłoki MySQL uruchom następujące elementy:

    ```plaintext
    mysql> select * from todo_items;
    +--------------------------------------+--------------------+-----------+
    | id                                   | name               | completed |
    +--------------------------------------+--------------------+-----------+
    | c906ff08-60e6-44e6-8f49-ed56a0853e85 | Do amazing things! |         0 |
    | 2912a79e-8486-4bc3-a4c5-460793a575ab | Be awesome!        |         0 |
    +--------------------------------------+--------------------+-----------+
    ```

    Oczywiście tabela będzie wyglądać inaczej, ponieważ zawiera elementy. Jednak powinny być tam przechowywane.

Jeśli szybko przyjrzysz się rozszerzeniu platformy Docker, zobaczysz, że masz uruchomione dwa kontenery aplikacji. Nie ma jednak rzeczywistego wskazania, że są one zgrupowane razem w jednej aplikacji. Wkrótce dowiesz się, jak to poprawić!

![Rozszerzenie platformy Docker przedstawiające dwa niezgrupowane kontenery aplikacji](media/vs-multi-container-app.png)

## <a name="recap"></a>Podsumowanie

W tym momencie masz aplikację, która teraz przechowuje swoje dane w zewnętrznej bazie danych uruchomionej w oddzielnym kontenerze. Wiesz już trochę na temat sieci kontenerów i wiesz, jak można przeprowadzić odnajdywanie usług przy użyciu systemu DNS.

Istnieje jednak dobra szansa, że zaczniesz przytłoczać się wszystkim, co musisz zrobić, aby uruchomić tę aplikację. Musisz utworzyć sieć, uruchomić kontenery, określić wszystkie zmienne środowiskowe, uwidocznić porty i nie tylko. To dużo do zapamiętania i z pewnością utrudnia to komuś innemu.

W następnej sekcji omówienia Docker Compose. Dzięki Docker Compose możesz udostępniać stosy aplikacji w znacznie łatwiejszy sposób i pozwolić innym na ich rozkręcanie za pomocą jednego (i prostego) polecenia.

## <a name="next-steps"></a>Następne kroki

Kontynuuj pracę z samouczkiem!

> [!div class="nextstepaction"]
> [Korzystanie z Docker Compose](use-docker-compose.md)
