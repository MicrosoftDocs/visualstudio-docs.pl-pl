---
title: Tworzenie aplikacji platformy Node.js i Express
description: W tym samouczku dowiesz się, jak utworzyć prostą aplikację Node.js przy użyciu struktury aplikacji sieci Web Express w programie Visual Studio.
ms.date: 04/20/2020
ms.topic: tutorial
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jmartens
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: d3b8413673318f2e0cd2a5f00cfb9d1d7f0b4097
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99957533"
---
# <a name="tutorial-create-a-nodejs-and-express-app-in-visual-studio"></a>Samouczek: Tworzenie aplikacji Node.js i ekspresowej w programie Visual Studio

W tym samouczku dla programowania programu Visual Studio przy użyciu Node.js i Express utworzysz prostą aplikację sieci Web Node.js, dodajesz kod, Dowiedz się kilka funkcji środowiska IDE i uruchomisz aplikację. 

::: moniker range="vs-2017"

Jeśli program Visual Studio nie został jeszcze zainstalowany, przejdź do strony [plików do pobrania programu Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) , aby zainstalować ją bezpłatnie.

::: moniker-end

::: moniker range="vs-2019"

Jeśli program Visual Studio nie został jeszcze zainstalowany, przejdź do strony [plików do pobrania programu Visual Studio](https://visualstudio.microsoft.com/downloads) , aby zainstalować ją bezpłatnie.

::: moniker-end

Z tego samouczka dowiesz się, jak wykonywać następujące czynności:
> [!div class="checklist"]
> * Tworzenie projektu platformy Node.js
> * Dodaj kod
> * Edytowanie kodu przy użyciu funkcji IntelliSense
> * Uruchamianie aplikacji
> * Trafienie punktu przerwania w debugerze

## <a name="before-you-begin"></a>Zanim rozpoczniesz

Oto krótkie często zadawane pytania, aby wprowadzić pewne kluczowe pojęcia.

### <a name="what-is-nodejs"></a>Co to jest środowisko Node.js?

Node.js to środowisko uruchomieniowe JavaScript po stronie serwera, które wykonuje kod JavaScript po stronie serwera.

### <a name="what-is-npm"></a>Co to jest npm?

npm jest domyślnym menedżerem pakietów dla Node.js. Menedżer pakietów ułatwia programistom publikowanie i udostępnianie kodu źródłowego bibliotek Node.js i służy do uproszczenia instalacji, aktualizacji i odinstalowywania bibliotek.

### <a name="what-is-express"></a>Co to jest Express?

Express to struktura aplikacji sieci Web, używana jako struktura serwera do Node.js tworzenia aplikacji sieci Web. Program Express umożliwia wybranie różnych platform frontonu w celu utworzenia interfejsu użytkownika, takiego jak Pug (dawniej Jade). Pug jest używany w tym samouczku.

## <a name="prerequisites"></a>Wymagania wstępne

* Musisz mieć zainstalowany program Visual Studio i Node.js obciążenie programowaniem.

    ::: moniker range=">=vs-2019"
    Jeśli program Visual Studio 2019 nie został jeszcze zainstalowany, przejdź do strony [plików do pobrania programu Visual Studio](https://visualstudio.microsoft.com/downloads/) , aby zainstalować ją bezpłatnie.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Jeśli program Visual Studio 2017 nie został jeszcze zainstalowany, przejdź do strony [plików do pobrania programu Visual Studio](https://visualstudio.microsoft.com/downloads/) , aby zainstalować ją bezpłatnie.
    ::: moniker-end

    Jeśli musisz zainstalować obciążenie, ale masz już program Visual Studio, przejdź do pozycji **Narzędzia**  >  **Pobierz narzędzia i funkcje..**., co spowoduje otwarcie Instalator programu Visual Studio. Wybierz **Node.js obciążenie programowaniem** , a następnie wybierz **Modyfikuj**.

    ![Node.js obciążenie w Instalatorze programu VS](../ide/media/quickstart-nodejs-workload.png)

* Musisz mieć zainstalowane środowisko uruchomieniowe Node.js.

    Jeśli go nie zainstalowano, zalecamy zainstalowanie wersji LTS z witryny internetowej [Node.js](https://nodejs.org/en/download/) w celu uzyskania najlepszej zgodności z zewnętrznymi platformami i bibliotekami. Node.js jest oparta na architekturze 32-bitowej i 64-bitowej. Narzędzia Node.js w programie Visual Studio, zawarte w obciążeniu Node.js, obsługują obie wersje. Tylko jeden jest wymagany, a Instalator Node.js obsługuje tylko jeden instalowany w danym momencie.
    
    Ogólnie rzecz biorąc, program Visual Studio automatycznie wykrywa zainstalowane Node.js środowiska uruchomieniowego. Jeśli nie wykryje zainstalowanego środowiska uruchomieniowego, można skonfigurować projekt do odwoływania się do zainstalowanego środowiska uruchomieniowego na stronie właściwości (po utworzeniu projektu kliknij prawym przyciskiem myszy węzeł projektu, wybierz polecenie **Właściwości**, a następnie ustaw **ścieżkęNode.exe**). Można użyć globalnej instalacji Node.js lub można określić ścieżkę do lokalnego interpretera w każdym z projektów Node.js. 

    Ten samouczek został przetestowany przy użyciu Node.js 8.10.0.

## <a name="create-a-new-nodejs-project"></a>Utwórz nowy projekt Node.js

Program Visual Studio zarządza plikami dla pojedynczej aplikacji w *projekcie*. Projekt zawiera kod źródłowy, zasoby i pliki konfiguracji.

W tym samouczku Zacznij od prostego projektu zawierającego kod dla Node.js i aplikacji Express.

1. Otwórz program Visual Studio.

1. Tworzenie nowego projektu.

    ::: moniker range=">=vs-2019"
    Naciśnij klawisz **ESC** , aby zamknąć okno uruchamiania. **Naciśnij klawisze CTRL + Q** , aby otworzyć pole wyszukiwania, wpisz **Node.js**, a następnie wybierz pozycję **utwórz nową podstawową aplikację Azure Node.js Express 4** (JavaScript). W wyświetlonym oknie dialogowym wybierz pozycję **Utwórz**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Na górnym pasku menu wybierz pozycję **plik**  >  **Nowy**  >  **projekt**. W lewym okienku okna dialogowego **Nowy projekt** rozwiń opcję **JavaScript**, a następnie wybierz **Node.js**. W środkowym okienku wybierz pozycję **podstawowa aplikacja Azure Node.js Express 4**, a następnie wybierz przycisk **OK**.
    ::: moniker-end
    Jeśli nie widzisz szablonu projektu **podstawowe aplikacje platformy Azure Node.js Express 4** , musisz dodaćNode.js obciążenie **programowaniem** . Aby uzyskać szczegółowe instrukcje, zobacz [wymagania wstępne](#prerequisites).

    Program Visual Studio tworzy nowe rozwiązanie i otwiera projekt w okienku po prawej stronie. Plik projektu *app.js* zostanie otwarty w edytorze (po lewej stronie).

    ![Struktura projektu](../javascript/media/tutorial-project-structure.png)

    (1) wyróżnione **czcionką pogrubioną** jest projektem, przy użyciu nazwy podanych w oknie dialogowym **Nowy projekt** . W systemie plików ten projekt jest reprezentowany przez plik *. njsproj* w folderze projektu. Aby ustawić właściwości i zmienne środowiskowe skojarzone z projektem, kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Właściwości**. Możesz wykonywać czynności okrężne przy użyciu innych narzędzi programistycznych, ponieważ plik projektu nie wprowadza niestandardowych zmian do źródła projektu Node.js.

    (2) na najwyższym poziomie jest rozwiązaniem, które domyślnie ma taką samą nazwę jak projekt. Rozwiązanie reprezentowane przez plik *. sln* na dysku jest kontenerem dla co najmniej jednego powiązanego projektu.

    (3) węzeł npm pokazuje wszystkie zainstalowane pakiety npm. Możesz kliknąć prawym przyciskiem myszy węzeł npm, aby wyszukać i zainstalować pakiety npm przy użyciu okna dialogowego lub zainstalować i zaktualizować pakiety przy użyciu ustawień w *package.jsna* i kliknij prawym przyciskiem myszy opcje w węźle npm.

    (4) *package.js* jest plikiem używanym przez npm do zarządzania zależnościami pakietów i wersjami pakietów dla pakietów zainstalowanych lokalnie. Aby uzyskać więcej informacji, zobacz [Zarządzanie pakietami npm](../javascript/npm-package-management.md).

    (5) pliki projektu, takie jak *app.js* , są wyświetlane w węźle projektu. *app.js* to plik startowy projektu i dlatego, że jest on wyświetlany **pogrubioną czcionką**. Aby ustawić plik startowy, kliknij prawym przyciskiem myszy plik w projekcie i wybierz polecenie **Ustaw jako plik startowy Node.js**.

1. Otwórz węzeł **npm** i upewnij się, że wszystkie wymagane pakiety npm są obecne.

    Jeśli brakuje któregoś z pakietów (ikona wykrzyknika), możesz kliknąć prawym przyciskiem myszy węzeł **npm** i wybrać polecenie **Zainstaluj pakiety npm**.

## <a name="add-some-code"></a>Dodaj kod

Aplikacja używa Pug dla platformy języka JavaScript frontonu. Pug używa prostego kodu znaczników, który kompiluje do języka HTML. (Pug jest ustawiony jako aparat widoku w *app.js*. Kod, który ustawia aparat widoku w *app.js* jest `app.set('view engine', 'pug');` .)

1. W Eksplorator rozwiązań (prawego okienka) Otwórz folder widoki, a następnie otwórz polecenie *index. Pug*.

1. Zastąp zawartość następującym znacznikiem.

    ```js
    extends layout

    block content
      h1= title
      p Welcome to #{title}
      script.
        var f1 = function() { document.getElementById('myImage').src='#{data.item1}' }
      script.
        var f2 = function() { document.getElementById('myImage').src='#{data.item2}' }
      script.
        var f3 = function() { document.getElementById('myImage').src='#{data.item3}' }

      button(onclick='f1()') One!
      button(onclick='f2()') Two!
      button(onclick='f3()') Three!
      p
      a: img(id='myImage' height='200' width='200' src='')
    ```

    Poprzedni kod służy do dynamicznego generowania strony HTML z tytułem i komunikatem powitalnym. Strona zawiera również kod umożliwiający wyświetlenie obrazu, który zmienia się po naciśnięciu przycisku.

1. W folderze Routes Otwórz *index.js*.

1. Dodaj następujący kod przed wywołaniem do `router.get` :

    ```js
    var getData = function () {
        var data = {
            'item1': 'http://public-domain-photos.com/free-stock-photos-1/flowers/cactus-76.jpg',
            'item2': 'http://public-domain-photos.com/free-stock-photos-1/flowers/cactus-77.jpg',
            'item3': 'http://public-domain-photos.com/free-stock-photos-1/flowers/cactus-78.jpg'
        }
        return data;
    }
    ````

    Ten kod tworzy obiekt danych przekazywany do dynamicznie generowanej strony HTML.

1. Zastąp `router.get` wywołanie funkcji następującym kodem:

    ```js
    router.get('/', function (req, res) {
        res.render('index', { title: 'Express', "data" });
    });
    ```

    Poprzedni kod ustawia bieżącą stronę przy użyciu obiektu routera Express i renderuje stronę, przekazując tytuł i obiekt danych do strony. Plik *index. Pug* jest określany jako strona do załadowania, gdy *index.js* zostanie uruchomiona. *index.js* jest skonfigurowany jako domyślna trasa w kodzie *app.js* (niepokazywany).

    Aby zademonstrować kilka funkcji programu Visual Studio, wystąpił świadomy błąd w wierszu kodu zawierającego `res.render` . Aby można było uruchomić aplikację, należy usunąć ten błąd, którą można wykonać w następnej sekcji.

## <a name="use-intellisense"></a>Korzystanie z funkcji IntelliSense

IntelliSense to narzędzie programu Visual Studio, które ułatwia pisanie kodu.

1. W *index.js* przejdź do wiersza kodu zawierającego `res.render` .

1. Umieść kursor po `data` ciągu, `: get` a funkcja IntelliSense wyświetli `getData` funkcję zdefiniowaną wcześniej w kodzie. Wybierz pozycję `getData`.

    ![Korzystanie z funkcji IntelliSense](../javascript/media/tutorial-nodejs-intellisense.png)

1. Dodaj nawiasy, aby uczynić go wywołaniem funkcji, `getData()` .

1. Usuń przecinek ( `,` ) wcześniej `"data"` i zobaczysz zieloną składnię wyróżniania w wyrażeniu. Umieść kursor nad wyróżnioną składnią.

    ![Wyświetl błąd składniowy](../javascript/media/tutorial-nodejs-syntax-checking.png)

    Ostatni wiersz tego komunikatu informuje, że interpreter JavaScript oczekiwał przecinka ( `,` ).

1. W dolnym okienku kliknij kartę **Lista błędów** i wybierz pozycję **kompilacja + IntelliSense** dla typu raportowanych problemów.

    Zobaczysz ostrzeżenie i opis wraz z nazwą pliku i numerem wiersza.

    ![Wyświetl listę błędów](../javascript/media/tutorial-nodejs-error-list.png)

1. Popraw kod przez dodanie przecinka ( `,` ) przed `"data"` .

    Po skorygowaniu wiersz kodu powinien wyglądać następująco: `res.render('index', { title: 'Express', "data": getData() });`

## <a name="set-a-breakpoint"></a>Ustawianie punktu przerwania

Następnie uruchomisz aplikację z dołączonym debugerem programu Visual Studio. Przed wykonaniem tej czynności należy ustawić punkt przerwania.

1. W *index.js* kliknij przycisk na lewym marginesie przed następującym wierszem kodu, aby ustawić punkt przerwania:

    `res.render('index', { title: 'Express', "data": getData() });`

    Punkty przerwania są najbardziej podstawową i istotną funkcją niezawodnego debugowania. Punkt przerwania wskazuje, gdzie program Visual Studio powinien zawiesić uruchomiony kod, aby można było przyjrzeć się wartościom zmiennych lub działaniu pamięci lub niezależnie od tego, czy gałąź kodu jest uruchamiana.

    ![Ustawianie punktu przerwania](../javascript/media/tutorial-nodejs-set-breakpoint.png)

## <a name="run-the-application"></a>Uruchamianie aplikacji

1. Wybierz element docelowy debugowania na pasku narzędzi debugowania, taki jak **serwer sieci Web (Google Chrome)** lub **serwer sieci Web (Microsoft Edge)**.

    ::: moniker range=">=vs-2019"
    ![Wybierz element docelowy debugowania](../javascript/media/vs-2019/tutorial-nodejs-deploy-target.png)
    ::: moniker-end
    ::: moniker range="vs-2017"
    ![Wybierz element docelowy debugowania](../javascript/media/tutorial-nodejs-deploy-target.png)
    ::: moniker-end

    Jeśli program Chrome jest dostępny na komputerze, ale nie jest wyświetlany jako opcja, wybierz pozycję **Przeglądaj z** listy rozwijanej element docelowy debugowania, a następnie wybierz pozycję Chrome jako domyślny element docelowy przeglądarki (wybierz pozycję **Ustaw jako domyślny**).

1. Naciśnij klawisz **F5** (**Debuguj**  >  **Rozpocznij debugowanie**), aby uruchomić aplikację.

    Debuger zatrzymuje się w ustawionym punkcie przerwania. Teraz można sprawdzić stan aplikacji.

1. Umieść wskaźnik myszy `getData` , aby wyświetlić jej właściwości w etykietki danych

    ![Sprawdzanie zmiennych](../javascript/media/tutorial-nodejs-inspect-variables.png)

1. Naciśnij klawisz **F5** (**Debuguj**  >  **Kontynuuj**), aby kontynuować.

    Aplikacja zostanie otwarta w przeglądarce.

    W oknie przeglądarki w pierwszym akapicie zobaczysz wyraz "Express" jako tytuł i "Witaj do Express".

1. Kliknij przyciski, aby wyświetlić różne obrazy.

    ![Aplikacja uruchomiona w przeglądarce](../javascript/media/tutorial-nodejs-running-in-browser.png)

1. Zamknij przeglądarkę internetową.

## <a name="optional-publish-to-azure-app-service"></a>Obowiązkowe Publikuj w Azure App Service

1. W Eksplorator rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Publikuj**.

   ![Publikowanie w usłudze Azure App Service](../javascript/media/tutorial-nodejs-publish-to-azure.png)

1. Wybierz **App Service Microsoft Azure**.

    W oknie dialogowym **App Service** możesz zalogować się do konta platformy Azure i połączyć się z istniejącymi subskrypcjami platformy Azure.

1. Wykonaj pozostałe kroki, aby wybrać subskrypcję, wybierz lub Utwórz grupę zasobów, wybierz lub Utwórz płaszczyznę usługi App Service, a następnie postępuj zgodnie z instrukcjami po wyświetleniu monitu o opublikowanie na platformie Azure. Aby uzyskać bardziej szczegółowe instrukcje, zobacz [Publikowanie w witrynie sieci Web platformy Azure za pomocą narzędzia Web Deploy](https://github.com/Microsoft/nodejstools/wiki/Publish-to-Azure-Website-using-Web-Deploy).

1. Okno **dane wyjściowe** pokazuje postęp wdrażania na platformie Azure.

    Po pomyślnym wdrożeniu aplikacja zostanie otwarta w przeglądarce działającej w Azure App Service. Kliknij przycisk, aby wyświetlić obraz.

   ![Aplikacja działająca w Azure App Service](../javascript/media/tutorial-nodejs-running-in-azure.png)

Gratulujemy ukończenia tego samouczka.

## <a name="next-steps"></a>Następne kroki

> [!div class="nextstepaction"]
> [Wdrażanie aplikacji w systemie Linux App Service](../javascript/publish-nodejs-app-azure.md)
