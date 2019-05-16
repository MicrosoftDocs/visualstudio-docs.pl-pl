---
title: Tworzenie aplikacji Node.js i React
description: W tym samouczku utworzysz aplikację przy użyciu narzędzia Node.js dla programu Visual Studio
ms.custom: mvc
ms.date: 11/01/2018
ms.topic: tutorial
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jillfra
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: 1283b447f750c3485029085d2669215abbf65dfd
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65695980"
---
# <a name="tutorial-create-a-nodejs-and-react-app-in-visual-studio"></a>Samouczek: Tworzenie aplikacji Node.js i React w programie Visual Studio

Program Visual Studio umożliwia łatwe tworzenie projektu środowiska Node.js i technologii IntelliSense i innych wbudowanych funkcji, które obsługuje środowiska Node.js. W tym samouczku dla programu Visual Studio utworzysz projekt aplikacji sieci web Node.js za pomocą szablonu programu Visual Studio. Następnie utworzysz prostą aplikację przy użyciu platformy React.

Ten samouczek zawiera informacje na temat wykonywania następujących czynności:
> [!div class="checklist"]
> * Tworzenie projektu platformy Node.js
> * Dodaj pakiety npm
> * Dodaj kod platformy React z aplikacją
> * Transpiluj JSX
> * Dołącz debuger

## <a name="before-you-begin"></a>Przed rozpoczęciem

Poniżej przedstawiono listę często zadawanych PYTAŃ szybkie wprowadzenie do niektórych kluczowych pojęć.

### <a name="what-is-nodejs"></a>Co to jest środowisko Node.js?

Node.js to środowisko uruchomieniowe JavaScript po stronie serwera, który wykonuje kodu JavaScript po stronie serwera.

### <a name="what-is-npm"></a>Co to jest npm?

npm jest domyślnego menedżera pakietów dla środowiska Node.js. Menedżer pakietów ułatwia programistom publikowania i udostępniać kod źródłowy bibliotek środowiska Node.js i upraszcza instalowania, aktualizowania i odinstalowywania bibliotek.

### <a name="what-is-react"></a>Co to jest React?

React to struktura frontonu do tworzenia interfejsu użytkownika.

### <a name="what-is-jsx"></a>Co to jest JSX?

JSX to rozszerzenie składni języka JavaScript, zwykle umożliwia platformie React opisano elementy interfejsu użytkownika. Kod JSX musi być transpiled zwykły języka JavaScript, zanim można uruchomić w przeglądarce.

### <a name="what-is-webpack"></a>Co to jest webpack?

webpack pakiety pliki JavaScript, dzięki czemu mogą działać w przeglądarce. Można również przekształcić lub innych zasobów i zasoby. Często służy do określania kompilatora, takich jak Babel lub TypeScript, transpiluj kodu JSX lub TypeScript w celu zwykłego kodu JavaScript.

## <a name="prerequisites"></a>Wymagania wstępne

