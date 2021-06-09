---
title: Tworzenie aplikacji platformy Node.js i Express
description: Z tego samouczka dowiesz się, jak utworzyć prostą aplikację Node.js przy użyciu struktury aplikacji internetowych Express w Visual Studio.
ms.date: 03/25/2021
ms.topic: tutorial
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jmartens
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: 5433ae0e84396f3c16dc5ed50f51ce7e9eb7056f
ms.sourcegitcommit: 01a411cd7ae3488b7b979a947bca92fd296a98e9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2021
ms.locfileid: "111760981"
---
# <a name="tutorial-create-a-nodejs-and-express-app-in-visual-studio"></a>Samouczek: tworzenie aplikacji Node.js Express w programie Visual Studio

W tym samouczku Visual Studio tworzenia aplikacji przy użyciu usług Node.js i Express utworzysz prostą aplikację internetową usługi Node.js, dodasz kod, poznasz niektóre funkcje środowiska IDE i uruchomemy aplikację. 

::: moniker range="vs-2017"

Jeśli jeszcze nie zainstalowano aplikacji Visual Studio, przejdź [](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) do strony pobierania Visual Studio, aby zainstalować ją bezpłatnie.

::: moniker-end

::: moniker range=">=vs-2019"

Jeśli jeszcze nie zainstalowano aplikacji Visual Studio, przejdź [](https://visualstudio.microsoft.com/downloads) do strony pobierania Visual Studio, aby zainstalować ją bezpłatnie.

::: moniker-end

Ten samouczek zawiera informacje na temat wykonywania następujących czynności:
> [!div class="checklist"]
> * Tworzenie projektu platformy Node.js
> * Dodawanie kodu
> * Edytowanie kodu za pomocą funkcji IntelliSense
> * Uruchamianie aplikacji
> * Trafianie punktu przerwania w debugerze

## <a name="before-you-begin"></a>Zanim rozpoczniesz

Oto krótkie często zadawane pytania wprowadzające do niektórych kluczowych pojęć.

### <a name="what-is-nodejs"></a>Co to jest środowisko Node.js?

Node.js to środowisko uruchomieniowe JavaScript po stronie serwera, które wykonuje skrypt JavaScript po stronie serwera.

### <a name="what-is-npm"></a>Co to jest npm?

Npm jest domyślnym menedżerem pakietów dla Node.js. Menedżer pakietów ułatwia programistom publikowanie i udostępnianie kodu źródłowego bibliotek Node.js oraz upraszcza instalowanie, aktualizowanie i odinstalowywanie bibliotek.

### <a name="what-is-express"></a>Co to jest express?

Express jest platformą aplikacji internetowych używaną jako serwerowa Node.js do kompilowania aplikacji internetowych. Dzięki platformie Express można wybrać różne struktury frontonu, aby utworzyć interfejs użytkownika, na przykład Pug (dawniej Jade). Pug jest używany w tym samouczku.

## <a name="prerequisites"></a>Wymagania wstępne

* Musisz mieć Visual Studio i obciążenie Node.js tworzenia aplikacji.

    ::: moniker range=">=vs-2019"
    Jeśli jeszcze nie zainstalowano programu Visual Studio 2019, [](https://visualstudio.microsoft.com/downloads/) przejdź do strony pobierania Visual Studio, aby zainstalować ją bezpłatnie.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Jeśli jeszcze nie zainstalowano programu Visual Studio 2017, [](https://visualstudio.microsoft.com/downloads/) przejdź do strony pobierania Visual Studio, aby zainstalować ją bezpłatnie.
    ::: moniker-end

    Jeśli musisz zainstalować obciążenie, ale masz już Visual Studio, przejdź do tematu Narzędzia Pobierz narzędzia i  >  **funkcje...,** co spowoduje otwarcie Instalator programu Visual Studio. Wybierz obciążenie **Node.js dewelopera,** a następnie wybierz pozycję **Modyfikuj.**

    ![Node.js obciążenia w instalatorze programu VS](../ide/media/quickstart-nodejs-workload.png)

* Musisz mieć zainstalowane Node.js uruchomieniowe.

    Jeśli nie jest on zainstalowany, zalecamy zainstalowanie wersji LTS z witryny internetowej [Node.js, ](https://nodejs.org/en/download/) aby uzyskać najlepszą zgodność z zewnętrznymi platformami i bibliotekami. Node.js jest zbudowana dla architektur 32-bitowych i 64-bitowych. Narzędzia Node.js w Visual Studio, zawarte w obciążeniu Node.js, obsługują obie wersje. Wymagany jest tylko jeden Node.js a instalator obsługuje tylko jedną funkcję instalowaną jednocześnie.
    
    Ogólnie rzecz biorąc, Visual Studio automatycznie wykrywa zainstalowane środowisko Node.js uruchomieniowe. Jeśli program nie wykryje zainstalowanego środowiska uruchomieniowego, możesz skonfigurować projekt do odwołania się do zainstalowanego środowiska uruchomieniowego na stronie **właściwości**(po utworzeniu projektu kliknij prawym przyciskiem myszy węzeł projektu, wybierz polecenie Właściwości i ustaw ścieżkęNode.exe ). Można użyć globalnej instalacji usługi Node.js lub określić ścieżkę do interpretera lokalnego w każdym z Node.js projektów. 

    Ten samouczek został przetestowany Node.js 8.10.0.

## <a name="create-a-new-nodejs-project"></a>Tworzenie nowego Node.js projektu

Visual Studio zarządza plikami dla jednej aplikacji w *projekcie*. Projekt zawiera kod źródłowy, zasoby i pliki konfiguracji.

W tym samouczku zaczniesz od prostego projektu zawierającego kod dla aplikacji Node.js express.

1. Otwórz program Visual Studio.

1. Tworzenie nowego projektu.

    ::: moniker range=">=vs-2019"
    Naciśnij **klawisz Esc,** aby zamknąć okno uruchamiania. Naciśnij **klawisze Ctrl + Q,** aby otworzyć pole wyszukiwania, wpisz **Node.js**, a następnie wybierz pozycję Utwórz nową podstawową aplikację azure Node.js **Express 4** (JavaScript). W wyświetlonym oknie dialogowym wybierz pozycję **Utwórz**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Na górnym pasku menu wybierz pozycję **File** New Project  >  **(Plik nowy**  >  **projekt).** W lewym okienku okna dialogowego **Nowy** projekt rozwiń pozycję **JavaScript,** a następnie wybierz **pozycjęNode.js**. W środkowym okienku wybierz pozycję **Podstawowa usługa Azure Node.js Express 4,** a następnie wybierz przycisk **OK.**
    ::: moniker-end
    Jeśli nie widzisz podstawowego szablonu projektu aplikacji **Azure Node.js Express 4,** musisz dodaćNode.js **tworzenia** aplikacji. Aby uzyskać szczegółowe instrukcje, zobacz [Wymagania wstępne.](#prerequisites)

    Visual Studio tworzy nowe rozwiązanie i otwiera projekt w okienku po prawej stronie. Plik *app.js* zostanie otwarty w edytorze (okienko po lewej stronie).

    ![Struktura projektu](../javascript/media/tutorial-project-structure.png)

    (1) Wyróżnione **pogrubioną** czcionką jest twój projekt, używając nazwy nadaowej w **oknie dialogowym Nowy** projekt. W systemie plików ten projekt jest reprezentowany przez plik *.njsproj* w folderze projektu. Możesz ustawić właściwości i zmienne środowiskowe skojarzone z projektem, klikając projekt prawym przyciskiem myszy i wybierając pozycję **Właściwości**. Można wykonać rundę z innymi narzędziami programistyki, ponieważ plik projektu nie wprowadza niestandardowych zmian w źródle Node.js projektu.

    (2) Na najwyższym poziomie znajduje się rozwiązanie, które domyślnie ma taką samą nazwę jak projekt. Rozwiązanie reprezentowane przez plik *sln* na dysku jest kontenerem dla co najmniej jednego powiązanego projektu.

    (3) Węzeł npm pokazuje wszystkie zainstalowane pakiety npm. Możesz kliknąć prawym przyciskiem myszy węzeł npm, aby wyszukać i zainstalować pakiety npm przy użyciu okna dialogowego lub zainstalować i zaktualizować pakiety przy użyciu ustawień w programie *package.js* i kliknąć prawym przyciskiem myszy opcje w węźle npm.

    (4) *package.jsjest* plikiem używanym przez program npm do zarządzania zależnościami pakietów i wersjami pakietów dla lokalnie zainstalowanych pakietów. Aby uzyskać więcej informacji, zobacz [Zarządzanie pakietami npm.](../javascript/npm-package-management.md)

    (5) Pliki projektu, takie *app.js* są wyświetlane w węźle projektu. *app.js* to plik startowy projektu i dlatego jest on pogrubiony.  Plik startowy można ustawić, klikając prawym przyciskiem myszy plik w projekcie i wybierając polecenie Ustaw jako **Node.js startowego**.

1. Otwórz węzeł **npm** i upewnij się, że są obecne wszystkie wymagane pakiety npm.

    Jeśli brakuje jakichkolwiek pakietów (ikona wykrzyknika), możesz kliknąć prawym przyciskiem myszy **węzeł npm** i wybrać **polecenie Zainstaluj pakiety npm.**

## <a name="add-some-code"></a>Dodawanie kodu

Aplikacja używa programu Pug na platformie JavaScript frontonu. Pug używa prostego kodu znaczników, który kompiluje się do formatu HTML. (Program Pug jest ustawiany jako aparat widoku *w* app.js. Kod, który ustawia aparat widoku w *app.js* to `app.set('view engine', 'pug');` ).

1. W Eksplorator rozwiązań okienku po prawej stronie otwórz folder views, a następnie otwórz *plik index.pug.*

1. Zastąp zawartość poniższym kodem.

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

    Powyższy kod służy do dynamicznego generowania strony HTML z tytułem i komunikatem powitalnym. Strona zawiera również kod do wyświetlania obrazu, który zmienia się po każdym naciśnięciu przycisku.

1. W folderze routes otwórz *folderindex.js*.

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

    Ten kod tworzy obiekt danych, który jest przekazywać do dynamicznie generowanej strony HTML.

1. Zastąp wywołanie `router.get` funkcji następującym kodem:

    ```js
    router.get('/', function (req, res) {
        res.render('index', { title: 'Express', "data" });
    });
    ```

    Poprzedni kod ustawia bieżącą stronę przy użyciu obiektu routera express i renderuje stronę, przekazując tytuł i obiekt danych do strony. Plik *index.pug* jest tutaj określony jako strona do załadowania po *index.js.* *index.js* jest skonfigurowana jako trasa domyślna w kodzie *app.js* (nie jest wyświetlana).

    Aby zademonstrować kilka Visual Studio, w wierszu kodu zawierającym wartość występuje celowy błąd `res.render` . Należy naprawić błąd przed uruchomieniem aplikacji, co zrobisz w następnej sekcji.

## <a name="use-intellisense"></a>Korzystanie z funkcji IntelliSense

IntelliSense to Visual Studio, które pomaga podczas pisania kodu.

1. W *index.js* przejdź do wiersza kodu zawierającego `res.render` .

1. Umieść kursor za ciągiem , wpisz , a funkcja IntelliSense pokaże funkcję `data` `: get` `getData` zdefiniowaną wcześniej w kodzie. Wybierz pozycję `getData`.

    ![Korzystanie z funkcji IntelliSense](../javascript/media/tutorial-nodejs-intellisense.png)

1. Dodaj nawiasy, aby było wywołaniem funkcji `getData()` .

1. Usuń przecinek ( ) przed , a w wyrażeniu zostanie `,` `"data"` wyróżniona zielona składnia. Umieść kursor na wyróżnianiu składni.

    ![Wyświetlanie błędu składni](../javascript/media/tutorial-nodejs-syntax-checking.png)

    Ostatni wiersz tego komunikatu informuje, że interpreter języka JavaScript oczekiwał przecinka ( `,` ).

1. W dolnym okienku kliknij kartę **Lista błędów** i wybierz **pozycję Kompilacja + IntelliSense** dla typu zgłoszonych problemów.

    Zobaczysz ostrzeżenie i opis wraz z nazwą pliku i numerem wiersza.

    ![Wyświetlanie listy błędów](../javascript/media/tutorial-nodejs-error-list.png)

1. Napraw kod, dodając przecinek ( `,` ) przed `"data"` .

    Po poprawioniu wiersz kodu powinien wyglądać tak: `res.render('index', { title: 'Express', "data": getData() });`

## <a name="set-a-breakpoint"></a>Ustawianie punktu przerwania

Następnym krokiem będzie uruchomienie aplikacji z dołączonym Visual Studio debugerem. Przed wykonaniem tej pracy należy ustawić punkt przerwania.

1. W *index.js* kliknij lewą rynnę przed następującym wierszem kodu, aby ustawić punkt przerwania:

    `res.render('index', { title: 'Express', "data": getData() });`

    Punkty przerwania są najbardziej podstawową i istotną funkcją niezawodnego debugowania. Punkt przerwania wskazuje, gdzie program Visual Studio powinien wstrzymać uruchomiony kod, aby można było przyjrzeć się wartościom zmiennych, zachowaniu pamięci lub czy jest uruchamiana gałąź kodu.

    ![Ustawianie punktu przerwania](../javascript/media/tutorial-nodejs-set-breakpoint.png)

## <a name="run-the-application"></a>Uruchamianie aplikacji

1. Wybierz element docelowy debugowania na pasku narzędzi Debugowanie, taki jak **Serwer internetowy (Google Chrome)** lub **Serwer internetowy (Microsoft Edge).**

    ::: moniker range=">=vs-2019"
    ![Wybieranie obiektu docelowego debugowania](../javascript/media/vs-2019/tutorial-nodejs-deploy-target.png)
    ::: moniker-end
    ::: moniker range="vs-2017"
    ![Wybieranie obiektu docelowego debugowania](../javascript/media/tutorial-nodejs-deploy-target.png)
    ::: moniker-end

    Jeśli przeglądarka Chrome jest dostępna na Twojej maszynie, ale nie jest wyświetlona jako opcja, wybierz pozycję **Przeglądaj** za pomocą z listy rozwijanej miejsca docelowego debugowania, a następnie wybierz chrome jako domyślny element docelowy przeglądarki (wybierz pozycję Ustaw jako **domyślny).**

1. Naciśnij **klawisz F5** **(Debuguj**  >  **rozpocznij debugowanie),** aby uruchomić aplikację.

    Debuger jest wstrzymywany w ustawionym punkcie przerwania. Teraz możesz sprawdzić stan aplikacji.

1. Umieść kursor `getData` nad , aby wyświetlić jego właściwości w etykietce danych

    ![Sprawdzanie zmiennych](../javascript/media/tutorial-nodejs-inspect-variables.png)

1. Naciśnij **klawisz F5** **(Kontynuuj**  >  **debugowanie),** aby kontynuować.

    Aplikacja zostanie otwarta w przeglądarce.

    W oknie przeglądarki w pierwszym akapicie zobaczysz wyrazy "Express" (Express) jako tytuł i "Welcome to Express".

1. Kliknij przyciski, aby wyświetlić różne obrazy.

    ![Aplikacja uruchomiona w przeglądarce](../javascript/media/tutorial-nodejs-running-in-browser.png)

1. Zamknij przeglądarkę internetową.

## <a name="optional-publish-to-azure-app-service"></a>(Opcjonalnie) Publikowanie w Azure App Service

1. W Eksplorator rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Opublikuj.**

   ![Publikowanie w usłudze Azure App Service](../javascript/media/tutorial-nodejs-publish-to-azure.png)

1. Wybierz **Microsoft Azure App Service**.

    W **oknie App Service** dialogowym możesz zalogować się do konta platformy Azure i nawiązać połączenie z istniejącymi subskrypcjami platformy Azure.

1. Wykonaj pozostałe kroki, aby wybrać subskrypcję, wybrać lub utworzyć grupę zasobów, wybrać lub utworzyć płaszczyznę usługi aplikacji, a następnie wykonaj kroki po wyświetleniu monitu o opublikowanie na platformie Azure. Aby uzyskać bardziej szczegółowe instrukcje, zobacz [Publikowanie w witrynie internetowej platformy Azure przy użyciu narzędzia Web Deploy.](https://github.com/Microsoft/nodejstools/wiki/Publish-to-Azure-Website-using-Web-Deploy)

1. Okno **Dane wyjściowe** pokazuje postęp wdrażania na platformie Azure.

    Po pomyślnym wdrożeniu aplikacja zostanie otwarta w przeglądarce uruchomionej w Azure App Service. Kliknij przycisk, aby wyświetlić obraz.

   ![Aplikacja uruchomiona w programie Azure App Service](../javascript/media/tutorial-nodejs-running-in-azure.png)

Gratulujemy ukończenia tego samouczka!

## <a name="next-steps"></a>Następne kroki

> [!div class="nextstepaction"]
> [Wdrażanie aplikacji w systemie Linux App Service](../javascript/publish-nodejs-app-azure.md)

> [!div class="nextstepaction"]
> [Rozszerzenie usługi językowej AngularJS](https://devblogs.microsoft.com/visualstudio/angular-language-service-for-visual-studio)
