---
title: Tworzenie Node.js i reagowanie aplikacji
description: W tym samouczku utworzysz aplikację przy użyciu narzędzi Node.js Tools for Visual Studio
ms.custom: ''
ms.date: 4/21/2020
ms.topic: tutorial
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jillfra
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: c6813e0ad482bb211269c9da3950842dda7f6abd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "81760123"
---
# <a name="tutorial-create-a-nodejs-and-react-app-in-visual-studio"></a>Samouczek: Tworzenie Node.js i reagowanie aplikacji w programie Visual Studio

Program Visual Studio umożliwia łatwe tworzenie projektu Node.js i korzystanie z technologii IntelliSense oraz innych wbudowanych funkcji, które obsługują Node.js. W tym samouczku dla programu Visual Studio utworzysz projekt aplikacji sieci Web Node.js na podstawie szablonu programu Visual Studio. Następnie utworzysz prostą aplikację przy użyciu funkcji reagowania.

Ten samouczek zawiera informacje na temat wykonywania następujących czynności:
> [!div class="checklist"]
> * Tworzenie projektu platformy Node.js
> * Dodaj pakiety npm
> * Dodawanie kodu reakcji do aplikacji
> * JSX transsterty
> * Dołącz debuger

## <a name="before-you-begin"></a>Przed rozpoczęciem

Oto krótkie często zadawane pytania, aby wprowadzić pewne kluczowe pojęcia.

### <a name="what-is-nodejs"></a>Co to jest środowisko Node.js?

Node.js to środowisko uruchomieniowe JavaScript po stronie serwera, które wykonuje kod JavaScript po stronie serwera.

### <a name="what-is-npm"></a>Co to jest npm?

npm jest domyślnym menedżerem pakietów dla Node.js. Menedżer pakietów ułatwia programistom publikowanie i udostępnianie kodu źródłowego bibliotek Node.js i służy do uproszczenia instalacji, aktualizacji i odinstalowywania bibliotek.

### <a name="what-is-react"></a>Co to jest reagowanie?

Reagowanie to platforma frontonu służąca do tworzenia interfejsu użytkownika.

### <a name="what-is-jsx"></a>Co to jest JSX?

JSX jest rozszerzeniem składni języka JavaScript, zwykle używanym w celu reagowania na opisywanie elementów interfejsu użytkownika. Przed uruchomieniem w przeglądarce kod JSX musi być transstertą do zwykłego języka JavaScript.

### <a name="what-is-webpack"></a>Co to jest pakiet WebPack?

