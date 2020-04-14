---
title: Tworzenie aplikacji Node.js i Express
description: W tym samouczku utworzysz aplikację przy użyciu narzędzi Node.js dla programu Visual Studio
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
ms.openlocfilehash: 260bc6ff6eb2d0bfbf0b9abd19062892c358728a
ms.sourcegitcommit: b4e0cc76d94fe8cf6d238c4cc09512d17131a195
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/13/2020
ms.locfileid: "81224527"
---
# <a name="tutorial-create-a-nodejs-and-express-app-in-visual-studio"></a>Samouczek: Tworzenie aplikacji Node.js i Express w programie Visual Studio

W tym samouczku dla rozwoju programu Visual Studio przy użyciu Node.js i Express, można utworzyć prostą aplikację sieci web Node.js, dodać kod, zbadać niektóre funkcje IDE i uruchomić aplikację. 

::: moniker range="vs-2017"

Jeśli program Visual Studio nie został jeszcze zainstalowany, przejdź do strony [pobierania programu Visual Studio,](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) aby zainstalować ją bezpłatnie.

::: moniker-end

::: moniker range="vs-2019"

Jeśli program Visual Studio nie został jeszcze zainstalowany, przejdź do strony [pobierania programu Visual Studio,](https://visualstudio.microsoft.com/downloads) aby zainstalować ją bezpłatnie.

::: moniker-end

Ten samouczek zawiera informacje na temat wykonywania następujących czynności:
> [!div class="checklist"]
> * Tworzenie projektu z użyciem narzędzia Node.js
> * Dodaj kod
> * Edytowanie kodu za pomocą funkcji IntelliSense
> * Uruchomienie aplikacji
> * Trafienie punktu przerwania w debugerze

## <a name="before-you-begin"></a>Przed rozpoczęciem

Oto krótkie często zadawane pytania, aby przedstawić Ci kilka kluczowych pojęć.

### <a name="what-is-nodejs"></a>Co to jest środowisko Node.js?

Node.js to środowisko wykonawcze JavaScript po stronie serwera, które wykonuje obsługę serwera JavaScript po stronie serwera.

### <a name="what-is-npm"></a>Co to jest npm?

npm jest domyślnym menedżerem pakietów dla node.js. Menedżer pakietów ułatwia programistom publikowanie i udostępnianie kodu źródłowego bibliotek Node.js i ma na celu uproszczenie instalacji, aktualizacji i deinstalacji bibliotek.

### <a name="what-is-express"></a>Co to jest ekspres?

Express to struktura aplikacji sieci web, używana jako struktura serwera dla node.js do tworzenia aplikacji sieci web. Express umożliwia wybranie różnych struktur front-end do tworzenia interfejsu użytkownika, takich jak Mops (dawniej nazywany Jade). Mops jest używany w tym samouczku.

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

    Ten samouczek został przetestowany z Node.js 8.10.0.

## <a name="create-a-new-nodejs-project"></a>Tworzenie nowego projektu node.js

Program Visual Studio zarządza plikami dla pojedynczej aplikacji w *projekcie*. Projekt zawiera kod źródłowy, zasoby i pliki konfiguracyjne.

W tym samouczku należy rozpocząć od prostego projektu zawierającego kod dla aplikacji Node.js i express.

1. Otwórz program Visual Studio.

1. Tworzenie nowego projektu.

    ::: moniker range=">=vs-2019"
    Naciśnij **klawisz Esc,** aby zamknąć okno początkowe. Wpisz **Ctrl + Q,** aby otworzyć pole wyszukiwania, wpisz **Node.js**, a następnie wybierz pozycję **Utwórz nową podstawową aplikację Azure Node.js Express 4** (JavaScript). W wyświetlonym oknie dialogowym wybierz pozycję **Utwórz**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Na górnym pasku menu wybierz pozycję **Plik** > **nowego** > **projektu**. W lewym okienku okna dialogowego **Nowy projekt** rozwiń węzeł **JavaScript**, a następnie wybierz polecenie **Node.js**. W środkowym okienku wybierz pozycję **Basic Azure Node.js Express 4 application**, a następnie wybierz przycisk **OK**.
    ::: moniker-end
    Jeśli nie widzisz szablonu projektu **aplikacji Basic Azure Node.js Express 4,** musisz dodać obciążenie **deweloperne node.js.** Aby uzyskać szczegółowe instrukcje, zobacz [Wymagania wstępne](#prerequisites).

    Visual Studio tworzy nowe rozwiązanie i otwiera projekt w prawym okienku. Plik projektu *app.js* zostanie otwarty w edytorze (lewe okienko).

    ![Struktura projektu](../javascript/media/tutorial-project-structure.png)

    (1) Wyróżniony **pogrubioną czcionką** jest twój projekt, używając nazwy podanych w oknie dialogowym **Nowy projekt.** W systemie plików ten projekt jest reprezentowany przez plik *njsproj* w folderze projektu. Właściwości i zmienne środowiskowe skojarzone z projektem można ustawić, klikając prawym przyciskiem myszy projekt i wybierając polecenie **Właściwości**. Można wykonać potknięcia zaokrąglenia z innymi narzędziami programistycznymi, ponieważ plik projektu nie wprowadzać niestandardowych zmian w źródle projektu Node.js.

    (2) Na najwyższym poziomie jest rozwiązanie, które domyślnie ma taką samą nazwę jak projekt. Rozwiązanie, reprezentowane przez plik *.sln* na dysku, jest kontenerem dla jednego lub więcej powiązanych projektów.

    (3) Węzeł npm pokazuje zainstalowane pakiety npm. Możesz kliknąć prawym przyciskiem myszy węzeł npm, aby wyszukać i zainstalować pakiety npm za pomocą okna dialogowego lub zainstalować i zaktualizować pakiety przy użyciu ustawień w *pliku package.json* i kliknij prawym przyciskiem myszy opcje w węźle npm.

    (4) *package.json* jest plikiem używanym przez npm do zarządzania zależnościami pakietów i wersjami pakietów dla pakietów zainstalowanych lokalnie. Aby uzyskać więcej informacji na temat tego pliku, zobacz [konfigurację package.json](../javascript/configure-packages-with-package-json.md)

    (5) Pliki projektu, takie jak *app.js* pojawiają się w węźle projektu. *app.js* jest plik startowy projektu i dlatego pojawia się **pogrubioną**. Plik startowy można ustawić, klikając prawym przyciskiem myszy plik w projekcie i wybierając **polecenie Ustaw jako plik startowy Node.js**.

1. Otwórz węzeł **npm** i upewnij się, że wszystkie wymagane pakiety npm są obecne.

    Jeśli brakuje pakietów (ikona wykrzyknika), możesz kliknąć prawym przyciskiem myszy węzeł **npm** i wybrać polecenie **Zainstaluj brakujące pakiety npm**.

## <a name="add-some-code"></a>Dodaj kod

Aplikacja używa Mops dla frontonu JavaScript framework. Mops używa prostego kodu znaczników, który kompiluje się do HTML. (Mops jest ustawiony jako silnik widoku w *app.js*. Kod, który ustawia aparat widoku w `app.set('view engine', 'pug');` *app.js* jest .)

1. W Eksploratorze rozwiązań (prawe okienko) otwórz folder widoków, a następnie otwórz *plik index.mops*.

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

    Poprzedni kod jest używany do dynamicznego generowania strony HTML z tytułem i wiadomością powitalną. Strona zawiera również kod, aby wyświetlić obraz, który zmienia się przy każdym naciśnięciu przycisku.

1. W folderze Trasy otwórz *plik index.js*.

1. Dodaj następujący kod przed `router.get`wywołaniem do:

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

    Ten kod tworzy obiekt danych, który jest przekazyzony do dynamicznie generowanej strony HTML.

1. Zastąp wywołanie `router.get` funkcji następującym kodem:

    ```js
    router.get('/', function (req, res) {
        res.render('index', { title: 'Express', "data" });
    });
    ```

    Poprzedni kod ustawia bieżącą stronę przy użyciu obiektu routera Express i renderuje stronę, przekazując tytuł i obiekt danych do strony. Plik *index.pug* jest określony w tym miejscu jako strona do załadowania podczas pracy *pliku index.js.* *index.js* jest skonfigurowany jako trasa domyślna w kodzie *app.js* (nie pokazano).

    Aby zademonstrować kilka funkcji programu Visual Studio, w wierszu `res.render`kodu zawierającym program zawiera zamierzony błąd. Musisz naprawić błąd przed uruchomieniem aplikacji, co zrobić w następnej sekcji.

## <a name="use-intellisense"></a>Korzystanie z funkcji IntelliSense

IntelliSense to narzędzie programu Visual Studio, które pomaga podczas pisania kodu.

1. W *pliku index.js*przejdź do wiersza kodu zawierającego `res.render`.

1. Umieść kursor po `data` ciągu, `: get` wpisz i IntelliSense `getData` pokaże funkcję zdefiniowaną wcześniej w kodzie. Wybierz pozycję `getData`.

    ![Korzystanie z funkcji IntelliSense](../javascript/media/tutorial-nodejs-intellisense.png)

1. Dodaj nawiasy, aby uczynić go `getData()`wywołaniem funkcji, .

1. Usuń przecinek`,`( `"data"` ) przed i zobaczysz zielone podświetlanie składni na wyrażeniu. Umieść wskaźnik myszy na podświetlaniu składni.

    ![Błąd składni widoku](../javascript/media/tutorial-nodejs-syntax-checking.png)

    Ostatni wiersz tej wiadomości informuje, że interpreter JavaScript`,`oczekuje przecinka ( ).

1. W dolnym okienku kliknij kartę **Lista błędów.**

    Zobaczysz ostrzeżenie i opis wraz z numerem pliku i wiersza.

    ![Wyświetl listę błędów](../javascript/media/tutorial-nodejs-error-list.png)

1. Napraw kod, dodając przecinek`,`( `"data"`) przed .

    Po skorygowaniu wiersz kodu powinien wyglądać następująco:`res.render('index', { title: 'Express', "data": getData() });`

## <a name="set-a-breakpoint"></a>Ustawianie punktu przerwania

Następnie uruchomisz aplikację z dołączonym debugerem programu Visual Studio. Zanim to zrobisz, należy ustawić punkt przerwania.

1. W *pliku index.js*kliknij lewy margines rynny przed następującym wierszem kodu, aby ustawić punkt przerwania:

    `res.render('index', { title: 'Express', "data": getData() });`

    Punkty przerwania są najbardziej podstawową i istotną cechą niezawodnego debugowania. Punkt przerwania wskazuje, gdzie visual studio należy zawiesić uruchomiony kod, dzięki czemu można spojrzeć na wartości zmiennych lub zachowanie pamięci lub czy gałąź kodu jest coraz uruchamiany.

    ![Ustawianie punktu przerwania](../javascript/media/tutorial-nodejs-set-breakpoint.png)

## <a name="run-the-application"></a>Uruchamianie aplikacji

1. Wybierz miejsce docelowe debugowania na pasku narzędzi Debugowania, takie jak Microsoft Edge lub Chrome.

    ::: moniker range=">=vs-2019"
    ![Wybierz obiekt docelowy debugowania](../javascript/media/vs-2019/tutorial-nodejs-deploy-target.png)
    ::: moniker-end
    ::: moniker range="vs-2017"
    ![Wybierz obiekt docelowy debugowania](../javascript/media/tutorial-nodejs-deploy-target.png)
    ::: moniker-end

    Jeśli Chrome jest dostępny na twoim komputerze, ale nie jest dostępny jako opcja, wybierz pozycję **Przeglądaj z** listy rozwijanej docelowej debugowania i wybierz Chrome jako domyślny cel przeglądarki (wybierz **pozycję Ustaw jako domyślny).**

1. Naciśnij **klawisz F5** **(Debugowanie** > **startowe),** aby uruchomić aplikację.

    Debuger wstrzymuje się w ustawionym punkcie przerwania. Teraz możesz sprawdzić stan aplikacji.

1. Umieść `getData` wskaźnik myszy na, aby wyświetlić jego właściwości w etykietce danych

    ![Sprawdzanie zmiennych](../javascript/media/tutorial-nodejs-inspect-variables.png)

1. Naciśnij **klawisz F5** **(Debug** > **Continue),** aby kontynuować.

    Aplikacja zostanie otwarta w przeglądarce.

    W oknie przeglądarki zobaczysz "Express" jako tytuł i "Witamy w Expressie" w pierwszym akapicie.

1. Kliknij przyciski, aby wyświetlić różne obrazy.

    ![Aplikacja uruchomiona w przeglądarce](../javascript/media/tutorial-nodejs-running-in-browser.png)

1. Zamknij przeglądarkę internetową.

## <a name="optional-publish-to-azure-app-service"></a>(Opcjonalnie) Publikowanie w usłudze Azure App Service

1. W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Publikuj**.

   ![Publikowanie w usłudze Azure App Service](../javascript/media/tutorial-nodejs-publish-to-azure.png)

1. Wybierz pozycję **Microsoft Azure App Service**.

    W oknie dialogowym **Usługa aplikacji** możesz zalogować się do swojego konta platformy Azure i połączyć się z istniejącymi subskrypcjami platformy Azure.

1. Wykonaj pozostałe kroki, aby wybrać subskrypcję, wybrać lub utworzyć grupę zasobów, wybrać lub utworzyć płaszczyznę usługi aplikacji, a następnie wykonaj kroki po wyświetleniu monitu o opublikowanie na platformie Azure. Aby uzyskać bardziej szczegółowe instrukcje, zobacz [Publikowanie w witrynie sieci Web platformy Azure przy użyciu wdrażania sieci Web.](https://github.com/Microsoft/nodejstools/wiki/Publish-to-Azure-Website-using-Web-Deploy)

1. Okno **Dane wyjściowe** pokazuje postęp wdrażania na platformie Azure.

    Po pomyślnym wdrożeniu aplikacja zostanie otwarta w przeglądarce uruchomionej w usłudze Azure App Service. Kliknij przycisk, aby wyświetlić obraz.

   ![Aplikacja uruchomiona w usłudze Azure App Service](../javascript/media/tutorial-nodejs-running-in-azure.png)

Gratulujemy ukończenia tego samouczka!

## <a name="next-steps"></a>Następne kroki

> [!div class="nextstepaction"]
> [Wdrażanie aplikacji w usłudze aplikacji systemu Linux](../javascript/publish-nodejs-app-azure.md)
