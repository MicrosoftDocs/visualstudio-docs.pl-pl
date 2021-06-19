---
title: Tworzenie pierwszej Node.js aplikacji
ms.custom:
- vs-acquisition
- SEO-VS-2020
description: W tym przewodniku Szybki start utworzysz aplikację Node.js w Visual Studio
ms.date: 03/25/2021
ms.technology: vs-javascript
ms.topic: quickstart
ms.devlang: javascript
ms.assetid: b0e4ebed-1a01-41ef-aad1-4d8465ce5322
author: mikejo5000
ms.author: mikejo
manager: jmartens
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: 0c44bfcfe1e7f07f83ca2b7dbb8b0604f5efe5f1
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112386166"
---
# <a name="quickstart-create-your-first-nodejs-app-with-visual-studio"></a>Szybki start: tworzenie pierwszej aplikacji Node.js za pomocą Visual Studio

W tym 5–10-minutowym wprowadzeniu do zintegrowanego środowiska projektowego (IDE) Visual Studio utworzysz prostą aplikację Node.js internetową.

## <a name="prerequisites"></a>Wymagania wstępne

Przed rozpoczęciem zainstaluj program Visual Studio i skonfiguruj Node.js środowiska.

### <a name="install-visual-studio"></a>Instalowanie programu Visual Studio

