---
title: 'Samouczek platformy Docker — część 1: kompilowanie i uruchamianie przykładowej aplikacji z listą zadań do uruchomienia'
description: Omówienie przykładowej aplikacji z listą zadań do Node.js.
ms.date: 08/04/2020
author: nebuk89
ms.author: ghogen
manager: jmartens
ms.topic: conceptual
ms.workload:
- azure
ms.openlocfilehash: 9229c3717b686a3f08ef49e7912ac0515864d793
ms.sourcegitcommit: 8b75524dc544e34d09ef428c3ebbc9b09f14982d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/02/2021
ms.locfileid: "113222815"
---
# <a name="build-and-run-the-todo-sample-app"></a>Kompilowanie i uruchamianie przykładowej aplikacji z todo

W pozostałej części tego samouczka będziesz pracować z prostym menedżerem listy zadań do Node.js. Jeśli nie znasz jeszcze Node.js, nie martw się. Nie jest potrzebne żadne rzeczywiste środowisko języka JavaScript!

W tym momencie twój zespół programistów jest dość mały i po prostu budowania aplikacji, aby udowodnić swoją minimalną konieczną konieczną konieczną konieczną jakość. Chcesz pokazać, jak to działa i co jest w stanie zrobić bez konieczności myślenia o tym, jak będzie działać dla dużego zespołu, wielu deweloperów i tak dalej.

![Zrzut ekranu menedżera listy zadań do zrzucie ekranu](media/todo-list-sample.png)

## <a name="get-the-app"></a>Pobierz aplikację

Przed uruchomieniem aplikacji należy pobrać kod źródłowy aplikacji na swoją maszynę. W przypadku rzeczywistych projektów zwykle klonowane jest repo. Jednak w tym samouczku utworzono plik ZIP zawierający aplikację.

