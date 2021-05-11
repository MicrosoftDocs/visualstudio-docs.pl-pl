---
title: Tworzenie aplikacji Node.js React
description: Dowiedz się, jak utworzyć Node.js aplikacji internetowej na podstawie Visual Studio szablonu.
ms.custom: ''
ms.date: 4/21/2020
ms.topic: tutorial
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jmartens
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: 80516adffcb058d6ce28751e7a9f30002ca3a640
ms.sourcegitcommit: a0f5e7188838c5989c9cc78d99fb29bb2813501e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/11/2021
ms.locfileid: "109729302"
---
# <a name="tutorial-create-a-nodejs-and-react-app-in-visual-studio"></a>Samouczek: tworzenie aplikacji Node.js React w programie Visual Studio

Visual Studio umożliwia łatwe tworzenie projektu Node.js i obsługę funkcji IntelliSense oraz innych wbudowanych funkcji, które obsługują Node.js. W tym samouczku Visual Studio aplikacji internetowej utworzysz projekt Node.js aplikacji internetowej na podstawie Visual Studio szablonu. Następnie utworzysz prostą aplikację przy użyciu oprogramowania React.

Ten samouczek zawiera informacje na temat wykonywania następujących czynności:
> [!div class="checklist"]
> * Tworzenie projektu platformy Node.js
> * Dodawanie pakietów npm
> * Dodawanie kodu react do aplikacji
> * Transpile JSX
> * Dołączanie debugera

## <a name="before-you-begin"></a>Zanim rozpoczniesz

Poniżej znajdziesz krótkie często zadawane pytania, w których znajdziesz wprowadzenie do niektórych kluczowych pojęć.

### <a name="what-is-nodejs"></a>Co to jest środowisko Node.js?

Node.js to środowisko uruchomieniowe JavaScript po stronie serwera, które wykonuje skrypt JavaScript po stronie serwera.

### <a name="what-is-npm"></a>Co to jest npm?

Npm jest domyślnym menedżerem pakietów dla Node.js. Menedżer pakietów ułatwia programistom publikowanie i udostępnianie kodu źródłowego bibliotek Node.js oraz upraszcza instalowanie, aktualizowanie i dezinstalację bibliotek.

### <a name="what-is-react"></a>Co to jest react?

React to platforma front end do tworzenia interfejsu użytkownika.

### <a name="what-is-jsx"></a>Co to jest JSX?

JSX to rozszerzenie składni języka JavaScript, zwykle używane z platformą React do opisywania elementów interfejsu użytkownika. Kod JSX musi zostać transpilowany na zwykły kod JavaScript, zanim będzie można go uruchomić w przeglądarce.

### <a name="what-is-webpack"></a>Co to jest pakiet webpack?

Pakiet webpack zawiera pliki JavaScript, które można uruchamiać w przeglądarce. Może również przekształcać lub pakować inne zasoby i zasoby. Jest często używany do określania kompilatora, takiego jak Babyl lub TypeScript, w celu transpilowania kodu JSX lub TypeScript na zwykły kod JavaScript.

## <a name="prerequisites"></a>Wymagania wstępne

