---
title: 'Szybki start: Utwórz swoją pierwszą aplikację Vue.js'
description: W tym przewodniku Szybki Start utworzysz aplikację Vue.js w programie Visual Studio przy użyciu narzędzia Node.js dla programu Visual Studio
ms.custom: seodec18
ms.date: 09/24/2018
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
ms.openlocfilehash: 869e60bf736f792255d36d83c9d9b06d20e67f02
ms.sourcegitcommit: 4ffb7be5384ad566ce46538032bf8561754c61a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2019
ms.locfileid: "58069596"
---
# <a name="quickstart-use-visual-studio-to-create-your-first-vuejs-app"></a>Szybki start: Utwórz swoją pierwszą aplikację Vue.js przy użyciu programu Visual Studio

W ramach tego wprowadzenia do programu Visual Studio zintegrowane środowisko programistyczne (IDE) 5 – 10 minut możesz utworzyć i uruchomić prostą aplikację sieci web Vue.js.

> [!IMPORTANT]
> Ten artykuł wymaga szablonu Vue.js, która jest dostępna, począwszy od programu Visual Studio 2017 w wersji 15.8.

## <a name="prerequisites"></a>Wymagania wstępne

* Musisz mieć zainstalowany program Visual Studio i obciążenie programowania Node.js.

    ::: moniker range=">=vs-2019"
    Jeśli jeszcze nie zainstalowano programu Visual Studio 2019 r, przejdź do strony [program Visual Studio pobiera](https://visualstudio.microsoft.com/downloads/) strony, aby zainstalować go za darmo.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Jeśli jeszcze nie zainstalowano programu Visual Studio 2017, przejdź do strony [program Visual Studio pobiera](https://visualstudio.microsoft.com/downloads/) strony, aby zainstalować go za darmo.
    ::: moniker-end

    Jeśli musisz zainstalować obciążenie, ale już program Visual Studio, przejdź do strony **narzędzia** > **Pobierz narzędzia i funkcje...** , która otwiera Instalatora programu Visual Studio. Wybierz **programowania Node.js** obciążenia, wybierz **Modyfikuj**.

    ![Obciążenie node.js w Instalatorze programu VS](../ide/media/quickstart-nodejs-workload.png)

* Konieczne jest posiadanie zainstalowanego środowiska uruchomieniowego Node.js.

    Jeśli nie jest ona zainstalowana, zainstaluj wersję LTS z [Node.js](https://nodejs.org/en/download/) witryny sieci Web. Ogólnie rzecz biorąc program Visual Studio automatycznie wykrywa zainstalowane środowisko uruchomieniowe Node.js. Jeśli nie zostanie wykryta zainstalowanego środowiska uruchomieniowego, można skonfigurować projekt, aby odwoływać się do zainstalowanego środowiska uruchomieniowego na stronie właściwości (po utworzeniu projektu, kliknij prawym przyciskiem myszy węzeł projektu i wybierz polecenie **właściwości**).

## <a name="create-a-project"></a>Tworzenie projektu

Najpierw utworzysz Vue.js projektu aplikacji sieci web.

1. Jeśli nie masz już zainstalowane środowisko uruchomieniowe Node.js, należy zainstalować wersję LTS z [Node.js](https://nodejs.org/en/download/) witryny sieci Web.

    Ogólnie rzecz biorąc program Visual Studio automatycznie wykrywa zainstalowane środowisko uruchomieniowe Node.js. Jeśli go nie wykryje zainstalowanego środowiska uruchomieniowego, można skonfigurować projekt, aby odwoływać się do zainstalowanego środowiska uruchomieniowego na stronie właściwości (po utworzeniu projektu, kliknij prawym przyciskiem myszy węzeł projektu i wybierz polecenie **właściwości**).

1. Otwórz program Visual Studio.

1. Na pasku menu u góry wybierz **pliku** > **New** > **projektu**.

1. Utwórz nowy projekt.

    ::: moniker range=">=vs-2019"
    W **Utwórz nowy projekt** okno dialogowe, typ **javascript** lub **typescript** w polu wyszukiwania, aby filtrować wyniki, a następnie wybierz **podstawowe Vue.js sieci Web Aplikacja**, a następnie wybierz **OK**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    W **nowy projekt** rozwiń w lewym okienku w oknie dialogowym **JavaScript**, następnie wybierz **Node.js**. W środkowym okienku wybierz **podstawowa Vue.js aplikacja sieci Web**, następnie wybierz **OK**.
    ::: moniker-end
    Jeśli nie widzisz **podstawowa Vue.js aplikacja sieci Web** szablonu projektu należy dodać **programowania Node.js** obciążenia. Aby uzyskać szczegółowe instrukcje, zobacz [wymagania wstępne](#prerequisites).

    ![Szablon VUE.js](../javascript/media/vuejs-template.png)

    Program Visual Studio tworzy nowy projekt. Nowy projekt zostanie otwarty w oknie Eksploratora rozwiązań (w okienku po prawej stronie).

1. Sprawdź, czy w oknie danych wyjściowych (dolne okienko) postęp na temat instalowania pakietów npm wymaganą dla aplikacji.

1. W Eksploratorze rozwiązań Otwórz **npm** węzła i upewnij się, że wszystkie pakiety npm wymienione są zainstalowane.

    Jeśli wszystkie pakiety brakuje (ikona wykrzyknika), możesz kliknąć prawym przyciskiem myszy **npm** węzeł i wybierz polecenie **Zainstaluj brakujące pakiety npm**.

## <a name="explore-the-ide"></a>Eksploruj IDE

1. Przyjrzyj się **Eksploratora rozwiązań** w okienku po prawej stronie.

     ![Rozwiązanie VUE.js](../javascript/media/vuejs-solution.png)

   - Wyróżnione czcionką pogrubioną jest projektu, przy użyciu nazwę nadaną w **nowy projekt** okno dialogowe. Na dysku, ten projekt jest reprezentowany przez. *njsproj* pliku w folderze projektu.

   - Na najwyższym poziomie to rozwiązanie, która domyślnie ma taką samą nazwę jak projektu. To rozwiązanie, reprezentowane przez. *sln* plików na dysku, to kontener dla jednego lub kilku powiązanych projektów.

   - **Npm** węzeł zawiera wszystkie pakiety npm zainstalowane. Możesz kliknąć prawym przyciskiem myszy węzeł npm, aby wyszukać i zainstalować pakiety npm przy użyciu okna dialogowego.

2. Jeśli chcesz zainstalować pakiety npm lub Uruchom polecenia Node.js z poziomu wiersza polecenia, kliknij prawym przyciskiem myszy węzeł projektu i wybierz **Otwórz wiersz polecenia w tym miejscu**.

## <a name="add-a-vue-file-to-the-project"></a>Dodaj plik .vue do projektu

1. W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy dowolny folder takich jak *src/components* folder, a następnie wybierz **Dodaj** > **nowy element**.

1. Wybierz opcję **JavaScript Vue pojedynczy plik składnika** lub **TypeScript Vue pojedynczy plik składnika**, a następnie kliknij przycisk **Dodaj**.

    Visual Studio dodaje nowy plik do projektu.

## <a name="build-the-project"></a>Skompiluj projekt

1. (Tylko projekt TypeScript) W programie Visual Studio, wybierz **kompilacji** > **czyste rozwiązanie**.

1. Następnie wybierz pozycję **kompilacji** > **Kompiluj rozwiązanie** do skompilowania projektu. Sprawdź **dane wyjściowe** okno, aby wyświetlić wyniki kompilacji, a następnie wybierz **kompilacji** z **Pokaż dane wyjściowe z** listy.

    Szablon projektu Vue.js używa `build` zdarzenie kompilacji npm skryptu, konfigurując wpis. Jeśli chcesz zmodyfikować to ustawienie, otwórz plik projektu (*\<projectname\>.njsproj*) z Eksploratora Windows i znajdź ten wiersz kodu:

    ```xml
    <PostBuildEvent>npm run build</PostBuildEvent>
    ```

## <a name="run-the-application"></a>Uruchamianie aplikacji

1. Naciśnij klawisz **Ctrl**+**F5** (lub **Debuguj > Uruchom bez debugowania**) do uruchamiania aplikacji.

   W konsoli zostanie wyświetlony komunikat *uruchamianie serwera wdrożeniowego*.

   Następnie aplikacja zostanie otwarta w przeglądarce.

   ![Aplikacja VUE.js działająca w przeglądarce](../javascript/media/vuejs-running-app.png)

1. Zamknij przeglądarkę sieci web.

Gratulujemy ukończenie tego przewodnika Szybki Start! Mamy nadzieję, że przedstawianymi nieco o korzystaniu z programu Visual Studio IDE z Vue.js. Jeśli chcesz delve głębiej do jego możliwości, kontynuować samouczek z **samouczki** części spisu treści.

## <a name="next-steps"></a>Następne kroki

- Zapoznaj się z artykułem [samouczek dotyczący Node.js lub Express](../nodejs/tutorial-nodejs.md)
- Zapoznaj się z artykułem [samouczku środowiska Node.js i React](/visualstudio/javascript/tutorial-nodejs-with-react-and-jsx)
- [Wdrażanie aplikacji do usługi App Service w systemie Linux](../javascript/publish-nodejs-app-azure.md)