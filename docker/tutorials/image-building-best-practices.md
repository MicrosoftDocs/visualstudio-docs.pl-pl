---
title: 'Samouczek platformy Docker — część 8: Tworzenie warstw obrazów'
description: Jak przejrzeć warstwy obrazu w obrazach platformy Docker i zarządzać nimi.
ms.date: 08/04/2020
author: nebuk89
ms.author: ghogen
manager: jillfra
ms.technology: vs-azure
ms.topic: conceptual
ms.workload:
- azure
ms.openlocfilehash: eae21a729f30a0c77fa52e5774a2f5157286dab1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "89178317"
---
# <a name="image-layering"></a>Tworzenie warstw obrazów

Czy wiesz, że możesz dowiedzieć się, jak to zrobić? Za pomocą `docker image history` polecenia można zobaczyć polecenie, które zostało użyte do utworzenia każdej warstwy w obrazie.

1. Użyj `docker image history` polecenia, aby wyświetlić warstwy `getting-started` obrazu utworzonego wcześniej w samouczku.

    ```bash
    docker image history getting-started
    ```

    Dane wyjściowe powinny wyglądać mniej więcej tak, jak to się dzieje (daty/identyfikatory mogą się różnić).

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

    Każda linia reprezentuje warstwę w obrazie. W tym miejscu wyświetlana jest podstawa u dołu z najnowszą warstwą u góry. Korzystając z tej opcji, można również szybko zobaczyć rozmiar każdej warstwy, pomagając zdiagnozować duże obrazy.

1. Zauważ, że kilka wierszy zostanie obcięty. Jeśli dodasz `--no-trunc` flagę, uzyskasz pełne dane wyjściowe (tak, aby uzyskać niecięte dane wyjściowe, Użyj flagi obciętego).

    ```bash
    docker image history --no-trunc getting-started
    ```

## <a name="layer-caching"></a>Buforowanie warstwy

Teraz, po zapoznaniu się z działaniem warstwowym, istnieje ważna lekcja umożliwiająca skrócenie czasu kompilowania obrazów kontenerów.

> Po zmianie warstwy wszystkie warstwy podrzędne muszą zostać ponownie utworzone.

Przyjrzyjmy się pliku dockerfileom, z których korzystasz jeszcze raz...

```dockerfile
FROM node:12-alpine
WORKDIR /app
COPY . .
RUN yarn install --production
CMD ["node", "/app/src/index.js"]
```

Powracając do danych wyjściowych historii obrazu, zobaczysz, że każde polecenie w pliku dockerfile będzie nową warstwą w obrazie. Warto pamiętać, że po wprowadzeniu zmiany w obrazie zależności przędzy musiały zostać ponownie zainstalowane. Czy istnieje sposób, aby rozwiązać ten problem? Nie ma sensu, aby zapewnić, że każdy z tych samych zależności jest dostarczany przy każdym kompilowaniu?

Aby rozwiązać ten problem, można zmienić strukturę pliku dockerfile, aby pomóc w buforowaniu zależności. W przypadku aplikacji opartych na węźle te zależności są zdefiniowane w `package.json` pliku. Co zrobić, jeśli skopiowano tylko ten plik w pierwszej kolejności, Zainstaluj zależności, a *następnie* Skopiuj wszystkie inne? Następnie można ponownie utworzyć zależności przędzy tylko w przypadku zmiany `package.json` . Czy warto mieć sens?

1. Zaktualizuj pliku dockerfile do kopiowania w `package.json` pierwszej kolejności, Zainstaluj zależności, a następnie skopiuj wszystko inne w.

    ```dockerfile hl_lines="3 4 5"
    FROM node:12-alpine
    WORKDIR /app
    COPY package.json yarn.lock ./
    RUN yarn install --production
    COPY . .
    CMD ["node", "/app/src/index.js"]
    ```

