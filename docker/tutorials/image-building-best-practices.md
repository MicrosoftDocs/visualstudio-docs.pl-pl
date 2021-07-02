---
title: 'Samouczek platformy Docker — część 8: warstwowanie obrazów'
description: Jak badać warstwy obrazów w obrazach platformy Docker i zarządzać nimi.
ms.date: 08/04/2020
author: nebuk89
ms.author: ghogen
manager: jmartens
ms.topic: conceptual
ms.workload:
- azure
ms.openlocfilehash: 8f669baf6f3275f54c7e4a6ff2b31f9c260b2bb9
ms.sourcegitcommit: 8b75524dc544e34d09ef428c3ebbc9b09f14982d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/02/2021
ms.locfileid: "113222672"
---
# <a name="image-layering"></a>Warstwy obrazów

Czy wiesz, że możesz przyjrzeć się, co składa się na obraz? Za pomocą `docker image history` polecenia można wyświetlić polecenie, które zostało użyte do utworzenia każdej warstwy w obrazie.

1. Użyj polecenia `docker image history` , aby wyświetlić warstwy na `getting-started` obrazie utworzonym wcześniej w tym samouczku.

    ```bash
    docker image history getting-started
    ```

    Powinny pojawić się dane wyjściowe podobne do tych (daty/identyfikatory mogą się różnić).

    ```plaintext
    IMAGE               CREATED             CREATED BY                                      SIZE                COMMENT
    a78a40cbf866        18 seconds ago      /bin/sh -c #(nop)  CMD ["node" "/app/src/ind…   0B                  
    f1d1808565d6        19 seconds ago      /bin/sh -c yarn install --production            85.4MB              
    a2c054d14948        36 seconds ago      /bin/sh -c #(nop) COPY dir:5dc710ad87c789593…   198kB               
    9577ae713121        37 seconds ago      /bin/sh -c #(nop) WORKDIR /app                  0B                  
    b95baba1cfdb        13 days ago         /bin/sh -c #(nop)  CMD ["node"]                 0B                  
    <missing>           13 days ago         /bin/sh -c #(nop)  ENTRYPOINT ["docker-entry…   0B                  
    <missing>           13 days ago         /bin/sh -c #(nop) COPY file:238737301d473041…   116B                
    <missing>           13 days ago         /bin/sh -c apk add --no-cache --virtual .bui…   5.35MB              
    <missing>           13 days ago         /bin/sh -c #(nop)  ENV YARN_VERSION=1.21.1      0B                  
    <missing>           13 days ago         /bin/sh -c addgroup -g 1000 node     && addu…   74.3MB              
    <missing>           13 days ago         /bin/sh -c #(nop)  ENV NODE_VERSION=12.14.1     0B                  
    <missing>           13 days ago         /bin/sh -c #(nop)  CMD ["/bin/sh"]              0B                  
    <missing>           13 days ago         /bin/sh -c #(nop) ADD file:e69d441d729412d24…   5.59MB   
    ```

    Każda linia reprezentuje warstwę na obrazie. W tym miejscu jest wyświetlana podstawa u dołu z najnowszą warstwą u góry. Dzięki temu można szybko sprawdzić rozmiar każdej warstwy, co ułatwia diagnozowanie dużych obrazów.

1. Zauważysz, że kilka wierszy jest obciętych. Jeśli dodasz flagę , otrzymasz pełne dane wyjściowe (tak, użyjesz obciętej flagi, aby uzyskać `--no-trunc` nieuprawnione dane wyjściowe).

    ```bash
    docker image history --no-trunc getting-started
    ```

## <a name="layer-caching"></a>Buforowanie warstwy

Teraz, gdy już wiesz, jaka jest warstwa w akcji, musisz nauczyć się, jak zmniejszyć czas kompilacji obrazów kontenerów.

> Po zmianie warstwy należy również ponownie utworzyć wszystkie warstwy podrzędne

Przyjrzyjmy się plikowi Dockerfile, który był jeszcze raz...

