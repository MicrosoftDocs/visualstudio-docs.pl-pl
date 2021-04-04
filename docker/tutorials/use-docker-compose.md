---
title: 'Samouczek platformy Docker — część 7: korzystanie z Docker Compose'
description: Opisuje sposób instalowania i używania Docker Compose.
ms.date: 08/04/2020
author: nebuk89
ms.author: ghogen
manager: jmartens
ms.technology: vs-azure
ms.topic: conceptual
ms.workload:
- azure
ms.openlocfilehash: 3bcf3a69dcf8053851e3d8519a25f61fe23ae7e3
ms.sourcegitcommit: 155d5f0fd54ac1d20df2f5b0245365924faa3565
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/31/2021
ms.locfileid: "106082568"
---
# <a name="use-docker-compose"></a>Korzystanie z narzędzia Docker Compose

[Docker Compose](https://docs.docker.com/compose/) to narzędzie, które zostało opracowane w celu ułatwienia definiowania i udostępniania aplikacji wielokontenerowych. Dzięki redagowaniu można utworzyć plik YAML w celu zdefiniowania usług i za pomocą jednego polecenia, co może spowodować, że wszystko jest w całości lub w dół.

*Dużą* zaletą korzystania z redagowania jest możliwość definiowania stosu aplikacji w pliku, utrzymywania go w katalogu głównym repozytorium projektu (jest teraz kontrolowana wersja) i umożliwianie innym osobom współtworzenia projektu. Ktoś będzie musiał tylko sklonować repozytorium i rozpocząć tworzenie aplikacji. W rzeczywistości w przypadku usługi GitHub/GitLab może być widoczne bardzo kilka projektów.

Jak zacząć?

## <a name="install-docker-compose"></a>Zainstaluj Docker Compose

Jeśli zainstalowano program Docker Desktop dla systemu Windows lub Mac, masz już Docker Compose! Wystąpienia play-with-Docker mają już zainstalowane Docker Compose. Jeśli korzystasz z komputera z systemem Linux, musisz zainstalować Docker Compose przy użyciu [instrukcji znajdujących się tutaj](https://docs.docker.com/compose/install/).

Po zakończeniu instalacji należy uruchomić następujące polecenie i wyświetlić informacje o wersji.

```bash
docker-compose version
```

## <a name="create-the-compose-file"></a>Utwórz plik redagowania

1. W katalogu głównym projektu aplikacji Utwórz plik o nazwie `docker-compose.yml` .

1. W pliku redagowania rozpocznie się od zdefiniowania wersji schematu. W większości przypadków najlepiej używać najnowszej obsługiwanej wersji. Możesz zapoznać się z informacjami dotyczącymi [redagowania pliku](https://docs.docker.com/compose/compose-file/) dla bieżących wersji schematu i macierzy zgodności.

    ```yaml
    version: "3.7"
    ```

1. Następnie zdefiniuj listę usług (lub kontenerów), które mają być uruchamiane jako część aplikacji.

    ```yaml hl_lines="3"
    version: "3.7"

    services:
    ```

Teraz można rozpocząć Migrowanie usługi w danym momencie do pliku redagowania.

## <a name="define-the-app-service"></a>Zdefiniuj App Service

Należy pamiętać, że było to polecenie użyte do zdefiniowania kontenera aplikacji (Zastąp ` \ ` znaki `` ` `` w programie Windows PowerShell).

```bash
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

1. Najpierw Zdefiniuj wpis usługi i obraz dla kontenera. Możesz wybrać dowolną nazwę dla usługi. Nazwa automatycznie stanie się aliasem sieciowym, co będzie przydatne podczas definiowania usługi MySQL.

    ```yaml hl_lines="4 5"
    version: "3.7"

    services:
      app:
        image: node:12-alpine
    ```

1. Zazwyczaj zobaczysz polecenie blisko `image` definicji, chociaż nie ma wymagań dotyczących porządkowania. Przejdź dalej i przenieś go do pliku.

    ```yaml hl_lines="6"
    version: "3.7"

    services:
      app:
        image: node:12-alpine
        command: sh -c "yarn install && yarn run dev"
    ```

1. Przeprowadź migrację `-p 3000:3000` części polecenia przez zdefiniowanie `ports` dla usługi. W tym miejscu będziesz używać [krótkiej składni](https://docs.docker.com/compose/compose-file/#short-syntax-1) , ale dostępna jest również bardziej pełna [składnia](https://docs.docker.com/compose/compose-file/#long-syntax-1) .

    ```yaml hl_lines="7 8"
    version: "3.7"

    services:
      app:
        image: node:12-alpine
        command: sh -c "yarn install && yarn run dev"
        ports:
          - 3000:3000
    ```

1. Następnie Przeprowadź migrację katalogu roboczego ( `-w /app` ) i mapowania woluminu ( `-v ${PWD}:/app` ) przy użyciu `working_dir` `volumes` definicji i. Woluminy mają również [krótką](https://docs.docker.com/compose/compose-file/#short-syntax-3) i [długą](https://docs.docker.com/compose/compose-file/#long-syntax-3) składnię.

   Jedną z zalet Docker Compose definicji woluminów jest użycie ścieżek względnych z bieżącego katalogu.

    ```yaml hl_lines="9 10 11"
    version: "3.7"

    services:
      app:
        image: node:12-alpine
        command: sh -c "yarn install && yarn run dev"
        ports:
          - 3000:3000
        working_dir: /app
        volumes:
          - ./:/app
    ```

1. Na koniec Migruj definicje zmiennych środowiskowych przy użyciu `environment` klucza.

    ```yaml hl_lines="12 13 14 15 16"
    version: "3.7"

    services:
      app:
        image: node:12-alpine
        command: sh -c "yarn install && yarn run dev"
        ports:
          - 3000:3000
        working_dir: /app
        volumes:
          - ./:/app
        environment:
          MYSQL_HOST: mysql
          MYSQL_USER: root
          MYSQL_PASSWORD: secret
          MYSQL_DB: todos
    ```

### <a name="define-the-mysql-service"></a>Definiowanie usługi MySQL

Teraz czas na zdefiniowanie usługi MySQL. Polecenie użyte dla tego kontenera było następujące (Zastąp ` \ ` znaki `` ` `` w programie Windows PowerShell):

```bash
docker run -d \
  --network todo-app --network-alias mysql \
  -v todo-mysql-data:/var/lib/mysql \
  -e MYSQL_ROOT_PASSWORD=secret \
  -e MYSQL_DATABASE=todos \
  mysql:5.7
```

1. Najpierw Zdefiniuj nową usługę i nadaj jej nazwę, `mysql` Aby automatycznie pobierali alias sieciowy. Określ również obraz, który ma być używany.

    ```yaml hl_lines="6 7"
    version: "3.7"

    services:
      app:
        # The app service definition
      mysql:
        image: mysql:5.7
    ```

1. Następnie zdefiniuj mapowanie woluminu. Po uruchomieniu kontenera przy użyciu `docker run` programu nazwany wolumin został utworzony automatycznie. Jednak nie dzieje się tak w przypadku tworzenia. Należy zdefiniować wolumin w sekcji najwyższego poziomu `volumes:` , a następnie określić mountpoint w konfiguracji usługi. Po prostu dostarczając tylko nazwę woluminu, są używane domyślne opcje. Istnieje [wiele dostępnych opcji](https://github.com/compose-spec/compose-spec/blob/master/spec.md#volumes-top-level-element) .

    ```yaml hl_lines="8 9 10 11 12"
    version: "3.7"

    services:
      app:
        # The app service definition
      mysql:
        image: mysql:5.7
        volumes:
          - todo-mysql-data:/var/lib/mysql
    
    volumes:
      todo-mysql-data:
    ```

1. Na koniec wystarczy określić zmienne środowiskowe.

    ```yaml hl_lines="10 11 12"
    version: "3.7"

    services:
      app:
        # The app service definition
      mysql:
        image: mysql:5.7
        volumes:
          - todo-mysql-data:/var/lib/mysql
        environment: 
          MYSQL_ROOT_PASSWORD: secret
          MYSQL_DATABASE: todos
    
    volumes:
      todo-mysql-data:
    ```

W tym momencie pełna `docker-compose.yml` powinna wyglądać następująco:

```yaml
version: "3.7"

services:
  app:
    image: node:12-alpine
    command: sh -c "yarn install && yarn run dev"
    ports:
      - 3000:3000
    working_dir: /app
    volumes:
      - ./:/app
    environment:
      MYSQL_HOST: mysql
      MYSQL_USER: root
      MYSQL_PASSWORD: secret
      MYSQL_DB: todos

  mysql:
    image: mysql:5.7
    volumes:
      - todo-mysql-data:/var/lib/mysql
    environment: 
      MYSQL_ROOT_PASSWORD: secret
      MYSQL_DATABASE: todos

volumes:
  todo-mysql-data:
```

## <a name="run-the-application-stack"></a>Uruchamianie stosu aplikacji

Teraz, gdy masz `docker-compose.yml` plik, możesz go uruchomić.

1. Najpierw upewnij się, że żadne inne kopie aplikacji i bazy danych nie działają ( `docker ps` i `docker rm -f <ids>` ).

1. Uruchom stos aplikacji przy użyciu `docker-compose up` polecenia. Dodaj `-d` flagę, aby uruchomić wszystko w tle. Alternatywnie możesz kliknąć prawym przyciskiem myszy plik redagowania i wybrać opcję **redagowanie** dla vs Code pasku bocznym. 

    ```bash
    docker-compose up -d
    ```

    Po uruchomieniu tego polecenia powinny zostać wyświetlone dane wyjściowe podobne do tego:

    ```plaintext
    Creating network "app_default" with the default driver
    Creating volume "app_todo-mysql-data" with default driver
    Creating app_app_1   ... done
    Creating app_mysql_1 ... done
    ```

    Zobaczysz, że wolumin został utworzony, a także w sieci. Domyślnie Docker Compose automatycznie tworzy sieć specyficzną dla stosu aplikacji (co oznacza, że nie został on zdefiniowany w pliku redagowania).

1. Zapoznaj się z dziennikami przy użyciu `docker-compose logs -f` polecenia. Zostaną wyświetlone dzienniki z każdej z usług przeplatanych w jeden strumień. Jest to niezwykle przydatne, gdy chcesz obejrzeć problemy związane z chronometrażem. `-f`Flaga "dalej" spowoduje wyświetlenie danych wyjściowych na żywo w miarę ich generowania.

    Jeśli jeszcze tego nie zrobiono, zobaczysz dane wyjściowe, które wyglądają następująco:

    ```plaintext
    mysql_1  | 2019-10-03T03:07:16.083639Z 0 [Note] mysqld: ready for connections.
    mysql_1  | Version: '5.7.27'  socket: '/var/run/mysqld/mysqld.sock'  port: 3306  MySQL Community Server (GPL)
    app_1    | Connected to mysql db at host mysql
    app_1    | Listening on port 3000
    ```

    Nazwa usługi jest wyświetlana na początku wiersza (często kolorowo), aby ułatwić odróżnienie komunikatów. Jeśli chcesz wyświetlić dzienniki dla określonej usługi, możesz dodać nazwę usługi na końcu polecenia Logs (na przykład `docker-compose logs -f app` ).

    > [!TIP]
    > **Oczekiwanie na bazę danych przed uruchomieniem aplikacji** Gdy aplikacja jest uruchamiana, w rzeczywistości znajduje się i czeka, aż baza danych MySQL zostanie uruchomiona przed podjęciem próby nawiązania połączenia z usługą it.DocKer nie ma wbudowanej obsługi przed zaczekaniem, aż inny kontener zostanie w pełni uruchomiony i będzie gotowy do uruchomienia innego kontenera. W przypadku projektów opartych na węzłach można użyć zależności [oczekiwania-portu](https://github.com/dwmkerr/wait-port) . Podobne projekty istnieją dla innych języków/platform.

1. W tym momencie powinno być możliwe otwarcie aplikacji i jej uruchomienie. I Hej! Nie jesteś w pojedynczym poleceniu.

## <a name="see-the-app-stack-in-the-docker-extension"></a>Zobacz stos aplikacji w rozszerzeniu platformy Docker

Jeśli szukasz rozszerzenia Docker, możesz zmienić opcje grupowania przy użyciu "koło zębate" i "Group by". W tym przypadku chcesz zobaczyć kontenery pogrupowane według nazwy redagowania projektu:

![Rozszerzenie programu VS z funkcją redagowania](media/vs-app-project-collapsed.png)

Po odwiedzeniu sieci zobaczysz dwa kontenery zdefiniowane w pliku redagowania.

![Rozszerzenie VS z rozwiniętym elementem redagowania](media/vs-app-project-expanded.png)

## <a name="tear-it-all-down"></a>Odrywa wszystko

Gdy wszystko jest gotowe do odrywania, po prostu uruchom `docker-compose down` lub kliknij prawym przyciskiem myszy aplikację na liście kontenery w rozszerzeniu docker vs Code i wybierz pozycję **Utwórz**. Kontenery zostaną zatrzymane, a sieć zostanie usunięta.

> [!WARNING]
> **Usuwanie woluminów** Domyślnie nazwane woluminy w pliku redagowania nie są usuwane podczas uruchamiania `docker-compose down` . Jeśli chcesz usunąć woluminy, musisz dodać `--volumes` flagę.

Po usunięciu można przełączyć się do innego projektu, uruchomić `docker-compose up` i przygotować się do współtworzenia tego projektu. Naprawdę nie jest to jeszcze prostsze.

## <a name="recap"></a>Podsumowanie

Ta sekcja zawiera informacje na temat Docker Compose i sposobu, w jaki znacznie upraszcza definiowanie i udostępnianie aplikacji wielousługowych. Utworzono plik redagowania poprzez przetłumaczenie poleceń, które były używane w odpowiednim formacie redagowania.

W tym momencie zaczynasz zawijać samouczek. Istnieje jednak kilka najlepszych rozwiązań dotyczących kompilowania obrazów, ponieważ występuje duży problem z pliku dockerfileem, z którego korzystasz. Teraz przyjrzyjmy się!

## <a name="next-steps"></a>Następne kroki

Kontynuuj pracę z samouczkiem.

> [!div class="nextstepaction"]
> [Najlepsze rozwiązania dotyczące tworzenia obrazów](image-building-best-practices.md)
