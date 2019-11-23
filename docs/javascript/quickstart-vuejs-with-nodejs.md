---
title: 'Szybki Start: Tworzenie pierwszej aplikacji Vue.js'
description: W tym przewodniku Szybki Start utworzysz aplikację Vue.js w programie Visual Studio przy użyciu narzędzia Node.js dla programu Visual Studio
ms.custom: ''
ms.date: 10/31/2019
ms.topic: quickstart
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jillfra
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: 5f7b877d825a573b935a9bf0f2c907ec2ce6f808
ms.sourcegitcommit: 2f64b3b231900018fceafb72b5a1c65140213a18
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/01/2019
ms.locfileid: "73428773"
---
# <a name="quickstart-use-visual-studio-to-create-your-first-vuejs-app"></a>Szybki Start: Używanie programu Visual Studio do utworzenia pierwszej aplikacji Vue.js

W ramach tego wprowadzenia do programu Visual Studio zintegrowane środowisko programistyczne (IDE) 5 – 10 minut możesz utworzyć i uruchomić prostą aplikację sieci web Vue.js.

> [!IMPORTANT]
> Ten artykuł wymaga szablonu Vue.js, która jest dostępna, począwszy od programu Visual Studio 2017 w wersji 15.8.

## <a name="prerequisites"></a>Wymagania wstępne

