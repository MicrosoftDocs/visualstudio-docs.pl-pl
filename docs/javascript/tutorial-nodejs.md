---
title: Tworzenie środowiska Node.js i aplikacji Express
description: W tym samouczku utworzysz aplikację przy użyciu narzędzia Node.js dla programu Visual Studio
ms.date: 09/24/2018
ms.topic: tutorial
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jillfra
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: da816891c53d4576518102ad7438c735c415f7b4
ms.sourcegitcommit: 5dc74b4fdff1357df43a19f6e8a51d7bf706abd6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/06/2019
ms.locfileid: "55768388"
---
# <a name="tutorial-create-a-nodejs-and-express-app-in-visual-studio"></a>Samouczek: Tworzenie środowiska Node.js i Express aplikacji w programie Visual Studio

Tego samouczka do tworzenia aplikacji programu Visual Studio przy użyciu środowiska Node.js i Express służy do tworzenia prostą aplikację sieci web środowiska Node.js, Dodaj kod, zapoznaj się z niektórymi funkcjami środowiska IDE i uruchamiania aplikacji. Jeśli jeszcze nie zainstalowano programu Visual Studio, zainstaluj go bezpłatnie [tutaj](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017).

Ten samouczek zawiera informacje na temat wykonywania następujących czynności:
> [!div class="checklist"]
> * Tworzenie projektu platformy Node.js
> * Dodawanie kodu
> * Korzystać z technologii IntelliSense w celu edytowania kodu
> * Uruchamianie aplikacji
> * Trafiony punkt przerwania w debugerze

## <a name="before-you-begin"></a>Przed rozpoczęciem

Poniżej przedstawiono listę często zadawanych PYTAŃ szybkie wprowadzenie do niektórych kluczowych pojęć.

### <a name="what-is-nodejs"></a>Co to jest środowisko Node.js?

Node.js to środowisko uruchomieniowe JavaScript po stronie serwera, który wykonuje kodu JavaScript po stronie serwera.

### <a name="what-is-npm"></a>Co to jest npm?

npm jest domyślnego menedżera pakietów dla środowiska Node.js. Menedżer pakietów ułatwia programistom publikowania i udostępniać kod źródłowy bibliotek środowiska Node.js i upraszcza instalowania, aktualizowania i odinstalowywania bibliotek.

### <a name="what-is-express"></a>Co to jest express?

Express to platforma aplikacji sieci web, używane jako struktura serwera dla środowiska Node.js do tworzenia aplikacji sieci web. Express umożliwia wybieranie różnych struktur frontonu do tworzenia interfejsu użytkownika, takie jak Pug (dawniej nazywanych Jade). Pug jest używany w ramach tego samouczka.

## <a name="prerequisites"></a>Wymagania wstępne

* Konieczne jest posiadanie programu Visual Studio 2017 i obciążenie programowania Node.js.

    Jeśli jeszcze nie zainstalowano programu Visual Studio, przejdź do strony [program Visual Studio pobiera](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) strony, aby zainstalować go za darmo.

    Jeśli musisz zainstalować obciążenie, ale już program Visual Studio, kliknij przycisk **Otwórz Instalator programu Visual Studio** łącze w okienku po lewej stronie **nowy projekt** okno dialogowe (wybierz **pliku**  >  **Nowe** > **projektu**). Uruchamia Instalatora programu Visual Studio. Wybierz **programowania Node.js** obciążenia, wybierz **Modyfikuj**.

