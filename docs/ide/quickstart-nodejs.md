---
title: Tworzenie pierwszej aplikacji Node.js
ms.custom: SEO-VS-2020
description: W tym przewodniku szybki start utworzysz aplikację Node.js w programie Visual Studio
ms.date: 06/27/2018
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
ms.openlocfilehash: c342018a2331b27a411b5efc23af1438fa18518d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99932621"
---
# <a name="quickstart-use-visual-studio-to-create-your-first-nodejs-app"></a>Szybki Start: Tworzenie pierwszej aplikacji Node.js przy użyciu programu Visual Studio

W tym 5-10 minutowym wprowadzeniu do zintegrowanego środowiska programistycznego (IDE) programu Visual Studio utworzysz prostą aplikację sieci Web Node.js.

## <a name="prerequisites"></a>Wymagania wstępne

* Musisz mieć zainstalowany program Visual Studio i Node.js obciążenie programowaniem.

    ::: moniker range=">=vs-2019"
    Jeśli program Visual Studio 2019 nie został jeszcze zainstalowany, przejdź do strony [plików do pobrania programu Visual Studio](https://visualstudio.microsoft.com/downloads) , aby zainstalować ją bezpłatnie.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Jeśli program Visual Studio 2017 nie został jeszcze zainstalowany, przejdź do strony [plików do pobrania programu Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) , aby zainstalować ją bezpłatnie.
    ::: moniker-end

    Jeśli musisz zainstalować obciążenie, ale masz już program Visual Studio, przejdź do pozycji **Narzędzia**  >  **Pobierz narzędzia i funkcje..**., co spowoduje otwarcie Instalator programu Visual Studio. Wybierz **Node.js obciążenie programowaniem** , a następnie wybierz **Modyfikuj**.

    ![Node.js obciążenie w Instalatorze programu VS](../ide/media/quickstart-nodejs-workload.png)

* Musisz mieć zainstalowane środowisko uruchomieniowe Node.js.

    Jeśli go nie zainstalowano, zalecamy zainstalowanie wersji LTS z witryny internetowej [Node.js](https://nodejs.org/en/download/) w celu uzyskania najlepszej zgodności z zewnętrznymi platformami i bibliotekami. Node.js jest oparta na architekturze 32-bitowej i 64-bitowej. Narzędzia Node.js w programie Visual Studio, zawarte w obciążeniu Node.js, obsługują obie wersje. Tylko jeden jest wymagany, a Instalator Node.js obsługuje tylko jeden instalowany w danym momencie.
    
    Ogólnie rzecz biorąc, program Visual Studio automatycznie wykrywa zainstalowane Node.js środowiska uruchomieniowego. Jeśli nie wykryje zainstalowanego środowiska uruchomieniowego, można skonfigurować projekt do odwoływania się do zainstalowanego środowiska uruchomieniowego na stronie właściwości (po utworzeniu projektu kliknij prawym przyciskiem myszy węzeł projektu, wybierz polecenie **Właściwości**, a następnie ustaw **ścieżkęNode.exe**). Można użyć globalnej instalacji Node.js lub można określić ścieżkę do lokalnego interpretera w każdym z projektów Node.js. 

## <a name="create-a-project"></a>Tworzenie projektu

Najpierw utworzysz projekt aplikacji sieci Web Node.js.

1. Jeśli nie masz już zainstalowanego środowiska uruchomieniowego Node.js, Zainstaluj wersję LTS z witryny [Node.js](https://nodejs.org/en/download/) .

    Aby uzyskać więcej informacji, zobacz Wymagania wstępne.

1. Otwórz program Visual Studio.

1. Tworzenie nowego projektu.

    ::: moniker range=">=vs-2019"
    Naciśnij klawisz **ESC** , aby zamknąć okno uruchamiania. **Naciśnij klawisze CTRL + Q** , aby otworzyć pole wyszukiwania, wpisz **Node.js**, a następnie wybierz pozycję **Utwórz nowe puste Node.js projekt aplikacji sieci Web** (JavaScript). W wyświetlonym oknie dialogowym wybierz pozycję **Utwórz**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Na górnym pasku menu wybierz pozycję **plik**  >  **Nowy**  >  **projekt**. W lewym okienku okna dialogowego **Nowy projekt** rozwiń opcję **JavaScript**, a następnie wybierz **Node.js**. W środkowym okienku wybierz pozycję **pusta Node.js aplikacja sieci Web**, a następnie wybierz przycisk **OK**.
    ::: moniker-end
    Jeśli nie widzisz szablonu projektu **pustej Node.js aplikacji sieci Web** , musisz dodać **Node.js obciążenie programowaniem** . Aby uzyskać szczegółowe instrukcje, zobacz [wymagania wstępne](#prerequisites).

    Program Visual Studio tworzy i nowe rozwiązanie i otwiera projekt. *server.js* otwiera się w edytorze w okienku po lewej stronie.

## <a name="explore-the-ide"></a>Eksplorowanie środowiska IDE

1. Zapoznaj się z **Eksplorator rozwiązań** w okienku po prawej stronie.

   ![Eksplorator rozwiązań](../ide/media/quickstart-nodejs-solution-explorer.png)

   - Wyróżnione czcionką pogrubioną jest projektem, przy użyciu nazwy podanych w oknie dialogowym **Nowy projekt** . Na dysku ten projekt jest reprezentowany przez plik *. njsproj* w folderze projektu.

   - Na najwyższym poziomie jest rozwiązaniem, które domyślnie ma taką samą nazwę jak projekt. Rozwiązanie reprezentowane przez plik *. sln* na dysku jest kontenerem dla co najmniej jednego powiązanego projektu.

   - W węźle npm są wyświetlane wszystkie zainstalowane pakiety npm. Możesz kliknąć prawym przyciskiem myszy węzeł npm, aby wyszukać i zainstalować pakiety npm przy użyciu okna dialogowego.

1. Jeśli chcesz zainstalować pakiety npm lub Node.js polecenia z wiersza polecenia, kliknij prawym przyciskiem myszy węzeł projektu, a następnie wybierz polecenie **Otwórz wiersz polecenia tutaj**.

   ![Wiersz polecenia Node.js](../ide/media/quickstart-nodejs-command-prompt.png)

1. W pliku *server.js* w edytorze (lewe okienko) wybierz, `http.createServer` a następnie naciśnij klawisz **F12** lub wybierz **Przejdź do definicji** z menu kontekstowego (kliknij prawym przyciskiem myszy). To polecenie umożliwia przejście do definicji `createServer` funkcji w *indeksie. d. TS*.

   ![Menu kontekstowe przejdź do definicji](../ide/media/quickstart-nodejs-gotodefinition.png)

1. Pobrano z powrotem do *server.js*, następnie umieść kursor na końcu ciągu w tym wierszu kodu, `res.end('Hello World\n');` i zmodyfikuj go tak, aby wyglądał następująco:

    `res.end('Hello World\n' + res.connection.`

    Gdy wpiszesz `connection.` , technologia IntelliSense udostępnia opcje do autouzupełniania wpisu kodu.

   ![Funkcja IntelliSense — Autouzupełnianie](../ide/media/quickstart-nodejs-intellisense.png)

1. Wybierz pozycję **localport**, a następnie wpisz, `);` Aby zakończyć instrukcję, tak aby wyglądała następująco:

    `res.end('Hello World\n' + res.connection.localPort);`

## <a name="run-the-application"></a>Uruchamianie aplikacji

1. Naciśnij klawisz **Ctrl** + **F5** (lub **Debuguj > Uruchom bez debugowania**), aby uruchomić aplikację. Aplikacja zostanie otwarta w przeglądarce.

1. W oknie przeglądarki zobaczysz ciąg "Hello world" oraz numer portu lokalnego.

1. Zamknij przeglądarkę internetową.

Gratulujemy zakończenia tego przewodnika Szybki Start, w którym rozpoczęto pracę z programem Visual Studio IDE i Node.js. Jeśli chcesz lepiej podzielić się swoimi możliwościami, przejdź do samouczka w sekcji **samouczki** spisu treści.

## <a name="next-steps"></a>Następne kroki

> [!div class="nextstepaction"]
> [Wdrażanie aplikacji w systemie Linux App Service](../javascript/publish-nodejs-app-azure.md)

- [Samouczek dla Node.js i Express](../javascript/tutorial-nodejs.md)
- [Samouczek dotyczący Node.js i reagowania](../javascript/tutorial-nodejs-with-react-and-jsx.md)