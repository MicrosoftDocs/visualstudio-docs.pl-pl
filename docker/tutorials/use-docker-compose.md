---
title: 'Samouczek platformy Docker — część 7: korzystanie z Docker Compose'
description: Opisuje sposób instalowania i używania Docker Compose.
ms.date: 08/04/2020
author: nebuk89
ms.author: ghogen
manager: jmartens
ms.topic: conceptual
ms.workload:
- azure
ms.openlocfilehash: 645d168aefe05040193d564d5c158acfb6688c11
ms.sourcegitcommit: 8b75524dc544e34d09ef428c3ebbc9b09f14982d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/02/2021
ms.locfileid: "113222750"
---
# <a name="use-docker-compose"></a>Korzystanie z narzędzia Docker Compose

[Docker Compose](https://docs.docker.com/compose/) to narzędzie, które zostało opracowane w celu definiowania i udostępniania aplikacji wielo kontenerów. Za pomocą programu Compose można utworzyć plik YAML w celu zdefiniowania usług, a za pomocą jednego polecenia można wszystko roztworzyć lub zerwać.

Główną *zaletą* korzystania z narzędzia Compose jest możliwość zdefiniowania stosu aplikacji w pliku, utrzymania go w katalogu głównym w projekcie (jest to teraz kontrolowana wersja) i łatwego umożliwienia innej osobie współtworzenia projektu. Ktoś musiałby sklonować Twoje repo i uruchomić aplikację do redagowania. W rzeczywistości można zobaczyć sporo projektów na platformie GitHub/GitLab robi to dokładnie teraz.

Jak więc rozpocząć pracę?

## <a name="install-docker-compose"></a>Instalowanie Docker Compose

Jeśli zainstalowano program Docker Desktop dla komputerów Windows lub Mac, masz już Docker Compose! Wystąpienia platformy Docker zostały już Docker Compose zainstalowane. Jeśli korzystasz z komputera z systemem Linux, musisz zainstalować program Docker Compose [zgodnie z instrukcjami podanymi tutaj.](https://docs.docker.com/compose/install/)

Po zakończeniu instalacji powinno być możliwe uruchomienie poniższego pliku i wyświetlanie informacji o wersji.

```bash
docker-compose version
```

## <a name="create-the-compose-file"></a>Tworzenie pliku redagowania

1. W katalogu głównym projektu aplikacji utwórz plik o nazwie `docker-compose.yml` .

1. W pliku compose zaczniemy od zdefiniowania wersji schematu. W większości przypadków najlepiej użyć najnowszej obsługiwanej wersji. Możesz przyjrzeć się [odwołaniem do pliku Compose](https://docs.docker.com/compose/compose-file/) dla bieżących wersji schematu i macierzy zgodności.

    ```yaml
    version: "3.7"
    ```

1. Następnie zdefiniuj listę usług (lub kontenerów), które mają być uruchamiane w ramach aplikacji.

    ```yaml hl_lines="3"
    version: "3.7"

    services:
    ```

Teraz zaczniesz migrować usługę jednocześnie do pliku compose.

## <a name="define-the-app-service"></a>Definiowanie App Service

Pamiętaj, że to polecenie zostało użyte do zdefiniowania kontenera aplikacji (zastąp znaki znakiem ` \ ` `` ` `` w Windows PowerShell).

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

1. Najpierw zdefiniuj wpis usługi i obraz dla kontenera. Możesz wybrać dowolną nazwę usługi. Nazwa automatycznie stanie się aliasem sieciowym, co będzie przydatne podczas definiowania usługi MySQL.

    ```yaml hl_lines="4 5"
    version: "3.7"

    services:
      app:
        image: node:12-alpine
    ```

1. Zazwyczaj polecenie jest w pobliżu definicji, chociaż nie jest wymagane `image` zamawianie. Przejdź dalej i przenieś go do pliku .

    ```yaml hl_lines="6"
    version: "3.7"

    services:
      app:
        image: node:12-alpine
        command: sh -c "yarn install && yarn run dev"
    ```

1. `-p 3000:3000`Zmigruj część polecenia, definiując `ports` element dla usługi. W tym miejscu [użyjesz krótkiej](https://docs.docker.com/compose/compose-file/#short-syntax-1) składni, ale dostępna jest również bardziej szczegółowa [długa](https://docs.docker.com/compose/compose-file/#long-syntax-1) składnia.

    ```yaml hl_lines="7 8"
    version: "3.7"

    services:
      app:
        image: node:12-alpine
        command: sh -c "yarn install && yarn run dev"
        ports:
          - 3000:3000
    ```

1. Następnie zmigruj katalog roboczy ( `-w /app` ) i mapowanie woluminów ( `-v ${PWD}:/app` ) przy użyciu definicji i `working_dir` `volumes` . Woluminy mają również [krótką](https://docs.docker.com/compose/compose-file/#short-syntax-3) [i długą składnię.](https://docs.docker.com/compose/compose-file/#long-syntax-3)

   Jedną z zalet Docker Compose woluminów jest użycie ścieżek względnych z bieżącego katalogu.

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

1. Na koniec przemigruj definicje zmiennych środowiskowych przy użyciu `environment` klucza .

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

Teraz należy zdefiniować usługę MySQL. Polecenie użyte dla tego kontenera było następujące (zastąp znaki znakiem ` \ ` `` ` `` w Windows PowerShell):

```bash
docker run -d \
  --network todo-app --network-alias mysql \
  -v todo-mysql-data:/var/lib/mysql \
  -e MYSQL_ROOT_PASSWORD=secret \
  -e MYSQL_DATABASE=todos \
  mysql:5.7
```

1. Najpierw zdefiniuj nową usługę i nadaj jej `mysql` nazwę, aby automatycznie pobierała alias sieciowy. Określ również obraz do użycia.

    ```yaml hl_lines="6 7"
    version: "3.7"

    services:
      app:
        # The app service definition
      mysql:
        image: mysql:5.7
    ```

1. Następnie zdefiniuj mapowanie woluminu. Podczas korzystania z kontenera z `docker run` programem nazwany wolumin został utworzony automatycznie. Jednak nie dzieje się tak w przypadku uruchamiania z programem Compose. Należy zdefiniować wolumin w sekcji najwyższego poziomu, a następnie `volumes:` określić punkt instalacji w konfiguracji usługi. Po prostu podając tylko nazwę woluminu, są używane opcje domyślne. Dostępnych [jest jednak o wiele więcej](https://github.com/compose-spec/compose-spec/blob/master/spec.md#volumes-top-level-element) opcji.

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

1. Na koniec wystarczy określić tylko zmienne środowiskowe.

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

W tym momencie ukończenie `docker-compose.yml` powinno wyglądać tak:

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

1. Najpierw upewnij się, że nie są uruchomione żadne inne kopie aplikacji i bazy danych ( `docker ps` i `docker rm -f <ids>` ).

1. Uruchom stos aplikacji przy użyciu `docker-compose up` polecenia . Dodaj `-d` flagę , aby uruchomić wszystko w tle. Alternatywnie możesz kliknąć prawym przyciskiem myszy plik Compose i wybrać opcję Utwórz **dla** VS Code bocznym. 

    ```bash
    docker-compose up -d
    ```

    Po uruchomieniu tego uruchomienia powinny zostać wyświetlony dane wyjściowe podobne do tych:

    ```plaintext
    Creating network "app_default" with the default driver
    Creating volume "app_todo-mysql-data" with default driver
    Creating app_app_1   ... done
    Creating app_mysql_1 ... done
    ```

    Zauważysz, że wolumin został utworzony, a także sieć! Domyślnie program Docker Compose automatycznie tworzy sieć specjalnie dla stosu aplikacji (dlatego nie zdefiniowano jej w pliku compose).

1. Przyjrzyj się dziennikom za pomocą `docker-compose logs -f` polecenia . Zobaczysz dzienniki z każdej z usług przeplatane w jeden strumień. Jest to niezwykle przydatne, gdy chcesz obserwować problemy związane z czasem. Flaga "następuje" w dzienniku, więc dane wyjściowe na `-f` żywo będą generowane.

    Jeśli jeszcze tego nie zrobisz, zobaczysz dane wyjściowe, które wyglądają następująco:

    ```plaintext
    mysql_1  | 2019-10-03T03:07:16.083639Z 0 [Note] mysqld: ready for connections.
    mysql_1  | Version: '5.7.27'  socket: '/var/run/mysqld/mysqld.sock'  port: 3306  MySQL Community Server (GPL)
    app_1    | Connected to mysql db at host mysql
    app_1    | Listening on port 3000
    ```

    Nazwa usługi jest wyświetlana na początku wiersza (często ma kolor), aby ułatwić odróżnienie komunikatów. Jeśli chcesz wyświetlić dzienniki dla określonej usługi, możesz dodać nazwę usługi na końcu polecenia logs (na przykład `docker-compose logs -f app` ).

    > [!TIP]
    > **Oczekiwanie na bazy danych przed uruchomieniem aplikacji** Gdy aplikacja jest uruchamiana, w rzeczywistości znajduje się i czeka, aż program MySQL będzie działać i będzie gotowy, zanim spróbuje nawiązać połączenie z kontenerem it.Docker nie ma wbudowanej obsługi oczekiwania na pełne uruchomienie i gotowość innego kontenera przed uruchomieniem innego kontenera. W przypadku projektów opartych na węzłach można użyć zależności [portu](https://github.com/dwmkerr/wait-port) oczekiwania. Podobne projekty istnieją dla innych języków/platform.

1. W tym momencie powinno być możliwe otwarcie aplikacji i jej uruchomienie. I hey! Możesz teraz chcieć za pomocą jednego polecenia.

## <a name="see-the-app-stack-in-the-docker-extension"></a>Wyświetlanie stosu aplikacji w rozszerzeniu platformy Docker

Jeśli przyjrzysz się rozszerzeniu platformy Docker, możesz zmienić opcje grupowania przy użyciu opcji "cog" i "grupuj według". W tym wystąpieniu chcesz wyświetlić kontenery pogrupowane według nazwy Project Compose:

![Rozszerzenie programu VS z rozszerzeniem Compose](media/vs-app-project-collapsed.png)

Jeśli nie działa sieć, zobaczysz dwa kontenery zdefiniowane w pliku compose.

![Rozszerzenie programu VS z rozwiniętym rozszerzeniem Compose](media/vs-app-project-expanded.png)

## <a name="tear-it-all-down"></a>Odrywanie wszystkiego

Gdy wszystko będzie gotowe, po prostu uruchom polecenie lub kliknij prawym przyciskiem myszy aplikację na liście kontenerów w rozszerzeniu VS Code Docker i wybierz polecenie Utwórz `docker-compose down` **w dół.** Kontenery zostaną zatrzymane, a sieć zostanie usunięta.

> [!WARNING]
> **Usuwanie woluminów** Domyślnie nazwane woluminy w pliku compose NIE są usuwane podczas uruchamiania programu `docker-compose down` . Jeśli chcesz usunąć woluminy, musisz dodać `--volumes` flagę .

Po rozsyłania możesz przełączyć się do innego projektu, uruchomić go i być gotowym `docker-compose up` do współtwomentu tego projektu. Tak naprawdę nie jest to o wiele prostsze!

## <a name="recap"></a>Podsumowanie

W tej sekcji opisano Docker Compose i sposób, w jaki pomaga znacznie uprościć definiowanie i udostępnianie aplikacji wielo usług. Plik Compose został utworzony przez przetłumaczenie używanych poleceń na odpowiedni format narzędzia Compose.

W tym momencie zaczynasz podsyłać samouczek. Istnieje jednak kilka najlepszych rozwiązań dotyczących budowania obrazów, które należy omiczyć, ponieważ istnieje duży problem z plikiem Dockerfile, który był już w użyciu. Przyjrzyjmy się temu!

## <a name="next-steps"></a>Następne kroki

Kontynuuj pracę z samouczkiem!

> [!div class="nextstepaction"]
> [Najlepsze rozwiązania dotyczące tworzenia obrazów](image-building-best-practices.md)