* Konieczne jest posiadanie zainstalowanego środowiska uruchomieniowego Node.js.

    Jeśli nie jest ona zainstalowana, zainstaluj wersję LTS z [Node.js](https://nodejs.org/en/download/) witryny sieci Web. Ogólnie rzecz biorąc program Visual Studio automatycznie wykrywa zainstalowane środowisko uruchomieniowe Node.js. Jeśli nie zostanie wykryta zainstalowanego środowiska uruchomieniowego, można skonfigurować projekt, aby odwoływać się do zainstalowanego środowiska uruchomieniowego na stronie właściwości (po utworzeniu projektu, kliknij prawym przyciskiem myszy węzeł projektu i wybierz polecenie **właściwości**).

    W tym samouczku został przetestowany przy użyciu środowiska Node.js 8.10.0.

## <a name="create-a-new-nodejs-project"></a>Utwórz nowy projekt środowiska Node.js

Program Visual Studio zarządza plikami dla pojedynczej aplikacji w *projektu*. Projekt zawiera pliki źródłowe kodu, zasoby i konfiguracji.

W tym samouczku możesz zaczynają się od prostego projektu zawierającego kod Node.js i aplikacji express.

1. Otwórz program Visual Studio 2017.

1. Na pasku menu u góry wybierz **pliku** > **New** > **projektu**.

1. W **nowy projekt** rozwiń w lewym okienku w oknie dialogowym **JavaScript**, a następnie wybierz **Node.js**. W środkowym okienku wybierz **podstawowe Azure aplikację Node.js Express 4** , a następnie wybierz **OK**.

     Jeśli nie widzisz **podstawowe Azure aplikację Node.js Express 4** szablonu projektu należy zainstalować **programowania Node.js** obciążenia pierwszy (patrz wymagania wstępne dotyczące instrukcji).

    Visual Studio tworzy nowego rozwiązania i otwiera projekt w okienku po prawej stronie. *App.js* plik projektu zostanie otwarty w edytorze (w okienku po lewej stronie).

    ![Struktura projektu](../javascript/media/tutorial-project-structure.png)

    (1) wyróżnione **bold** jest projektu, przy użyciu nazwę nadaną w **nowy projekt** okno dialogowe. W systemie plików tego projektu jest reprezentowany przez *.njsproj* pliku w folderze projektu. Można ustawić właściwości i zmienne środowiskowe związane z projektem, klikając prawym przyciskiem myszy projekt i wybierając pozycję **właściwości**. Możesz tworzyć Pełna zgodnooć wersji z innymi narzędziami deweloperskimi, ponieważ plik projektu nie wprowadzać zmian niestandardowego źródła projektu środowiska Node.js.

    (2) na najwyższym poziomie to rozwiązanie, która domyślnie ma taką samą nazwę jak projektu. To rozwiązanie, reprezentowane przez *.sln* plików na dysku, to kontener dla jednego lub kilku powiązanych projektów.

    (3 węzeł npm zawiera wszystkie pakiety npm zainstalowane. Możesz kliknąć prawym przyciskiem myszy węzeł npm, aby wyszukać i zainstalować pakiety npm w oknie dialogowym lub zainstaluj aktualizację pakietów przy użyciu ustawień w *package.json* i kliknij prawym przyciskiem myszy opcje w węźle npm.

    (4) *package.json* to plik używany przez narzędzie npm do zarządzania zależności pakietów i wersji pakietu dla lokalnie zainstalowane pakiety. Aby uzyskać więcej informacji na temat tego pliku, zobacz [konfiguracji pliku package.json](../javascript/configure-packages-with-package-json.md)

    (5) pliki projektu, takie jak *app.js* wyświetlane w węźle projektu. *App.js* jest plik startowy projektu, a to znaczy Dlaczego ona wyświetlona na liście **bold**. Można ustawić pliku uruchamiania, kliknij prawym przyciskiem myszy plik w projekcie i wybierając **Ustaw jako plik startowy środowiska Node.js**.

1. Otwórz **npm** węzła i upewnij się, że wszystkie pakiety npm wymagane są obecne.

    Jeśli wszystkie pakiety brakuje (ikona wykrzyknika), możesz kliknąć prawym przyciskiem myszy **npm** węzeł i wybierz polecenie **Zainstaluj brakujące pakiety npm**.

## <a name="add-some-code"></a>Dodawanie kodu

Aplikacja używa Pug dla frontonu platformy języka JavaScript. Pug korzysta z kodu znaczników prostego, który kompiluje w formacie HTML. (Pug jest ustawiony jako aparat widoku w *app.js*. Kod, który ustawia aparat widoku w *app.js* jest `app.set('view engine', 'pug');`.)

1. W Eksploratorze rozwiązań (w okienku po prawej stronie), otwórz folder, widoki, a następnie otwórz *index.pug*.

1. Zastąp zawartość następującym kodem.

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

    Powyższy kod jest używana do dynamicznego generowania strony HTML z tytułem i komunikat powitalny. Strona zawiera również kod, aby wyświetlić obraz, który zmienia się przy każdym naciśnięciu przycisku.

1. W folderze tras Otwórz *index.js*.

1. Dodaj następujący kod przed wywołaniem do `router.get`:

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

    Ten kod tworzy obiekt danych, które przechodzą do strony HTML, dynamicznie generowanych.

1. Zastąp `router.get` wywołania funkcji z następującym kodem:

    ```js
    router.get('/', function (req, res) {
        res.render('index', { title: 'Express', "data" });
    });
    ```

    Powyższy kod ustawia bieżącej strony za pomocą obiektu routera Express i renderuje stronę, przekazanie obiektu tytuł i danych na stronę. *Index.pug* określony plik tutaj jako strony Aby załadować kiedy *index.js* działa. *index.js* jest skonfigurowany jako domyślną trasę w *app.js* kodu (niewyświetlany).

    Aby zademonstrować kilka funkcji programu Visual Studio, występuje błąd zamierzonego wiersz kodu zawierający `res.render`. Należy naprawić ten błąd, zanim można uruchomić aplikacji, co zrobić w następnej sekcji.

## <a name="use-intellisense"></a>Korzystanie z funkcji IntelliSense

Funkcja IntelliSense jest narzędzia programu Visual Studio, która pomaga podczas pisania kodu.

1. W *index.js*, przejdź do wiersza zawierającego kod `res.render`.

1. Umieść kursor po `data` ciąg, wpisz `: get` i technologia IntelliSense pokaże Ci `getData` funkcję zdefiniowaną wcześniej w kodzie. Wybierz `getData`.

    ![Korzystanie z funkcji IntelliSense](../javascript/media/tutorial-nodejs-intellisense.png)

1. Usuń przecinek (`,`) przed `"data"` i zostanie wyświetlony, wyróżnianie składni zielony na wyrażeniu. Umieść kursor nad wyróżniania składni.

    ![Błąd składni w widoku](../javascript/media/tutorial-nodejs-syntax-checking.png)

    Ostatni wiersz ten komunikat informuje, że interpreter języka JavaScript oczekiwany przecinek (`,`).

1. W dolnym okienku kliknij **lista błędów** kartę.

    Zobaczysz ostrzeżenie i opis oraz nazwę pliku i numer wiersza.

    ![Wyświetl listę błędów](../javascript/media/tutorial-nodejs-error-list.png)

1. Naprawić kod poprzez dodanie przecinka (`,`) przed `"data"`.

    Po naprawieniu wiersz kodu powinien wyglądać następująco: `res.render('index', { title: 'Express', "data": getData() });`

## <a name="set-a-breakpoint"></a>Ustaw punkt przerwania

Następnie zamierzasz uruchomić aplikację w debugerze programu Visual Studio. Przed wykonaniem tych czynności, należy ustawić punkt przerwania.

1. W *index.js*, kliknij na lewym marginesie przed następujący wiersz kodu, aby ustawić punkt przerwania:

    `res.render('index', { title: 'Express', "data": getData() });`

    Punkty przerwania są najbardziej podstawowa i podstawowych funkcji niezawodne debugowanie. Punkt przerwania wskazuje, gdzie programu Visual Studio powinny zawiesić uruchamianie kodu, dzięki czemu możesz zapoznaj się z wartości zmiennych lub zachowanie pamięci lub czy gałąź kodu wprowadzenie uruchomieniu.

    ![Ustaw punkt przerwania](../javascript/media/tutorial-nodejs-set-breakpoint.png)

## <a name="run-the-application"></a>Uruchamianie aplikacji

1. Wybierz cel debugowania na pasku narzędzi debugowania, takie jak przeglądarki Edge lub Chrome.

    ![Wybierz element docelowy debugowania](../javascript/media/tutorial-nodejs-deploy-target.png)

    Jeśli dla programu Chrome jest dostępne na danym komputerze, ale nie są wyświetlane jako opcja, wybierz opcję **przeglądanie za pomocą** z listy rozwijanej docelowego debugowania i wybierz opcję dla programu Chrome jako domyślny element docelowy przeglądarki (wybierz **Ustaw jako domyślny**).

1. Naciśnij klawisz **F5** (**debugowania** > **Rozpocznij debugowanie**) do uruchamiania aplikacji.

    Debuger zatrzymuje się w punkcie przerwania, które można ustawić. Teraz możesz sprawdzić stan swojej aplikacji.

1. Umieść kursor nad `getData` Aby wyświetlić jego właściwości w DataTip

    ![Sprawdzanie zmiennych](../javascript/media/tutorial-nodejs-inspect-variables.png)

1. Naciśnij klawisz **F5** (**debugowania** > **Kontynuuj**) aby kontynuować.

    Aplikacja zostanie otwarta w przeglądarce.

    W oknie przeglądarki zostanie wyświetlony "Express" jako tytuł i "Powitalnej Express" w pierwszym akapicie.

1. Przyciski do wyświetlania różnych obrazów.

    ![Aplikacja działająca w przeglądarce](../javascript/media/tutorial-nodejs-running-in-browser.png)

1. Zamknij przeglądarkę sieci web.

## <a name="optional-publish-to-azure-app-service"></a>(Opcjonalnie) Publikowanie w usłudze Azure App Service

1. W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Publikuj**.

   ![Publikowanie w usłudze Azure App Service](../javascript/media/tutorial-nodejs-publish-to-azure.png)

1. Wybierz **platformy Microsoft Azure App Service**.

    W **usługi App Service** okno dialogowe, możesz zalogować się do konta platformy Azure i łączenie do istniejącej subskrypcji platformy Azure.

1. Wykonaj pozostałe kroki, aby Wybierz subskrypcję, wybierz lub Utwórz grupę zasobów, wybierz lub Utwórz płaszczyznę usługi aplikacji, a następnie postępuj zgodnie z instrukcjami po wyświetleniu monitu o publikowanie na platformie Azure. Aby uzyskać szczegółowe instrukcje, zobacz [Publikuj w witrynie internetowej platformy Azure za pomocą sieci web wdrażanie](https://github.com/Microsoft/nodejstools/wiki/Publish-to-Azure-Website-using-Web-Deploy).

1. **Dane wyjściowe** okno pokazuje postęp wdrażania na platformie Azure.

    Na pomyślne wdrożenie aplikacji zostanie otwarta w przeglądarce uruchomionej w usłudze Azure App Service. Kliknij przycisk, aby wyświetlić obraz.

   ![Aplikacja działająca w usłudze Azure App Service](../javascript/media/tutorial-nodejs-running-in-azure.png)

Gratulujemy wykonanie kroków tego samouczka!

## <a name="next-steps"></a>Następne kroki

> [!div class="nextstepaction"]
> [Wdrażanie aplikacji do usługi App Service w systemie Linux](../javascript/publish-nodejs-app-azure.md)