```dockerfile
FROM node:12-alpine
WORKDIR /app
COPY . .
RUN yarn install --production
CMD ["node", "/app/src/index.js"]
```

Po powrocie do danych wyjściowych historii obrazu zobaczysz, że każde polecenie w pliku Dockerfile staje się nową warstwą obrazu. Być może pamiętasz, że podczas zmiany obrazu konieczne było ponowne zainstalowanie zależności yarn. Czy istnieje sposób na rozwiązanie tego problemu? Nie ma sensu, aby wysyłać te same zależności za każdym razem, gdy tworzysz, prawda?

Aby rozwiązać ten problem, możesz zmienić strukturę pliku Dockerfile, aby ułatwić obsługę buforowania zależności. W przypadku aplikacji opartych na węzłach te zależności są zdefiniowane w `package.json` pliku . Co więc zrobić, jeśli w pierwszej kolejności skopiowano tylko ten plik, zainstaluj zależności, a następnie *skopiuj* wszystko inne? Następnie zależności yarn są tworzone ponownie tylko w przypadku zmiany właściwości `package.json` . Sensu?

1. Zaktualizuj plik Dockerfile, aby skopiował plik w pierwszej kolejności, zainstaluj `package.json` zależności, a następnie skopiuj wszystkie inne pliki.

    ```dockerfile hl_lines="3 4 5"
    FROM node:12-alpine
    WORKDIR /app
    COPY package.json yarn.lock ./
    RUN yarn install --production
    COPY . .
    CMD ["node", "/app/src/index.js"]
    ```

1. Skompilowanie nowego obrazu przy użyciu funkcji `docker build` .

    ```bash
    docker build -t getting-started .
    ```

    Powinny zostać wyświetlony dane wyjściowe podobne do tych...

    ```plaintext
    Sending build context to Docker daemon  219.1kB
    Step 1/6 : FROM node:12-alpine
    ---> b0dc3a5e5e9e
    Step 2/6 : WORKDIR /app
    ---> Using cache
    ---> 9577ae713121
    Step 3/6 : COPY package* yarn.lock ./
    ---> bd5306f49fc8
    Step 4/6 : RUN yarn install --production
    ---> Running in d53a06c9e4c2
    yarn install v1.17.3
    [1/4] Resolving packages...
    [2/4] Fetching packages...
    info fsevents@1.2.9: The platform "linux" is incompatible with this module.
    info "fsevents@1.2.9" is an optional dependency and failed compatibility check. Excluding it from installation.
    [3/4] Linking dependencies...
    [4/4] Building fresh packages...
    Done in 10.89s.
    Removing intermediate container d53a06c9e4c2
    ---> 4e68fbc2d704
    Step 5/6 : COPY . .
    ---> a239a11f68d8
    Step 6/6 : CMD ["node", "/app/src/index.js"]
    ---> Running in 49999f68df8f
    Removing intermediate container 49999f68df8f
    ---> e709c03bc597
    Successfully built e709c03bc597
    Successfully tagged getting-started:latest
    ```

    Zobaczysz, że wszystkie warstwy zostały ponownie sbudować. Idealnie, ponieważ plik Dockerfile został dość zmieniony.

1. Teraz zmień plik (np. zmień nazwę na `src/static/index.html` `<title>` "The Awesome Todo App").

1. Skompilowanie obrazu platformy Docker teraz ponownie przy `docker build` użyciu narzędzia . Tym razem dane wyjściowe powinny wyglądać nieco inaczej.

    ```plaintext hl_lines="5 8 11"
    Sending build context to Docker daemon  219.1kB
    Step 1/6 : FROM node:12-alpine
    ---> b0dc3a5e5e9e
    Step 2/6 : WORKDIR /app
    ---> Using cache
    ---> 9577ae713121
    Step 3/6 : COPY package* yarn.lock ./
    ---> Using cache
    ---> bd5306f49fc8
    Step 4/6 : RUN yarn install --production
    ---> Using cache
    ---> 4e68fbc2d704
    Step 5/6 : COPY . .
    ---> cccde25a3d9a
    Step 6/6 : CMD ["node", "/app/src/index.js"]
    ---> Running in 2be75662c150
    Removing intermediate container 2be75662c150
    ---> 458e5c6f080c
    Successfully built 458e5c6f080c
    Successfully tagged getting-started:latest
    ```

    Po pierwsze należy zauważyć, że kompilacja była znacznie szybsza. Zobaczysz, że wszystkie kroki 1–4 `Using cache` mają . Więc hooray! Używasz pamięci podręcznej kompilacji. Wypychanie i ściąganie tego obrazu oraz aktualizacje do niego będą również znacznie szybsze. Brawo!

