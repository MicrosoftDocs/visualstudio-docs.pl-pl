---
title: 'Szybki start: tworzenie pierwszej aplikacji Vue.js'
description: W tym przewodniku Szybki start utworzysz aplikację Vue.js w programie Visual Studio przy użyciu narzędzia Node.js dla programu Visual Studio
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
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2020
ms.locfileid: "78235109"
---
# <a name="quickstart-use-visual-studio-to-create-your-first-vuejs-app"></a>Szybki start: tworzenie pierwszej aplikacji Vue.js za pomocą programu Visual Studio

W tym 5-10 minut wprowadzenie do środowiska programistycznego zintegrowanego programu Visual Studio (IDE), utworzysz i uruchomisz prostą aplikację sieci web Vue.js.

> [!IMPORTANT]
> Ten artykuł wymaga szablonu Vue.js, który jest dostępny od programu Visual Studio 2017 w wersji 15.8.

## <a name="prerequisites"></a>Wymagania wstępne

* Musi być zainstalowany program Visual Studio i obciążenie deweloperskie node.js.

    ::: moniker range=">=vs-2019"
    Jeśli program Visual Studio 2019 nie został jeszcze zainstalowany, przejdź do strony pobierania programu Visual [Studio,](https://visualstudio.microsoft.com/downloads/)aby zainstalować ją bezpłatnie.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Jeśli program Visual Studio 2017 nie został jeszcze zainstalowany, przejdź do strony pobierania programu Visual [Studio,](https://visualstudio.microsoft.com/downloads/)aby zainstalować ją bezpłatnie.
    ::: moniker-end

    Jeśli chcesz zainstalować obciążenie, ale masz już program Visual Studio, przejdź do **narzędzia** > **Pobierz narzędzia i funkcje...**, który otwiera Instalator programu Visual Studio. Wybierz obciążenie **deweloperne node.js,** a następnie wybierz pozycję **Modyfikuj**.

    ![Obciążenie node.js w instalatorze usługi VS](../ide/media/quickstart-nodejs-workload.png)

* Musi być zainstalowany środowisko uruchomieniowe Node.js.

    Jeśli nie masz go zainstalowanego, zaleca się zainstalowanie wersji LTS z witryny [node.js](https://nodejs.org/en/download/) w celu uzyskania najlepszej zgodności z zewnętrznymi strukturami i bibliotekami. Node.js jest przeznaczony dla architektur 32-bitowych i 64-bitowych. Narzędzia Node.js w programie Visual Studio, uwzględnione w obciążeniu Node.js, obsługują obie wersje. Wymagany jest tylko jeden, a instalator Node.js obsługuje tylko jeden instalowany jednocześnie.
    
    Ogólnie rzecz biorąc program Visual Studio automatycznie wykrywa zainstalowane środowisko uruchomieniowe Node.js. Jeśli nie wykryje zainstalowanego środowiska uruchomieniowego, można skonfigurować projekt tak, aby odwoływał się do zainstalowanego środowiska uruchomieniowego na stronie właściwości (po utworzeniu projektu kliknij prawym przyciskiem myszy węzeł projektu, wybierz polecenie **Właściwości**i ustaw **ścieżkę Node.exe**). Można użyć instalacji globalnej node.js lub można określić ścieżkę do lokalnego interpretera w każdym z projektów Node.js. 

## <a name="create-a-project"></a>Tworzenie projektu

Najpierw utworzysz projekt aplikacji sieci web Vue.js.

1. Jeśli nie masz już zainstalowanego środowiska uruchomieniowego Node.js, zainstaluj wersję LTS z [witryny node.js.](https://nodejs.org/en/download/)

    Aby uzyskać więcej informacji, zobacz wymagania wstępne.

1. Otwórz program Visual Studio.

1. Tworzenie nowego projektu.

    ::: moniker range=">=vs-2019"
    Naciśnij **klawisz Esc,** aby zamknąć okno początkowe. Wpisz **Ctrl + Q,** aby otworzyć pole wyszukiwania, wpisz **Basic Vue.js**, a następnie wybierz **podstawową aplikację sieci Web Vue.js** (JavaScript lub TypeScript). W wyświetlonym oknie dialogowym wpisz nazwę **basic-vuejs**, a następnie wybierz polecenie **Utwórz**.

    ![Szablon Vue.js](../javascript/media/vs-2019/vuejs-template.png)
    ::: moniker-end
    ::: moniker range="vs-2017"
    Na górnym pasku menu wybierz pozycję **Plik** > **nowego** > **projektu**. W lewym okienku okna dialogowego **Nowy projekt** rozwiń węzeł **JavaScript** lub **TypeScript**, a następnie wybierz polecenie **Node.js**. W środkowym okienku wybierz pozycję **Basic Vue.js Web application**, wpisz nazwę **basic-vuejs**, a następnie wybierz przycisk **OK**.

    ![Szablon Vue.js](../javascript/media/vuejs-template.png)
    ::: moniker-end
    Jeśli nie widzisz szablonu projektu **aplikacji sieci Web Basic Vue.js,** należy dodać obciążenie **deweloperne node.js.** Aby uzyskać szczegółowe instrukcje, zobacz [Wymagania wstępne](#prerequisites).

    Visual Studio tworzy nowy projekt. Nowy projekt zostanie otwarty w Eksploratorze rozwiązań (prawe okienko).

1. Sprawdź okno Dane wyjściowe (dolne okienko), aby uzyskać postęp w instalacji pakietów npm wymaganych dla aplikacji.

1. W Eksploratorze rozwiązań otwórz węzeł **npm** i upewnij się, że wszystkie wymienione pakiety npm są zainstalowane.

    Jeśli brakuje pakietów (ikona wykrzyknika), możesz kliknąć prawym przyciskiem myszy węzeł **npm** i wybrać polecenie **Zainstaluj brakujące pakiety npm**.

## <a name="explore-the-ide"></a>Poznaj IDE

1. Zapoznaj się z **Eksploratorem rozwiązań** w prawym okienku.

     ![Rozwiązanie Vue.js](../javascript/media/vuejs-solution.png)

   - Wyróżniony pogrubioną czcionką jest projekt, przy użyciu nazwy nadany w oknie dialogowym **Nowy projekt.** Na dysku ten projekt jest reprezentowany przez plik . *njsproj* w folderze projektu.

   - Na najwyższym poziomie jest rozwiązanie, które domyślnie ma taką samą nazwę jak projekt. Rozwiązanie, reprezentowane przez . *sln* jest kontenerem dla jednego lub więcej powiązanych projektów.

   - Węzeł **npm** pokazuje wszystkie zainstalowane pakiety npm. Można kliknąć prawym przyciskiem myszy węzeł npm, aby wyszukać i zainstalować pakiety npm za pomocą okna dialogowego.

2. Jeśli chcesz zainstalować pakiety npm lub uruchomić polecenia Node.js z wiersza polecenia, kliknij prawym przyciskiem myszy węzeł projektu i wybierz polecenie **Otwórz wiersz polecenia tutaj**.

## <a name="add-a-vue-file-to-the-project"></a>Dodawanie pliku .vue do projektu

1. W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy dowolny folder, taki jak folder *src/components,* a następnie wybierz polecenie **Dodaj** > **nowy element**.

1. Wybierz pojedynczy **składnik pliku JavaScript Vue** lub **składnik pojedynczego pliku TypeScript Vue,** a następnie kliknij przycisk **Dodaj**.

    Visual Studio dodaje nowy plik do projektu.

## <a name="build-the-project"></a>Kompilowanie projektu

1. (Tylko projekt TypeScript) W programie Visual Studio wybierz pozycję **Zbuduj** > **czyste rozwiązanie**.

    ::: moniker range=">=vs-2019"
    W szablonie TypeScript dołączonym do programu Visual Studio 2019 pomiń ten krok.
    ::: moniker-end

1. Następnie **wybierz** > build**build solution** do tworzenia projektu. Sprawdź **dane wyjściowe** okna, aby wyświetlić wyniki kompilacji i wybierz **build** z **listy Pokaż dane wyjściowe.**

    Szablon projektu JavaScript Vue.js (i starsze wersje szablonu `build` TypeScript) używają skryptu npm, konfigurując zdarzenie kompilacji postu. Jeśli chcesz zmodyfikować to ustawienie, otwórz plik projektu (*\<projectname\>.njsproj*) z Eksploratora Windows i znajdź ten wiersz kodu:

    ```xml
    <PostBuildEvent>npm run build</PostBuildEvent>
    ```

## <a name="run-the-application"></a>Uruchamianie aplikacji

1. Naciśnij **klawisze Ctrl**+**F5** (lub **Debugowanie > start bez debugowania),** aby uruchomić aplikację.

   W konsoli zostanie wyświetlony komunikat *Uruchamianie serwera programistycznego*.

   Następnie aplikacja zostanie otwarta w przeglądarce.
   
   Jeśli nie widzisz uruchomionej aplikacji, odśwież stronę.

   ![Aplikacja Vue.js działająca w przeglądarce](../javascript/media/vuejs-running-app.png)

1. Zamknij przeglądarkę internetową.

Gratulujemy ukończenia tego szybkiego startu! Mamy nadzieję, że dowiedziałeś się trochę o użyciu środowiska IDE programu Visual Studio w vue.js. Jeśli chcesz zagłębić się w jego możliwości, kontynuuj samouczek w sekcji **Samouczki** spisu treści.

## <a name="next-steps"></a>Następne kroki

- Przejdź przez [samouczek dla Node.js i Express](tutorial-nodejs.md)
- Przejdź przez [samouczek dla Node.js i react](tutorial-nodejs-with-react-and-jsx.md)
- [Wdrażanie aplikacji w usłudze aplikacji systemu Linux](../javascript/publish-nodejs-app-azure.md)