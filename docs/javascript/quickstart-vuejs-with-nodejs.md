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
ms.openlocfilehash: a1995353d00f9e48811f388e1d853c93850b85f4
ms.sourcegitcommit: 9eff8371b7a79a637ebb6850f775dd3eed343d8b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/03/2020
ms.locfileid: "78235109"
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

    Jeśli musisz zainstalować obciążenie, ale masz już program Visual Studio, przejdź do pozycji **narzędzia** > **Pobierz narzędzia i funkcje..** ., co spowoduje otwarcie Instalator programu Visual Studio. Wybierz obciążenie **środowiska Node. js** , a następnie wybierz polecenie **Modyfikuj**.

    ![Obciążenie node.js w Instalatorze programu VS](../ide/media/quickstart-nodejs-workload.png)

* Konieczne jest posiadanie zainstalowanego środowiska uruchomieniowego Node.js.

    Jeśli go nie zainstalowano, zalecamy zainstalowanie wersji LTS z poziomu witryny sieci Web [Node. js](https://nodejs.org/en/download/) w celu uzyskania najlepszej zgodności z zewnętrznymi platformami i bibliotekami. Architektura Node. js została skompilowana dla architektur 32-bitowych i 64-bitowych. Narzędzia Node. js w programie Visual Studio, zawarte w obciążeniu Node. js, obsługują obie wersje. Tylko jeden jest wymagany, a Instalator środowiska Node. js obsługuje tylko jeden instalowany w danym momencie.
    
    Ogólnie rzecz biorąc program Visual Studio automatycznie wykrywa zainstalowane środowisko uruchomieniowe Node.js. Jeśli nie wykryje zainstalowanego środowiska uruchomieniowego, można skonfigurować projekt do odwoływania się do zainstalowanego środowiska uruchomieniowego na stronie właściwości (po utworzeniu projektu kliknij prawym przyciskiem myszy węzeł projektu, wybierz polecenie **Właściwości**, a następnie ustaw **ścieżkę pliku Node. exe**). Można użyć globalnej instalacji środowiska Node. js lub określić ścieżkę do lokalnego interpretera w każdym z projektów Node. js. 

## <a name="create-a-project"></a>Tworzenie projektu

Najpierw utworzysz Vue.js projektu aplikacji sieci web.

1. Jeśli nie masz już zainstalowanego środowiska uruchomieniowego Node. js, Zainstaluj wersję LTS z witryny sieci Web [Node. js](https://nodejs.org/en/download/) .

    Aby uzyskać więcej informacji, zobacz Wymagania wstępne.

1. Otwórz program Visual Studio.

1. Tworzenie nowego projektu.

    ::: moniker range=">=vs-2019"
    Naciśnij klawisz **ESC** , aby zamknąć okno uruchamiania. Wpisz **Ctrl + Q** , aby otworzyć pole wyszukiwania, wpisz **Basic Vue. js**, a następnie wybierz **podstawową aplikację sieci Web Vue. js** (JavaScript lub TypeScript). W wyświetlonym oknie dialogowym wpisz nazwę **Basic-vuejs**, a następnie wybierz pozycję **Utwórz**.

    ![Szablon VUE.js](../javascript/media/vs-2019/vuejs-template.png)
    ::: moniker-end
    ::: moniker range="vs-2017"
    Na górnym pasku menu wybierz kolejno pozycje **plik** > **Nowy** > **projekt**. W lewym okienku okna dialogowego **Nowy projekt** rozwiń węzeł **JavaScript** lub **TypeScript**, a następnie wybierz polecenie **Node. js**. W środkowym okienku wybierz **podstawową aplikację sieci Web Vue. js**, wpisz nazwę **Basic-vuejs**, a następnie wybierz **przycisk OK**.

    ![Szablon VUE.js](../javascript/media/vuejs-template.png)
    ::: moniker-end
    Jeśli nie widzisz szablonu projektu **podstawowe aplikacje sieci Web Vue. js** , musisz dodać obciążenie **programowania Node. js** . Aby uzyskać szczegółowe instrukcje, zobacz [wymagania wstępne](#prerequisites).

    Program Visual Studio tworzy nowy projekt. Nowy projekt zostanie otwarty w oknie Eksploratora rozwiązań (w okienku po prawej stronie).

1. Sprawdź, czy w oknie danych wyjściowych (dolne okienko) postęp na temat instalowania pakietów npm wymaganą dla aplikacji.

1. W Eksplorator rozwiązań otwórz węzeł **npm** i upewnij się, że wszystkie wymienione pakiety npm są zainstalowane.

    Jeśli brakuje któregoś z pakietów (ikona wykrzyknika), możesz kliknąć prawym przyciskiem myszy węzeł **npm** i wybrać polecenie **Zainstaluj brakujące pakiety npm**.

## <a name="explore-the-ide"></a>Eksploruj IDE

1. Zapoznaj się z **Eksplorator rozwiązań** w okienku po prawej stronie.

     ![Rozwiązanie VUE.js](../javascript/media/vuejs-solution.png)

   - Wyróżnione czcionką pogrubioną jest projektem, przy użyciu nazwy podanych w oknie dialogowym **Nowy projekt** . Na dysku ten projekt jest reprezentowany przez. *njsproj* plik w folderze projektu.

   - Na najwyższym poziomie to rozwiązanie, która domyślnie ma taką samą nazwę jak projektu. Rozwiązanie reprezentowane przez. plik *sln* na dysku jest kontenerem dla co najmniej jednego powiązanego projektu.

   - W węźle **npm** są wyświetlane wszystkie zainstalowane pakiety npm. Możesz kliknąć prawym przyciskiem myszy węzeł npm, aby wyszukać i zainstalować pakiety npm przy użyciu okna dialogowego.

2. Jeśli chcesz zainstalować pakiety npm lub uruchomić polecenia Node. js z wiersza polecenia, kliknij prawym przyciskiem myszy węzeł projektu, a następnie wybierz polecenie **Otwórz wiersz polecenia tutaj**.

## <a name="add-a-vue-file-to-the-project"></a>Dodaj plik .vue do projektu

1. W Eksplorator rozwiązań kliknij prawym przyciskiem myszy dowolny folder, taki jak folder *src/Components* , a następnie wybierz polecenie **Dodaj** > **nowy element**.

1. Wybierz opcję **JavaScript Vue Single File Component** lub **Single Vue Component**, a następnie kliknij przycisk **Dodaj**.

    Visual Studio dodaje nowy plik do projektu.

## <a name="build-the-project"></a>Kompilowanie projektu

1. (Tylko projekt TypeScript) W programie Visual Studio wybierz kolejno opcje **kompiluj** > **Wyczyść rozwiązanie**.

    ::: moniker range=">=vs-2019"
    W szablonie TypeScript zawartym w programie Visual Studio 2019 Pomiń ten krok.
    ::: moniker-end

1. Następnie wybierz kolejno opcje **kompiluj** > **Kompiluj rozwiązanie** , aby skompilować projekt. Sprawdź okno **dane wyjściowe** , aby wyświetlić wyniki kompilacji, a następnie wybierz opcję **Kompiluj** z listy **Pokaż dane wyjściowe z** .

    Szablon projektu JavaScript Vue. js (oraz starsze wersje szablonu TypeScript) używają skryptu `build` npm przez skonfigurowanie zdarzenia po kompilacji. Jeśli chcesz zmodyfikować to ustawienie, Otwórz plik projektu ( *\<projectname\>. njsproj*) w Eksploratorze Windows i Znajdź ten wiersz kodu:

    ```xml
    <PostBuildEvent>npm run build</PostBuildEvent>
    ```

## <a name="run-the-application"></a>Uruchamianie aplikacji

1. Naciśnij klawisz **Ctrl**+**F5** (lub **Debuguj > Uruchom bez debugowania**), aby uruchomić aplikację.

   W konsoli zostanie wyświetlony komunikat *Uruchamianie serwera deweloperskiego*.

   Następnie aplikacja zostanie otwarta w przeglądarce.
   
   Jeśli nie widzisz uruchomionej aplikacji, Odśwież stronę.

   ![Aplikacja VUE.js działająca w przeglądarce](../javascript/media/vuejs-running-app.png)

1. Zamknij przeglądarkę sieci Web.

Gratulujemy ukończenie tego przewodnika Szybki Start! Mamy nadzieję, że przedstawianymi nieco o korzystaniu z programu Visual Studio IDE z Vue.js. Jeśli chcesz lepiej podzielić się swoimi możliwościami, przejdź do samouczka w sekcji **samouczki** spisu treści.

## <a name="next-steps"></a>Następne kroki

- Przejdź do [samouczka dotyczącego środowiska Node. js i języka Express](tutorial-nodejs.md)
- Przejdź do [samouczka dotyczącego środowiska Node. js i reaguj](tutorial-nodejs-with-react-and-jsx.md)
- [Wdrażanie aplikacji w systemie Linux App Service](../javascript/publish-nodejs-app-azure.md)