## <a name="multi-stage-builds"></a>Kompilacje wieloetapowe

Chociaż w tym samouczku nie będziemy zbyt wiele zagłębiać się w ten samouczek, kompilacje wieloetapowe są niezwykle wydajnym narzędziem, które pomaga utworzyć obraz przy użyciu wielu etapów. Istnieje kilka zalet tych opcji:

- Oddziel zależności czasu kompilacji od zależności środowiska uruchomieniowego
- Zmniejsz ogólny rozmiar obrazu, *wysyłając* tylko te informacje, których aplikacja potrzebuje do uruchomienia

### <a name="maventomcat-example"></a>Przykład maven/tomcat

Podczas kompilowania aplikacji opartych na języku Java potrzebny jest zestaw JDK do skompilowania kodu źródłowego do kodu bajtowego Java. Jednak ten JDK nie jest wymagany w środowisku produkcyjnym. Ponadto możesz używać narzędzi, takich jak Maven lub Gradle, aby ułatwić tworzenie aplikacji.
Nie są one również potrzebne na ostatnim obrazie. Pomocna jest kompilacja wieloetapowa.

```dockerfile
FROM maven AS build
WORKDIR /app
COPY . .
RUN mvn package

FROM tomcat
COPY --from=build /app/target/file.war /usr/local/tomcat/webapps 
```

W tym przykładzie użyto jednego etapu (o nazwie ), aby wykonać `build` rzeczywistą kompilację języka Java przy użyciu narzędzia Maven. Drugi etap (rozpoczynający się `FROM tomcat` od ) kopiuje pliki z `build` etapu. Ostatni obraz jest tylko ostatnim tworzonym etapem (który można przesłonić przy użyciu `--target` flagi ).

### <a name="react-example"></a>React przykład

Podczas kompilowania React potrzebujesz środowiska Node, aby skompilować kod JS (zazwyczaj JSX), arkusze stylów SASS i inne elementy do statycznego kodu HTML, JS i CSS. Jeśli nie korzystasz z renderowania po stronie serwera, nie potrzebujesz nawet środowiska Node na potrzeby kompilacji produkcyjnej. Dlaczego nie wysyłać zasobów statycznych w statycznym kontenerze nginx?

```dockerfile
FROM node:12 AS build
WORKDIR /app
COPY package* yarn.lock ./
RUN yarn install
COPY public ./public
COPY src ./src
RUN yarn run build

FROM nginx:alpine
COPY --from=build /app/build /usr/share/nginx/html
```

W tym miejscu używasz obrazu do wykonania kompilacji (maksymalizowania buforowania warstwy), a następnie skopiowania danych wyjściowych `node:12` do kontenera nginx. Chłodno, prawda?

## <a name="recap"></a>Podsumowanie

Po zrozumieniu nieco struktury obrazów można szybciej tworzyć obrazy i wprowadzać mniejszą liczbę zmian. Kompilacje wieloetapowe pomagają również zmniejszyć ogólny rozmiar obrazu i zwiększyć ostateczne zabezpieczenia kontenera przez oddzielenie zależności czasu kompilacji od zależności środowiska uruchomieniowego.

## <a name="next-steps"></a>Następne kroki

Kontynuuj pracę z samouczkiem!

> [!div class="nextstepaction"]
> [Wdrażanie w chmurze](deploy-to-cloud.md)