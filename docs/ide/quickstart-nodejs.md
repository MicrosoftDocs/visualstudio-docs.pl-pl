---
title: 'Szybki start: tworzenie pierwszej aplikacji Node.js za pomocą programu Visual Studio'
description: W tym przewodniku Szybki start utworzysz aplikację Node.js w programie Visual Studio
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
ms.openlocfilehash: f716421da3b9f888dbb7656c55db6814de88332b
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2020
ms.locfileid: "78235057"
---
# <a name="quickstart-use-visual-studio-to-create-your-first-nodejs-app"></a>Szybki start: tworzenie pierwszej aplikacji Node.js za pomocą programu Visual Studio

W tym 5-10 minut wprowadzenie do środowiska programistycznego zintegrowanego programu Visual Studio (IDE) utworzysz prostą aplikację sieci web Node.js.

## <a name="prerequisites"></a>Wymagania wstępne

* Musi być zainstalowany program Visual Studio i obciążenie deweloperskie node.js.

    ::: moniker range=">=vs-2019"
    Jeśli program Visual Studio 2019 nie został jeszcze zainstalowany, przejdź do strony pobierania programu Visual [Studio,](https://visualstudio.microsoft.com/downloads)aby zainstalować ją bezpłatnie.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Jeśli program Visual Studio 2017 nie został jeszcze zainstalowany, przejdź do strony pobierania programu Visual [Studio,](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download)aby zainstalować ją bezpłatnie.
    ::: moniker-end

    Jeśli chcesz zainstalować obciążenie, ale masz już program Visual Studio, przejdź do **narzędzia** > **Pobierz narzędzia i funkcje...**, który otwiera Instalator programu Visual Studio. Wybierz obciążenie **deweloperne node.js,** a następnie wybierz pozycję **Modyfikuj**.

    ![Obciążenie node.js w instalatorze usługi VS](../ide/media/quickstart-nodejs-workload.png)

* Musi być zainstalowany środowisko uruchomieniowe Node.js.

    Jeśli nie masz go zainstalowanego, zaleca się zainstalowanie wersji LTS z witryny [node.js](https://nodejs.org/en/download/) w celu uzyskania najlepszej zgodności z zewnętrznymi strukturami i bibliotekami. Node.js jest przeznaczony dla architektur 32-bitowych i 64-bitowych. Narzędzia Node.js w programie Visual Studio, uwzględnione w obciążeniu Node.js, obsługują obie wersje. Wymagany jest tylko jeden, a instalator Node.js obsługuje tylko jeden instalowany jednocześnie.
    
    Ogólnie rzecz biorąc program Visual Studio automatycznie wykrywa zainstalowane środowisko uruchomieniowe Node.js. Jeśli nie wykryje zainstalowanego środowiska uruchomieniowego, można skonfigurować projekt tak, aby odwoływał się do zainstalowanego środowiska uruchomieniowego na stronie właściwości (po utworzeniu projektu kliknij prawym przyciskiem myszy węzeł projektu, wybierz polecenie **Właściwości**i ustaw **ścieżkę Node.exe**). Można użyć instalacji globalnej node.js lub można określić ścieżkę do lokalnego interpretera w każdym z projektów Node.js. 

## <a name="create-a-project"></a>Tworzenie projektu

Najpierw utworzysz projekt aplikacji sieci web Node.js.

1. Jeśli nie masz już zainstalowanego środowiska uruchomieniowego Node.js, zainstaluj wersję LTS z [witryny node.js.](https://nodejs.org/en/download/)

    Aby uzyskać więcej informacji, zobacz wymagania wstępne.

1. Otwórz program Visual Studio.

1. Tworzenie nowego projektu.

    ::: moniker range=">=vs-2019"
    Naciśnij **klawisz Esc,** aby zamknąć okno początkowe. Wpisz **Ctrl + Q,** aby otworzyć pole wyszukiwania, wpisz **Node.js**, a następnie wybierz pozycję **Utwórz nowy projekt aplikacji sieci Web Pusty Node.js** (JavaScript). W wyświetlonym oknie dialogowym wybierz pozycję **Utwórz**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Na górnym pasku menu wybierz pozycję **Plik** > **nowego** > **projektu**. W lewym okienku okna dialogowego **Nowy projekt** rozwiń węzeł **JavaScript**, a następnie wybierz polecenie **Node.js**. W środkowym okienku wybierz pozycję **Pusta aplikacja sieci Web Node.js**, a następnie wybierz przycisk **OK**.
    ::: moniker-end
    Jeśli nie widzisz szablonu projektu **pustej aplikacji sieci Web Pusty Node.js,** należy dodać obciążenie **deweloperne node.js.** Aby uzyskać szczegółowe instrukcje, zobacz [Wymagania wstępne](#prerequisites).

    Visual Studio tworzy i nowe rozwiązanie i otwiera projekt. *server.js* zostanie otwarty w edytorze w lewym okienku.

## <a name="explore-the-ide"></a>Poznaj IDE

1. Zapoznaj się z **Eksploratorem rozwiązań** w prawym okienku.

   ![Eksplorator rozwiązań](../ide/media/quickstart-nodejs-solution-explorer.png)

   - Wyróżniony pogrubioną czcionką jest projekt, przy użyciu nazwy nadany w oknie dialogowym **Nowy projekt.** Na dysku ten projekt jest reprezentowany przez plik *njsproj* w folderze projektu.

   - Na najwyższym poziomie jest rozwiązanie, które domyślnie ma taką samą nazwę jak projekt. Rozwiązanie, reprezentowane przez plik *.sln* na dysku, jest kontenerem dla jednego lub więcej powiązanych projektów.

   - Węzeł npm pokazuje wszystkie zainstalowane pakiety npm. Można kliknąć prawym przyciskiem myszy węzeł npm, aby wyszukać i zainstalować pakiety npm za pomocą okna dialogowego.

1. Jeśli chcesz zainstalować pakiety npm lub polecenia Node.js z wiersza polecenia, kliknij prawym przyciskiem myszy węzeł projektu i wybierz polecenie **Otwórz wiersz polecenia tutaj**.

   ![Wiersz polecenia Node.js](../ide/media/quickstart-nodejs-command-prompt.png)

1. W pliku *server.js* w edytorze (lewe okienko) wybierz, `http.createServer` a następnie naciśnij klawisz **F12** lub wybierz polecenie Przejdź do **definicji** z menu kontekstu (kliknięcie prawym przyciskiem myszy). To polecenie prowadzi do definicji `createServer` funkcji w *index.d.ts*.

   ![Przejdź do menu kontekstowego Definicja](../ide/media/quickstart-nodejs-gotodefinition.png)

1. Wróciłem do *server.js*, a następnie umieścić kursor na końcu ciągu `res.end('Hello World\n');`w tym wierszu kodu, i zmodyfikować go tak, że wygląda tak:

    `res.end('Hello World\n' + res.connection.`

    W przypadku `connection.`wpisywać program IntelliSense udostępnia opcje automatycznego wypełniania wpisu kodu.

   ![Automatyczne uzupełnianie intellisense](../ide/media/quickstart-nodejs-intellisense.png)

1. Wybierz **localPort**, `);` a następnie wpisz, aby zakończyć instrukcję, tak aby wyglądała następująco:

    `res.end('Hello World\n' + res.connection.localPort);`

## <a name="run-the-application"></a>Uruchamianie aplikacji

1. Naciśnij **klawisze Ctrl**+**F5** (lub **Debugowanie > start bez debugowania),** aby uruchomić aplikację. Aplikacja zostanie otwarta w przeglądarce.

1. W oknie przeglądarki zobaczysz "Hello World" plus lokalny numer portu.

1. Zamknij przeglądarkę internetową.

Gratulujemy ukończenia tego przewodnika Szybki start, w którym rozpoczęto korzystanie z ide programu Visual Studio i node.js. Jeśli chcesz zagłębić się w jego możliwości, kontynuuj samouczek w sekcji **Samouczki** spisu treści.

## <a name="next-steps"></a>Następne kroki

> [!div class="nextstepaction"]
> [Wdrażanie aplikacji w usłudze aplikacji systemu Linux](../javascript/publish-nodejs-app-azure.md)

- [Samouczek dla Node.js i Express](../javascript/tutorial-nodejs.md)
- [Samouczek dla Node.js i React](../javascript/tutorial-nodejs-with-react-and-jsx.md)