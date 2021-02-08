---
title: 'Samouczek platformy Docker — część 6: aplikacje z obsługą kontenera'
description: Jak skonfigurować sieć między kontenerami i dodać kontener dla bazy danych MySQL.
ms.date: 08/04/2020
author: nebuk89
ms.author: ghogen
manager: jmartens
ms.technology: vs-azure
ms.topic: conceptual
ms.workload:
- azure
ms.openlocfilehash: 0c8c9fb4072da071ba06d5dc371e85db8291353a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99841786"
---
# <a name="multi-container-apps"></a>Aplikacje z wieloma kontenerami

Do tego momentu pracujesz z aplikacjami z jednym kontenerem. Jednak teraz dodasz MySQL do stosu aplikacji. Poniższe pytania często się pojawiają — "gdzie będzie działać MySQL? Zainstaluj ją w tym samym kontenerze lub Uruchom osobno? ". Ogólnie rzecz biorąc, **każdy kontener powinien wykonać jedną czynność i zrobić to dobrze.** Kilka przyczyn:

- Istnieje dobrym prawdopodobieństwem, że trzeba będzie skalować interfejsy API i frontony inaczej niż bazy danych
- Oddzielne kontenery umożliwiają przedzielenie wersji i aktualizacji na wersje
- W przypadku korzystania z lokalnego kontenera bazy danych może być konieczne użycie usługi zarządzanej dla bazy danych w środowisku produkcyjnym. Nie chcesz dostarczać aparatu bazy danych do aplikacji.
- Uruchomienie wielu procesów wymaga Menedżera procesów (kontener rozpocznie się tylko jeden proces), co zwiększa złożoność uruchamiania/zamykania kontenera.

Z tego powodu. W związku z tym zaktualizujesz aplikację w taki sposób, aby działała następująco:

![Aplikacja do wykonania połączona z kontenerem MySQL](media/multi-app-architecture.png)

## <a name="container-networking"></a>Sieć kontenerów

Należy pamiętać, że kontenery są domyślnie uruchamiane w izolacji i nie wiedzą o innych procesach i kontenerach na tym samym komputerze. Jak to zrobić, aby umożliwić komunikację jednego kontenera z innym? Odpowiedź to **Sieć**. Teraz nie musisz być inżynierem sieciowym (hura!). Po prostu Zapamiętaj tę regułę...

> [!NOTE]
> Jeśli dwa kontenery znajdują się w tej samej sieci, mogą komunikować się ze sobą. Jeśli nie, nie mogą.

## <a name="start-mysql"></a>Uruchom MySQL

Istnieją dwa sposoby umieszczania kontenera w sieci: należy przypisać je na początku lub połączyć istniejący kontener. Na razie najpierw utworzysz sieć i Dołącz kontener MySQL przy uruchamianiu.

1. Utwórz sieć.

    ```bash
    docker network create todo-app
    ```

