---
title: 'Szybki Start: Tworzenie pierwszej aplikacji Vue.js'
description: W tym przewodniku szybki start utworzysz aplikację Vue.js w programie Visual Studio przy użyciu narzędzi Node.js Tools for Visual Studio.
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
ms.openlocfilehash: 882c3a148164ab88412a817abd72d0608fadf9b2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "81744974"
---
# <a name="quickstart-use-visual-studio-to-create-your-first-vuejs-app"></a>Szybki Start: Tworzenie pierwszej aplikacji Vue.js przy użyciu programu Visual Studio

W tym 5-10 minutowym wprowadzeniu do zintegrowanego środowiska programistycznego (IDE) programu Visual Studio utworzysz i uruchomisz prostą aplikację sieci Web Vue.js.

> [!IMPORTANT]
> Ten artykuł wymaga szablonu Vue.js, który jest dostępny w programie Visual Studio 2017 w wersji 15,8.

## <a name="prerequisites"></a>Wymagania wstępne

* Musisz mieć zainstalowany program Visual Studio i Node.js obciążenie programowaniem.

    ::: moniker range=">=vs-2019"
    Jeśli program Visual Studio 2019 nie został jeszcze zainstalowany, przejdź do strony [plików do pobrania programu Visual Studio](https://visualstudio.microsoft.com/downloads/),   Aby zainstalować ją bezpłatnie.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Jeśli program Visual Studio 2017 nie został jeszcze zainstalowany, przejdź do strony [plików do pobrania programu Visual Studio](https://visualstudio.microsoft.com/downloads/),   Aby zainstalować ją bezpłatnie.
    ::: moniker-end

    Jeśli musisz zainstalować obciążenie, ale masz już program Visual Studio, przejdź do pozycji **Narzędzia**  >  **Pobierz narzędzia i funkcje..**., co spowoduje otwarcie Instalator programu Visual Studio. Wybierz **Node.js obciążenie programowaniem** , a następnie wybierz **Modyfikuj**.

    ![Node.js obciążenie w Instalatorze programu VS](../ide/media/quickstart-nodejs-workload.png)

* Musisz mieć zainstalowane środowisko uruchomieniowe Node.js.

    Jeśli go nie zainstalowano, zalecamy zainstalowanie wersji LTS z witryny internetowej [Node.js](https://nodejs.org/en/download/) w celu uzyskania najlepszej zgodności z zewnętrznymi platformami i bibliotekami. Node.js jest oparta na architekturze 32-bitowej i 64-bitowej. Narzędzia Node.js w programie Visual Studio, zawarte w obciążeniu Node.js, obsługują obie wersje. Tylko jeden jest wymagany, a Instalator Node.js obsługuje tylko jeden instalowany w danym momencie.
    
    Ogólnie rzecz biorąc, program Visual Studio automatycznie wykrywa zainstalowane Node.js środowiska uruchomieniowego. Jeśli nie wykryje zainstalowanego środowiska uruchomieniowego, można skonfigurować projekt do odwoływania się do zainstalowanego środowiska uruchomieniowego na stronie właściwości (po utworzeniu projektu kliknij prawym przyciskiem myszy węzeł projektu, wybierz polecenie **Właściwości**, a następnie ustaw ** ścieżkęNode.exe**). Można użyć globalnej instalacji Node.js lub można określić ścieżkę do lokalnego interpretera w każdym z projektów Node.js. 

## <a name="create-a-project"></a>Tworzenie projektu

Najpierw utworzysz projekt aplikacji sieci Web Vue.js.

1. Jeśli nie masz już zainstalowanego środowiska uruchomieniowego Node.js, Zainstaluj wersję LTS z witryny [Node.js](https://nodejs.org/en/download/) .

    Aby uzyskać więcej informacji, zobacz Wymagania wstępne.

1. Otwórz program Visual Studio.

1. Tworzenie nowego projektu.

    ::: moniker range=">=vs-2019"
    Naciśnij klawisz **ESC** , aby zamknąć okno uruchamiania. **Naciśnij klawisze CTRL + Q** , aby otworzyć pole wyszukiwania, wpisz **podstawowe Vue.js**, a następnie wybierz pozycję **podstawowa aplikacja sieci Web Vue.js** (JavaScript lub TypeScript). W wyświetlonym oknie dialogowym wpisz nazwę **Basic-vuejs**, a następnie wybierz pozycję **Utwórz**.

    ![Szablon Vue.js](../javascript/media/vs-2019/vuejs-template.png)
    ::: moniker-end
    ::: moniker range="vs-2017"
    Na górnym pasku menu wybierz pozycję **plik**  >  **Nowy**  >  **projekt**. W lewym okienku okna dialogowego **Nowy projekt** rozwiń węzeł **JavaScript** lub **TypeScript**, a następnie wybierz **Node.js**. W środkowym okienku wybierz pozycję **podstawowa aplikacja sieci Web Vue.js**, wpisz nazwę **Basic-vuejs**, a następnie wybierz **przycisk OK**.

    ![Szablon Vue.js](../javascript/media/vuejs-template.png)
    ::: moniker-end
    Jeśli nie widzisz szablonu projektu **podstawowa Vue.js aplikacji sieci Web** , musisz dodaćNode.js obciążenie ** programowaniem** . Aby uzyskać szczegółowe instrukcje, zobacz [wymagania wstępne](#prerequisites).

    Program Visual Studio tworzy nowy projekt. Nowy projekt zostanie otwarty w Eksplorator rozwiązań (okienko po prawej).

1. Sprawdź okno dane wyjściowe (dolne okienko) na potrzeby postępu instalowania pakietów npm wymaganych dla aplikacji.

1. W Eksplorator rozwiązań otwórz węzeł **npm** i upewnij się, że wszystkie wymienione pakiety npm są zainstalowane.

    Jeśli brakuje któregoś z pakietów (ikona wykrzyknika), możesz kliknąć prawym przyciskiem myszy węzeł **npm** i wybrać polecenie **Zainstaluj brakujące pakiety npm**.

## <a name="explore-the-ide"></a>Eksplorowanie środowiska IDE

1. Zapoznaj się z **Eksplorator rozwiązań** w okienku po prawej stronie.

     ![Vue.js rozwiązanie](../javascript/media/vuejs-solution.png)

   - Wyróżnione czcionką pogrubioną jest projektem, przy użyciu nazwy podanych w oknie dialogowym **Nowy projekt** . Na dysku ten projekt jest reprezentowany przez. *njsproj* plik w folderze projektu.

   - Na najwyższym poziomie jest rozwiązaniem, które domyślnie ma taką samą nazwę jak projekt. Rozwiązanie reprezentowane przez. plik *sln* na dysku jest kontenerem dla co najmniej jednego powiązanego projektu.

   - W węźle **npm** są wyświetlane wszystkie zainstalowane pakiety npm. Możesz kliknąć prawym przyciskiem myszy węzeł npm, aby wyszukać i zainstalować pakiety npm przy użyciu okna dialogowego.

2. Jeśli chcesz zainstalować pakiety npm lub uruchamiać Node.js polecenia z wiersza polecenia, kliknij prawym przyciskiem myszy węzeł projektu, a następnie wybierz polecenie **Otwórz wiersz polecenia tutaj**.

## <a name="add-a-vue-file-to-the-project"></a>Dodawanie pliku. VUE do projektu

1. W Eksplorator rozwiązań kliknij prawym przyciskiem myszy dowolny folder, taki jak folder *src/Components* , a następnie wybierz polecenie **Dodaj**  >  **nowy element**.

1. Wybierz opcję **JavaScript Vue Single File Component** lub **Single Vue Component**, a następnie kliknij przycisk **Dodaj**.

    Program Visual Studio dodaje nowy plik do projektu.

## <a name="build-the-project"></a>Kompilowanie projektu

::: moniker range=">=vs-2019"
1. Następnie wybierz pozycję **Kompiluj** > **kompilację rozwiązania** , aby skompilować projekt.

1. Sprawdź okno **dane wyjściowe** , aby wyświetlić wyniki kompilacji, a następnie wybierz opcję **Kompiluj** z listy **Pokaż dane wyjściowe z** .
::: moniker-end
::: moniker range="vs-2017"
1. (Tylko projekt TypeScript) W programie Visual Studio wybierz kolejno opcje **Kompiluj** > **czyste rozwiązanie**.

1. Następnie wybierz pozycję **Kompiluj** > **kompilację rozwiązania** , aby skompilować projekt.

1. Sprawdź okno **dane wyjściowe** , aby wyświetlić wyniki kompilacji, a następnie wybierz opcję **Kompiluj** z listy **Pokaż dane wyjściowe z** .
::: moniker-end

Szablon projektu Vue.js JavaScript (oraz starsze wersje szablonu TypeScript) używają `build` skryptu npm przez skonfigurowanie zdarzenia po kompilacji. Jeśli chcesz zmodyfikować to ustawienie, Otwórz plik projektu (* \<projectname\> . njsproj*) z Eksploratora Windows i Znajdź ten wiersz kodu:

```xml
<PostBuildEvent>npm run build</PostBuildEvent>
```

## <a name="run-the-application"></a>Uruchamianie aplikacji

1. Naciśnij klawisz **Ctrl** + **F5** (lub **Debuguj > Uruchom bez debugowania**), aby uruchomić aplikację.

   W konsoli zostanie wyświetlony komunikat *Uruchamianie serwera deweloperskiego*.

   Następnie aplikacja zostanie otwarta w przeglądarce.
   
   Jeśli nie widzisz uruchomionej aplikacji, Odśwież stronę.

   ![Aplikacja Vue.js uruchomiona w przeglądarce](../javascript/media/vuejs-running-app.png)

1. Zamknij przeglądarkę internetową.

Gratulujemy zakończenia tego przewodnika Szybki Start! Mamy nadzieję, że uczysz się nieco z używania środowiska IDE programu Visual Studio z Vue.js. Jeśli chcesz lepiej podzielić się swoimi możliwościami, przejdź do samouczka w sekcji **samouczki** spisu treści.

## <a name="next-steps"></a>Następne kroki

- Zapoznaj się z artykułem [Vue.js](create-application-with-vuejs.md)
- Zapoznaj się z [samouczkiem dotyczącym Node.js i Express](tutorial-nodejs.md)
- [Wdrażanie aplikacji w systemie Linux App Service](../javascript/publish-nodejs-app-azure.md)