::: moniker range=">=vs-2019"
Jeśli jeszcze nie zainstalowano programu Visual Studio 2019, [](https://visualstudio.microsoft.com/downloads) przejdź do strony pobierania Visual Studio, aby zainstalować ją bezpłatnie.
::: moniker-end
::: moniker range="vs-2017"
Jeśli jeszcze nie zainstalowano programu Visual Studio 2017, [](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) przejdź do strony pobierania Visual Studio, aby zainstalować ją bezpłatnie.
::: moniker-end

### <a name="set-up-your-nodejs-environment"></a>Konfigurowanie środowiska Node.js danych

Visual Studio może pomóc w skonfigurowaniu środowiska, w tym instalowania narzędzi wspólnych dla Node.js tworzenia aplikacji.

1. W Visual Studio narzędzia Pobierz narzędzia  >  **i funkcje.**

1. W Instalator programu Visual Studio wybierz pakietNode.js **i** wybierz **pozycję** Modyfikuj, aby pobrać i zainstalować obciążenie.

    ![Node.js obciążenia w Instalator programu Visual Studio](../ide/media/quickstart-nodejs-workload.png)

1. Zainstaluj wersję LTS środowiska [Node.js uruchomieniowego](https://nodejs.org/en/download/). Zalecamy wersję LTS, aby uzyskać najlepszą zgodność z zewnętrznymi platformami i bibliotekami.

    Chociaż Node.js jest zbudowany dla architektur 32-bitowych i 64-bitowych, instalator Node.js obsługuje tylko jedną zainstalowaną wersję na raz.

1. Jeśli Visual Studio nie wykryje zainstalowanego środowiska uruchomieniowego (zwykle tak jest), skonfiguruj projekt, aby odwoływać się do zainstalowanego środowiska uruchomieniowego:

   1. Po [utworzeniu projektu kliknij](#create-your-app-project)prawym przyciskiem myszy węzeł projektu.

   1. Wybierz **pozycję** Właściwości i ustaw **Node.exe ścieżkę.** Możesz użyć globalnej instalacji usługi Node.js lub określić ścieżkę do interpretera lokalnego w każdym z Node.js projektów.

## <a name="create-your-app-project"></a>Tworzenie projektu aplikacji

1. Jeśli nie zostało to jeszcze zainstalowane, zainstaluj wersję LTS środowiska [Node.js uruchomieniowego](https://nodejs.org/en/download/). Aby uzyskać więcej informacji, zobacz [wymagania wstępne](#prerequisites).

1. Otwórz program Visual Studio.

1. Tworzenie nowego projektu.

    ::: moniker range=">=vs-2019"

    1. Naciśnij **klawisz Esc,** aby zamknąć okno uruchamiania.

    1. Naciśnij **klawisze Ctrl + Q,** aby otworzyć pole wyszukiwania, a następnie **wpiszNode.js**.

    1. Wybierz **pozycję Puste Node.js web application (JavaScript).** W oknie dialogowym wybierz pozycję **Utwórz**.

    ::: moniker-end

    ::: moniker range="vs-2017"
    1. Na górnym pasku menu wybierz pozycję **File** New Project > **(Plik nowy** > **projekt).**

    1. W lewym okienku okna dialogowego **Nowy** projekt rozwiń pozycję **JavaScript** i wybierz **pozycjęNode.js**.

    1. W środkowym okienku wybierz pozycję **Puste Node.js aplikacji internetowej** i wybierz przycisk **OK.**

    ::: moniker-end
    
    Jeśli nie widzisz szablonu projektu **pustej Node.js aplikacji** internetowej, musisz dodaćNode.js **projektowego.** Aby uzyskać szczegółowe instrukcje, zobacz [wymagania wstępne](#prerequisites).

    Visual Studio tworzy i otwiera projekt. Plikserver.js *projektu* zostanie otwarty w edytorze po lewej stronie.

## <a name="explore-the-ide"></a>Eksplorowanie środowiska IDE

1. W okienku po prawej stronie **przyjrzyj** się Eksplorator rozwiązań .

   ![Eksplorator rozwiązań](../ide/media/quickstart-nodejs-solution-explorer.png)

   - Wyróżnione pogrubioną czcionką jest projekt, używając nazwy podanej podczas jego skonfigurowania. Na dysku ten projekt jest reprezentowany przez *plik .njsproj* w folderze projektu.

   - Na najwyższym poziomie znajduje się rozwiązanie, które domyślnie ma taką samą nazwę jak projekt. Rozwiązanie reprezentowane przez plik *sln* na dysku jest kontenerem dla co najmniej jednego powiązanego projektu.

   - W **węźle npm** są dostępne zainstalowane pakiety npm. Możesz kliknąć prawym przyciskiem myszy węzeł npm, aby wyszukać i zainstalować pakiety npm przy użyciu okna dialogowego.

1. Jeśli chcesz zainstalować pakiety npm lub polecenia Node.js wiersza polecenia, kliknij prawym przyciskiem myszy węzeł projektu i wybierz polecenie **Otwórz wiersz polecenia tutaj.**

   ![Wiersz polecenia node dot j s](../ide/media/quickstart-nodejs-command-prompt.png)

1. Jeśli chcesz przetestować nawigację do kodu źródłowego, z otwartego pliku *server.js* wybierz pozycję **http.createServer** i naciśnij **klawisz F12** lub wybierz pozycję **Przejdź** do definicji z menu kontekstowego (kliknięcie prawym przyciskiem myszy). To polecenie przenosi do definicji funkcji `createServer` w *http.d.ts*.

   ![Menu kontekstowe Przejdź do definicji](../ide/media/quickstart-nodejs-gotodefinition.png)

1. Wstecz, *server.js* i odszukaj ten wiersz kodu: `res.end('Hello World\n');` . Zmodyfikuj kod w taki sposób:

    `res.end('Hello World\n' + res.connection.`

    Po wpisaniu **połączenia funkcja** IntelliSense udostępnia opcje automatycznego ukończenia wpisu kodu.

   ![Automatyczne ukończenie funkcji IntelliSense](../ide/media/quickstart-nodejs-intellisense.png)

1. Wybierz **pozycję localPort i** wpisz **);** w celu ukończenia instrukcji :

    `res.end('Hello World\n' + res.connection.localPort);`

## <a name="run-the-app"></a>Uruchamianie aplikacji

1. Naciśnij **klawisze Ctrl+F5** (lub **Debuguj** rozpocznij  >  **bez** debugowania), aby uruchomić aplikację. 
 
   Aplikacja zostanie otwarta w przeglądarce.

1. W przeglądarce sprawdź, czy jest wyświetlany komunikat "Hello world" i numer portu lokalnego.

Gratulacje! Utworzono prostą aplikację Node.js za pomocą Visual Studio. Aby bardziej zagłębić się w ten temat, przejdź do sekcji **Samouczki** spisu treści.

## <a name="next-steps"></a>Następne kroki

> [!div class="nextstepaction"]
> [Wdrażanie aplikacji w systemie Linux App Service](../javascript/publish-nodejs-app-azure.md)

> [!div class="nextstepaction"]
> [Samouczek dotyczący Node.js i Express](../javascript/tutorial-nodejs.md)

> [!div class="nextstepaction"]
> [Samouczek dotyczący Node.js i React](../javascript/tutorial-nodejs-with-react-and-jsx.md)