1. Upewnij się, że na komputerze lokalnym zainstalowano platformę Docker for Windows lub Docker Community Edition. Zobacz [dokumentację dotyczącą instalacji Windows Docker.](https://docs.docker.com/docker-for-windows/install/) Proces instalacji udostępnia plik ZIP zawierający przykład pod adresem localhost.

1. Pobierz źródło aplikacji z repo [platformy Docker.](https://github.com/docker/getting-started) Możesz pobrać plik ZIP dla tego repo. Aby pobrać plik ZIP, użyj zielonego **przycisku Kod** i wybierz **pozycję Pobierz plik ZIP.** Otwórz plik ZIP i wyodrębnij wszystko, aby wyodrębnić źródło aplikacji z folderu *aplikacji* do folderu na dysku twardym.

   ![Zrzut ekranu przedstawiający zielony przycisk Kod i opcję Pobierz plik ZIP](media/download-zip.png)

1. Po wyodrębnienia użyj ulubionego edytora kodu, aby otworzyć projekt. Jeśli potrzebujesz edytora, możesz użyć Visual Studio Code [.](https://code.visualstudio.com/) Powinny zostać wyświetlony `package.json` podkatalogi i ( `src` i `spec` ).

    ![Zrzut ekranu Visual Studio Code otwarty z załadowaną aplikacją](media/ide-screenshot.png)

## <a name="building-the-apps-container-image"></a>Budowania obrazu kontenera aplikacji

Aby skompilować aplikację, należy użyć `Dockerfile` . Plik Dockerfile jest po prostu skryptem tekstowym z instrukcjami używanymi do tworzenia obrazu kontenera. Jeśli pliki Dockerfile zostały utworzone wcześniej, w poniższym pliku Dockerfile może być kilka wad. Ale nie martw się! Przejmiemy je.

1. Utwórz plik o nazwie `Dockerfile` w tym samym folderze co plik o `package.json` następującej zawartości.

    ```dockerfile
    FROM node:12-alpine
    WORKDIR /app
    COPY . .
    RUN yarn install --production
    CMD ["node", "/app/src/index.js"]
    ```

    Sprawdź, czy plik nie `Dockerfile` ma rozszerzenia pliku, takiego jak `.txt` . Niektóre edytory mogą automatycznie dołączać to rozszerzenie pliku, co spowoduje błąd w następnym kroku.

1. Jeśli jeszcze tego nie zrobiono, otwórz terminal i przejdź do `app` katalogu za pomocą . `Dockerfile` Teraz skompilowanie obrazu kontenera przy użyciu `docker build` polecenia .

    ```bash
    docker build -t getting-started .
    ```

    Alternatywnie możesz również kliknąć prawym przyciskiem myszy plik Dockerfile i wybrać polecenie Build Image... (Skompilować **obraz),a** następnie określić tag w wierszu polecenia.

    To polecenie użyło pliku Dockerfile do skompilowania nowego obrazu kontenera. Być może udało Ci się zauważyć, że pobrano wiele "warstw". Wynika to z tego, że poinstruowany konstruktor, że chcesz rozpocząć od `node:12-alpine` obrazu. Jednak ponieważ nie masz go na swojej maszynie, ten obraz musiał zostać pobrany.

    Po pobraniu obrazu został on skopiowany w aplikacji i użyty do zainstalowania `yarn` zależności aplikacji. Dyrektywa `CMD` określa domyślne polecenie do uruchomienia podczas uruchamiania kontenera z tego obrazu.

    Na koniec `-t` flaga oznacza obraz. Pomyśl o tym po prostu jako o czytelnej dla człowieka nazwie obrazu końcowego. Ponieważ obraz został nazwany `getting-started` , możesz odwołać się do tego obrazu po uruchomieniu kontenera.

    Na końcu polecenia informuje, że docker powinien szukać w `.` `docker build` bieżącym `Dockerfile` katalogu.

## <a name="starting-an-app-container"></a>Uruchamianie kontenera aplikacji

Teraz, gdy masz obraz, uruchom aplikację. Aby to zrobić, użyj `docker run` polecenia (pamiętaj, że wcześniej?).

1. Uruchom kontener przy użyciu polecenia i określ nazwę właśnie `docker run` utworzonego obrazu:

    ```bash
    docker run -dp 3000:3000 getting-started
    ```

    Pamiętasz `-d` `-p` flagi i ? Nowy kontener jest uruchomiony w trybie "odłączony" (w tle) i tworzysz mapowanie między portem 3000 hosta a portem 3000 kontenera. Bez mapowania portów nie można uzyskać dostępu do aplikacji.

1. Po kilku sekundach otwórz w przeglądarce internetowej adres [http://localhost:3000](http://localhost:3000) .
    Powinna zostać wyświetlony aplikacja!

    ![Pusta lista zadań do zdjęć](media/todo-list-empty.png)

1. Dodaj element lub dwa i zobacz, że działa zgodnie z oczekiwaniami. Elementy można oznaczać jako ukończone i usuwać. Frontonia pomyślnie przechowuje elementy w za zaplecza. Dosyć szybko i łatwo, prawda?

W tym momencie powinien być uruchomiony menedżer listy zadań do rzeczy do uruchomienia z kilkoma elementami, wszystko sbudowaną przez Ciebie. Teraz dokonajmy kilku zmian i dowiedzmy się więcej na temat zarządzania kontenerami.

Jeśli szybko przyjrzysz się rozszerzeniu VS Code, powinny zostać teraz uruchomione dwa kontenery (ten samouczek i twój nowo uruchomiony kontener aplikacji)!

![Rozszerzenie platformy Docker z uruchomionym samouczkiem i kontenerami aplikacji](media/vs-two-containers.png)

## <a name="recap"></a>Podsumowanie

W tej krótkiej sekcji poznaliśmy podstawowe informacje dotyczące tworzenia obrazu kontenera i utworzono w tym celu plik Dockerfile. Po s zbudowaniu obrazu uruchomiliśmy kontener i zobaczyliśmy uruchominą aplikację.

Następnie dokonasz modyfikacji aplikacji i dowiesz się, jak zaktualizować uruchamianą aplikację przy użyciu nowego obrazu. W ten sposób poznasz kilka innych przydatnych poleceń.

## <a name="next-steps"></a>Następne kroki

Kontynuuj pracę z samouczkiem!

> [!div class="nextstepaction"]
> [Aktualizowanie aplikacji](update-your-app.md)
