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
ms.openlocfilehash: ac09fa17ea550df127660a56a04d315f8f1a788f
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55911172"
---
# <a name="quickstart-use-visual-studio-to-create-your-first-vuejs-app"></a>Szybki start: Utwórz swoją pierwszą aplikację Vue.js przy użyciu programu Visual Studio

W ramach tego wprowadzenia do programu Visual Studio zintegrowane środowisko programistyczne (IDE) 5 – 10 minut możesz utworzyć i uruchomić prostą aplikację sieci web Vue.js. Jeśli jeszcze nie zainstalowano programu Visual Studio 2017, przejdź do strony [program Visual Studio pobiera](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs) strony, aby zainstalować go za darmo.

> [!IMPORTANT]
> Ten artykuł wymaga szablonu Vue.js, która jest dostępna, począwszy od programu Visual Studio 2017 w wersji 15.8.

## <a name="create-a-project"></a>Tworzenie projektu

Najpierw utworzysz Vue.js projektu aplikacji sieci web.

1. Jeśli nie masz już zainstalowane środowisko uruchomieniowe Node.js, należy zainstalować wersję LTS z [Node.js](https://nodejs.org/en/download/) witryny sieci Web.

    Ogólnie rzecz biorąc program Visual Studio automatycznie wykrywa zainstalowane środowisko uruchomieniowe Node.js. Jeśli go nie wykryje zainstalowanego środowiska uruchomieniowego, można skonfigurować projekt, aby odwoływać się do zainstalowanego środowiska uruchomieniowego na stronie właściwości (po utworzeniu projektu, kliknij prawym przyciskiem myszy węzeł projektu i wybierz polecenie **właściwości**).

1. Otwórz program Visual Studio 2017.

1. Na pasku menu u góry wybierz **pliku** > **New** > **projektu**.

1. W **nowy projekt** okno dialogowe, w obszarze **JavaScript** > **Node.js** lub **TypeScript**  >   **Node.js**, wybierz **Podstawowa aplikacja sieci Web Vue.js**. Wprowadź nazwę projektu, a następnie kliknij przycisk **OK**.

     ![Szablon VUE.js](../javascript/media/vuejs-template.png)

    Program Visual Studio tworzy nowy projekt. Nowy projekt zostanie otwarty w oknie Eksploratora rozwiązań (w okienku po prawej stronie).

     Jeśli nie widzisz **podstawowa Vue.js aplikacja sieci Web** szablonu projektu, kliknij przycisk **Otwórz Instalator programu Visual Studio** łącze w okienku po lewej stronie **nowy projekt** okno dialogowe. Uruchamia Instalatora programu Visual Studio. Wybierz **programowania Node.js** obciążenia, wybierz **Modyfikuj**.

     ![Obciążenie node.js w Instalatorze programu VS](../ide/media/quickstart-nodejs-workload.png)

    Program Visual Studio tworzy i nowego rozwiązania i otwiera projekt.

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