1. Uruchom kontener MySQL i dołącz go do sieci. Definiujemy również kilka zmiennych środowiskowych, których baza danych będzie używać w celu zainicjowania bazy danych programu (zobacz sekcję "zmienne środowiskowe" w programie [MySQL Docker Hub list](https://hub.docker.com/_/mysql/)) (Zastąp ` \ ` znaki `` ` `` w programie Windows PowerShell).

    ```bash
    docker run -d \
        --network todo-app --network-alias mysql \
        -v todo-mysql-data:/var/lib/mysql \
        -e MYSQL_ROOT_PASSWORD=secret \
        -e MYSQL_DATABASE=todos \
        mysql:5.7
    ```

    Zobaczysz również, że określono `--network-alias` flagę. Powrócimy do tego przez chwilę.

    > [!TIP]
    > Zauważysz, że używasz tutaj nazwy woluminu `todo-mysql-data` i instalujesz ją w lokalizacji, w której dane są przechowywane w usłudze `/var/lib/mysql` MySQL. Jednak nigdy nie uruchomiono `docker volume create` polecenia. Platforma Docker rozpoznaje, że chcesz użyć nazwanego woluminu i automatycznie utworzy ją.

1. Aby upewnić się, że baza danych została uruchomiona i działa, nawiąż połączenie z bazą danych i sprawdź, czy jest ona połączona.

    ```bash
    docker exec -it <mysql-container-id> mysql -p
    ```

    Po wyświetleniu monitu o hasło wpisz **wpis tajny**. W programie MySQL Shell Utwórz listę baz danych i sprawdź, czy została wyświetlona `todos` baza danych.

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

    Hura! Twoja `todos` baza danych jest gotowa do użycia.

## <a name="connect-to-mysql"></a>Łączenie z bazą danych MySQL

Teraz, gdy już wiesz, że baza danych MySQL jest uruchomiona, użyjmy go! Ale pytanie to... Jaka? Jeśli uruchamiasz inny kontener w tej samej sieci, jak znaleźć kontener (Pamiętaj, że każdy kontener ma własny adres IP)?

Aby to zrobić, zamierzasz korzystać z kontenera [nicolaka/](https://github.com/nicolaka/netshoot) , który dostarcza *wiele* narzędzi, które są przydatne do rozwiązywania problemów lub debugowania problemów z siecią.

1. Rozpocznij nowy kontener przy użyciu `nicolaka/netshoot` obrazu. Upewnij się, że połączenie jest nawiązywane z tą samą siecią.

    ```bash
    docker run -it --network todo-app nicolaka/netshoot
    ```

1. W kontenerze Użyj `dig` polecenia, które jest użytecznym NARZĘDZIEM DNS. Wyszukaj adres IP dla nazwy hosta `mysql` .

    ```bash
    dig mysql
    ```

    Otrzymasz dane wyjściowe podobne do tego...

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

    W sekcji "odpowiedź" zobaczysz `A` rekord dla programu `mysql` , który jest rozpoznawany jako `172.23.0.2` (adres IP prawdopodobnie będzie miał inną wartość). Chociaż `mysql` zwykle nie jest prawidłową nazwą hosta, Aparat Docker mógł go rozpoznać na adres IP kontenera, który miał ten alias sieci (należy pamiętać, że `--network-alias` flaga została użyta wcześniej?).

    Co oznacza to... Aplikacja tylko po prostu musi nawiązać połączenie z hostem o nazwie `mysql` i będzie komunikować się z bazą danych. Nie jest to znacznie prostsze niż to wszystko!

## <a name="run-your-app-with-mysql"></a>Uruchamianie aplikacji za pomocą programu MySQL

Aplikacja do zrobienia obsługuje ustawienie kilku zmiennych środowiskowych w celu określenia ustawień połączenia MySQL. Są to:

- `MYSQL_HOST` -Nazwa hosta dla uruchomionego serwera MySQL
- `MYSQL_USER` -Nazwa użytkownika do użycia w przypadku połączenia
- `MYSQL_PASSWORD` -hasło, które ma być używane na potrzeby połączenia
- `MYSQL_DB` — Baza danych, która ma być używana po połączeniu

> [!WARNING]
> **Ustawianie ustawień połączenia za pomocą zmiennych środowiskowych** Chociaż użycie zmiennych środowiskowych do ustawiania ustawień połączenia jest ogólnie dobry dla rozwoju, zdecydowanie odradza się w przypadku uruchamiania aplikacji w środowisku produkcyjnym. Aby zrozumieć, dlaczego, zobacz [dlaczego nie należy używać zmiennych środowiskowych dla danych tajnych](https://diogomonica.com/2017/03/27/why-you-shouldnt-use-env-variables-for-secret-data/).
> Bardziej bezpieczny mechanizm polega na użyciu tajnej pomocy technicznej dostarczonej przez strukturę aranżacji kontenerów. W większości przypadków te wpisy tajne są instalowane jako pliki w działającym kontenerze. Zobaczysz wiele aplikacji (w tym obraz MySQL i aplikacja do zrobienia), które obsługują także ENV zmiennych z `_FILE` sufiksem, aby wskazywał plik zawierający plik.
> Na przykład ustawienie `MYSQL_PASSWORD_FILE` var spowoduje, że aplikacja będzie używać zawartości pliku, do którego istnieje odwołanie, jako hasła połączenia. Platforma Docker nie wykonuje żadnych czynności do obsługi tych zmiennych ENV. Aplikacja musi wiedzieć, aby wyszukać zmienną i pobrać zawartość pliku.

Ze wszystkich tych wyjaśnień Rozpocznij tworzenie kontenera deweloperskiego!

1. Określ wszystkie powyższe zmienne środowiskowe i Połącz kontener z siecią aplikacji (Zastąp ` \ ` znaki `` ` `` w programie Windows PowerShell).

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

1. Jeśli przeszukiwane są dzienniki dla kontenera ( `docker logs <container-id>` ), powinien zostać wyświetlony komunikat informujący o tym, że używa bazy danych MySQL.

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

1. Otwórz aplikację w przeglądarce i Dodaj kilka elementów do listy zadań do wykonania.

1. Nawiąż połączenie z bazą danych MySQL i Dowiedz się, że elementy są zapisywane w bazie danych. Pamiętaj, że hasło jest **tajne**.

    ```bash
    docker exec -ti <mysql-container-id> mysql -p todos
    ```

    I w usłudze MySQL Shell Uruchom następujące polecenie:

    ```plaintext
    mysql> select * from todo_items;
    +--------------------------------------+--------------------+-----------+
    | id                                   | name               | completed |
    +--------------------------------------+--------------------+-----------+
    | c906ff08-60e6-44e6-8f49-ed56a0853e85 | Do amazing things! |         0 |
    | 2912a79e-8486-4bc3-a4c5-460793a575ab | Be awesome!        |         0 |
    +--------------------------------------+--------------------+-----------+
    ```

    Oczywiście tabela będzie wyglądać inaczej, ponieważ zawiera Twoje elementy. Powinny jednak być widoczne tam, gdzie są przechowywane.

Jeśli przejdziesz do rozszerzenia Docker, zobaczysz, że masz uruchomione dwa kontenery aplikacji. Nie istnieje jednak rzeczywiste wskazanie, że są zgrupowane w jednej aplikacji. Zobaczysz, jak to zrobić lepiej!

![Rozszerzenie platformy Docker przedstawia dwa niezgrupowane kontenery aplikacji](media/vs-multi-container-app.png)

## <a name="recap"></a>Podsumowanie

W tym momencie masz aplikację, która przechowuje swoje dane w zewnętrznej bazie danych działającej w osobnym kontenerze. Zapoznaj się z małą ilością informacji o sieci kontenerów i zobacz, jak można wykonać odnajdywanie usługi przy użyciu systemu DNS.

Jednak istnieje dobry szansa, że zaczynasz nieco przeciążyć wszystko, czego potrzebujesz do uruchomienia tej aplikacji. Musisz utworzyć sieć, uruchomić kontenery, określić wszystkie zmienne środowiskowe, uwidocznić porty i inne. Jest to bardzo dużo do zapamiętania, co pozwala na trudniejsze przekazanie do kogoś innego.

W następnej sekcji porozmawiamy o Docker Compose. Dzięki Docker Compose można udostępniać stosy aplikacji w znacznie łatwiejszy sposób i umożliwić innym osobom ich zaniechanie za pomocą jednego (i prostego) polecenia.

## <a name="next-steps"></a>Następne kroki

Kontynuuj pracę z samouczkiem.

> [!div class="nextstepaction"]
> [Używanie Docker Compose](use-docker-compose.md)
