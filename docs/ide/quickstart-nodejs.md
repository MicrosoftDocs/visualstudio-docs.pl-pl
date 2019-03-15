---
title: 'Szybki start: Tworzenie pierwszej aplikacji Node.js przy użyciu programu Visual Studio'
description: W tym przewodniku Szybki Start utworzysz aplikację Node.js w programie Visual Studio
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
ms.openlocfilehash: 8d306436f8948d6f1d22d02984b00c2e0bc8f38f
ms.sourcegitcommit: f7c401a376ce410336846835332a693e6159c551
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57867015"
---
# <a name="quickstart-use-visual-studio-to-create-your-first-nodejs-app"></a>Szybki start: Tworzenie pierwszej aplikacji Node.js przy użyciu programu Visual Studio

W ramach tego wprowadzenia do programu Visual Studio zintegrowane środowisko programistyczne (IDE) 5 – 10 minut utworzysz prostą aplikację sieci web środowiska Node.js. Jeśli jeszcze nie zainstalowano programu Visual Studio 2017, przejdź do strony [program Visual Studio pobiera](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) strony, aby zainstalować go za darmo.

## <a name="create-a-project"></a>Tworzenie projektu

Najpierw utworzysz projekt aplikacji sieci web środowiska Node.js.

1. Jeśli nie masz już zainstalowane środowisko uruchomieniowe Node.js, należy zainstalować wersję LTS z [Node.js](https://nodejs.org/en/download/) witryny sieci Web.

    Ogólnie rzecz biorąc program Visual Studio automatycznie wykrywa zainstalowane środowisko uruchomieniowe Node.js. Jeśli nie zostanie wykryta zainstalowanego środowiska uruchomieniowego, można skonfigurować projekt, aby odwoływać się do zainstalowanego środowiska uruchomieniowego na stronie właściwości (po utworzeniu projektu, kliknij prawym przyciskiem myszy węzeł projektu i wybierz polecenie **właściwości**).

1. Otwórz program Visual Studio 2017.

1. Na pasku menu u góry wybierz **pliku** > **New** > **projektu**.

1. W **nowy projekt** rozwiń w lewym okienku w oknie dialogowym **JavaScript**, następnie wybierz **Node.js**. W środkowym okienku wybierz **pusta aplikacja internetowa Node.js**, następnie wybierz **OK**.

     Jeśli nie widzisz **pusta aplikacja internetowa Node.js** szablonu projektu, kliknij przycisk **Otwórz Instalator programu Visual Studio** łącze w okienku po lewej stronie **nowy projekt** okno dialogowe. Uruchamia Instalatora programu Visual Studio. Wybierz **programowania Node.js** obciążenia, wybierz **Modyfikuj**.

     ![Obciążenie node.js w Instalatorze programu VS](../ide/media/quickstart-nodejs-workload.png)

    Po wybraniu **pusta aplikacja sieci Web Node.js** szablon i kliknij przycisk **OK**, program Visual Studio tworzy i nowego rozwiązania i otwiera projekt. *Server.js* zostanie otwarty w edytorze w okienku po lewej stronie.

## <a name="explore-the-ide"></a>Eksploruj IDE

1. Przyjrzyj się **Eksploratora rozwiązań** w okienku po prawej stronie.

   ![Eksplorator rozwiązań](../ide/media/quickstart-nodejs-solution-explorer.png)

   - Wyróżnione czcionką pogrubioną jest projektu, przy użyciu nazwę nadaną w **nowy projekt** okno dialogowe. Na dysku, ten projekt jest reprezentowany przez *.njsproj* pliku w folderze projektu.

   - Na najwyższym poziomie to rozwiązanie, która domyślnie ma taką samą nazwę jak projektu. To rozwiązanie, reprezentowane przez *.sln* plików na dysku, to kontener dla jednego lub kilku powiązanych projektów.

   - Węzeł npm zawiera wszystkie pakiety npm zainstalowane. Możesz kliknąć prawym przyciskiem myszy węzeł npm, aby wyszukać i zainstalować pakiety npm przy użyciu okna dialogowego.

1. Jeśli chcesz zainstalować pakiety npm lub poleceń środowiska Node.js z poziomu wiersza polecenia, kliknij prawym przyciskiem myszy węzeł projektu i wybierz polecenie **Otwórz wiersz polecenia w tym miejscu**.

   ![Wiersz polecenia środowiska node.js](../ide/media/quickstart-nodejs-command-prompt.png)

1. W *server.js* plik w edytorze (w okienku po lewej stronie), wybierz `http.createServer` , a następnie naciśnij klawisz **F12** lub wybierz **przejdź do definicji** z menu kontekstowego (kliknij prawym przyciskiem myszy). To polecenie powoduje przejście do definicji `createServer` działa w programach *index.d.ts*.

   ![Menu kontekstowe przejdź do definicji](../ide/media/quickstart-nodejs-gotodefinition.png)

1. Otrzymano do *server.js*, następnie umieść kursor na końcu ciągu w ten wiersz kodu, `res.end('Hello World\n');`i zmodyfikuj go tak, aby wygląda następująco:

    `res.end('Hello World\n' + res.connection.`

    Miejscem, gdzie wpisujesz `connection.`, technologia IntelliSense zawiera opcje automatycznego uzupełniania wpis kodu.

   ![Automatyczne uzupełnianie IntelliSense](../ide/media/quickstart-nodejs-intellisense.png)

1. Wybierz **localPort**, a następnie wpisz `);` można wykonać instrukcji wygląda następująco:

    `res.end('Hello World\n' + res.connection.localPort);`

## <a name="run-the-application"></a>Uruchamianie aplikacji

1. Naciśnij klawisz **Ctrl**+**F5** (lub **Debuguj > Uruchom bez debugowania**) do uruchamiania aplikacji. Aplikacja zostanie otwarta w przeglądarce.

1. W oknie przeglądarki zostanie wyświetlone, "Hello World" oraz numer portu lokalnego.

1. Zamknij przeglądarkę sieci web.

Gratulacje z okazji ukończenie tego przewodnika Szybki Start, w którym stało się do korzystania z programu Visual Studio IDE i Node.js. Jeśli chcesz delve głębiej do jego możliwości, kontynuować samouczek z **samouczki** części spisu treści.

## <a name="next-steps"></a>Następne kroki

> [!div class="nextstepaction"]
> [Wdrażanie aplikacji do usługi App Service w systemie Linux](../javascript/publish-nodejs-app-azure.md)

- [Samouczek dotyczący Node.js lub Express](../javascript/tutorial-nodejs.md)
- [Samouczek dotyczący środowiska Node.js i React](../javascript/tutorial-nodejs-with-react-and-jsx.md)