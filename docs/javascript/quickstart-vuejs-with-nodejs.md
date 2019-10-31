---
title: 'Szybki Start: Tworzenie pierwszej aplikacji Vue. js'
description: W tym przewodniku szybki start utworzysz aplikację Vue. js w programie Visual Studio przy użyciu Node.js Tools for Visual Studio
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
ms.openlocfilehash: ba1f403cd722b4d3dd1860c4a8b135c87b80bb4d
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2019
ms.locfileid: "73189483"
---
# <a name="quickstart-use-visual-studio-to-create-your-first-vuejs-app"></a>Szybki Start: Tworzenie pierwszej aplikacji Vue. js za pomocą programu Visual Studio

W tym 5-10 minutowym wprowadzeniu do zintegrowanego środowiska programistycznego (IDE) programu Visual Studio utworzysz i uruchomisz prostą aplikację sieci Web Vue. js.

> [!IMPORTANT]
> Ten artykuł wymaga szablonu Vue. js, który jest dostępny w programie Visual Studio 2017 w wersji 15,8.

## <a name="prerequisites"></a>Wymagania wstępne

* Musisz mieć zainstalowany program Visual Studio i obciążenie programowaniem Node. js.

    ::: moniker range=">=vs-2019"
    Jeśli program Visual Studio 2019 nie został jeszcze zainstalowany, przejdź do strony [pobierania programu Visual studio](https://visualstudio.microsoft.com/downloads/)  page, aby zainstalować go bezpłatnie.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Jeśli program Visual Studio 2017 nie został jeszcze zainstalowany, przejdź do strony [pobierania programu Visual studio](https://visualstudio.microsoft.com/downloads/)  page, aby zainstalować go bezpłatnie.
    ::: moniker-end

    Jeśli musisz zainstalować obciążenie, ale masz już program Visual Studio, przejdź do pozycji **narzędzia**  > **Pobierz narzędzia i funkcje..** ., co spowoduje otwarcie Instalator programu Visual Studio. Wybierz obciążenie **środowiska Node. js** , a następnie wybierz polecenie **Modyfikuj**.

    ![Obciążenie środowiska Node. js w Instalatorze programu VS](../ide/media/quickstart-nodejs-workload.png)

* Musisz mieć zainstalowane środowisko uruchomieniowe Node. js.

    Jeśli go nie zainstalowano, Zainstaluj wersję LTS z witryny sieci Web [Node. js](https://nodejs.org/en/download/) . Ogólnie rzecz biorąc, program Visual Studio automatycznie wykrywa zainstalowane środowisko uruchomieniowe Node. js. Jeśli nie wykryje zainstalowanego środowiska uruchomieniowego, można skonfigurować projekt do odwoływania się do zainstalowanego środowiska uruchomieniowego na stronie właściwości (po utworzeniu projektu kliknij prawym przyciskiem myszy węzeł projektu i wybierz polecenie **Właściwości**).

## <a name="create-a-project"></a>Tworzenie projektu

Najpierw utworzysz projekt aplikacji sieci Web Vue. js.

1. Jeśli nie masz już zainstalowanego środowiska uruchomieniowego Node. js, Zainstaluj wersję LTS z witryny sieci Web [Node. js](https://nodejs.org/en/download/) .

    Ogólnie rzecz biorąc, program Visual Studio automatycznie wykrywa zainstalowane środowisko uruchomieniowe Node. js. Jeśli nie wykryje zainstalowanego środowiska uruchomieniowego, można skonfigurować projekt do odwoływania się do zainstalowanego środowiska uruchomieniowego na stronie właściwości (po utworzeniu projektu kliknij prawym przyciskiem myszy węzeł projektu i wybierz polecenie **Właściwości**).

1. Otwórz program Visual Studio.

1. Utwórz nowy projekt.

    ::: moniker range=">=vs-2019"
    Naciśnij klawisz **ESC** , aby zamknąć okno uruchamiania. Wpisz **Ctrl + Q** , aby otworzyć pole wyszukiwania, wpisz **Basic Vue. js**, a następnie wybierz **podstawową aplikację sieci Web Vue. js** (JavaScript lub TypeScript). W wyświetlonym oknie dialogowym wpisz nazwę **Basic-vuejs**, a następnie wybierz pozycję **Utwórz**.

    ![Szablon Vue. js](../javascript/media/vs-2019/vuejs-template.png)
    ::: moniker-end
    ::: moniker range="vs-2017"
    Na górnym pasku menu wybierz kolejno pozycje **plik**  > **Nowy**  > **projekt**. W lewym okienku okna dialogowego **Nowy projekt** rozwiń węzeł **JavaScript** lub **TypeScript**, a następnie wybierz polecenie **Node. js**. W środkowym okienku wybierz **podstawową aplikację sieci Web Vue. js**, wpisz nazwę **Basic-vuejs**, a następnie wybierz **przycisk OK**.

    ![Szablon Vue. js](../javascript/media/vuejs-template.png)
    ::: moniker-end
    Jeśli nie widzisz szablonu projektu **podstawowe aplikacje sieci Web Vue. js** , musisz dodać obciążenie **programowania Node. js** . Aby uzyskać szczegółowe instrukcje, zobacz [wymagania wstępne](#prerequisites).

    Program Visual Studio tworzy nowy projekt. Nowy projekt zostanie otwarty w Eksplorator rozwiązań (okienko po prawej).

1. Sprawdź okno dane wyjściowe (dolne okienko) na potrzeby postępu instalowania pakietów npm wymaganych dla aplikacji.

1. W Eksplorator rozwiązań otwórz węzeł **npm** i upewnij się, że wszystkie wymienione pakiety npm są zainstalowane.

    Jeśli brakuje któregoś z pakietów (ikona wykrzyknika), możesz kliknąć prawym przyciskiem myszy węzeł **npm** i wybrać polecenie **Zainstaluj brakujące pakiety npm**.

## <a name="explore-the-ide"></a>Eksplorowanie środowiska IDE

1. Zapoznaj się z **Eksplorator rozwiązań** w okienku po prawej stronie.

     ![Rozwiązanie Vue. js](../javascript/media/vuejs-solution.png)

   - Wyróżnione czcionką pogrubioną jest projektem, przy użyciu nazwy podanych w oknie dialogowym **Nowy projekt** . Na dysku ten projekt jest reprezentowany przez. *njsproj* plik w folderze projektu.

   - Na najwyższym poziomie jest rozwiązaniem, które domyślnie ma taką samą nazwę jak projekt. Rozwiązanie reprezentowane przez. plik *sln* na dysku jest kontenerem dla co najmniej jednego powiązanego projektu.

   - W węźle **npm** są wyświetlane wszystkie zainstalowane pakiety npm. Możesz kliknąć prawym przyciskiem myszy węzeł npm, aby wyszukać i zainstalować pakiety npm przy użyciu okna dialogowego.

2. Jeśli chcesz zainstalować pakiety npm lub uruchomić polecenia Node. js z wiersza polecenia, kliknij prawym przyciskiem myszy węzeł projektu, a następnie wybierz polecenie **Otwórz wiersz polecenia tutaj**.

## <a name="add-a-vue-file-to-the-project"></a>Dodawanie pliku. VUE do projektu

1. W Eksplorator rozwiązań kliknij prawym przyciskiem myszy dowolny folder, taki jak folder *src/Components* , a następnie wybierz polecenie **Dodaj** > **nowy element**.

1. Wybierz opcję **JavaScript Vue Single File Component** lub **Single Vue Component**, a następnie kliknij przycisk **Dodaj**.

    Program Visual Studio dodaje nowy plik do projektu.

## <a name="build-the-project"></a>Kompilowanie projektu

1. (Tylko projekt TypeScript) W programie Visual Studio wybierz kolejno opcje **kompiluj** > **Wyczyść rozwiązanie**.

1. Następnie wybierz kolejno opcje **kompiluj** > **Kompiluj rozwiązanie** , aby skompilować projekt. Sprawdź okno **dane wyjściowe** , aby wyświetlić wyniki kompilacji, a następnie wybierz opcję **Kompiluj** z listy **Pokaż dane wyjściowe z** .

    Szablon projektu Vue. js używa skryptu `build` npm przez skonfigurowanie zdarzenia po kompilacji. Jeśli chcesz zmodyfikować to ustawienie, Otwórz plik projektu ( *\<projectname\>. njsproj*) w Eksploratorze Windows i Znajdź ten wiersz kodu:

    ```xml
    <PostBuildEvent>npm run build</PostBuildEvent>
    ```

## <a name="run-the-application"></a>Uruchom aplikację

1. Naciśnij klawisz **Ctrl**+**F5** (lub **Debuguj > Uruchom bez debugowania**), aby uruchomić aplikację.

   W konsoli zostanie wyświetlony komunikat *Uruchamianie serwera deweloperskiego*.

   Następnie aplikacja zostanie otwarta w przeglądarce.

   ![Aplikacja Vue. js uruchomiona w przeglądarce](../javascript/media/vuejs-running-app.png)

1. Zamknij przeglądarkę sieci Web.

Gratulujemy zakończenia tego przewodnika Szybki Start! Mamy nadzieję, że uczysz się nieco z używania środowiska IDE programu Visual Studio z Vue. js. Jeśli chcesz lepiej podzielić się swoimi możliwościami, przejdź do samouczka w sekcji **samouczki** spisu treści.

## <a name="next-steps"></a>Następne kroki

- Przejdź do [samouczka dotyczącego środowiska Node. js i języka Express](tutorial-nodejs.md)
- Przejdź do [samouczka dotyczącego środowiska Node. js i reaguj](tutorial-nodejs-with-react-and-jsx.md)
- [Wdrażanie aplikacji w systemie Linux App Service](../javascript/publish-nodejs-app-azure.md)