* Musisz mieć zainstalowany program Visual Studio i obciążenie programowania Node.js.

    ::: moniker range=">=vs-2019"
    Jeśli jeszcze nie zainstalowano programu Visual Studio 2019 r, przejdź do strony [program Visual Studio pobiera](https://visualstudio.microsoft.com/downloads/) strony, aby zainstalować go za darmo.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Jeśli jeszcze nie zainstalowano programu Visual Studio 2017, przejdź do strony [program Visual Studio pobiera](https://visualstudio.microsoft.com/downloads/) strony, aby zainstalować go za darmo.
    ::: moniker-end

    Jeśli musisz zainstalować obciążenie, ale już program Visual Studio, przejdź do strony **narzędzia** > **Pobierz narzędzia i funkcje...** , która otwiera Instalatora programu Visual Studio. Wybierz **programowania Node.js** obciążenia, wybierz **Modyfikuj**.

    ![Obciążenie node.js w Instalatorze programu VS](../ide/media/quickstart-nodejs-workload.png)

* Konieczne jest posiadanie zainstalowanego środowiska uruchomieniowego Node.js.

    W tym samouczku został przetestowany przy użyciu wersji 8.11.2.

    Jeśli nie jest ona zainstalowana, zainstaluj wersję LTS z [Node.js](https://nodejs.org/en/download/) witryny sieci Web. Ogólnie rzecz biorąc program Visual Studio automatycznie wykrywa zainstalowane środowisko uruchomieniowe Node.js. Jeśli nie zostanie wykryta zainstalowanego środowiska uruchomieniowego, można skonfigurować projekt, aby odwoływać się do zainstalowanego środowiska uruchomieniowego na stronie właściwości (po utworzeniu projektu, kliknij prawym przyciskiem myszy węzeł projektu i wybierz polecenie **właściwości**).

## <a name="create-a-project"></a>Tworzenie projektu

Najpierw utwórz projekt aplikacji sieci web środowiska Node.js.

1. Otwórz program Visual Studio.

1. Utwórz nowy projekt.

    ::: moniker range=">=vs-2019"
    Naciśnij klawisz **Esc** aby zamknąć okno rozpoczęcia. Typ **Ctrl + Q** aby otworzyć pole wyszukiwania, wpisz **Node.js**, następnie wybierz **pusta aplikacja sieci Web Node.js** (JavaScript). W oknie dialogowym wybierz **Utwórz**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Na pasku menu u góry wybierz **pliku** > **New** > **projektu**. W okienku po lewej stronie **nowy projekt** okna dialogowego rozwiń **JavaScript**, następnie wybierz **Node.js**. W środkowym okienku wybierz **pusta aplikacja sieci Web Node.js**, wpisz nazwę **NodejsWebAppBlank**, następnie wybierz **OK**.
    ::: moniker-end
    Jeśli nie widzisz **pusta aplikacja sieci Web Node.js** szablonu projektu należy dodać **programowania Node.js** obciążenia. Aby uzyskać szczegółowe instrukcje, zobacz [wymagania wstępne](#prerequisites).

    Visual Studio tworzy nowego rozwiązania i otwiera projekt.

    ![Projekt node.js w Eksploratorze rozwiązań](../javascript/media/tutorial-nodejs-react-project-structure.png)

    (1) wyróżnione **bold** jest projektu, przy użyciu nazwę nadaną w **nowy projekt** okno dialogowe. W systemie plików tego projektu jest reprezentowany przez *.njsproj* pliku w folderze projektu. Można ustawić właściwości i zmienne środowiskowe związane z projektem, klikając prawym przyciskiem myszy projekt i wybierając pozycję **właściwości**. Możesz tworzyć Pełna zgodnooć wersji z innymi narzędziami deweloperskimi, ponieważ plik projektu nie wprowadzać zmian niestandardowego źródła projektu środowiska Node.js.

    (2) na najwyższym poziomie to rozwiązanie, która domyślnie ma taką samą nazwę jak projektu. To rozwiązanie, reprezentowane przez *.sln* plików na dysku, to kontener dla jednego lub kilku powiązanych projektów.

    (3 węzeł npm zawiera wszystkie pakiety npm zainstalowane. Możesz kliknąć prawym przyciskiem myszy węzeł npm, aby wyszukać i zainstalować pakiety npm w oknie dialogowym lub zainstaluj aktualizację pakietów przy użyciu ustawień w *package.json* i kliknij prawym przyciskiem myszy opcje w węźle npm.

    (4) *package.json* to plik używany przez narzędzie npm do zarządzania zależności pakietów i wersji pakietu dla lokalnie zainstalowane pakiety. Aby uzyskać więcej informacji na temat tego pliku, zobacz [konfiguracji pliku package.json](../javascript/configure-packages-with-package-json.md)

    (5) pliki projektu, takie jak *server.js* wyświetlane w węźle projektu. *Server.js* jest plik startowy projektu, a to znaczy Dlaczego ona wyświetlona na liście **bold**. Można ustawić pliku uruchamiania, kliknij prawym przyciskiem myszy plik w projekcie i wybierając **Ustaw jako plik startowy środowiska Node.js**.

## <a name="add-npm-packages"></a>Dodaj pakiety npm

Ta aplikacja wymaga numeru moduły npm, by działała poprawnie.

* react
* react-dom
* express
* ścieżka
* ts-loader
* typescript
* webpack
* webpack-cli

1. W Eksploratorze rozwiązań (w okienku po prawej stronie), kliknij prawym przyciskiem myszy **npm** węzeł projektu i wybierz polecenie **zainstalować nowe pakiety npm**.

    W **zainstalować nowe pakiety npm** okno dialogowe, możesz zainstalować najnowszą wersję pakietu lub określ wersję. Jeśli zdecydujesz się zainstalować najnowszą wersję tych pakietów, ale wystąpiły nieoczekiwane błędy później, konieczne może być zainstalować wersje dokładny pakietu opisane w dalszej części tych kroków.

1. W **zainstalować nowe pakiety npm** okno dialogowe, wyszukaj pakiet platformy react, a następnie wybierz pozycję **zainstaluj pakiet** go zainstalować.

    ![Instalowanie pakietów npm](../javascript/media/tutorial-nodejs-react-install-packages.png)

    Wybierz **dane wyjściowe** okno, aby wyświetlić postęp na temat instalowania pakietu (wybierz **Npm** w **Pokaż dane wyjściowe z** pola). Po zainstalowaniu pakietu jest wyświetlany w obszarze **npm** węzła.

    Projekt *package.json* plik został zaktualizowany o nowe informacje o pakiecie, łącznie z wersją pakietu.

1. Zamiast przy użyciu interfejsu użytkownika do wyszukania i dodania pozostałe pakiety jednego naraz, wklej następujący kod do *package.json*. Aby to zrobić, Dodaj `dependencies` sekcji przy użyciu tego kodu:

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

    Jeśli istnieje już `dependencies` sekcji w używanej wersji pustego szablonu, po prostu zastąpić poprzedni kod JSON. Aby uzyskać więcej informacji na temat użycia tego pliku, zobacz [konfiguracji pliku package.json](../javascript/configure-packages-with-package-json.md)

1. Kliknij prawym przyciskiem myszy **npm** węzeł projektu i wybierz polecenie **zaktualizuj pakiety npm**.

    W dolnym okienku zaznacz **dane wyjściowe** okno, aby wyświetlić postęp na temat instalowania pakietów. Instalacja może zająć kilka minut i może nie od razu Zobacz wyniki. Aby wyświetlić dane wyjściowe, upewnij się, że wybrano **Npm** w **Pokaż dane wyjściowe z** pole **dane wyjściowe** okna.

    Poniżej przedstawiono moduły npm, w jakiej występują w Eksploratorze rozwiązań po ich zainstalowaniu.

    ![pakiety npm](../javascript/media/tutorial-nodejs-react-npm-modules.png)

    > [!NOTE]
    > Jeśli wolisz zainstalować pakiety npm przy użyciu wiersza polecenia, kliknij prawym przyciskiem myszy węzeł projektu i wybierz polecenie **Otwórz wiersz polecenia w tym miejscu**. Użyj standardowych poleceń środowiska Node.js, aby zainstalować pakiety.

## <a name="add-project-files"></a>Dodaj pliki projektów

W ramach tej procedury dodasz cztery nowe pliki do projektu.

* *app.tsx*
* *webpack-config.js*
* *index.html*
* *tsconfig.json*

Dla tej prostej aplikacji możesz dodawać nowe pliki projektu, w katalogu głównym projektu. (W przypadku większości aplikacji są zazwyczaj Dodaj pliki do podfolderów i odpowiednio dostosować odwołania do ścieżki względnej.)

1. W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy projekt **NodejsWebAppBlank** i wybierz polecenie **Dodaj** > **nowy element**.

1. W **Dodaj nowy element** okna dialogowego wybierz **plik TypeScript JSX**, wpisz nazwę *app.tsx*i wybierz **OK**.

1. Powtórz te kroki, aby dodać *webpack config.js*. A nie plikiem TypeScript JSX wybierz **plik JavaScript**.

1. Powtórz te same kroki, aby dodać *index.html* do projektu. Zamiast pliku JavaScript, wybierz **plik HTML**.

1. Powtórz te same kroki, aby dodać *tsconfig.json* do projektu. Zamiast pliku JavaScript, wybierz **pliku konfiguracji JSON TypeScript**.

## <a name="add-app-code"></a>Dodawanie kodu aplikacji

1. Otwórz *server.js* i Zastąp istniejący kod następującym kodem:

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

   Powyższy kod używa Express, aby uruchomić środowisko Node.js jako serwer aplikacji sieci web. Ten kod ustawia port numer portu we właściwościach projektu skonfigurowano (domyślnie port skonfigurowano 1337 we właściwościach). Aby otworzyć okno właściwości projektu, kliknij prawym przyciskiem myszy projekt w Eksploratorze rozwiązań, a następnie wybierz **właściwości**.

1. Otwórz *app.tsx* i Dodaj następujący kod:

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

    Powyższy kod użyto składnia JSX i React, aby wyświetlić wiadomość proste.

1. Otwórz *index.html* i Zastąp **treści** sekcję poniższym kodem:

    ```html
    <body>
        <div id="root"></div>
        <!-- scripts -->
        <script src="./dist/app-bundle.js"></script>
    </body>
    ```

    Ta strona HTML ładuje się *bundle.js aplikacji*, zawierającą transpiled kodu JSX i React zwykły języka JavaScript. Obecnie *bundle.js aplikacji* plik jest pusty. W następnej sekcji skonfigurujesz opcje transpiluj kodu.

## <a name="configure-webpack-and-typescript-compiler-options"></a>Skonfiguruj opcje kompilatora TypeScript i webpack

W poprzednich krokach dodano *webpack config.js* do projektu. Następnie dodasz kod konfiguracji webpack. Doda konfiguracji webpack prostego, który określa plik wejściowy (*app.tsx*) i plik wyjściowy (*bundle.js aplikacji*) do tworzenia pakietów i transpiling JSX do zwykłego kodu JavaScript. Dla transpiling możesz również skonfigurować niektóre opcje kompilatora TypeScript. Ten kod jest podstawowej konfiguracji, który jest przeznaczony jako wprowadzenie do webpack i kompilatora TypeScript.

1. W Eksploratorze rozwiązań Otwórz *webpack config.js* i Dodaj następujący kod.

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

    Kod konfiguracji webpack powoduje, że webpack, aby użyć modułu ładującego TypeScript do transpiluj JSX.

1. Otwórz *tsconfig.json* i Zastąp następujący kod, który określa opcje kompilatora TypeScript w kodzie domyślnym:

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

    *App.tsx* jest określony jako pliku źródłowego.

## <a name="transpile-the-jsx"></a>Transpiluj JSX

1. W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy węzeł projektu, a następnie wybierz **Otwórz wiersz polecenia w tym miejscu**.

1. W wierszu polecenia wpisz następujące polecenie:

    `node_modules\.bin\webpack app.tsx --config webpack-config.js`

    W oknie wiersza polecenia zawiera wynik.

    ![Uruchom webpack](../javascript/media/tutorial-nodejs-react-run-webpack.png)

    Jeśli widzisz błędy zamiast powyższym danych wyjściowych, należy je rozwiązać, zanim aplikacja będzie działać. Jeśli Twojej wersji pakietu npm różnią się od wersji przedstawiona w tym samouczku, który może być źródłem błędów. Jest jednym ze sposobów, aby naprawić błędy do użycia wersje dokładny pokazano w poprzednich krokach. Ponadto w przypadku co najmniej jeden z tych wersji pakietu jest przestarzała i powoduje błąd, może być konieczne zainstalowanie nowszej wersji, aby naprawić błędy. Aby uzyskać informacje na temat korzystania z *package.json* do kontroli wersji pakietu npm, zobacz [konfiguracji pliku package.json](../javascript/configure-packages-with-package-json.md).

1. W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy węzeł projektu, a następnie wybierz **Dodaj** > **istniejący Folder**, następnie wybierz *dist* folder i wybierz polecenie  **Wybierz Folder**.

    Program Visual Studio dodaje *dist* folderu do projektu, który zawiera *bundle.js aplikacji* i *bundle.js.map aplikacji*.

1. Otwórz *bundle.js aplikacji* się transpiled kodu JavaScript.

1. Jeśli zostanie wyświetlony monit, aby ponownie załadować zewnętrznie zmodyfikowane pliki, wybierz opcję **tak na wszystko**.

    ![Obciążenia zmodyfikowanych plików](../javascript/media/tutorial-nodejs-react-reload-files.png)

Każdym wprowadzeniu zmiany *app.tsx*, należy ponownie uruchomić polecenie webpack.

## <a name="run-the-app"></a>Uruchamianie aplikacji

1. Wybierz dla programu Chrome, jak bieżący obiekt docelowy debugowania.

    ::: moniker range=">=vs-2019"
    ![Wybierz cel debugowania Chrome](../javascript/media/vs-2019/tutorial-nodejs-react-debug-target.png)
    ::: moniker-end
    ::: moniker range="vs-2017"
    ![Wybierz cel debugowania Chrome](../javascript/media/tutorial-nodejs-react-debug-target.png)
    ::: moniker-end

    Jeśli dla programu Chrome jest dostępne na danym komputerze, ale nie są wyświetlane jako opcja, wybierz opcję **przeglądanie za pomocą** z listy rozwijanej docelowego debugowania i wybierz opcję dla programu Chrome jako domyślny element docelowy przeglądarki (wybierz **Ustaw jako domyślny**).

1. Aby uruchomić aplikację, naciśnij klawisz **F5** (**debugowania** > **Rozpocznij debugowanie**) lub przycisku zieloną strzałkę.

    Zostanie otwarte okno konsoli środowiska Node.js, pokazujący port, na którym nasłuchuje debugera.

    Program Visual Studio uruchamia aplikację, uruchamiając plik startowy *server.js*.

    ![Uruchamianie platformy React w przeglądarce](../javascript/media/tutorial-nodejs-react-running-react.png)

1. Zamknij okno przeglądarki.

1. Zamknij okno konsoli.

## <a name="set-a-breakpoint-and-run-the-app"></a>Ustaw punkt przerwania i uruchamianie aplikacji

1. W *server.js*, kliknij na marginesie po lewej stronie `staticPath` deklaracji, aby ustawić punkt przerwania:

    ![Ustaw punkt przerwania](../javascript/media/tutorial-nodejs-react-set-breakpoint.png)

    Punkty przerwania są najbardziej podstawowa i podstawowych funkcji niezawodne debugowanie. Punkt przerwania wskazuje, gdzie programu Visual Studio powinny zawiesić uruchamianie kodu, dzięki czemu możesz zapoznaj się z wartości zmiennych lub zachowanie pamięci lub czy gałąź kodu wprowadzenie uruchomieniu.

1. Aby uruchomić aplikację, naciśnij klawisz **F5** (**debugowania** > **Rozpocznij debugowanie**).

    Debuger zatrzymuje się w punkcie przerwania zestawu (bieżąca instrukcja jest oznaczona kolorem żółtym). Teraz możesz sprawdzić stan swojej aplikacji, ustawiając kursor nad zmiennych, które obecnie znajdują się w zakresie, za pomocą okna debugera, takie jak **lokalne** i **Obejrzyj** systemu windows.

1. Naciśnij klawisz **F5** kontynuowanie działania aplikacji.

1. Jeśli chcesz użyć narzędzia deweloperskie dla programu Chrome, naciśnij klawisz **F12**. Można użyć tych narzędzi do badania modelu DOM i interakcji z aplikacją przy użyciu konsoli języka JavaScript.

1. Zamknij przeglądarkę sieci web i konsoli.

## <a name="set-and-hit-a-breakpoint-in-the-client-side-react-code"></a>Ustaw i Traf punkt przerwania w kodzie po stronie klienta platformy React

W poprzedniej sekcji debuger jest dołączony do kodu w języku Node.js po stronie serwera. Aby dołączyć debuger za pomocą programu Visual Studio i identyfikować punkty przerwania w kodzie platformy React po stronie klienta, debuger potrzebuje pomocy, aby zidentyfikować korygowania procesu. Oto jeden ze sposobów, aby włączyć tę opcję.

1. Zamknij wszystkie okna przeglądarki Chrome.

2. Otwórz **Uruchom** polecenia Windows **Start** przycisk (kliknij prawym przyciskiem myszy i wybierz polecenie **Uruchom**), a następnie wprowadź następujące polecenie:

    `chrome.exe --remote-debugging-port=9222`

    Spowoduje to uruchomienie przeglądarki Chrome z włączonym debugowaniem.

    ::: moniker range=">=vs-2019"

    > [!NOTE]
    > Można również ustawić `--remote-debugging-port` flagę podczas uruchamiania przeglądarki, wybierając **przeglądanie za pomocą...**  > z **debugowania** narzędzi, wybierając **Dodaj**, a następnie ustawienie flagi **argumenty** pola. Użyj innej nazwy przyjazne przeglądarki, takich jak **dla programu Chrome przy użyciu debugowania**. Aby uzyskać więcej informacji, zobacz [wersji](https://docs.microsoft.com/visualstudio/releases/2019/release-notes-preview#browser-cli-params-support).

    ::: moniker-end

3. Przełącz się do programu Visual Studio i ustaw punkt przerwania *bundle.js aplikacji* możesz pisać kod w `render()` funkcji, jak pokazano na poniższej ilustracji:

    ![Ustaw punkt przerwania](../javascript/media/tutorial-nodejs-react-set-breakpoint-client-code.png)

    Można znaleźć `render()` działa w programach *bundle.js aplikacji*, użyj **Ctrl**+**F** (**Edytuj**  >   **Znajdź i Zamień** > **szybkiego wyszukiwania**).

4. Za pomocą przeglądarki Chrome wybrany jako cel debugowania w programie Visual Studio, naciśnij klawisz **Ctrl**+**F5** (**debugowania** > **Rozpocznij bez debugowania** ) do uruchomienia aplikacji w przeglądarce.

    Aplikacja zostanie otwarta nowa karta przeglądarki.

5. Wybierz **debugowania** > **dołączyć do procesu**.

6. W **dołączyć do procesu** okna dialogowego wybierz **kodu aparatu Webkit** w **dołączyć do** wpisz **chrome** w polu filtru, aby filtrować wyniki wyszukiwania.

7. Wybierz proces dla programu Chrome przy użyciu właściwy host port (1337, w tym przykładzie), a następnie wybierz pozycję **Dołącz**.

    ![Dołącz do procesu](../javascript/media/tutorial-nodejs-react-attach-to-process.png)

    Wiesz, że debuger został dołączony poprawnie otwieraniu konsoli języka JavaScript i narzędzia DOM Explorer w programie Visual Studio. Te narzędzia do debugowania są podobne do narzędzia programistyczne dla programu Chrome i F12 Tools dla Microsoft Edge.

    > [!NOTE]
    > Jeśli debuger nie dołączy i zostanie wyświetlony komunikat "nie można dołączyć do procesu. Operacja jest niedozwolona w bieżącym stanie. ", zamknij wszystkie wystąpienia programu Chrome, przed rozpoczęciem Chrome w trybie debugowania za pomocą Menedżera zadań. Rozszerzenia dla programu Chrome może być uruchomiony i zapobieganie tryb pełnego debugowania.

8. Ponieważ kod za pomocą punktu przerwania zostały już wykonane czynności, Odśwież stronę przeglądarki w taki sposób, aby trafiony punkt przerwania.

    Gdy wstrzymaniu w debugerze, można sprawdzić stan swojej aplikacji, przenosząc kursor myszy nad zmienne okien i korzystanie z debugera. Debuger może przejść przez krokowe wykonywanie kodu (**F5**, **F10**, i **F11**).

    Może być trafiony punkt przerwania w jednym *bundle.js aplikacji* lub lokalizacji zamapowanych w *app.tsx*, w zależności od stanu usługi środowisko i przeglądarki. W obu przypadkach możesz przejść przez kod i Sprawdź zmienne.

   * Jeśli potrzebujesz wszedł do kodu w *app.tsx* i nie można to zrobić, użyj **dołączyć do procesu** zgodnie z opisem w poprzednich krokach, aby dołączyć debuger. Następnie otwórz dynamicznie generowanym *app.tsx* pliku z Eksploratora rozwiązań, otwierając **dokumenty skryptów** > **app.tsx**, a następnie ustaw punkt przerwania i Odśwież strony w przeglądarce (ustawić punkt przerwania w wierszu kodu, który umożliwia punkty przerwania, takich jak `return` instrukcji lub `var` deklaracji).

       Alternatywnie Jeśli potrzebujesz wszedł do kodu w *app.tsx* i nie można to zrobić, spróbuj użyć `debugger;` instrukcji w *app.tsx*, lub zamiast tego ustawić punkty przerwania w Developer Tools dla programu Chrome.

   * Jeśli potrzebujesz wszedł do kodu w *bundle.js aplikacji* i nie można to zrobić, usuń plik mapy źródłowej *bundle.js.map aplikacji*.

     > [!TIP]
     > Po dołączeniu do procesu po raz pierwszy wykonać następujące kroki, możesz szybko dołączyć do tego samego procesu w programie Visual Studio 2017, wybierając **debugowania** > **ponownie Dołącz do procesu**.

## <a name="next-steps"></a>Następne kroki

> [!div class="nextstepaction"]
> [Wdrażanie aplikacji do usługi App Service w systemie Linux](../javascript/publish-nodejs-app-azure.md)