* Musisz mieć Visual Studio i obciążenie Node.js tworzenia aplikacji.

    ::: moniker range=">=vs-2019"
    Jeśli jeszcze nie zainstalowano programu Visual Studio 2019, [](https://visualstudio.microsoft.com/downloads/) przejdź do strony pobierania Visual Studio, aby zainstalować ją bezpłatnie.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Jeśli jeszcze nie zainstalowano programu Visual Studio 2017, [](https://visualstudio.microsoft.com/downloads/) przejdź do strony pobierania Visual Studio, aby zainstalować ją bezpłatnie.
    ::: moniker-end

    Jeśli musisz zainstalować obciążenie, ale masz już Visual Studio, przejdź do tematu Narzędzia Pobierz narzędzia i  >  **funkcje...,** co spowoduje otwarcie Instalator programu Visual Studio. Wybierz obciążenie **Node.js dewelopera,** a następnie wybierz pozycję **Modyfikuj.**

    ![Node.js obciążenia w Instalatorze programu VS](../ide/media/quickstart-nodejs-workload.png)

* Musisz mieć zainstalowane Node.js uruchomieniowe.

    Ten samouczek został przetestowany przy użyciu wersji 12.6.2.

    Jeśli nie jest on zainstalowany, zalecamy zainstalowanie wersji LTS z witryny internetowejNode.js, aby [ uzyskać ](https://nodejs.org/en/download/) najlepszą zgodność z zewnętrznymi platformami i bibliotekami. Node.js jest zbudowana dla architektur 32-bitowych i 64-bitowych. Narzędzia Node.js w Visual Studio, zawarte w obciążeniu Node.js, obsługują obie wersje. Wymagany jest tylko jeden Node.js a instalator obsługuje tylko jedną funkcję instalowaną jednocześnie.

    Ogólnie rzecz biorąc, Visual Studio automatycznie wykrywa zainstalowane Node.js uruchomieniowe. Jeśli program nie wykryje zainstalowanego środowiska uruchomieniowego, możesz skonfigurować projekt tak, aby odwołył się do zainstalowanego środowiska uruchomieniowego na stronie właściwości (po utworzeniu projektu kliknij prawym przyciskiem myszy węzeł projektu, wybierz polecenie Właściwości **(lub** naciśnij klawisz **Alt**  +  **Enter**) **i** ustaw ścieżkęNode.exe ). Można użyć globalnej instalacji Node.js lub określić ścieżkę do interpretera lokalnego w każdym z Node.js projektów. 

## <a name="create-a-project"></a>Tworzenie projektu

Najpierw utwórz projekt Node.js aplikacji internetowej.

1. Otwórz program Visual Studio.

1. Tworzenie nowego projektu.

    ::: moniker range=">=vs-2019"
    Naciśnij **klawisz Esc,** aby zamknąć okno uruchamiania. Naciśnij **klawisze Ctrl + Q,** aby otworzyć pole wyszukiwania, wpiszNode.js, **a** następnie wybierz pozycję Pusta Node.js web application **- JavaScript.** (Mimo że w tym samouczku jest używany kompilator języka TypeScript, kroki wymagają rozpoczęcia od szablonu **języka JavaScript).**
    
    W wyświetlonym oknie dialogowym wybierz pozycję **Utwórz.**
    ::: moniker-end
    ::: moniker range="vs-2017"
    Na górnym pasku menu wybierz pozycję **File** New Project  >  **(Plik nowy**  >  **projekt).** W lewym okienku okna dialogowego **Nowy** projekt rozwiń pozycję **JavaScript,** a następnie wybierz **pozycjęNode.js**. W środkowym okienku wybierz pozycję **Node.js aplikacji internetowej,** wpisz nazwę **NodejsWebAppBlank,** a następnie wybierz przycisk **OK.**
    ::: moniker-end
    Jeśli nie widzisz szablonu projektu **Blank Node.js Web Application,** musisz dodaćNode.js **projektowego.** Aby uzyskać szczegółowe instrukcje, zobacz [Wymagania wstępne.](#prerequisites)

    Visual Studio tworzy nowe rozwiązanie i otwiera projekt.

    ![Node.js projektu w programie Eksplorator rozwiązań](../javascript/media/tutorial-nodejs-react-project-structure.png)

    (1) Wyróżnione  pogrubioną czcionką jest projekt, używając nazwy nadanych w oknie **dialogowym Nowy** projekt. W systemie plików ten projekt jest reprezentowany przez plik *.njsproj* w folderze projektu. Możesz ustawić właściwości i zmienne środowiskowe skojarzone z projektem, klikając projekt prawym przyciskiem myszy i wybierając polecenie **Właściwości** (lub naciśnij **klawisz Alt**  +  **Enter**). Można wykonać rundy z innymi narzędziami programistyki, ponieważ plik projektu nie wprowadza niestandardowych zmian w źródle Node.js projektu.

    (2) Na najwyższym poziomie znajduje się rozwiązanie, które domyślnie ma taką samą nazwę jak projekt. Rozwiązanie reprezentowane przez plik *sln* na dysku jest kontenerem dla co najmniej jednego powiązanego projektu.

    (3) Węzeł npm pokazuje wszystkie zainstalowane pakiety npm. Możesz kliknąć prawym przyciskiem myszy węzeł npm, aby wyszukać i zainstalować pakiety npm przy użyciu okna dialogowego lub zainstalować i zaktualizować pakiety przy użyciu ustawień w programie *package.js* i kliknąć prawym przyciskiem myszy opcje w węźle npm.

    (4) *package.jsto* plik używany przez program npm do zarządzania zależnościami pakietów i wersjami pakietów dla lokalnie zainstalowanych pakietów. Aby uzyskać więcej informacji, zobacz [Zarządzanie pakietami npm.](../javascript/npm-package-management.md)

    (5) Pliki projektu, takie *server.js* są wyświetlane w węźle projektu. *server.js* to plik startowy projektu i dlatego jest on pogrubiony.  Plik startowy można ustawić, klikając prawym przyciskiem myszy plik w projekcie i wybierając polecenie Ustaw jako **Node.js startowego**.

## <a name="add-npm-packages"></a>Dodawanie pakietów npm

Ta aplikacja wymaga poprawnego działania kilku modułów npm.

* Reagować
* react-dom
* express
* path
* ts-loader
* typescript
* pakiet webpack
* webpack-cli

1. W Eksplorator rozwiązań (w prawym okienku) kliknij prawym przyciskiem myszy węzeł **npm** w projekcie i wybierz polecenie **Zainstaluj nowe pakiety npm.**

    W **oknie dialogowym Instalowanie nowych** pakietów npm możesz zainstalować najnowszą wersję pakietu lub określić wersję. Jeśli zdecydujesz się zainstalować bieżącą wersję tych pakietów, ale później wystąpiły nieoczekiwane błędy, możesz zainstalować dokładne wersje pakietów opisane w dalszej części tych kroków.

1. W **oknie dialogowym Install New npm Packages (Instalowanie** nowych pakietów npm) wyszukaj pakiet react i wybierz pozycję Install Package (Zainstaluj **pakiet),** aby go zainstalować.

    ![Instalowanie pakietów npm](../javascript/media/tutorial-nodejs-react-install-package.png)

    Wybierz okno **Dane wyjściowe,** aby zobaczyć postęp instalacji pakietu (wybierz pozycję **Npm** w polu **Pokaż dane wyjściowe** z). Po zainstalowaniu pakiet jest wyświetlany w **węźle npm.**

    Plik aplikacji projektu *package.js* zaktualizowany o informacje o nowym pakiecie, w tym o wersji pakietu.

1. Zamiast używać interfejsu użytkownika do wyszukiwania i dodawania pozostałych pakietów po jednym na raz, wklej następujący kod dopackage.js *na .* W tym celu dodaj `dependencies` sekcję z tym kodem:

    ```json
    "dependencies": {
      "express": "~4.17.1",
      "path": "~0.12.7",
      "react": "~16.13.1",
      "react-dom": "~16.13.1",
      "ts-loader": "~7.0.1",
      "typescript": "~3.8.3",
      "webpack": "~4.42.1",
      "webpack-cli": "~3.3.11"
    }
    ```

    Jeśli w Twojej wersji pustego szablonu istnieje już sekcja, wystarczy zastąpić ją poprzednim `dependencies` kodem JSON. Aby uzyskać więcej informacji na temat korzystania z tego pliku, zobacz [package.jsna temat konfiguracji](../javascript/configure-packages-with-package-json.md).

1. Zapisz zmiany.

1. Kliknij prawym przyciskiem myszy **węzeł npm** w projekcie i wybierz polecenie **Zainstaluj pakiety npm.**

    To polecenie uruchamia polecenie npm install bezpośrednio.

    W dolnym okienku wybierz okno Dane **wyjściowe,** aby zobaczyć postęp instalowania pakietów. Instalacja może potrwać kilka minut, a wyniki mogą nie zostać natychmiast wyświetlonych. Aby wyświetlić dane wyjściowe, upewnij się, że w polu Pokaż dane **wyjściowe** z w oknie **Dane wyjściowe** wybierz pozycję **Npm.** (Aby otworzyć okno, wybierz pozycję **Widok**  >  **Dane** wyjściowe lub naciśnij **klawisze Ctrl**  +  **Alt**  +  **O).**

    Poniżej znajdują się moduły npm wyświetlane w Eksplorator rozwiązań po ich zainstalowaniu.

    ![Pakiety npm](../javascript/media/tutorial-nodejs-react-npm-modules-installed.png)

    > [!NOTE]
    > Jeśli wolisz instalować pakiety npm przy użyciu wiersza polecenia, kliknij prawym przyciskiem myszy węzeł projektu i wybierz polecenie **Otwórz wiersz polecenia tutaj.** Do instalowania pakietów Node.js standardowych poleceń.

## <a name="add-project-files"></a>Dodawanie plików projektu

W tych krokach dodasz cztery nowe pliki do projektu.

* *app.tsx*
* *webpack-config.js*
* *index.html*
* *tsconfig.json*

W przypadku tej prostej aplikacji dodasz nowe pliki projektu w katalogu głównym projektu. (W większości aplikacji zwykle dodaje się pliki do podfolderów i odpowiednio dostosowuje się odwołania do ścieżki względnej).

1. W Eksplorator rozwiązań prawym przyciskiem myszy projekt **NodejsWebAppBlank** i wybierz polecenie Dodaj nowy  >  **element** (lub naciśnij **klawisze Ctrl**  +  **SHIFT**  +  **A**).

1. W **oknie dialogowym Dodawanie** nowego elementu wybierz pozycję **Plik JSX TypeScript,** wpisz nazwę *app.tsx* i wybierz pozycję **Dodaj** lub **OK.**

1. Powtórz te kroki, aby *dodaćwebpack-config.js*. Zamiast pliku JSX TypeScript wybierz pozycję **Plik JavaScript.**

1. Powtórz te same kroki, aby *index.html* do projektu. Zamiast pliku JavaScript wybierz pozycję **Plik HTML.**

1. Powtórz te same kroki, aby *tsconfig.jsdo* projektu. Zamiast pliku JavaScript wybierz pozycję **Plik konfiguracji JSON języka TypeScript.**

## <a name="add-app-code"></a>Dodawanie kodu aplikacji

1. Otwórz *server.js* i zastąp istniejący kod następującym kodem:

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

   Powyższy kod używa programu Express do uruchamiania Node.js jako serwera aplikacji internetowej. Ten kod ustawia port na numer portu skonfigurowany we właściwościach projektu (domyślnie port jest skonfigurowany we właściwościach na 1337). Aby otworzyć właściwości projektu, kliknij prawym przyciskiem myszy projekt w oknie Eksplorator rozwiązań wybierz pozycję **Właściwości.**

1. Otwórz *program app.tsx* i dodaj następujący kod:

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

    Powyższy kod używa składni JSX i react do wyświetlania prostego komunikatu.

1. Otwórz *index.html* i zastąp **sekcję body** następującym kodem:

    ```html
    <body>
        <div id="root"></div>
        <!-- scripts -->
        <script src="./dist/app-bundle.js"></script>
    </body>
    ```

    Ta strona HTML *ładujeapp-bundle.js*, który zawiera transpilowany kod JSX i React na zwykły kod JavaScript. Obecnie *app-bundle.js* jest pustym plikiem. W następnej sekcji skonfigurujesz opcje transpilowania kodu.

## <a name="configure-webpack-and-typescript-compiler-options"></a>Konfigurowanie opcji kompilatora webpack i TypeScript

W poprzednich krokach dodano *webpack-config.js* projektu. Następnie należy dodać kod konfiguracji pakietów webpack. Dodasz prostą konfigurację pakietów webpack, która określa plik wejściowy *(app.tsx)* i plik wyjściowy *(app-bundle.js*) na celu kompilowanie i transpilowanie pliku JSX w języku JavaScript. W przypadku transpilowania należy również skonfigurować niektóre opcje kompilatora języka TypeScript. Ten kod jest podstawową konfiguracją, która ma stanowić wprowadzenie do pakietów webpack i kompilatora języka TypeScript.

1. W Eksplorator rozwiązań otwórz *webpack-config.js* i dodaj następujący kod.

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

    Kod konfiguracji pakietów webpack nakazuje pakietowi webpack użycie modułu ładującego TypeScript do transpilowania pliku JSX.

1. Otwórz *tsconfig.jsi* zastąp kod domyślny następującym kodem, który określa opcje kompilatora języka TypeScript:

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

    *Plik app.tsx* jest określony jako plik źródłowy.

## <a name="transpile-the-jsx"></a>Transpilowanie JSX

1. W Eksplorator rozwiązań kliknij prawym przyciskiem myszy węzeł projektu i wybierz polecenie **Otwórz wiersz polecenia tutaj.**

1. W wierszu polecenia wpisz następujące polecenie:

    `node_modules\.bin\webpack app.tsx --config webpack-config.js`

    W oknie wiersza polecenia zostanie wyświetlony wynik.

    ![Uruchamianie pakietów webpack](../javascript/media/tutorial-nodejs-react-run-webpack-cmd.png)

    Jeśli zamiast powyższych danych wyjściowych zostaną wyświetlony jakiekolwiek błędy, należy je rozwiązać, zanim aplikacja będzie działać. Jeśli wersje pakietu npm są inne niż wersje pokazane w tym samouczku, może to być źródłem błędów. Jednym ze sposobów na naprawienie błędów jest użycie dokładnych wersji pokazanych we wcześniejszych krokach. Ponadto jeśli co najmniej jedna z tych wersji pakietu jest przestarzała i powoduje błąd, może być konieczne zainstalowanie najnowszej wersji w celu naprawienia błędów. Aby uzyskać informacje na temat *używaniapackage.jsna do* kontrolowania wersji pakietu npm, [ zobaczpackage.jskonfiguracji](../javascript/configure-packages-with-package-json.md).

1. W Eksplorator rozwiązań prawym przyciskiem myszy węzeł projektu i wybierz polecenie **Dodaj** istniejący  >  **folder,** a następnie wybierz folder *dist* i wybierz **pozycję Wybierz folder**.

    Visual Studio dodaje do projektu folder *dist,* który zawiera pliki *app-bundle.js* *iapp-bundle.js.map.*

1. Otwórz *app-bundle.js,* aby zobaczyć transpilowany kod JavaScript.

1. Jeśli zostanie wyświetlony monit o ponowne załadowanie zewnętrznie zmodyfikowanych plików, wybierz **pozycję Tak na wszystkie.**

    ![Ładowanie zmodyfikowanych plików](../javascript/media/tutorial-nodejs-react-reload-files.png)

Za każdym razem, gdy wprowadzasz zmiany w *programie app.tsx,* musisz ponownie uruchomić polecenie webpack. Aby zautomatyzować ten krok, dodaj skrypt kompilacji w celu transpilowania skryptu JSX.

## <a name="add-a-build-script-to-transpile-the-jsx"></a>Dodawanie skryptu kompilacji w celu transpilowania JSX

Począwszy od Visual Studio 2019 r., wymagany jest skrypt kompilacji. Zamiast transpilować JSX w wierszu polecenia (jak pokazano w poprzedniej sekcji), można transpilować JSX podczas kompilowania z Visual Studio.

* Otwórz *package.jsi* dodaj następującą sekcję po sekcji `dependencies` :

   ```json
   "scripts": {
    "build": "webpack-cli app.tsx --config webpack-config.js"
   }
   ```

## <a name="run-the-app"></a>Uruchamianie aplikacji

1. Wybierz serwer **sieci Web (Google Chrome)** lub **serwer internetowy (Microsoft Edge)** jako bieżący element docelowy debugowania.

    ::: moniker range=">=vs-2019"
    ![Wybieranie przeglądarki Chrome jako obiektu docelowego debugowania](../javascript/media/vs-2019/tutorial-nodejs-react-debug-target.png)
    ::: moniker-end
    ::: moniker range="vs-2017"
    ![Wybieranie przeglądarki Chrome jako obiektu docelowego debugowania](../javascript/media/tutorial-nodejs-react-debug-target.png)
    ::: moniker-end

    Jeśli przeglądarka Chrome jest dostępna na Twojej maszynie, ale nie jest dostępna jako opcja, wybierz pozycję **Przeglądaj** za pomocą z listy rozwijanej docelowego debugowania, a następnie wybierz chrome jako domyślny element docelowy przeglądarki (wybierz pozycję Ustaw jako **domyślny).**

1. Aby uruchomić aplikację, naciśnij **klawisz F5** **(Debuguj**  >  **rozpocznij debugowanie)** lub przycisk z zieloną strzałką.

    Zostanie Node.js konsoli z portem, na którym debuger nasłuchuje.

    Visual Studio uruchamia aplikację, uruchamiając plik *startowy,* server.js.

    ![Uruchamianie aplikacji React w przeglądarce](../javascript/media/tutorial-nodejs-react-running-react.png)

1. Zamknij okno przeglądarki.

1. Zamknij okno konsoli.

## <a name="set-a-breakpoint-and-run-the-app"></a>Ustawianie punktu przerwania i uruchamianie aplikacji

1. W *server.js* kliknij rynnę z lewej strony deklaracji, aby `staticPath` ustawić punkt przerwania:

    ![Zrzut ekranu przedstawiający okno Visual Studio kodu dla server.js. Czerwona kropka w lewym rynnie wskazuje, że punkt przerwania jest ustawiony dla deklaracji staticPath.](../javascript/media/tutorial-nodejs-react-set-breakpoint.png)

    Punkty przerwania to najbardziej podstawowa i najważniejsza funkcja niezawodnego debugowania. Punkt przerwania wskazuje, gdzie Visual Studio powinien wstrzymać uruchomiony kod, aby można było przyjrzeć się wartościom zmiennych, zachowaniu pamięci lub czy gałąź kodu jest uruchamiana.

1. Aby uruchomić aplikację, naciśnij **klawisz F5** **(Debuguj**  >  **rozpocznij debugowanie).**

    Debuger jest wstrzymywany w ustawionym punkcie przerwania (bieżąca instrukcja jest oznaczona kolorem żółtym). Teraz możesz sprawdzić stan aplikacji, umieszczając kursor na zmiennych, które są obecnie  w zakresie, przy użyciu okien debugera, takich jak okna Zmiennych lokalnych **i Czujka.**

1. Naciśnij **klawisz F5,** aby kontynuować aplikację.

1. Jeśli chcesz użyć narzędzia Chrome Narzędzia deweloperskie lub F12 Tools for Microsoft Edge, naciśnij **klawisz F12.** Możesz użyć tych narzędzi do zbadania modelu DOM i interakcji z aplikacją przy użyciu konsoli języka JavaScript.

1. Zamknij przeglądarkę internetową i konsolę.

## <a name="set-and-hit-a-breakpoint-in-the-client-side-react-code"></a>Ustawianie i trafianie punktu przerwania w kodzie React po stronie klienta

W poprzedniej sekcji dołączono debuger do kodu Node.js serwera. Aby dołączyć debuger z Visual Studio i trafić punkty przerwania w kodzie React po stronie klienta, debuger potrzebuje pomocy w zidentyfikowaniu prawidłowego procesu. Oto jeden ze sposobów, aby to umożliwić.

### <a name="prepare-the-browser-for-debugging"></a>Przygotowywanie przeglądarki do debugowania

::: moniker range=">=vs-2019"
W tym scenariuszu użyj nazwy Microsoft Edge (Chromium), obecnie **Microsoft Edge Beta** w ide lub Chrome.
::: moniker-end
::: moniker range="vs-2017"
W tym scenariuszu użyj przeglądarki Chrome.
::: moniker-end

1. Zamknij wszystkie okna przeglądarki docelowej.

   Inne wystąpienia przeglądarki mogą uniemożliwić otwieranie przeglądarki z włączonym debugowaniem. (Rozszerzenia przeglądarki mogą być uruchomione i uniemożliwiać pełny tryb debugowania, więc może być konieczne otwarcie okna Menedżer zadań w celu znalezienia nieoczekiwanych wystąpień przeglądarki Chrome).

   ::: moniker range=">=vs-2019"
   W Microsoft Edge (Chromium) wyłącz również wszystkie wystąpienia przeglądarki Chrome. Ponieważ obie przeglądarki współdzielą kod chromium, daje to najlepsze wyniki.
   ::: moniker-end

2. Uruchom przeglądarkę z włączonym debugowaniem.

    ::: moniker range=">=vs-2019"
    Począwszy od Visual Studio 2019 r., możesz ustawić flagę podczas uruchamiania przeglądarki, wybierając pozycję Przeglądaj za pomocą... > na pasku narzędzi Debugowanie, a następnie wybierając pozycję Dodaj , a następnie ustawiając flagę w polu `--remote-debugging-port=9222`   **Argumenty.**  Użyj innej przyjaznej nazwy przeglądarki, takiej jak **Edge z debugowaniem** lub **Chrome z debugowaniem**. Aby uzyskać szczegółowe informacje, zobacz [Informacje o wersji](/visualstudio/releases/2019/release-notes-v16.2).

    ![Konfigurowanie otwierania przeglądarki z włączonym debugowaniem](../javascript/media/tutorial-nodejs-react-edge-with-debugging.png)

    Alternatywnie otwórz polecenie **Uruchom za** pomocą przycisku Start **systemu** Windows (kliknij prawym przyciskiem myszy i wybierz polecenie **Uruchom),** a następnie wprowadź następujące polecenie:

    `msedge --remote-debugging-port=9222`

    Lub

    `chrome.exe --remote-debugging-port=9222`
    ::: moniker-end

    ::: moniker range="vs-2017"
    Otwórz polecenie **Uruchom** za pomocą przycisku Start **systemu** Windows (kliknij prawym przyciskiem myszy i wybierz polecenie **Uruchom),** a następnie wprowadź następujące polecenie:

    `chrome.exe --remote-debugging-port=9222`
    ::: moniker-end

    Uruchomi to przeglądarkę z włączonym debugowaniem.

    Aplikacja nie jest jeszcze uruchomiona, więc zostanie uruchomiona pusta strona przeglądarki.

### <a name="attach-the-debugger-to-client-side-script"></a>Dołączanie debugera do skryptu po stronie klienta

1. Przejdź do Visual Studio, a następnie ustaw punkt przerwania w kodzie źródłowym, albo *app-bundle.js* *lub app.tsx.*

    Aby *app-bundle.js*, ustaw punkt przerwania w `render()` funkcji , jak pokazano na poniższej ilustracji:

    ![Zrzut ekranu przedstawiający Visual Studio kodu dla app-bundle.js. Czerwona kropka w lewym śmietku wskazuje, że punkt przerwania jest ustawiony w funkcji renderowania.](../javascript/media/tutorial-nodejs-react-set-breakpoint-client-code.png)

    Aby znaleźć funkcję w transpilowanych plikachapp-bundle.js, użyj `render()` **klawiszy Ctrl** F (Edytuj funkcję Znajdź i  +    >    >  **zamień szybkie wyszukiwanie).**

    W *przypadku funkcji app.tsx* ustaw punkt przerwania wewnątrz `render()` funkcji w instrukcji `return` .

    ![Zrzut ekranu przedstawiający okno Visual Studio kodu aplikacji app.tsx. Czerwona kropka w lewym rynnie wskazuje, że punkt przerwania jest ustawiony na instrukcji return funkcji renderowania.](../javascript/media/tutorial-nodejs-react-set-breakpoint-in-tsx-file.png)

2. Jeśli ustawiasz punkt przerwania w pliku *tsx* (zamiastapp-bundle.js *),* musisz zaktualizować *webpack-config.js*. Zastąp następujący kod:

    ```javascript
    output: {
        filename: "./app-bundle.js",
    },
    ```

    następującym:

    ```javascript
    output: {
        filename: "./app-bundle.js",
        devtoolModuleFilenameTemplate: '[resource-path]'  // removes the webpack:/// prefix
    },
    ```

    Jest to ustawienie tylko dla programistów umożliwiające debugowanie w Visual Studio. To ustawienie umożliwia zastąpienie wygenerowanych odwołań w pliku mapy źródłowej *app-bundle.js.map* podczas tworzenia aplikacji. Domyślnie odwołania do pakietów webpack w pliku mapy źródłowej zawierają prefiks *webpack:///,* który uniemożliwia Visual Studio znalezienie pliku źródłowego *app.tsx.* W szczególności w przypadku tej zmiany odwołanie do pliku źródłowego *app.tsx* jest zmieniane z *webpack:///./app.tsx* na *./app.tsx,* co umożliwia debugowanie.

3. Wybierz przeglądarkę docelową jako element docelowy debugowania w Visual Studio, a następnie naciśnij klawisze **Ctrl** + **F5** (Rozpocznij debugowanie bez debugowania), aby uruchomić aplikację  >  w przeglądarce.

    ::: moniker range=">=vs-2019"
    Jeśli utworzono konfigurację przeglądarki o przyjaznej nazwie, wybierz tę konfigurację jako miejsce docelowe debugowania.
    ::: moniker-end

    Aplikacja zostanie otwarta na nowej karcie przeglądarki.

4. Wybierz **pozycję**  >  **Debuguj dołączanie do procesu** (lub naciśnij klawisze **Ctrl**  +  **Alt**  +  **P).**

    > [!TIP]
    > Począwszy od Visual Studio 2017 r., po dołączeniu do procesu po raz pierwszy, korzystając z tych kroków, można szybko ponownie dołączyć do tego samego procesu, wybierając opcję   >  **Debuguj** ponowne dołączenie do procesu (lub naciśnij klawisz **Shift**  +  **Alt**  +  **P).**

5. W **oknie dialogowym Dołączanie** do procesu pobierz filtrowaną listę wystąpień przeglądarki, do których można dołączyć.

    ::: moniker range=">=vs-2019"
    W programie Visual Studio 2019 wybierz poprawny debuger dla przeglądarki docelowej, języka **JavaScript (Chrome)** lub  **JavaScript (Microsoft Edge — Chromium)** w polu Dołącz do, wpisz **chrome** lub **edge** w polu filtru, aby przefiltrować wyniki wyszukiwania.
    ::: moniker-end
    ::: moniker range="vs-2017"
    W Visual Studio 2017 wybierz pozycję Kod zestawu **Webkit** w polu Dołącz do, wpisz **chrome** w polu filtru, aby przefiltrować wyniki wyszukiwania. 
    ::: moniker-end

6. Wybierz proces przeglądarki z prawidłowym portem hosta (w tym przykładzie localhost), a następnie wybierz pozycję **Dołącz**.

    Port (1337) może również pojawić się w polu **Tytuł,** aby ułatwić wybranie poprawnego wystąpienia przeglądarki.

    ::: moniker range=">=vs-2019"
    W poniższym przykładzie pokazano, jak wygląda Microsoft Edge (Chromium).

    ![Dołączanie do procesu](../javascript/media/tutorial-nodejs-react-attach-to-process-edge.png)
    ::: moniker-end
    ::: moniker range="vs-2017"
    ![Dołączanie do procesu](../javascript/media/tutorial-nodejs-react-attach-to-process.png)

    Wiesz, że debuger został poprawnie dołączony po otwarciu DOM Explorer i konsoli JavaScript w Visual Studio. Te narzędzia debugowania są podobne do narzędzi Chrome Narzędzia deweloperskie i F12 Tools for Microsoft Edge.
    ::: moniker-end

    > [!TIP]
    > Jeśli debuger nie zostanie dołączenia i zostanie wyświetlony komunikat "Nie można dołączyć do procesu. Operacja nie jest legalna w bieżącym stanie". Użyj Menedżer zadań, aby zamknąć wszystkie wystąpienia przeglądarki docelowej przed uruchomieniem przeglądarki w trybie debugowania. Rozszerzenia przeglądarki mogą być uruchomione i uniemożliwiać pełny tryb debugowania.

7. Ponieważ kod z już wykonanym punktem przerwania, odśwież stronę przeglądarki, aby trafić do punktu przerwania.

    Po wstrzymaniu w debugerze możesz sprawdzić stan aplikacji, umieszczając kursor na zmiennych i używając okien debugera. Debuger można przechodzić dalej przez wykonywanie krokowe kodu **(F5,** **F10** i **F11).** Aby uzyskać więcej informacji na temat podstawowych funkcji debugowania, zobacz [Pierwsze spojrzenie na debuger](../debugger/debugger-feature-tour.md).

    Możesz trafić punkt przerwania w lokalizacji *app-bundle.js* lub jej zamapowanych lokalizacjach w *programie app.tsx,* w zależności od kroków, które zostały wcześniej podjęte, wraz ze środowiskiem i stanem przeglądarki. W obu sposób możesz przejść przez kod i przeanalizować zmienne.

   * Jeśli musisz włamać się do kodu w programie *app.tsx* i nie możesz tego zrobić, użyj polecenia **Attach to Process** (Dołącz do procesu), jak opisano w poprzednich krokach, aby dołączyć debuger. Upewnij się, że środowisko jest prawidłowo skonfigurowane:

      * Zamknięto wszystkie wystąpienia przeglądarki, w tym rozszerzenia przeglądarki Chrome (przy użyciu Menedżer zadań), aby można było uruchomić przeglądarkę w trybie debugowania. Upewnij się, że przeglądarka jest uruchamiana w trybie debugowania.

      * Upewnij się, że plik mapy źródłowej zawiera odwołanie do *pliku ./app.tsx,* a nie plik *webpack:///./app.tsx*, co uniemożliwia debugerowi Visual Studio lokalizowanie pliku *app.tsx.*
       Alternatywnie, jeśli musisz włamać się do kodu w programie *app.tsx* i nie możesz tego zrobić, spróbuj użyć instrukcji w programie app.tsx lub ustawić punkty przerwania w narzędziu `debugger;` Chrome Narzędzia deweloperskie (lub F12 Tools for Microsoft Edge). 

   * Jeśli musisz włamać się do kodu w pliku *app-bundle.js* i nie możesz tego zrobić, usuń źródłowy plik mapy, *app-bundle.js.map*.

## <a name="next-steps"></a>Następne kroki

> [!div class="nextstepaction"]
> [Wdrażanie aplikacji w systemie Linux App Service](../javascript/publish-nodejs-app-azure.md)
