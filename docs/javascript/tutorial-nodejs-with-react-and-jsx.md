---
title: Tworzenie aplikacji Node.js i React
description: W tym samouczku utworzysz aplikację przy użyciu narzędzi Node.js dla programu Visual Studio
ms.custom: mvc
ms.date: 11/01/2019
ms.topic: tutorial
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jillfra
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: 55086c473929158f50f05db790cf5842f1b696db
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2020
ms.locfileid: "79550028"
---
# <a name="tutorial-create-a-nodejs-and-react-app-in-visual-studio"></a>Samouczek: Tworzenie aplikacji Node.js i React w programie Visual Studio

Visual Studio umożliwia łatwe tworzenie projektu Node.js i doświadczenie IntelliSense i innych wbudowanych funkcji, które obsługują Node.js. W tym samouczku dla programu Visual Studio utworzysz projekt aplikacji sieci web Node.js z szablonu programu Visual Studio. Następnie należy utworzyć prostą aplikację za pomocą React.

Niniejszy samouczek zawiera informacje na temat wykonywania następujących czynności:
> [!div class="checklist"]
> * Tworzenie projektu z użyciem narzędzia Node.js
> * Dodawanie pakietów npm
> * Dodawanie kodu React do aplikacji
> * Transpile JSX
> * Dołączanie debugera

## <a name="before-you-begin"></a>Przed rozpoczęciem

Oto krótkie często zadawane pytania, aby przedstawić Ci kilka kluczowych pojęć.

### <a name="what-is-nodejs"></a>Co to jest środowisko Node.js?

Node.js to środowisko wykonawcze JavaScript po stronie serwera, które wykonuje obsługę serwera JavaScript po stronie serwera.

### <a name="what-is-npm"></a>Co to jest npm?

npm jest domyślnym menedżerem pakietów dla node.js. Menedżer pakietów ułatwia programistom publikowanie i udostępnianie kodu źródłowego bibliotek Node.js i ma na celu uproszczenie instalacji, aktualizacji i deinstalacji bibliotek.

### <a name="what-is-react"></a>Co to jest React?

React to struktura front-end do utworzenia interfejsu użytkownika.

### <a name="what-is-jsx"></a>Co to jest JSX?

JSX jest rozszerzeniem składni JavaScript, zwykle używane z React do opisania elementów interfejsu użytkownika. Kod JSX musi zostać przesiedlony do zwykłego języka JavaScript, zanim będzie można go uruchomić w przeglądarce.

### <a name="what-is-webpack"></a>Co to jest webpack?