1. Utwórz nowy obraz przy użyciu polecenia `docker build` .

    ```bash
    docker build -t getting-started .
    ```

    Powinny pojawić się dane wyjściowe podobne do tego...

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

    Zobaczysz, że wszystkie warstwy zostały odbudowane. Doskonale prawidłowo, ponieważ pliku dockerfile całkiem jakiś bit.

1. Teraz wprowadź zmiany w `src/static/index.html` pliku (na przykład zmień, `<title>` aby powiedzieć, że aplikacja awesome do zrobienia).

1. Utwórz teraz obraz platformy Docker `docker build` . Tym razem dane wyjściowe powinny wyglądać nieco inaczej.

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

    Najpierw należy zauważyć, że kompilacja była znacznie szybsza! Zobaczysz, że wszystkie kroki 1-4 wszystkie mają `Using cache` . Więc hura! Korzystasz z pamięci podręcznej kompilacji. Wypychanie i ściąganie tego obrazu oraz jego aktualizacje będą znacznie szybsze. Hura!

## <a name="multi-stage-builds"></a>Kompilacje wieloetapowe

Mimo że nie szczegółowe się do niego za dużo w tym samouczku, kompilacje wieloetapowe są niezwykle zaawansowanym narzędziem ułatwiającym Tworzenie obrazu przy użyciu wielu etapów. Istnieje kilka korzyści dla nich:

- Oddzielanie zależności czasu kompilacji od zależności środowiska uruchomieniowego
- Zmniejszenie ogólnego rozmiaru obrazu przez wysyłkę *tylko* tego, co aplikacja musi uruchamiać

### <a name="maventomcat-example"></a>Przykład Maven/Tomcat

Podczas kompilowania aplikacji opartych na języku Java JDK jest wymagany do kompilowania kodu źródłowego na kod bajtowy Java. Jednak ten JDK nie jest wymagany w środowisku produkcyjnym. Ponadto możesz używać narzędzi takich jak Maven lub Gradle, aby pomóc w tworzeniu aplikacji.
Nie są one również potrzebne w końcowym obrazie. Wieloetapowe kompilacje — pomoc.

```dockerfile
FROM maven AS build
WORKDIR /app
COPY . .
RUN mvn package

FROM tomcat
COPY --from=build /app/target/file.war /usr/local/tomcat/webapps 
```

W tym przykładzie użyto jednego etapu (o nazwie `build` ) do wykonania rzeczywistej kompilacji w języku Java przy użyciu Maven. Drugi etap (począwszy od `FROM tomcat` ) kopiuje pliki z `build` etapu. Końcowy obraz jest tylko ostatnim tworzonym etapem, który można zastąpić przy użyciu `--target` flagi.

### <a name="react-example"></a>Przykład reakcji

Podczas kompilowania aplikacji do reagowania potrzebne jest środowisko węzła do kompilowania kodu JS (zazwyczaj JSX), arkuszy stylów SASS i innych do statycznych języków HTML, JS i CSS. Jeśli nie wykonujesz renderowania po stronie serwera, nie potrzebujesz jeszcze środowiska węzła dla kompilacji produkcyjnej. Dlaczego nie należy dostarczać zasobów statycznych w statycznym kontenerze Nginx?

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

W tym miejscu jest używany `node:12` obraz do wykonania kompilacji (maksymalizowanie pamięci podręcznej), a następnie skopiowanie danych wyjściowych do kontenera Nginx. Chłodna, tak?

## <a name="recap"></a>Podsumowanie

Dzięki zrozumieniu nieco informacji o strukturze obrazów można szybciej tworzyć obrazy i dostarczać mniejszą liczbę zmian. Kompilacje wieloetapowe pomagają również zmniejszyć ogólny rozmiar obrazu i zwiększyć zabezpieczenia kontenera końcowego, oddzielając zależności czasu kompilacji od zależności środowiska uruchomieniowego.

## <a name="next-steps"></a>Następne kroki

Kontynuuj pracę z samouczkiem.

> [!div class="nextstepaction"]
> [Wdrażanie w chmurze](deploy-to-cloud.md)