* Musisz mieć zainstalowany program Visual Studio i obciążenie programowaniem Node. js.

    ::: moniker range=">=vs-2019"
    Jeśli program Visual Studio 2019 nie został jeszcze zainstalowany, przejdź do strony [plików do pobrania programu Visual Studio](https://visualstudio.microsoft.com/downloads/) , aby zainstalować ją bezpłatnie.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Jeśli program Visual Studio 2017 nie został jeszcze zainstalowany, przejdź do strony [plików do pobrania programu Visual Studio](https://visualstudio.microsoft.com/downloads/) , aby zainstalować ją bezpłatnie.
    ::: moniker-end

    Jeśli musisz zainstalować obciążenie, ale masz już program Visual Studio, przejdź do pozycji **narzędzia** > **Pobierz narzędzia i funkcje..** ., co spowoduje otwarcie Instalator programu Visual Studio. Wybierz **programowania Node.js** obciążenia, wybierz **Modyfikuj**.

    ![Obciążenie node.js w Instalatorze programu VS](../ide/media/quickstart-nodejs-workload.png)

* Konieczne jest posiadanie zainstalowanego środowiska uruchomieniowego Node.js.

    Jeśli nie jest ona zainstalowana, zainstaluj wersję LTS z [Node.js](https://nodejs.org/en/download/) witryny sieci Web. Ogólnie rzecz biorąc program Visual Studio automatycznie wykrywa zainstalowane środowisko uruchomieniowe Node.js. Jeśli nie zostanie wykryta zainstalowanego środowiska uruchomieniowego, można skonfigurować projekt, aby odwoływać się do zainstalowanego środowiska uruchomieniowego na stronie właściwości (po utworzeniu projektu, kliknij prawym przyciskiem myszy węzeł projektu i wybierz polecenie **właściwości**).

## <a name="create-a-project"></a>Tworzenie projektu

Najpierw utworzysz Vue.js projektu aplikacji sieci web.

1. Jeśli nie masz już zainstalowane środowisko uruchomieniowe Node.js, należy zainstalować wersję LTS z [Node.js](https://nodejs.org/en/download/) witryny sieci Web.

    Ogólnie rzecz biorąc program Visual Studio automatycznie wykrywa zainstalowane środowisko uruchomieniowe Node.js. Jeśli nie wykryje zainstalowanego środowiska uruchomieniowego, można skonfigurować projekt do odwoływania się do zainstalowanego środowiska uruchomieniowego na stronie właściwości (po utworzeniu projektu kliknij prawym przyciskiem myszy węzeł projektu i wybierz polecenie **Właściwości**).

1. Otwórz program Visual Studio.

1. Utwórz nowy projekt.

    ::: moniker range=">=vs-2019"
    Naciśnij klawisz **ESC** , aby zamknąć okno uruchamiania. Wpisz **Ctrl + Q** , aby otworzyć pole wyszukiwania, wpisz **Basic Vue. js**, a następnie wybierz **podstawową aplikację sieci Web Vue. js** (JavaScript lub TypeScript). W wyświetlonym oknie dialogowym wpisz nazwę **Basic-vuejs**, a następnie wybierz pozycję **Utwórz**.

    ![Szablon VUE.js](../javascript/media/vs-2019/vuejs-template.png)
    ::: moniker-end
    ::: moniker range="vs-2017"
    Na pasku menu u góry wybierz **pliku** > **New** > **projektu**. W lewym okienku okna dialogowego **Nowy projekt** rozwiń węzeł **JavaScript** lub **TypeScript**, a następnie wybierz polecenie **Node. js**. W środkowym okienku wybierz **podstawową aplikację sieci Web Vue. js**, wpisz nazwę **Basic-vuejs**, a następnie wybierz **przycisk OK**.

    ![Szablon VUE.js](../javascript/media/vuejs-template.png)
    ::: moniker-end
    Jeśli nie widzisz szablonu projektu **podstawowe aplikacje sieci Web Vue. js** , musisz dodać obciążenie **programowania Node. js** . Aby uzyskać szczegółowe instrukcje, zobacz [wymagania wstępne](#prerequisites).

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

1. W Eksplorator rozwiązań kliknij prawym przyciskiem myszy dowolny folder, taki jak folder *src/Components* , a następnie wybierz polecenie **Dodaj** > **nowy element**.

1. Wybierz opcję **JavaScript Vue pojedynczy plik składnika** lub **TypeScript Vue pojedynczy plik składnika**, a następnie kliknij przycisk **Dodaj**.

    Visual Studio dodaje nowy plik do projektu.

## <a name="build-the-project"></a>Skompiluj projekt

1. (Tylko projekt TypeScript) W programie Visual Studio, wybierz **kompilacji** > **czyste rozwiązanie**.

    ::: moniker range=">=vs-2019"
    W szablonie TypeScript zawartym w programie Visual Studio 2019 Pomiń ten krok.
    ::: moniker-end

1. Następnie wybierz pozycję **kompilacji** > **Kompiluj rozwiązanie** do skompilowania projektu. Sprawdź okno **dane wyjściowe** , aby wyświetlić wyniki kompilacji, a następnie wybierz opcję **Kompiluj** z listy **Pokaż dane wyjściowe z** .

    Szablon projektu JavaScript Vue. js (oraz starsze wersje szablonu TypeScript) używają skryptu `build` npm przez skonfigurowanie zdarzenia po kompilacji. Jeśli chcesz zmodyfikować to ustawienie, otwórz plik projektu ( *\<projectname\>.njsproj*) z Eksploratora Windows i znajdź ten wiersz kodu:

    ```xml
    <PostBuildEvent>npm run build</PostBuildEvent>
    ```

## <a name="run-the-application"></a>Uruchamianie aplikacji

1. Naciśnij klawisz **Ctrl**+**F5** (lub **Debuguj > Uruchom bez debugowania**) do uruchamiania aplikacji.

   W konsoli zostanie wyświetlony komunikat *uruchamianie serwera wdrożeniowego*.

   Następnie aplikacja zostanie otwarta w przeglądarce.
   
   Jeśli nie widzisz uruchomionej aplikacji, Odśwież stronę.

   ![Aplikacja VUE.js działająca w przeglądarce](../javascript/media/vuejs-running-app.png)

1. Zamknij przeglądarkę sieci web.

Gratulujemy ukończenie tego przewodnika Szybki Start! Mamy nadzieję, że przedstawianymi nieco o korzystaniu z programu Visual Studio IDE z Vue.js. Jeśli chcesz lepiej podzielić się swoimi możliwościami, przejdź do samouczka w sekcji **samouczki** spisu treści.

## <a name="next-steps"></a>Następne kroki

- Zapoznaj się z artykułem [samouczek dotyczący Node.js lub Express](tutorial-nodejs.md)
- Zapoznaj się z artykułem [samouczku środowiska Node.js i React](tutorial-nodejs-with-react-and-jsx.md)
- [Wdrażanie aplikacji do usługi App Service w systemie Linux](../javascript/publish-nodejs-app-azure.md)