webpack zawiera pliki JavaScript, dzięki czemu mogą działać w przeglądarce. Może również przekształcać lub pakować inne zasoby i zasoby. Jest często używany do określenia kompilatora, takich jak Babel lub TypeScript, do transpile JSX lub TypeScript kod do zwykłego JavaScript.

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

    Ten samouczek został przetestowany w wersji 10.16.0.

    Jeśli nie masz go zainstalowanego, zaleca się zainstalowanie wersji LTS z witryny [node.js](https://nodejs.org/en/download/) w celu uzyskania najlepszej zgodności z zewnętrznymi strukturami i bibliotekami. Node.js jest przeznaczony dla architektur 32-bitowych i 64-bitowych. Narzędzia Node.js w programie Visual Studio, uwzględnione w obciążeniu Node.js, obsługują obie wersje. Wymagany jest tylko jeden, a instalator Node.js obsługuje tylko jeden instalowany jednocześnie.
    
    Ogólnie rzecz biorąc program Visual Studio automatycznie wykrywa zainstalowane środowisko uruchomieniowe Node.js. Jeśli nie wykryje zainstalowanego środowiska uruchomieniowego, można skonfigurować projekt tak, aby odwoływał się do zainstalowanego środowiska uruchomieniowego na stronie właściwości (po utworzeniu projektu kliknij prawym przyciskiem myszy węzeł projektu, wybierz polecenie **Właściwości**i ustaw **ścieżkę Node.exe**). Można użyć instalacji globalnej node.js lub można określić ścieżkę do lokalnego interpretera w każdym z projektów Node.js. 

## <a name="create-a-project"></a>Tworzenie projektu

Najpierw utwórz projekt aplikacji sieci web Node.js.

1. Otwórz program Visual Studio.

1. Tworzenie nowego projektu.

    ::: moniker range=">=vs-2019"
    Naciśnij **klawisz Esc,** aby zamknąć okno początkowe. Wpisz **Ctrl + Q,** aby otworzyć pole wyszukiwania, wpisz **Node.js**, a następnie wybierz **puste node.js Aplikacji sieci Web - JavaScript**. (Chociaż w tym samouczku używa się kompilatora TypeScript, kroki wymagają, aby rozpocząć od szablonu **JavaScript.)**
    
    W wyświetlonym oknie dialogowym wybierz pozycję **Utwórz**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Na górnym pasku menu wybierz pozycję **Plik** > **nowego** > **projektu**. W lewym okienku okna dialogowego **Nowy projekt** rozwiń węzeł **JavaScript**, a następnie wybierz polecenie **Node.js**. W środkowym okienku wybierz pozycję **Pusta aplikacja sieci Web Node.js**, wpisz nazwę **NodejsWebAppBlank**, a następnie wybierz przycisk **OK**.
    ::: moniker-end
    Jeśli nie widzisz szablonu projektu **pustego pliku Node.js Web Application,** należy dodać obciążenie **deweloperne node.js.** Aby uzyskać szczegółowe instrukcje, zobacz [Wymagania wstępne](#prerequisites).

    Visual Studio tworzy nowe rozwiązanie i otwiera projekt.

    ![Projekt Node.js w Eksploratorze rozwiązań](../javascript/media/tutorial-nodejs-react-project-structure.png)

    (1) Wyróżniony **pogrubioną czcionką** jest twój projekt, używając nazwy podanych w oknie dialogowym **Nowy projekt.** W systemie plików ten projekt jest reprezentowany przez plik *njsproj* w folderze projektu. Właściwości i zmienne środowiskowe skojarzone z projektem można ustawić, klikając prawym przyciskiem myszy projekt i wybierając polecenie **Właściwości**. Można wykonać potknięcia zaokrąglenia z innymi narzędziami programistycznymi, ponieważ plik projektu nie wprowadzać niestandardowych zmian w źródle projektu Node.js.

    (2) Na najwyższym poziomie jest rozwiązanie, które domyślnie ma taką samą nazwę jak projekt. Rozwiązanie, reprezentowane przez plik *.sln* na dysku, jest kontenerem dla jednego lub więcej powiązanych projektów.

    (3) Węzeł npm pokazuje zainstalowane pakiety npm. Możesz kliknąć prawym przyciskiem myszy węzeł npm, aby wyszukać i zainstalować pakiety npm za pomocą okna dialogowego lub zainstalować i zaktualizować pakiety przy użyciu ustawień w *pliku package.json* i kliknij prawym przyciskiem myszy opcje w węźle npm.

    (4) *package.json* jest plikiem używanym przez npm do zarządzania zależnościami pakietów i wersjami pakietów dla pakietów zainstalowanych lokalnie. Aby uzyskać więcej informacji na temat tego pliku, zobacz [konfigurację package.json](../javascript/configure-packages-with-package-json.md)

    (5) Pliki projektu, takie jak *server.js* pojawiają się w węźle projektu. *server.js* jest plik startowy projektu i dlatego pojawia się **pogrubioną**. Plik startowy można ustawić, klikając prawym przyciskiem myszy plik w projekcie i wybierając **polecenie Ustaw jako plik startowy Node.js**.

## <a name="add-npm-packages"></a>Dodawanie pakietów npm

Ta aplikacja wymaga wielu modułów npm, aby działać poprawnie.

* Reagować
* reasja-dom
* express
* ścieżka
* ts-ładowarka
* typescript
* pakiet internetowy
* webpack-cli

1. W Eksploratorze rozwiązań (prawe okienko) kliknij prawym przyciskiem myszy węzeł **npm** w projekcie i wybierz polecenie **Zainstaluj nowe pakiety npm**.

    W oknie dialogowym **Instalowanie nowych pakietów npm** można zainstalować najnowszą wersję pakietu lub określić wersję. Jeśli zdecydujesz się zainstalować bieżącą wersję tych pakietów, ale później napotkasz nieoczekiwane błędy, może być konieczne zainstalowanie dokładnych wersji pakietu opisanych w dalszej części tych kroków.

1. W oknie dialogowym **Instalowanie nowych pakietów npm** wyszukaj pakiet react i wybierz pozycję **Zainstaluj pakiet,** aby go zainstalować.

    ![Instalowanie pakietów npm](../javascript/media/tutorial-nodejs-react-install-packages.png)

    Wybierz okno **Dane wyjściowe,** aby wyświetlić postęp w instalacji pakietu (wybierz **npm** w polu **Pokaż dane wyjściowe z).** Po zainstalowaniu pakiet pojawia się pod **węzłem npm.**

    Plik *package.json* projektu jest aktualizowany o nowe informacje o pakiecie, w tym o wersję pakietu.

1. Zamiast używać interfejsu użytkownika do wyszukiwania i dodawania pozostałych pakietów po jednym na raz, wklej następujący kod do *pliku package.json*. Aby to zrobić, `dependencies` dodaj sekcję z tym kodem:

    ```json
    "dependencies": {
      "express": "~4.16.4",
      "path": "~0.12.7",
      "react": "~16.6.0",
      "react-dom": "~16.6.0",
      "ts-loader": "~5.3.0",
      "typescript": "~3.1.5",
      "webpack": "~4.23.1",
      "webpack-cli": "~3.1.2"
    }
    ```

    Jeśli w wersji `dependencies` pustego szablonu znajduje się już sekcja, po prostu zastąp ją poprzednim kodem JSON. Aby uzyskać więcej informacji na temat korzystania z tego pliku, zobacz [package.json configuration](../javascript/configure-packages-with-package-json.md).

1. Zapisz zmiany.

1. Kliknij prawym przyciskiem myszy węzeł **npm** w projekcie i wybierz polecenie **Aktualizuj pakiety npm**.

    W dolnym okienku wybierz okno **Dane wyjściowe,** aby wyświetlić postęp w instalacji pakietów. Instalacja może potrwać kilka minut i mogą nie być widoczne wyniki natychmiast. Aby wyświetlić dane wyjściowe, upewnij się, że w polu **Pokaż dane wyjściowe** w oknie Dane **wyjściowe** wybrano opcję **Npm.**

    Oto moduły npm, które pojawiają się w Eksploratorze rozwiązań po ich zainstalowaniu.

    ![pakiety npm](../javascript/media/tutorial-nodejs-react-npm-modules.png)

    > [!NOTE]
    > Jeśli wolisz zainstalować pakiety npm za pomocą wiersza polecenia, kliknij prawym przyciskiem myszy węzeł projektu i wybierz polecenie **Otwórz wiersz polecenia tutaj**. Użyj standardowych poleceń Node.js, aby zainstalować pakiety.

## <a name="add-project-files"></a>Dodawanie plików projektu

W tych krokach należy dodać cztery nowe pliki do projektu.

* *strona app.tsx*
* *webpack-config.js*
* *Index.html*
* *tsconfig.json*

Dla tej prostej aplikacji należy dodać nowe pliki projektu w katalogu głównym projektu. (W większości aplikacji zazwyczaj pliki są dodawanye do podfolderów i odpowiednio dostosowywane odwołania do ścieżki względnej).

1. W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy projekt **NodejsWebAppBlank** i wybierz polecenie **Dodaj** > **nowy element**.

1. W oknie dialogowym **Dodawanie nowego elementu** wybierz pozycję **TypeScript JSX file**, type the name *app.tsx*, and select **Add** or **OK**.

1. Powtórz te kroki, aby dodać *webpack-config.js*. Zamiast pliku JSX TypeScript wybierz **plik JavaScript**.

1. Powtórz te same kroki, aby dodać *index.html* do projektu. Zamiast pliku JavaScript wybierz **plik HTML**.

1. Powtórz te same kroki, aby dodać *tsconfig.json* do projektu. Zamiast pliku JavaScript wybierz plik **konfiguracji Języka JSON w języku TypeScript**.

## <a name="add-app-code"></a>Dodawanie kodu aplikacji

1. Otwórz *plik server.js* i zastąp istniejący kod następującym kodem:

    ```javascript
    'use strict';
    var path = require('path');
    var express = require('express');

    var app = express();

    var staticPath = path.join(__dirname, '/');
    app.use(express.static(staticPath));

    // Allows you to set port in the project properties.
    app.set('port', process.env.PORT || 3000);

    var server = app.listen(app.get('port'), function() {
        console.log('listening');
    });
    ```

   Poprzedni kod używa expressu do uruchamiania node.js jako serwera aplikacji sieci web. Ten kod ustawia port na numer portu skonfigurowany we właściwościach projektu (domyślnie port jest skonfigurowany do 1337 we właściwościach). Aby otworzyć właściwości projektu, kliknij projekt prawym przyciskiem myszy w Eksploratorze **rozwiązań**i wybierz polecenie Właściwości .

1. Otwórz *plik app.tsx* i dodaj następujący kod:

    ```javascript
    declare var require: any

    var React = require('react');
    var ReactDOM = require('react-dom');

    export class Hello extends React.Component {
        render() {
            return (
                <h1>Welcome to React!!</h1>
            );
        }
    }

    ReactDOM.render(<Hello />, document.getElementById('root'));
    ```

    Poprzedni kod używa składni JSX i React, aby wyświetlić prosty komunikat.

1. Otwórz *index.html* i zastąp sekcję **treści** następującym kodem:

    ```html
    <body>
        <div id="root"></div>
        <!-- scripts -->
        <script src="./dist/app-bundle.js"></script>
    </body>
    ```

    Ta strona HTML ładuje *app-bundle.js*, który zawiera kod JSX i React transpiled do zwykłego JavaScript. Obecnie *app-bundle.js* jest pustym plikiem. W następnej sekcji można skonfigurować opcje, aby przesiedlić kod.

## <a name="configure-webpack-and-typescript-compiler-options"></a>Konfigurowanie opcji pakietu internetowego i kompilatora TypeScript

W poprzednich krokach dodano *webpack-config.js* do projektu. Następnie należy dodać kod konfiguracji pakietu internetowego. Dodasz prostą konfigurację pakietu internetowego, która określa plik wejściowy *(app.tsx)* i plik wyjściowy *(app-bundle.js)* do łączenia i transpilowania JSX do zwykłego języka JavaScript. Do transpilowania można również skonfigurować niektóre opcje kompilatora TypeScript. Ten kod jest podstawową konfiguracją, która jest przeznaczona jako wprowadzenie do pakietu internetowego i kompilatora TypeScript.

1. W Eksploratorze rozwiązań otwórz *webpack-config.js* i dodaj następujący kod.

    ```json
    module.exports = {
        devtool: 'source-map',
        entry: "./app.tsx",
        mode: "development",
        output: {
            filename: "./app-bundle.js"
        },
        resolve: {
            extensions: ['.Webpack.js', '.web.js', '.ts', '.js', '.jsx', '.tsx']
        },
        module: {
            rules: [
                {
                    test: /\.tsx$/,
                    exclude: /(node_modules|bower_components)/,
                    use: {
                        loader: 'ts-loader'
                    }
                }
            ]
        }
    }
    ```

    Kod konfiguracji pakietu internetowego nakazuje webpackowi użycie modułu ładującego TypeScript do transpilowania JSX.

1. Otwórz *plik tsconfig.json* i zastąp domyślny kod następującym kodem, który określa opcje kompilatora TypeScript:

    ```json
    {
      "compilerOptions": {
        "noImplicitAny": false,
        "module": "commonjs",
        "noEmitOnError": true,
        "removeComments": false,
        "sourceMap": true,
        "target": "es5",
        "jsx": "react"
      },
      "exclude": [
        "node_modules"
      ],
      "files": [
        "app.tsx"
      ]
    }
    ```

    *app.tsx* jest określony jako plik źródłowy.

## <a name="transpile-the-jsx"></a>Transpile the JSX

1. W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy węzeł projektu i wybierz polecenie **Otwórz wiersz polecenia tutaj**.

1. W wierszu polecenia wpisz następujące polecenie:

    `node_modules\.bin\webpack app.tsx --config webpack-config.js`

    Okno wiersza polecenia pokazuje wynik.

    ![Uruchamianie pakietu internetowego](../javascript/media/tutorial-nodejs-react-run-webpack.png)

    Jeśli widzisz żadnych błędów zamiast poprzedniego danych wyjściowych, należy je rozwiązać, zanim aplikacja będzie działać. Jeśli wersje pakietu npm różnią się od wersji pokazanych w tym samouczku, może to być źródłem błędów. Jednym ze sposobów naprawienia błędów jest użycie dokładnych wersji pokazanych we wcześniejszych krokach. Ponadto jeśli jedna lub więcej z tych wersji pakietu została przestarzała i powoduje błąd, może być konieczne zainstalowanie nowszej wersji, aby naprawić błędy. Aby uzyskać informacje na temat *używania pliku package.json* do kontrolowania wersji pakietu npm, zobacz [konfigurację package.json](../javascript/configure-packages-with-package-json.md).

1. W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy węzeł projektu i wybierz polecenie **Dodaj** > **istniejący folder,** a następnie wybierz folder *dist* i wybierz polecenie **Wybierz folder**.

    Program Visual Studio dodaje folder *dist* do projektu, który zawiera *app-bundle.js* i *app-bundle.js.map*.

1. Otwórz *app-bundle.js,* aby zobaczyć przełączony kod JavaScript.

1. Jeśli zostanie wyświetlony monit o ponowne załadowanie plików zmodyfikowanych zewnętrznie, wybierz pozycję **Tak na wszystkich**.

    ![Ładowanie zmodyfikowanych plików](../javascript/media/tutorial-nodejs-react-reload-files.png)

Za każdym razem, gdy wprowadzać zmiany w *pliku app.tsx*należy ponownie uruchomić polecenie webpack. Aby zautomatyzować ten krok, dodaj skrypt kompilacji, aby transpilować JSX.

## <a name="add-a-build-script-to-transpile-the-jsx"></a>Dodawanie skryptu kompilacji w celu transpile JSX

Począwszy od programu Visual Studio 2019 wymagany jest skrypt kompilacji. Zamiast transpiling JSX w wierszu polecenia (jak pokazano w poprzedniej sekcji), można transpile JSX podczas tworzenia z programu Visual Studio.

* Otwórz *package.json* i dodaj następującą sekcję `dependencies` po sekcji:

   ```json
   "scripts": {
    "build": "webpack-cli app.tsx --config webpack-config.js"
   }
   ```

## <a name="run-the-app"></a>Uruchomienie aplikacji

1. Wybierz Microsoft Edge lub Chrome jako bieżący cel debugowania.

    ::: moniker range=">=vs-2019"
    ![Wybierz Chrome jako miejsce docelowe debugowania](../javascript/media/vs-2019/tutorial-nodejs-react-debug-target.png)
    ::: moniker-end
    ::: moniker range="vs-2017"
    ![Wybierz Chrome jako miejsce docelowe debugowania](../javascript/media/tutorial-nodejs-react-debug-target.png)
    ::: moniker-end

    ::: moniker range=">=vs-2019"
    Jeśli Chrome jest dostępny na twoim komputerze, ale nie jest dostępny jako opcja, wybierz **pozycję Przeglądarka internetowa (nazwa przeglądarki)** > **Wybierz przeglądarkę internetową** z listy rozwijanej docelowej debugowania i wybierz **Chrome** jako domyślny cel przeglądarki.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Jeśli Chrome jest dostępny na twoim komputerze, ale nie jest dostępny jako opcja, wybierz **przeglądarkę internetową (nazwa przeglądarki)** > **Google Chrome** z listy rozwijanej docelowej debugowania i wybierz **Chrome** jako domyślny cel przeglądarki.
    ::: moniker-end

1. Aby uruchomić aplikację, naciśnij **klawisz F5** **(Debug** > **start debugowania)** lub zielony przycisk strzałki.

    Zostanie otwarte okno konsoli Node.js z portem, na którym nasłuchuje debuger.

    Program Visual Studio uruchamia aplikację, uruchamiając plik startowy *server.js*.

    ![Uruchom React w przeglądarce](../javascript/media/tutorial-nodejs-react-running-react.png)

1. Zamknij okno przeglądarki.

1. Zamknij okno konsoli.

## <a name="set-a-breakpoint-and-run-the-app"></a>Ustawianie punktu przerwania i uruchamianie aplikacji

1. W *pliku server.js*kliknij w marginesie `staticPath` deklaracji po lewej stronie deklaracji, aby ustawić punkt przerwania:

    ![Ustawianie punktu przerwania](../javascript/media/tutorial-nodejs-react-set-breakpoint.png)

    Punkty przerwania są najbardziej podstawową i istotną cechą niezawodnego debugowania. Punkt przerwania wskazuje, gdzie visual studio należy zawiesić uruchomiony kod, dzięki czemu można spojrzeć na wartości zmiennych lub zachowanie pamięci lub czy gałąź kodu jest coraz uruchamiany.

1. Aby uruchomić aplikację, naciśnij **klawisz F5** (**Debugowanie** > **start debugowania**).

    Debuger wstrzymuje się w punkcie przerwania, który można ustawić (bieżąca instrukcja jest oznaczona na żółto). Teraz możesz sprawdzić stan aplikacji, najeżdżając kursorem na zmienne, które są obecnie w zakresie, używając okien debugera, takich jak **okna Locals** i **Watch.**

1. Naciśnij **klawisz F5,** aby kontynuować aplikację.

1. Jeśli chcesz korzystać z narzędzi programistycznych Chrome lub F12 Tools dla microsoft edge, naciśnij **klawisz F12**. Za pomocą tych narzędzi można sprawdzić dom i interakcji z aplikacją za pomocą konsoli JavaScript.

1. Zamknij przeglądarkę internetową i konsolę.

## <a name="set-and-hit-a-breakpoint-in-the-client-side-react-code"></a>Ustaw i trafienie punktu przerwania w kodzie React po stronie klienta

W poprzedniej sekcji dołączona jest debuger do kodu Node.js po stronie serwera. Aby dołączyć debuger z programu Visual Studio i trafić punkty przerwania w kodzie React po stronie klienta, debuger potrzebuje pomocy w celu zidentyfikowania prawidłowego procesu. Oto jeden ze sposobów, aby to włączyć.

### <a name="prepare-the-browser-for-debugging"></a>Przygotowanie przeglądarki do debugowania

::: moniker range=">=vs-2019"
W tym scenariuszu użyj microsoft edge (Chromium), obecnie o nazwie **Microsoft Edge Beta** w IDE lub Chrome.
::: moniker-end
::: moniker range="vs-2017"
W tym scenariuszu użyj Chrome.
::: moniker-end

1. Zamknij wszystkie okna przeglądarki docelowej.

   Inne wystąpienia przeglądarki mogą uniemożliwić otwarcie przeglądarki z włączonym debugowaniem. (Rozszerzenia przeglądarki mogą działać i uniemożliwiać pełny tryb debugowania, więc może być konieczne otwarcie Menedżera zadań w celu znalezienia nieoczekiwanych wystąpień Chrome).

   ::: moniker range=">=vs-2019"
   W przypadku przeglądarki Microsoft Edge (Chromium) zamknij również wszystkie wystąpienia Chrome. Ponieważ obie przeglądarki współużytkuje podstawy kodu chromu, daje to najlepsze wyniki.
   ::: moniker-end

2. Uruchom przeglądarkę z włączonym debugowaniem.

    ::: moniker range=">=vs-2019"
    Począwszy od programu Visual Studio `--remote-debugging-port=9222` 2019, można ustawić flagę podczas uruchamiania przeglądarki, wybierając pozycję **Przeglądaj z...** > z paska narzędzi **Debugowania,** a następnie wybierając pozycję **Dodaj**, a następnie ustawiając flagę w polu **Argumenty.** Użyj innej przyjaznej nazwy dla przeglądarki, takiej jak **Edge z debugowaniem** lub **Chrome z debugowaniem**. Aby uzyskać szczegółowe informacje, zobacz [Informacje o wersji](/visualstudio/releases/2019/release-notes-v16.2).

    ![Ustawianie otwierania przeglądarki z włączoną debugowaniem](../javascript/media/tutorial-nodejs-react-edge-with-debugging.png)

    Możesz też otworzyć polecenie **Uruchom** za pomocą przycisku **Start** systemu Windows (kliknij prawym przyciskiem myszy i wybierz polecenie **Uruchom)** i wprowadź następujące polecenie:

    `msedge --remote-debugging-port=9222`

    Lub

    `chrome.exe --remote-debugging-port=9222`
    ::: moniker-end

    ::: moniker range="vs-2017"
    Otwórz polecenie **Uruchom** z przycisku **Start** systemu Windows (kliknij prawym przyciskiem myszy i wybierz polecenie **Uruchom)** i wprowadź następujące polecenie:

    `chrome.exe --remote-debugging-port=9222`
    ::: moniker-end

    Spowoduje to uruchomienie przeglądarki z włączonym debugowaniem.

    Aplikacja nie jest jeszcze uruchomiona, więc masz pustą stronę przeglądarki.

### <a name="attach-the-debugger-to-client-side-script"></a>Dołączanie debugera do skryptu po stronie klienta

1. Przełącz się do programu Visual Studio, a następnie ustaw punkt przerwania w kodzie źródłowym, *app-bundle.js* lub *app.tsx*.

    W przypadku *pliku app-bundle.js*ustaw `render()` punkt przerwania w funkcji, jak pokazano na poniższej ilustracji:

    ![Ustawianie punktu przerwania](../javascript/media/tutorial-nodejs-react-set-breakpoint-client-code.png)

    Aby znaleźć `render()` tę funkcję w pliku *transpiled app-bundle.js,* użyj **klawisza Ctrl**+**F** (**Edytuj** > **znajdowanie i zamienianie** > **szybkiego znajdowania**).

    Dla *app.tsx*, ustawić punkt `render()` przerwania `return` wewnątrz funkcji, na instrukcji.

    ![Ustawianie punktu przerwania](../javascript/media/tutorial-nodejs-react-set-breakpoint-in-tsx-file.png)

2. Jeśli ustawiasz punkt przerwania w pliku *tsx* (a nie *app-bundle.js),* musisz zaktualizować *webpack-config.js*. Zastąp następujący kod:

    ```javascript
    output: {
        filename: "./app-bundle.js",
    },
    ```

    z tym kodem:

    ```javascript
    output: {
        filename: "./app-bundle.js",
        devtoolModuleFilenameTemplate: '[resource-path]'  // removes the webpack:/// prefix
    },
    ```

    Jest to ustawienie tylko do rozwoju, aby włączyć debugowanie w programie Visual Studio. To ustawienie umożliwia zastąpienie wygenerowanych odwołań w pliku mapy źródłowej, *app-bundle.js.map,* podczas tworzenia aplikacji. Domyślnie odwołania do pakietu webpack w pliku mapy źródłowej zawierają prefiks *webpack:///,* który uniemożliwia programowi Visual Studio znajdowanie pliku *źródłowego, app.tsx*. W szczególności po wprowadzeniu tej zmiany odwołanie do pliku źródłowego, *app.tsx*, zostanie zmienione z *webpack:///./app.tsx* na *./app.tsx*, co umożliwia debugowanie.

3. Wybierz przeglądarkę docelową jako miejsce docelowe debugowania w programie Visual Studio, a następnie naciśnij **klawisze Ctrl**+**F5** **(Debugowanie** > **start bez debugowania),** aby uruchomić aplikację w przeglądarce.

    ::: moniker range=">=vs-2019"
    Jeśli utworzono konfigurację przeglądarki o przyjaznej nazwie, wybierz go jako miejsce docelowe debugowania.
    ::: moniker-end

    Aplikacja zostanie otwarta w nowej karcie przeglądarki.

4. Wybierz **pozycję Debugowanie** > **dołączanie do procesu**.

    > [!TIP]
    > Począwszy od programu Visual Studio 2017, po dołączeniu do procesu po raz pierwszy, wykonując następujące kroki, można szybko ponownie dołączyć do tego samego procesu, wybierając **debugowanie** > **ponownie do procesu.**

5. W oknie dialogowym **Dołączanie do procesu** pobierz filtrowany wykaz wystąpień przeglądarki, do których można dołączyć.

    ::: moniker range=">=vs-2019"
    W programie Visual Studio 2019 wybierz odpowiedni debuger dla przeglądarki docelowej, **JavaScript (Chrome)** lub **JavaScript (Microsoft Edge - Chromium)** w polu **Dołącz do,** wpisz **chrome** lub **edge** w polu filtru, aby filtrować wyniki wyszukiwania.
    ::: moniker-end
    ::: moniker range="vs-2017"
    W programie Visual Studio 2017 wybierz **pozycję Kod zestawu Webkit** w polu **Dołącz do,** wpisz **chrome** w polu filtru, aby filtrować wyniki wyszukiwania.
    ::: moniker-end

6. Wybierz proces przeglądarki z właściwym portem hosta (localhost w tym przykładzie) i wybierz **dołącz**.

    Port (1337) może również pojawić się w polu **Tytuł,** aby ułatwić wybranie poprawnego wystąpienia przeglądarki.

    ::: moniker range=">=vs-2019"
    W poniższym przykładzie pokazano, jak to wygląda dla przeglądarki Microsoft Edge (Chromium).

    ![Dołącz do procesu](../javascript/media/tutorial-nodejs-react-attach-to-process-edge.png)
    ::: moniker-end
    ::: moniker range="vs-2017"
    ![Dołącz do procesu](../javascript/media/tutorial-nodejs-react-attach-to-process.png)

    Wiesz, że debuger został dołączony poprawnie, gdy Eksplorator DOM i konsola JavaScript są otwarte w programie Visual Studio. Te narzędzia debugowania są podobne do narzędzi programistycznych Chrome i F12 Tools for Microsoft Edge.
    ::: moniker-end

    > [!TIP]
    > Jeśli debuger nie zostanie dołączony i zostanie wyświetlony komunikat "Nie można dołączyć do procesu. Operacja nie jest legalna w bieżącym stanie.", użyj Menedżera zadań, aby zamknąć wszystkie wystąpienia przeglądarki docelowej przed uruchomieniem przeglądarki w trybie debugowania. Rozszerzenia przeglądarki mogą być uruchomione i uniemożliwia tryb pełnego debugowania.

7. Ponieważ kod z punktem przerwania już wykonane, odśwież stronę przeglądarki, aby trafić punkt przerwania.

    Wstrzymane w debugerze można sprawdzić stan aplikacji, najeżdżając kursorem na zmienne i używając okien debugera. Debuger można przejść przez krok po kroku przez kod (**F5**, **F10**i **F11**). Aby uzyskać więcej informacji na temat podstawowych funkcji debugowania, zobacz [Pierwsze spojrzenie na debuger](../debugger/debugger-feature-tour.md).

    Punkt przerwania można trafić w *pliku app-bundle.js* lub jego lokalizacji mapowanej w *pliku app.tsx*, w zależności od kroków, które zostały wcześniej wykonać, wraz ze środowiskiem i stanem przeglądarki. Tak czy inaczej, można przejść przez kod i zbadać zmienne.

   * Jeśli chcesz podzielić się na kod w *app.tsx* i nie możesz tego zrobić, użyj **dołącz do procesu,** jak opisano w poprzednich krokach, aby dołączyć debuger. Upewnij się, że środowisko jest poprawnie skonfigurowane:

      * Zamknięto wszystkie wystąpienia przeglądarki, w tym rozszerzenia Chrome (za pomocą Menedżera zadań), dzięki czemu można uruchomić przeglądarkę w trybie debugowania. Upewnij się, że przeglądarka została uruchomiona w trybie debugowania.

      * Upewnij się, że plik mapy źródłowej zawiera odwołanie do *pliku ./app.tsx,* a nie *webpack:///./app.tsx*, co uniemożliwia debugerowi programu Visual Studio lokalizowanie *pliku app.tsx*.
       Alternatywnie, jeśli chcesz podzielić się na kod w *app.tsx* i `debugger;` nie możesz tego zrobić, spróbuj użyć instrukcji w *app.tsx*lub ustaw punkty przerwania w narzędziach programistycznych Chrome (lub F12 Tools for Microsoft Edge).

   * Jeśli chcesz podzielić się na kod w *app-bundle.js* i nie możesz tego zrobić, usuń plik mapy źródłowej, *app-bundle.js.map*.

## <a name="next-steps"></a>Następne kroki

> [!div class="nextstepaction"]
> [Wdrażanie aplikacji w usłudze aplikacji systemu Linux](../javascript/publish-nodejs-app-azure.md)
