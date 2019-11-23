---
title: 'Szybki Start: Tworzenie pierwszej aplikacji node. js przy użyciu programu Visual Studio'
description: W tym przewodniku szybki start utworzysz aplikację Node. js w programie Visual Studio
ms.date: 06/27/2018
ms.technology: vs-javascript
ms.topic: quickstart
ms.devlang: javascript
ms.assetid: b0e4ebed-1a01-41ef-aad1-4d8465ce5322
author: mikejo5000
ms.author: mikejo
manager: jillfra
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: 4995c6b95ba12eb776130b17dab1911c47988871
ms.sourcegitcommit: 44e9b1d9230fcbbd081ee81be9d4be8a485d8502
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/30/2019
ms.locfileid: "70180328"
---
# <a name="quickstart-use-visual-studio-to-create-your-first-nodejs-app"></a>Szybki Start: Tworzenie pierwszej aplikacji node. js przy użyciu programu Visual Studio

W tym 5-10 minutowym wprowadzeniu do zintegrowanego środowiska programistycznego (IDE) programu Visual Studio utworzysz prostą aplikację sieci Web Node. js.

## <a name="prerequisites"></a>Wymagania wstępne

* Musisz mieć zainstalowany program Visual Studio i obciążenie programowaniem Node. js.

    ::: moniker range=">=vs-2019"
    Jeśli program Visual Studio 2019 nie został jeszcze zainstalowany, przejdź do strony [plików do pobrania programu Visual Studio](https://visualstudio.microsoft.com/downloads) , aby zainstalować ją bezpłatnie.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Jeśli program Visual Studio 2017 nie został jeszcze zainstalowany, przejdź do strony [plików do pobrania programu Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) , aby zainstalować ją bezpłatnie.
    ::: moniker-end

    Jeśli musisz zainstalować obciążenie, ale masz już program Visual Studio, przejdź do pozycji **narzędzia** > **Pobierz narzędzia i funkcje..** ., co spowoduje otwarcie Instalator programu Visual Studio. Wybierz **programowania Node.js** obciążenia, wybierz **Modyfikuj**.

    ![Obciążenie node.js w Instalatorze programu VS](../ide/media/quickstart-nodejs-workload.png)

* Konieczne jest posiadanie zainstalowanego środowiska uruchomieniowego Node.js.

    Jeśli nie jest ona zainstalowana, zainstaluj wersję LTS z [Node.js](https://nodejs.org/en/download/) witryny sieci Web. Ogólnie rzecz biorąc program Visual Studio automatycznie wykrywa zainstalowane środowisko uruchomieniowe Node.js. Jeśli nie zostanie wykryta zainstalowanego środowiska uruchomieniowego, można skonfigurować projekt, aby odwoływać się do zainstalowanego środowiska uruchomieniowego na stronie właściwości (po utworzeniu projektu, kliknij prawym przyciskiem myszy węzeł projektu i wybierz polecenie **właściwości**).

## <a name="create-a-project"></a>Tworzenie projektu

Najpierw utworzysz projekt aplikacji sieci Web środowiska Node. js.

1. Jeśli nie masz już zainstalowane środowisko uruchomieniowe Node.js, należy zainstalować wersję LTS z [Node.js](https://nodejs.org/en/download/) witryny sieci Web.

    Ogólnie rzecz biorąc program Visual Studio automatycznie wykrywa zainstalowane środowisko uruchomieniowe Node.js. Jeśli nie zostanie wykryta zainstalowanego środowiska uruchomieniowego, można skonfigurować projekt, aby odwoływać się do zainstalowanego środowiska uruchomieniowego na stronie właściwości (po utworzeniu projektu, kliknij prawym przyciskiem myszy węzeł projektu i wybierz polecenie **właściwości**).

1. Otwórz program Visual Studio.

1. Utwórz nowy projekt.

    ::: moniker range=">=vs-2019"
    Naciśnij klawisz **ESC** , aby zamknąć okno uruchamiania. **Naciśnij klawisze CTRL + Q** , aby otworzyć pole wyszukiwania, wpisz **Node. js**, a następnie wybierz pozycję **Utwórz nowy pusty projekt aplikacji sieci Web Node. js** (JavaScript). W wyświetlonym oknie dialogowym wybierz pozycję **Utwórz**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Na pasku menu u góry wybierz **pliku** > **New** > **projektu**. W lewym okienku okna dialogowego **Nowy projekt** rozwiń węzeł **JavaScript**, a następnie wybierz polecenie **Node. js**. W środkowym okienku wybierz **pustą aplikację sieci Web Node. js**, a następnie wybierz **przycisk OK**.
    ::: moniker-end
    Jeśli nie widzisz szablonu projektu **pustej aplikacji sieci Web Node. js** , musisz dodać obciążenie **programowania Node. js** . Aby uzyskać szczegółowe instrukcje, zobacz [wymagania wstępne](#prerequisites).

    Program Visual Studio tworzy i nowego rozwiązania i otwiera projekt. *serwer. js* zostanie otwarty w edytorze w okienku po lewej stronie.

## <a name="explore-the-ide"></a>Eksploruj IDE

1. Przyjrzyj się **Eksploratora rozwiązań** w okienku po prawej stronie.

   ![Eksplorator rozwiązań](../ide/media/quickstart-nodejs-solution-explorer.png)

   - Wyróżnione czcionką pogrubioną jest projektu, przy użyciu nazwę nadaną w **nowy projekt** okno dialogowe. Na dysku ten projekt jest reprezentowany przez plik *. njsproj* w folderze projektu.

   - Na najwyższym poziomie to rozwiązanie, która domyślnie ma taką samą nazwę jak projektu. To rozwiązanie, reprezentowane przez *.sln* plików na dysku, to kontener dla jednego lub kilku powiązanych projektów.

   - W węźle npm są wyświetlane wszystkie zainstalowane pakiety npm. Możesz kliknąć prawym przyciskiem myszy węzeł npm, aby wyszukać i zainstalować pakiety npm przy użyciu okna dialogowego.

1. Jeśli chcesz zainstalować pakiety npm lub polecenia Node. js z poziomu wiersza polecenia, kliknij prawym przyciskiem myszy węzeł projektu i wybierz polecenie **Otwórz wiersz polecenia tutaj**.

   ![Wiersz polecenia środowiska Node. js](../ide/media/quickstart-nodejs-command-prompt.png)

1. W pliku *Server. js* w edytorze (po lewej stronie) wybierz `http.createServer` a następnie naciśnij klawisz **F12** lub wybierz **Przejdź do definicji** z menu kontekstowego (kliknij prawym przyciskiem myszy). To polecenie umożliwia przejście do definicji funkcji `createServer` w *indeksie. d. TS*.

   ![Menu kontekstowe przejdź do definicji](../ide/media/quickstart-nodejs-gotodefinition.png)

1. Odwróć do *serwera Server. js*, a następnie umieść kursor na końcu ciągu w tym wierszu kodu, `res.end('Hello World\n');`i zmodyfikuj go tak, aby wyglądał następująco:

    `res.end('Hello World\n' + res.connection.`

    W przypadku wpisywania `connection.`technologia IntelliSense udostępnia opcje Autouzupełniania wpisu kodu.

   ![Funkcja IntelliSense — Autouzupełnianie](../ide/media/quickstart-nodejs-intellisense.png)

1. Wybierz pozycję **localport**, a następnie wpisz `);`, aby zakończyć instrukcję, tak aby wyglądała następująco:

    `res.end('Hello World\n' + res.connection.localPort);`

## <a name="run-the-application"></a>Uruchamianie aplikacji

1. Naciśnij klawisz **Ctrl**+**F5** (lub **Debuguj > Uruchom bez debugowania**) do uruchamiania aplikacji. Aplikacja zostanie otwarta w przeglądarce.

1. W oknie przeglądarki zobaczysz ciąg "Hello world" oraz numer portu lokalnego.

1. Zamknij przeglądarkę sieci web.

Gratulujemy zakończenia tego przewodnika Szybki Start, w którym rozpoczęto pracę z programem Visual Studio IDE i środowiskiem Node. js. Jeśli chcesz lepiej podzielić się swoimi możliwościami, przejdź do samouczka w sekcji **samouczki** spisu treści.

## <a name="next-steps"></a>Następne kroki

> [!div class="nextstepaction"]
> [Wdrażanie aplikacji do usługi App Service w systemie Linux](../javascript/publish-nodejs-app-azure.md)

- [Samouczek dla środowiska Node. js i Express](../javascript/tutorial-nodejs.md)
- [Samouczek dotyczący środowiska Node. js i reagowanie](../javascript/tutorial-nodejs-with-react-and-jsx.md)