Pakiet WebPack służy do łączenia plików JavaScript, dzięki czemu mogą być uruchamiane w przeglądarce. Może również przekształcić inne zasoby i zasoby. Często jest używany do określenia kompilatora, takiego jak Babel lub TypeScript, do JSX kodu TypeScript do zwykłego języka JavaScript.

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

    Ten samouczek został przetestowany przy użyciu wersji 12.6.2.

    Jeśli go nie zainstalowano, zalecamy zainstalowanie wersji LTS z witryny internetowej [Node.js](https://nodejs.org/en/download/) w celu uzyskania najlepszej zgodności z zewnętrznymi platformami i bibliotekami. Node.js jest oparta na architekturze 32-bitowej i 64-bitowej. Narzędzia Node.js w programie Visual Studio, zawarte w obciążeniu Node.js, obsługują obie wersje. Tylko jeden jest wymagany, a Instalator Node.js obsługuje tylko jeden instalowany w danym momencie.
    
    Ogólnie rzecz biorąc, program Visual Studio automatycznie wykrywa zainstalowane Node.js środowiska uruchomieniowego. Jeśli nie wykryje zainstalowanego środowiska uruchomieniowego, można skonfigurować projekt do odwoływania się do zainstalowanego środowiska uruchomieniowego na stronie właściwości (po utworzeniu projektu kliknij prawym przyciskiem myszy węzeł projektu, wybierz polecenie **Właściwości**, a następnie ustaw ** ścieżkęNode.exe**). Można użyć globalnej instalacji Node.js lub można określić ścieżkę do lokalnego interpretera w każdym z projektów Node.js. 

## <a name="create-a-project"></a>Tworzenie projektu

Najpierw utwórz projekt aplikacji sieci Web Node.js.

1. Otwórz program Visual Studio.

1. Tworzenie nowego projektu.

    ::: moniker range=">=vs-2019"
    Naciśnij klawisz **ESC** , aby zamknąć okno uruchamiania. **Naciśnij klawisze CTRL + Q** , aby otworzyć pole wyszukiwania, wpisz **Node.js**, a następnie wybierz **puste Node.js aplikacji sieci Web — JavaScript**. (Chociaż w tym samouczku jest używane kompilator języka TypeScript, kroki te wymagają rozpoczęcia od szablonu **JavaScript** ).
    
    W wyświetlonym oknie dialogowym wybierz pozycję **Utwórz**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Na górnym pasku menu wybierz pozycję **plik**  >  **Nowy**  >  **projekt**. W lewym okienku okna dialogowego **Nowy projekt** rozwiń opcję **JavaScript**, a następnie wybierz **Node.js**. W środkowym okienku wybierz **puste Node.js aplikacji sieci Web**, wpisz nazwę **NodejsWebAppBlank**, a następnie wybierz **przycisk OK**.
    ::: moniker-end
    Jeśli nie widzisz szablonu projektu **pustej Node.js aplikacji sieci Web** , musisz dodać **Node.js obciążenie programowaniem** . Aby uzyskać szczegółowe instrukcje, zobacz [wymagania wstępne](#prerequisites).

    Program Visual Studio tworzy nowe rozwiązanie i otwiera projekt.

    ![Node.js projekt w Eksplorator rozwiązań](../javascript/media/tutorial-nodejs-react-project-structure.png)

    (1) wyróżnione **czcionką pogrubioną** jest projektem, przy użyciu nazwy podanych w oknie dialogowym **Nowy projekt** . W systemie plików ten projekt jest reprezentowany przez plik *. njsproj* w folderze projektu. Aby ustawić właściwości i zmienne środowiskowe skojarzone z projektem, kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Właściwości**. Możesz wykonywać czynności okrężne przy użyciu innych narzędzi programistycznych, ponieważ plik projektu nie wprowadza niestandardowych zmian do źródła projektu Node.js.

    (2) na najwyższym poziomie jest rozwiązaniem, które domyślnie ma taką samą nazwę jak projekt. Rozwiązanie reprezentowane przez plik *. sln* na dysku jest kontenerem dla co najmniej jednego powiązanego projektu.

    (3) węzeł npm pokazuje wszystkie zainstalowane pakiety npm. Możesz kliknąć prawym przyciskiem myszy węzeł npm, aby wyszukać i zainstalować pakiety npm przy użyciu okna dialogowego lub zainstalować i zaktualizować pakiety przy użyciu ustawień w *package.jsna* i kliknij prawym przyciskiem myszy opcje w węźle npm.

    (4) *package.js* jest plikiem używanym przez npm do zarządzania zależnościami pakietów i wersjami pakietów dla pakietów zainstalowanych lokalnie. Aby uzyskać więcej informacji, zobacz [Zarządzanie pakietami npm](../javascript/npm-package-management.md).

    (5) pliki projektu, takie jak *server.js* , są wyświetlane w węźle projektu. *server.js* to plik startowy projektu i dlatego, że jest on wyświetlany **pogrubioną czcionką**. Aby ustawić plik startowy, kliknij prawym przyciskiem myszy plik w projekcie i wybierz polecenie **Ustaw jako plik startowy Node.js**.

## <a name="add-npm-packages"></a>Dodaj pakiety npm

Ta aplikacja wymaga poprawnego działania wielu modułów npm.

* biern
* reagowanie — dom
* express
* path
* TS-Loader
* typescript
* Pakiet WebPack
* WebPack — interfejs wiersza polecenia

1. W Eksplorator rozwiązań (prawego okienka) kliknij prawym przyciskiem myszy węzeł **npm** w projekcie i wybierz polecenie **Zainstaluj nowe pakiety npm**.

    W oknie dialogowym **Instalowanie nowych pakietów npm** można wybrać opcję instalacji najnowszej wersji pakietu lub określić wersję. Jeśli zdecydujesz się zainstalować bieżącą wersję tych pakietów, ale później przeprowadzisz do nieoczekiwanych błędów, możesz chcieć zainstalować dokładne wersje pakietów opisane w dalszej części tych kroków.

1. W oknie dialogowym **Instalowanie nowych pakietów npm** Wyszukaj pakiet reakcję i wybierz pozycję **Zainstaluj pakiet** , aby go zainstalować.

    ![Zainstaluj pakiety npm](../javascript/media/tutorial-nodejs-react-install-package.png)

    Wybierz okno **dane wyjściowe** , aby zobaczyć postęp instalowania pakietu (wybierz **npm** w polu **Pokaż dane wyjściowe z** ). Po zainstalowaniu pakiet pojawia się pod węzłem **npm** .

    *package.jsprojektu na* pliku zostanie zaktualizowany o nowe informacje o pakiecie, w tym wersję pakietu.

1. Zamiast korzystać z interfejsu użytkownika w celu wyszukania i dodania reszty pakietów po jednej naraz, wklej poniższy kod do *package.js*. Aby to zrobić, Dodaj `dependencies` sekcję z tym kodem:

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

    Jeśli `dependencies` w wersji pustego szablonu znajduje się już sekcja, należy ją zamienić na poprzedni kod JSON. Aby uzyskać więcej informacji na temat korzystania z tego pliku, zobacz [package.json Configuration](../javascript/configure-packages-with-package-json.md).

1. Zapisz zmiany.

1. Kliknij prawym przyciskiem myszy węzeł **npm** w projekcie i wybierz polecenie **Zainstaluj pakiety npm**.

    To polecenie uruchamia polecenie npm Install bezpośrednio.

    W dolnym okienku wybierz okno **dane wyjściowe** , aby zobaczyć postęp instalowania pakietów. Instalacja może potrwać kilka minut, a wyniki natychmiast nie są widoczne. Aby wyświetlić dane wyjściowe, upewnij się, że wybrano pozycję **npm** w polu **Pokaż dane wyjściowe z** w oknie **danych wyjściowych** .

    Oto moduły npm, które są wyświetlane w Eksplorator rozwiązań po ich zainstalowaniu.

    ![pakiety npm](../javascript/media/tutorial-nodejs-react-npm-modules-installed.png)

    > [!NOTE]
    > Jeśli wolisz zainstalować pakiety npm przy użyciu wiersza polecenia, kliknij prawym przyciskiem myszy węzeł projektu, a następnie wybierz polecenie **Otwórz wiersz polecenia tutaj**. Użyj standardowych poleceń Node.js, aby zainstalować pakiety.

## <a name="add-project-files"></a>Dodaj pliki projektu

W tych krokach dodasz cztery nowe pliki do projektu.

* *App. TSX*
* *webpack-config.js*
* *index.html*
* *tsconfig.json*

W przypadku tej prostej aplikacji dodawane są nowe pliki projektu w katalogu głównym projektu. (W większości aplikacji zazwyczaj pliki są dodawane do podfolderów i dopasowują odpowiednio odwołania ścieżek względnych).

1. W Eksplorator rozwiązań kliknij prawym przyciskiem myszy projekt **NodejsWebAppBlank** i wybierz polecenie **Dodaj**  >  **nowy element**.

1. W oknie dialogowym **Dodaj nowy element** wybierz pozycję **plik JSX TypeScript**, wpisz nazwę *App. TSX*, a następnie wybierz pozycję **Dodaj** lub **przycisk OK**.

1. Powtórz te kroki, aby dodać *webpack-config.js*. Zamiast pliku TypeScript JSX wybierz **plik JavaScript**.

1. Powtórz te same czynności, aby dodać *index.html* do projektu. Zamiast pliku JavaScript, wybierz **plik HTML**.

1. Powtórz te same czynności, aby dodać *tsconfig.js* do projektu. Zamiast pliku JavaScript wybierz **plik konfiguracyjny języka TYPESCRIPT JSON**.

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

   Poprzedni kod używa programu Express do uruchamiania Node.js jako serwer aplikacji sieci Web. Ten kod ustawia port na numer portu skonfigurowany we właściwościach projektu (domyślnie port jest skonfigurowany do 1337 we właściwościach). Aby otworzyć właściwości projektu, kliknij prawym przyciskiem myszy projekt w Eksplorator rozwiązań i wybierz polecenie **Właściwości**.

1. Otwórz *aplikację App. TSX* i Dodaj następujący kod:

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

    Poprzedni kod używa składni JSX i reaguje na wyświetlanie prostego komunikatu.

1. Otwórz *index.html* i Zastąp sekcję **treść** następującym kodem:

    ```html
    <body>
        <div id="root"></div>
        <!-- scripts -->
        <script src="./dist/app-bundle.js"></script>
    </body>
    ```

    Ta strona HTML ładuje *app-bundle.js*, która zawiera JSX i reaguje na zwykły kod JavaScript. Obecnie *app-bundle.js* jest pustym plikiem. W następnej sekcji skonfigurujesz opcje, aby transstertować kod.

## <a name="configure-webpack-and-typescript-compiler-options"></a>Konfigurowanie opcji środowiska WebPack i kompilatora języka TypeScript

W poprzednich krokach dodano *webpack-config.js* do projektu. Następnie należy dodać kod konfiguracji pakietu WebPack. Zostanie dodana prosta konfiguracja pakietu WebPack, która określa plik wejściowy (*App. TSX*) i plik wyjściowy (*app-bundle.js*) na potrzeby tworzenia i transpiling JSX do zwykłego języka JavaScript. W przypadku transpiling należy również skonfigurować niektóre opcje kompilatora języka TypeScript. Ten kod jest podstawową konfiguracją, która została zaprojektowana jako wprowadzenie do pakietu WebPack i kompilatora języka TypeScript.

1. W Eksplorator rozwiązań Otwórz *webpack-config.js* i Dodaj następujący kod.

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

    Kod konfiguracji pakietu WebPack nakazuje pakietowi WebPack użycie modułu ładującego TypeScript do JSX.

1. Otwórz *tsconfig.jsna* i Zastąp domyślny kod następującym kodem, który określa opcje kompilatora języka TypeScript:

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

    *App. TSX* jest określony jako plik źródłowy.

## <a name="transpile-the-jsx"></a>JSX

1. W Eksplorator rozwiązań kliknij prawym przyciskiem myszy węzeł projektu, a następnie wybierz polecenie **Otwórz wiersz polecenia tutaj**.

1. W wierszu polecenia wpisz następujące polecenie:

    `node_modules\.bin\webpack app.tsx --config webpack-config.js`

    W oknie wiersza polecenia zostanie wyświetlony wynik.

    ![Uruchom pakiet WebPack](../javascript/media/tutorial-nodejs-react-run-webpack-cmd.png)

    Jeśli zobaczysz jakiekolwiek błędy zamiast powyższych danych wyjściowych, musisz je rozwiązać, zanim aplikacja będzie działała. Jeśli wersje pakietu npm są inne niż wersje przedstawione w tym samouczku, które mogą być źródłem błędów. Jednym ze sposobów na rozwiązanie błędów jest użycie dokładnych wersji przedstawionych w poprzednich krokach. Ponadto, jeśli co najmniej jedna z tych wersji pakietu była przestarzała i powoduje błąd, może być konieczne zainstalowanie nowszej wersji w celu rozwiązania błędów. Aby uzyskać informacje na temat korzystania z *package.jsw* celu kontrolowania wersji pakietu npm, zobacz [package.json Configuration](../javascript/configure-packages-with-package-json.md).

1. W Eksplorator rozwiązań kliknij prawym przyciskiem myszy węzeł projektu i wybierz polecenie **Dodaj**  >  **istniejący folder**, a następnie wybierz folder *ROZKŁ* i wybierz **pozycję Wybierz folder**.

    Program Visual Studio dodaje do projektu folder *ROZKŁ* zawierający *app-bundle.js* i *app-bundle.js. map*.

1. Otwórz *app-bundle.js* , aby zobaczyć przewarty kod JavaScript.

1. Jeśli zostanie wyświetlony monit o ponowne załadowanie plików zmodyfikowanych zewnętrznie, wybierz pozycję **tak dla wszystkich**.

    ![Załaduj zmodyfikowane pliki](../javascript/media/tutorial-nodejs-react-reload-files.png)

Za każdym razem, gdy wprowadzasz zmiany do *App. TSX*, musisz ponownie uruchomić polecenie WebPack. Aby zautomatyzować ten krok, Dodaj skrypt kompilacji w celu transsterty JSX.

## <a name="add-a-build-script-to-transpile-the-jsx"></a>Dodawanie skryptu kompilacji w celu transsterty JSX

Począwszy od programu Visual Studio 2019, wymagany jest skrypt kompilacji. Zamiast transpiling JSX w wierszu polecenia (jak pokazano w poprzedniej sekcji), można prze JSX podczas kompilowania z programu Visual Studio.

* Otwórz *package.jsna* i Dodaj następującą sekcję po `dependencies` sekcji:

   ```json
   "scripts": {
    "build": "webpack-cli app.tsx --config webpack-config.js"
   }
   ```

## <a name="run-the-app"></a>Uruchamianie aplikacji

1. Wybierz opcję **serwer sieci Web (Google Chrome)** lub **serwer sieci Web (Microsoft Edge)** jako bieżący element docelowy debugowania.

    ::: moniker range=">=vs-2019"
    ![Wybierz Chrome jako element docelowy debugowania](../javascript/media/vs-2019/tutorial-nodejs-react-debug-target.png)
    ::: moniker-end
    ::: moniker range="vs-2017"
    ![Wybierz Chrome jako element docelowy debugowania](../javascript/media/tutorial-nodejs-react-debug-target.png)
    ::: moniker-end

    Jeśli program Chrome jest dostępny na komputerze, ale nie jest wyświetlany jako opcja, wybierz pozycję **Przeglądaj z** listy rozwijanej element docelowy debugowania, a następnie wybierz pozycję Chrome jako domyślny element docelowy przeglądarki (wybierz pozycję **Ustaw jako domyślny**).

1. Aby uruchomić aplikację, naciśnij klawisz **F5** (**Debuguj**  >  **Rozpocznij debugowanie**) lub przycisk Zielona strzałka.

    Zostanie otwarte okno konsoli Node.js, w którym jest wyświetlany port, na którym debuger nasłuchuje.

    Program Visual Studio uruchamia aplikację przez uruchomienie pliku startowego *server.js*.

    ![Uruchom reagowanie w przeglądarce](../javascript/media/tutorial-nodejs-react-running-react.png)

1. Zamknij okno przeglądarki.

1. Zamknij okno konsoli.

## <a name="set-a-breakpoint-and-run-the-app"></a>Ustawianie punktu przerwania i uruchamianie aplikacji

1. W *server.js*kliknij przycisk na marginesie po lewej stronie `staticPath` deklaracji, aby ustawić punkt przerwania:

    ![Ustawianie punktu przerwania](../javascript/media/tutorial-nodejs-react-set-breakpoint.png)

    Punkty przerwania są najbardziej podstawową i istotną funkcją niezawodnego debugowania. Punkt przerwania wskazuje, gdzie program Visual Studio powinien zawiesić uruchomiony kod, aby można było przyjrzeć się wartościom zmiennych lub działaniu pamięci lub niezależnie od tego, czy gałąź kodu jest uruchamiana.

1. Aby uruchomić aplikację, naciśnij klawisz **F5** (**Debuguj**  >  **Rozpocznij debugowanie**).

    Debuger wstrzymuje się w ustawionym punkcie przerwania (Bieżąca instrukcja jest oznaczona kolorem żółtym). Teraz można sprawdzić stan aplikacji, umieszczając kursor na zmiennych, które znajdują się obecnie w zakresie, korzystając **z okien debugera** , takich jak **lokalne** i kontrolki okien.

1. Naciśnij klawisz **F5** , aby kontynuować aplikację.

1. Jeśli chcesz użyć narzędzi Chrome Narzędzia deweloperskie lub F12 dla przeglądarki Microsoft Edge, naciśnij klawisz **F12**. Za pomocą tych narzędzi można przeanalizować DOM i korzystać z aplikacji za pomocą konsoli JavaScript.

1. Zamknij przeglądarkę sieci Web i konsolę programu.

## <a name="set-and-hit-a-breakpoint-in-the-client-side-react-code"></a>Ustawianie i trafienie punktu przerwania w kodzie reakcji po stronie klienta

W poprzedniej sekcji został dołączony debuger do kodu Node.js po stronie serwera. Aby dołączyć debuger z programu Visual Studio i trafiać punkty przerwania w kodzie reakcji po stronie klienta, debuger musi pomóc w zidentyfikowaniu prawidłowego procesu. Aby to umożliwić, należy wykonać jedną z tych metod.

### <a name="prepare-the-browser-for-debugging"></a>Przygotowanie przeglądarki do debugowania

::: moniker range=">=vs-2019"
W tym scenariuszu należy użyć przeglądarki Microsoft Edge (chrom), obecnie o nazwie **Microsoft Edge beta** w środowisku IDE lub w przeglądarce Chrome.
::: moniker-end
::: moniker range="vs-2017"
W tym scenariuszu należy użyć programu Chrome.
::: moniker-end

1. Zamknij wszystkie okna dla przeglądarki docelowej.

   Inne wystąpienia przeglądarki mogą uniemożliwiać otwarcie przeglądarki z włączonym debugowaniem. (Mogą być uruchomione rozszerzenia przeglądarki i uniemożliwiać tryb pełnego debugowania, więc może być konieczne otwarcie Menedżera zadań w celu znalezienia nieoczekiwanych wystąpień programu Chrome).

   ::: moniker range=">=vs-2019"
   Dla przeglądarki Microsoft Edge (chrom) Zamknij również wszystkie wystąpienia programu Chrome. Ponieważ obie przeglądarki korzystają z bazy kodu chromu, daje to najlepsze wyniki.
   ::: moniker-end

2. Uruchom przeglądarkę z włączonym debugowaniem.

    ::: moniker range=">=vs-2019"
    Począwszy od programu Visual Studio 2019, można ustawić `--remote-debugging-port=9222` flagę podczas uruchamiania przeglądarki, wybierając pozycję **Przeglądaj za pomocą..** . > z paska narzędzi **debugowania** , a następnie wybierając pozycję **Dodaj**, a następnie ustawiając flagę w polu **argumenty** . Użyj innej przyjaznej nazwy dla przeglądarki, takiej jak **Edge z debugowaniem** lub **Chrome z debugowaniem**. Aby uzyskać szczegółowe informacje, zobacz [Informacje o wersji](/visualstudio/releases/2019/release-notes-v16.2).

    ![Ustawianie otwarcia przeglądarki z włączonym debugowaniem](../javascript/media/tutorial-nodejs-react-edge-with-debugging.png)

    Alternatywnie Otwórz polecenie **Uruchom** z przycisku **Start** systemu Windows (kliknij prawym przyciskiem myszy i wybierz polecenie **Uruchom**), a następnie wprowadź następujące polecenie:

    `msedge --remote-debugging-port=9222`

    oraz

    `chrome.exe --remote-debugging-port=9222`
    ::: moniker-end

    ::: moniker range="vs-2017"
    Otwórz polecenie **Uruchom** z przycisku **Start** systemu Windows (kliknij prawym przyciskiem myszy i wybierz polecenie **Uruchom**), a następnie wprowadź następujące polecenie:

    `chrome.exe --remote-debugging-port=9222`
    ::: moniker-end

    Spowoduje to uruchomienie przeglądarki z włączonym debugowaniem.

    Aplikacja nie jest jeszcze uruchomiona, dlatego możesz uzyskać pustą stronę przeglądarki.

### <a name="attach-the-debugger-to-client-side-script"></a>Dołącz debuger do skryptu po stronie klienta

1. Przejdź do programu Visual Studio, a następnie ustaw punkt przerwania w kodzie źródłowym, *app-bundle.js*  lub *App. TSX*.

    Dla *app-bundle.js*Ustaw punkt przerwania w `render()` funkcji, jak pokazano na poniższej ilustracji:

    ![Ustawianie punktu przerwania](../javascript/media/tutorial-nodejs-react-set-breakpoint-client-code.png)

    Aby znaleźć `render()` funkcję w pliku *app-bundle.js* , użyj **klawiszy CTRL** + **F** (**Edycja**  >  **Znajdź i Zamień**  >  **szybkie wyszukiwanie**).

    W przypadku *aplikacji App. TSX*Ustaw punkt przerwania wewnątrz `render()` funkcji na `return` instrukcji.

    ![Ustawianie punktu przerwania](../javascript/media/tutorial-nodejs-react-set-breakpoint-in-tsx-file.png)

2. Jeśli ustawiasz punkt przerwania w pliku *TSX* (a nie *app-bundle.js*), musisz zaktualizować *webpack-config.js*. Zastąp następujący kod:

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

    Jest to ustawienie tylko do programowania, aby włączyć debugowanie w programie Visual Studio. To ustawienie umożliwia przesłonięcie wygenerowanych odwołań w pliku mapy źródłowej, *app-bundle.js. map*podczas kompilowania aplikacji. Domyślnie odwołania do pakietu WebPack w pliku mapy źródłowej zawierają prefiks *WebPack:///* , który uniemożliwia programowi Visual Studio znalezienie pliku źródłowego, *App. TSX*. W przypadku wprowadzenia tej zmiany odwołanie do pliku źródłowego, *App. TSX*można zmienić z *WebPack:///./app.TSX* na *./app.TSX*, co umożliwia debugowanie.

3. Wybierz docelową przeglądarkę jako element docelowy debugowania w programie Visual Studio, a następnie naciśnij klawisz **Ctrl** + **F5** (**Debuguj**  >  **Rozpocznij bez debugowania**), aby uruchomić aplikację w przeglądarce.

    ::: moniker range=">=vs-2019"
    Jeśli utworzono konfigurację przeglądarki z przyjazną nazwą, wybierz ją jako element docelowy debugowania.
    ::: moniker-end

    Aplikacja zostanie otwarta na nowej karcie przeglądarki.

4. Wybierz polecenie **Debuguj**  >  **Dołącz do procesu**.

    > [!TIP]
    > Począwszy od programu Visual Studio 2017, po dołączeniu do procesu po raz pierwszy, wykonując poniższe kroki, można szybko ponownie dołączyć do tego samego procesu, wybierając **debugowanie**  >  **ponownie Dołącz do procesu**.

5. W oknie dialogowym **Dołącz do procesu** Pobierz przefiltrowaną listę wystąpień przeglądarki, do których można dołączać.

    ::: moniker range=">=vs-2019"
    W programie Visual Studio 2019 wybierz poprawny debuger dla przeglądarki docelowej, **JavaScript (Chrome)** lub **JavaScript (Microsoft Edge-chrom)** w polu **Dołącz do** wpisz **Chrome** lub **Edge** w polu Filtr, aby odfiltrować wyniki wyszukiwania.
    ::: moniker-end
    ::: moniker range="vs-2017"
    W programie Visual Studio 2017 wybierz pozycję **kod WebKit** w polu **Dołącz do** , wpisz **Chrome** w polu Filtr, aby odfiltrować wyniki wyszukiwania.
    ::: moniker-end

6. Wybierz proces przeglądarki z właściwym portem hosta (localhost w tym przykładzie) i wybierz pozycję **Dołącz**.

    Port (1337) może również pojawić się w polu **title** , aby ułatwić wybranie prawidłowego wystąpienia przeglądarki.

    ::: moniker range=">=vs-2019"
    Poniższy przykład pokazuje, jak wygląda wyszukiwanie w przeglądarce Microsoft Edge (chrom).

    ![Dołącz do procesu](../javascript/media/tutorial-nodejs-react-attach-to-process-edge.png)
    ::: moniker-end
    ::: moniker range="vs-2017"
    ![Dołącz do procesu](../javascript/media/tutorial-nodejs-react-attach-to-process.png)

    Wiadomo, że debuger został prawidłowo dołączony, gdy DOM Explorer i konsola JavaScript zostanie otwarta w programie Visual Studio. Te narzędzia debugowania są podobne do narzędzi Chrome Narzędzia deweloperskie i F12 dla przeglądarki Microsoft Edge.
    ::: moniker-end

    > [!TIP]
    > Jeśli debuger nie zostanie dołączony i zostanie wyświetlony komunikat "nie można dołączyć do procesu. Operacja nie jest dozwolona w bieżącym stanie ". przed uruchomieniem przeglądarki w trybie debugowania należy zamknąć wszystkie wystąpienia przeglądarki docelowej za pomocą Menedżera zadań. Mogą działać rozszerzenia przeglądarki i uniemożliwiać tryb pełnego debugowania.

7. Ponieważ kod z punktem przerwania został już wykonany, Odśwież stronę przeglądarki, aby trafić punkt przerwania.

    W debugerze można przeanalizować stan aplikacji, umieszczając kursor nad zmiennymi i korzystając z okien debugera. Debuger można uzyskać, przechodząc przez kod (**F5**, **F10**i **F11**). Aby uzyskać więcej informacji na temat podstawowych funkcji debugowania, zobacz [pierwsze spojrzenie na debuger](../debugger/debugger-feature-tour.md).

    Punkt przerwania można napotkać w *app-bundle.js* lub w jego zamapowanej lokalizacji w *App. TSX*, w zależności od tego, które czynności zostały wcześniej wykonane, wraz ze środowiskiem i stanem przeglądarki. W obu przypadkach możesz przejść przez kod i przeanalizować zmienne.

   * Jeśli konieczne jest zabicie do kodu w *aplikacji App. TSX* i nie można tego zrobić, użyj **dołączenia do procesu** , jak opisano w poprzednich krokach, aby dołączyć debuger. Upewnij się, że środowisko zostało prawidłowo skonfigurowane:

      * Zamknięto wszystkie wystąpienia przeglądarki, w tym rozszerzenia programu Chrome (przy użyciu Menedżera zadań), dzięki czemu można uruchomić przeglądarkę w trybie debugowania. Upewnij się, że przeglądarka została uruchomiona w trybie debugowania.

      * Upewnij się, że plik mapy źródłowej zawiera odwołanie do *./app.TSX* , a nie *WebPack:///./app.TSX*, co uniemożliwia debugerowi programu Visual Studio lokalizowanie *aplikacji App. TSX*.
       Alternatywnie, jeśli konieczne jest zabicie do kodu w *App. TSX* i nie można tego zrobić, spróbuj użyć `debugger;` instrukcji w *App. TSX*lub ustawić punkty przerwania w programie Chrome narzędzia deweloperskie (lub F12 Tools for Microsoft Edge).

   * Jeśli musisz przerwać wykonywanie kodu w *app-bundle.js* i nie można tego zrobić, usuń plik mapy źródłowej, *app-bundle.js. map*.

## <a name="next-steps"></a>Następne kroki

> [!div class="nextstepaction"]
> [Wdrażanie aplikacji w systemie Linux App Service](../javascript/publish-nodejs-app-azure.md)
