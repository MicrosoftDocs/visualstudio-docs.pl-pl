---
title: 'Samouczek platformy Docker — część 1: kompilowanie i uruchamianie przykładowej aplikacji z listą zadań do zrobienia'
description: Omówienie przykładowej aplikacji z listą zadań do wykonania działającą w Node.js.
ms.date: 08/04/2020
author: nebuk89
ms.author: ghogen
manager: jillfra
ms.technology: vs-azure
ms.topic: conceptual
ms.workload:
- azure
ms.openlocfilehash: fb92f5aae84a7c164f04145abe24eb32d7792056
ms.sourcegitcommit: fb8babf5cd72f1fc2f97ffe4ad7b62d91f325f61
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2020
ms.locfileid: "89485444"
---
# <a name="build-and-run-the-todo-sample-app"></a>Kompiluj i uruchamiaj przykładową aplikację do zrobienia

W pozostałej części tego samouczka będziesz pracować z prostym menedżerem listy zadań do wykonania, który działa w Node.js. Jeśli nie masz doświadczenia w korzystaniu z Node.js, nie martw się. Nie jest wymagana Prawdziwa obsługa języka JavaScript.

W tym momencie zespół programistyczny jest dość mały i po prostu tworzysz aplikację, która będzie mogła udowodnić swój MVP (minimalny produkt żywotny). Chcesz zobaczyć, jak to działa, i czego może robić, nie trzeba myśleć o tym, jak będzie działać dla dużego zespołu, wielu deweloperów itd.

![Zrzut ekranu przedstawiający listę zadań do zrobienia](media/todo-list-sample.png)

## <a name="get-the-app"></a>Pobierz aplikację

Przed uruchomieniem aplikacji należy uzyskać kod źródłowy aplikacji na komputerze. W przypadku rzeczywistych projektów zwykle zostanie Sklonowane repozytorium. Jednak w tym samouczku utworzono plik ZIP zawierający aplikację.

1. [Pobierz plik zip](/assets/app.zip). Otwórz plik ZIP i upewnij się, że wyodrębnisz zawartość.

1. Po wyodrębnieniu użyj ulubionego edytora kodu, aby otworzyć projekt. Jeśli potrzebujesz edytora, możesz użyć [Visual Studio Code](https://code.visualstudio.com/). Powinny pojawić się `package.json` i dwa podkatalogi ( `src` i `spec` ).

    ![Zrzut ekranu przedstawiający Visual Studio Code otwarty przy użyciu aplikacji załadowanej](media/ide-screenshot.png)

## <a name="building-the-apps-container-image"></a>Kompilowanie obrazu kontenera aplikacji

W celu skompilowania aplikacji należy użyć `Dockerfile` . Pliku dockerfile to po prostu skrypt tekstowy zawierający instrukcje, które są używane do tworzenia obrazu kontenera. Jeśli wcześniej utworzono wieloetapowe dockerfile, zobaczysz kilka wad w pliku dockerfile poniżej. Ale nie martw się! Przejdziemy do nich.

1. Utwórz plik o nazwie `Dockerfile` w tym samym folderze, w którym znajduje się plik `package.json` o następującej zawartości.

    ```dockerfile
    FROM node:12-alpine
    WORKDIR /app
    COPY . .
    RUN yarn install --production
    CMD ["node", "/app/src/index.js"]
    ```

    Upewnij się, że plik `Dockerfile` nie ma rozszerzenia pliku, takiego jak `.txt` . Niektóre edytory mogą automatycznie dołączyć to rozszerzenie pliku, co spowoduje wystąpienie błędu w następnym kroku.

1. Jeśli jeszcze tego nie zrobiono, Otwórz Terminal i przejdź do `app` katalogu przy użyciu `Dockerfile` . Teraz Skompiluj obraz kontenera za pomocą `docker build` polecenia.

    ```bash
    docker build -t getting-started .
    ```

    Alternatywnie można również kliknąć prawym przyciskiem myszy pliku dockerfile i wybrać polecenie **Kompiluj obraz...** , a następnie określić tag w wierszu polecenia.

    To polecenie użyło pliku dockerfile do skompilowania nowego obrazu kontenera. Być może zauważono, że pobrano wiele "warstw". Dzieje się tak dlatego, że wyinstruujesz konstruktora, który miał zostać uruchomiony z `node:12-alpine` obrazu. Ale ponieważ nie masz go na swojej maszynie, ten obraz musi zostać pobrany.

    Po pobraniu obrazu program skopiował do aplikacji i użyty `yarn` do zainstalowania zależności aplikacji. `CMD`Dyrektywa określa domyślne polecenie do uruchomienia podczas uruchamiania kontenera z tego obrazu.

    Na końcu `-t` flaga oznacza obraz. Zastanów się to po prostu jako czytelna dla człowieka nazwa obrazu końcowego. Ze względu na to, że nadano nazwę obrazu `getting-started` , można odwoływać się do tego obrazu podczas uruchamiania kontenera.

    `.`Na końcu `docker build` polecenia zostanie wyświetlona informacja o tym, że platforma Docker powinna szukać `Dockerfile` w bieżącym katalogu.

## <a name="starting-an-app-container"></a>Uruchamianie kontenera aplikacji

Teraz, gdy masz obraz, uruchom aplikację. Aby to zrobić, użyj `docker run` polecenia (należy pamiętać, że wcześniej?).

1. Uruchom kontener przy użyciu `docker run` polecenia i określ nazwę właśnie utworzonego obrazu:

    ```bash
    docker run -dp 3000:3000 getting-started
    ```

    Zapamiętaj `-d` `-p` flagi i? Uruchamiasz nowy kontener w trybie odłączenia (w tle) i utworzysz mapowanie między portem 3000 hosta a portem 3000. Bez mapowania portów nie będziesz mieć możliwości uzyskania dostępu do aplikacji.

1. Po kilku sekundach Otwórz przeglądarkę internetową, aby [http://localhost:3000](http://localhost:3000) .
    Powinna zostać wyświetlona aplikacja.

    ![Pusta lista zadań do wykonania](media/todo-list-empty.png)

1. Przejdź dalej i Dodaj element lub dwa i sprawdź, czy działa zgodnie z oczekiwaniami. Elementy można oznaczyć jako ukończone i usunąć. Fronton zapisuje elementy w zapleczu. Całkiem szybka i łatwa, tak?

Na tym etapie należy mieć uruchomiony Menedżer listy zadań do wykonania z kilkoma elementami, które zostały utworzone przez Ciebie. Teraz Wprowadźmy kilka zmian i dowiesz się, jak zarządzać kontenerami.

Jeśli dowiesz się, jak korzystać z rozszerzenia VS Code, powinny zostać wyświetlone dwa kontenery uruchomione teraz (ten samouczek i świeżo uruchomiony kontener aplikacji)!

![Rozszerzenie platformy Docker z uruchomionym samouczkiem i kontenerami aplikacji](media/vs-two-containers.png)

## <a name="recap"></a>Podsumowanie

W tej krótkiej sekcji przedstawiono podstawowe informacje na temat tworzenia obrazu kontenera i tworzenia pliku dockerfile. Po skompilowaniu obrazu, rozpocząłsz kontener i wykorzystasz uruchomioną aplikację.

Następnie wprowadzisz modyfikację aplikacji i dowiesz się, jak zaktualizować działającą aplikację przy użyciu nowego obrazu. W ten sposób poznasz kilka innych przydatnych poleceń.

## <a name="next-steps"></a>Następne kroki

Kontynuuj pracę z samouczkiem.

> [!div class="nextstepaction"]
> [Aktualizowanie aplikacji](update-your-app.md)