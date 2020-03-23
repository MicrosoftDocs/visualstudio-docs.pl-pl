---
title: Debugowanie aplikacji JavaScript lub TypeScript
description: Program Visual Studio zapewnia obsługę debugowania aplikacji JavaScript i TypeScript w programie Visual Studio
ms.date: 11/01/2019
ms.topic: conceptual
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jillfra
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: 3f8fa8fcd859a7464d471972689728dc556a79bd
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75678977"
---
# <a name="debug-a-javascript-or-typescript-app-in-visual-studio"></a>Debugowanie aplikacji JavaScript lub TypeScript w programie Visual Studio

Za pomocą programu Visual Studio można debugować kod JavaScript i TypeScript. Można ustawić i trafić punkty przerwania, dołączyć debuger, sprawdzić zmienne, wyświetlić stos wywołań i użyć innych funkcji debugowania.

> [!TIP]
> Jeśli program Visual Studio nie został jeszcze zainstalowany, przejdź do strony [pobierania programu Visual Studio,](https://visualstudio.microsoft.com/downloads/) aby zainstalować ją bezpłatnie. W zależności od typu tworzenia aplikacji, które robisz, może być konieczne **zainstalowanie obciążenia deweloperskie Node.js** w programie Visual Studio.

## <a name="debug-server-side-script"></a>Skrypt po stronie serwera debugowania

1. Po otwarciu projektu w programie Visual Studio otwórz plik JavaScript po stronie serwera (na przykład *server.js*), kliknij w marginesie na oprawę po lewej stronie marginesu, aby ustawić punkt przerwania:

    ![Ustawianie punktu przerwania](../javascript/media/tutorial-nodejs-react-set-breakpoint.png)

    Punkty przerwania są najbardziej podstawową i istotną cechą niezawodnego debugowania. Punkt przerwania wskazuje, gdzie visual studio należy zawiesić uruchomiony kod, dzięki czemu można spojrzeć na wartości zmiennych lub zachowanie pamięci lub czy gałąź kodu jest coraz uruchamiany.

1. Aby uruchomić aplikację, naciśnij **klawisz F5** (**Debugowanie** > **start debugowania**).

    Debuger wstrzymuje się w punkcie przerwania, który można ustawić (bieżąca instrukcja jest oznaczona na żółto). Teraz możesz sprawdzić stan aplikacji, najeżdżając kursorem na zmienne, które są obecnie w zakresie, używając okien debugera, takich jak **okna Locals** i **Watch.**

1. Naciśnij **klawisz F5,** aby kontynuować aplikację.

1. Jeśli chcesz korzystać z narzędzi programistycznych Chrome lub F12 Tools, naciśnij **klawisz F12**. Za pomocą tych narzędzi można sprawdzić dom i interakcji z aplikacją za pomocą konsoli JavaScript.

## <a name="debug-client-side-script"></a>Debugowanie skryptu po stronie klienta

::: moniker range=">=vs-2019"
Visual Studio zapewnia obsługę debugowania po stronie klienta tylko dla Chrome i Microsoft Edge (Chromium) tylko. W niektórych scenariuszach debuger automatycznie trafia punkty przerwania w kodzie JavaScript i TypeScript oraz w osadzonych skryptach w plikach HTML. Aby uzyskać debugowanie skryptu po stronie klienta w ASP.NET aplikacji, zobacz wpis na blogu [Debug JavaScript w Microsoft Edge](https://devblogs.microsoft.com/visualstudio/debug-javascript-in-microsoft-edge-from-visual-studio/) i ten [post dla Google Chrome](https://devblogs.microsoft.com/aspnet/client-side-debugging-of-asp-net-projects-in-google-chrome). Aby uzyskać możliwość debugowania kodu TypeScript w ASP.NET Core, zobacz Tworzenie [aplikacji core ASP.NET za pomocą języka TypeScript](tutorial-aspnet-with-typescript.md).
::: moniker-end
::: moniker range="vs-2017"
Program Visual Studio zapewnia obsługę debugowania po stronie klienta tylko dla Chrome i Internet Explorer. W niektórych scenariuszach debuger automatycznie trafia punkty przerwania w kodzie JavaScript i TypeScript oraz w osadzonych skryptach w plikach HTML. Aby uzyskać debugowanie skryptu po stronie klienta w ASP.NET aplikacji, zobacz wpis na blogu [Debugowanie po stronie klienta projektów ASP.NET w Google Chrome](https://devblogs.microsoft.com/aspnet/client-side-debugging-of-asp-net-projects-in-google-chrome/).
::: moniker-end

W przypadku aplikacji innych niż ASP.NET wykonaj kroki opisane w tym miejscu.

### <a name="prepare-your-app-for-debugging"></a>Przygotowanie aplikacji do debugowania

Jeśli źródło jest zdominowane lub utworzone przez transpiler, taki jak TypeScript lub Babel, użycie [map źródłowych](#generate_source_maps) jest wymagane dla najlepszego środowiska debugowania. Bez map źródłowych nadal można dołączyć debuger do uruchomionego skryptu po stronie klienta. Jednak można ustawić i trafić punkty przerwania tylko w pliku minified lub transpiled, a nie w oryginalnym pliku źródłowym. Na przykład w aplikacji Vue.js, wbudowany skrypt zostanie `eval` przekazany jako ciąg do instrukcji i nie ma sposobu, aby przejść przez ten kod skutecznie przy użyciu debugera programu Visual Studio, chyba że używasz map źródłowych. W złożonych scenariuszach debugowania możesz również użyć narzędzi programistycznych Chrome lub F12 Tools dla przeglądarki Microsoft Edge.

Aby uzyskać pomoc dotyczącą generowania map źródłowych, zobacz [Generowanie map źródłowych do debugowania](#generate_source_maps).

### <a name="prepare-the-browser-for-debugging"></a><a name="prepare_the_browser_for_debugging"></a>Przygotowanie przeglądarki do debugowania

::: moniker range=">=vs-2019"
W tym scenariuszu użyj microsoft edge (Chromium), obecnie o nazwie **Microsoft Edge Beta** w IDE lub Chrome.
::: moniker-end
::: moniker range="vs-2017"
W tym scenariuszu użyj Chrome.
::: moniker-end

1. Zamknij wszystkie okna przeglądarki docelowej.

   Inne wystąpienia przeglądarki mogą uniemożliwić otwarcie przeglądarki z włączonym debugowaniem. (Rozszerzenia przeglądarki mogą działać i uniemożliwiać pełny tryb debugowania, więc może być konieczne otwarcie Menedżera zadań w celu znalezienia nieoczekiwanych wystąpień Chrome).

   ::: moniker range=">=vs-2019"
   W przypadku przeglądarki Microsoft Edge (Chromium) zamknij również wszystkie wystąpienia Chrome. Ponieważ obie przeglądarki używają podstawy kodu chromu, daje to najlepsze wyniki.
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

Aby dołączyć debuger z programu Visual Studio i trafić punkty przerwania w kodzie po stronie klienta, debuger potrzebuje pomocy w celu zidentyfikowania prawidłowego procesu. Oto jeden ze sposobów, aby to włączyć.

1. Przełącz się do programu Visual Studio, a następnie ustaw punkt przerwania w kodzie źródłowym, który może być plikiem JavaScript, plikiem TypeScript lub plikiem JSX. (Ustaw punkt przerwania w wierszu kodu, który umożliwia punkty przerwania, takie jak return instrukcji lub deklaracji var.)

    ![Ustawianie punktu przerwania](../javascript/media/tutorial-nodejs-react-set-breakpoint-client-code.png)

    Aby znaleźć określony kod w transpiled pliku, użyj **Ctrl**+**F** (**Edytuj** > **znajdź i zamień** > szybkie**znajdowanie**).

    W przypadku kodu po stronie klienta, aby trafić punkt przerwania w pliku TypeScript, plik *.vue*lub JSX zazwyczaj wymaga użycia [map źródłowych](#generate_source_maps). Mapa źródłowa musi być poprawnie skonfigurowana do obsługi debugowania w programie Visual Studio.

2. Wybierz przeglądarkę docelową jako miejsce docelowe debugowania w programie Visual Studio, a następnie naciśnij **klawisze Ctrl**+**F5** **(Debugowanie** > **start bez debugowania),** aby uruchomić aplikację w przeglądarce.

    ::: moniker range=">=vs-2019"
    Jeśli utworzono konfigurację przeglądarki o przyjaznej nazwie, wybierz go jako miejsce docelowe debugowania.
    ::: moniker-end

    Aplikacja zostanie otwarta w nowej karcie przeglądarki.

3. Wybierz **pozycję Debugowanie** > **dołączanie do procesu**.

    > [!TIP]
    > Począwszy od programu Visual Studio 2017, po dołączeniu do procesu po raz pierwszy, wykonując następujące kroki, można szybko ponownie dołączyć do tego samego procesu, wybierając **debugowanie** > **ponownie do procesu.**

4. W oknie dialogowym **Dołączanie do procesu** pobierz filtrowany wykaz wystąpień przeglądarki, do których można dołączyć.
    ::: moniker range=">=vs-2019"
    W programie Visual Studio 2019 wybierz odpowiedni debuger dla przeglądarki docelowej, **JavaScript (Chrome)** lub **JavaScript (Microsoft Edge - Chromium)** w polu **Dołącz do,** wpisz **chrome** lub **edge** w polu filtru, aby filtrować wyniki wyszukiwania.
    ::: moniker-end
    ::: moniker range="vs-2017"
    W programie Visual Studio 2017 wybierz **pozycję Kod zestawu Webkit** w polu **Dołącz do,** wpisz **chrome** w polu filtru, aby filtrować wyniki wyszukiwania.
    ::: moniker-end

5. Wybierz proces przeglądarki z właściwym portem hosta (localhost w tym przykładzie) i wybierz **dołącz**.

    Port (na przykład 1337) może również pojawić się w polu **Tytuł,** aby ułatwić wybranie poprawnego wystąpienia przeglądarki.

    ::: moniker range=">=vs-2019"
    W poniższym przykładzie pokazano, jak to wygląda dla przeglądarki Microsoft Edge (Chromium).

    ![Dołącz do procesu](../javascript/media/tutorial-nodejs-react-attach-to-process-edge.png)
    ::: moniker-end
    ::: moniker range="vs-2017"
    ![Dołącz do procesu](../javascript/media/tutorial-nodejs-react-attach-to-process.png)

    Wiesz, że debuger został dołączony poprawnie, gdy Eksplorator DOM i konsola JavaScript są otwarte w programie Visual Studio. Te narzędzia debugowania są podobne do narzędzi programistycznych Chrome i F12 Tools for Microsoft Edge.
    ::: moniker-end

    > [!TIP]
    > Jeśli debuger nie zostanie dołączony i zostanie wyświetlony komunikat "Nie można uruchomić karty debugowania" lub "Nie można dołączyć do procesu. Operacja nie jest legalna w bieżącym stanie.", użyj Menedżera zadań systemu Windows, aby zamknąć wszystkie wystąpienia przeglądarki docelowej przed uruchomieniem przeglądarki w trybie debugowania. Rozszerzenia przeglądarki mogą być uruchomione i uniemożliwia tryb pełnego debugowania.

6. Ponieważ kod z punktem przerwania może być już wykonany, odśwież stronę przeglądarki. Jeśli to konieczne, podjąć działania, aby spowodować kod z punktem przerwania do wykonania.

    Wstrzymane w debugerze można sprawdzić stan aplikacji, najeżdżając kursorem na zmienne i używając okien debugera. Debuger można przejść przez krok po kroku przez kod (**F5**, **F10**i **F11**). Aby uzyskać więcej informacji na temat podstawowych funkcji debugowania, zobacz [Pierwsze spojrzenie na debuger](../debugger/debugger-feature-tour.md).

    Punkt przerwania może trafić w transpiled pliku *.js* lub pliku źródłowego, w zależności od typu aplikacji, które kroki zostały wcześniej obserwowane i innych czynników, takich jak stan przeglądarki. Tak czy inaczej, można przejść przez kod i zbadać zmienne.

   * Jeśli chcesz podzielić się kodem w pliku źródłowym TypeScript, JSX lub *.vue* i nie możesz tego zrobić, upewnij się, że środowisko jest poprawnie skonfigurowane, zgodnie z opisem w sekcji [Rozwiązywanie problemów.](#troubleshooting_source_maps)

   * Jeśli chcesz podzielić się na kod w przesiedlonym pliku JavaScript (na przykład *app-bundle.js)* i nie możesz tego zrobić, usuń plik mapy źródłowej, *filename.js.map*.

### <a name="troubleshooting-breakpoints-and-source-maps"></a><a name="troubleshooting_source_maps"></a>Rozwiązywanie problemów z punktami przerwania i mapami źródłowymi

Jeśli chcesz podzielić się na kod w pliku źródłowym TypeScript lub JSX i nie możesz tego zrobić, użyj **dołącz do procesu** zgodnie z opisem w poprzednich krokach, aby dołączyć debuger. Upewnij się, że środowisko jest poprawnie skonfigurowane:

* Zamknięto wszystkie wystąpienia przeglądarki, w tym rozszerzenia Chrome (za pomocą Menedżera zadań), dzięki czemu można uruchomić przeglądarkę w trybie debugowania.
      
* Upewnij się, że [przeglądarka została uruchomiona w trybie debugowania](#prepare_the_browser_for_debugging).

* Upewnij się, że plik mapy źródłowej zawiera poprawną ścieżkę względną do pliku źródłowego i że nie zawiera nieobsługiwał prefiksów, takich jak *webpack:///*, co uniemożliwia debugerowi programu Visual Studio lokalizowanie pliku źródłowego. Na przykład odwołanie, takie jak *webpack:///.app.tsx,* może zostać poprawione na *./app.tsx*. Można to zrobić ręcznie w pliku mapy źródłowej (co jest przydatne do testowania) lub za pośrednictwem niestandardowej konfiguracji kompilacji. Aby uzyskać więcej informacji, zobacz [Generowanie map źródłowych do debugowania](#generate_source_maps).

Alternatywnie, jeśli chcesz podzielić się na kod w pliku źródłowym (na przykład *app.tsx)* i nie możesz tego zrobić, spróbuj użyć `debugger;` instrukcji w pliku źródłowym lub ustaw punkty przerwania w Narzędziach programistycznych Chrome (lub F12 Tools for Microsoft Edge).

## <a name="generate-source-maps-for-debugging"></a><a name="generate_source_maps"></a>Generowanie map źródłowych do debugowania

Program Visual Studio ma możliwość używania i generowania map źródłowych w plikach źródłowych JavaScript. Jest to często wymagane, jeśli źródło jest znieksumowane lub utworzone przez transpiler, taki jak TypeScript lub Babel. Dostępne opcje zależą od typu projektu.

* Projekt TypeScript w programie Visual Studio domyślnie generuje mapy źródłowe. Aby uzyskać więcej informacji, zobacz [Konfigurowanie map źródłowych przy użyciu pliku tsconfig.json](#configure_source_maps).

* W projekcie JavaScript można generować mapy źródłowe przy użyciu pakietu, takiego jak webpack i kompilator, taki jak kompilator TypeScript (lub Babel), które można dodać do projektu. W przypadku kompilatora TypeScript należy również dodać plik *tsconfig.json* i ustawić opcję kompilatora. `sourceMap` Na przykład, który pokazuje, jak to zrobić przy użyciu podstawowej konfiguracji pakietu [internetowego, zobacz Tworzenie aplikacji Node.js z React](../javascript/tutorial-nodejs-with-react-and-jsx.md).

> [!NOTE]
> Jeśli jesteś nowy w mapach źródłowych, przeczytaj [wprowadzenie do map źródłowych JavaScript](https://www.html5rocks.com/en/tutorials/developertools/sourcemaps/) przed kontynuowaniem. 

Aby skonfigurować zaawansowane ustawienia map źródłowych, należy użyć *pliku tsconfig.json* lub ustawień projektu w projekcie TypeScript, ale nie obu.

Aby włączyć debugowanie przy użyciu programu Visual Studio, należy upewnić się, że odwołania do pliku źródłowego w wygenerowanej mapie źródłowej są poprawne (może to wymagać testowania). Na przykład w przypadku korzystania z pakietu webpack odwołania w pliku mapy źródłowej zawierają prefiks *webpack:///,* który uniemożliwia programowi Visual Studio znajdowanie pliku źródłowego TypeScript lub JSX. W szczególności po skorygowaniu tego do celów debugowania odwołanie do pliku źródłowego (na przykład *app.tsx*), musi zostać zmienione z czegoś takiego jak *webpack:///./app.tsx* na coś takiego *./app.tsx*, co umożliwia debugowanie (ścieżka jest względem pliku źródłowego). Poniższy przykład pokazuje, jak można skonfigurować mapy źródłowe w pakiecie internetowym, który jest jednym z najczęstszych bundlers, tak aby pracować z programem Visual Studio.

(Tylko webpack) Jeśli ustawiasz punkt przerwania w kodzie typescript pliku JSX (a nie w transpilowanym pliku JavaScript), musisz zaktualizować konfigurację pakietu internetowego. Na przykład w *webpack-config.js*może być konieczne zastąpienie następującego kodu:

```javascript
  output: {
    filename: "./app-bundle.js", // This is an example of the filename in your project
  },
```

z tym kodem:

```javascript
  output: {
    filename: "./app-bundle.js", // Replace with the filename in your project
    devtoolModuleFilenameTemplate: '[resource-path]'  // Removes the webpack:/// prefix
  },
```

Jest to ustawienie tylko do rozwoju, aby włączyć debugowanie kodu po stronie klienta w programie Visual Studio.

W przypadku skomplikowanych scenariuszy narzędzia przeglądarki **(F12)** czasami działają najlepiej do debugowania, ponieważ nie wymagają zmian w prefiksach niestandardowych.

### <a name="configure-source-maps-using-a-tsconfigjson-file"></a><a name="configure_source_maps"></a>Konfigurowanie map źródłowych przy użyciu pliku tsconfig.json

Jeśli dodasz plik *tsconfig.json* do projektu, program Visual Studio traktuje katalog główny jako projekt TypeScript. Aby dodać plik, kliknij prawym przyciskiem myszy projekt w Eksploratorze rozwiązań, a następnie wybierz polecenie **Dodaj > Nowy element > pliku konfiguracyjnego TypeScript JSON**. Plik *tsconfig.json* podobny do następującego pliku zostanie dodany do projektu.

```json
{
  "compilerOptions": {
    "noImplicitAny": false,
    "noEmitOnError": true,
    "removeComments": false,
    "sourceMap": true,
    "target": "es5"
  },
  "exclude": [
    "node_modules",
    "wwwroot"
  ]
}
```

#### <a name="compiler-options-for-tsconfigjson"></a>Opcje kompilatora dla tsconfig.json

* **inlineSourceMap**: Emituj pojedynczy plik z mapami źródłowymi zamiast tworzenia oddzielnej mapy źródłowej dla każdego pliku źródłowego.
* **inlineSources**: Emituj źródło obok map źródłowych w jednym pliku; wymaga *inlineSourceMap* lub *sourceMap* do zestawu.
* **mapRoot**: Określa lokalizację, w której debuger powinien znaleźć pliki mapy źródłowej (*.map*) zamiast domyślnej lokalizacji. Użyj tej flagi, jeśli pliki *.map* w czasie wykonywania muszą znajdować się w innym miejscu niż pliki *.js.* Określona lokalizacja jest osadzona na mapie źródłowej w celu skierowana debugera do lokalizacji plików *.map.*
* **sourceMap**: Generuje odpowiedni plik *.map.*
* **sourceRoot**: Określa lokalizację, w której debuger powinien znajdować pliki TypeScript zamiast lokalizacji źródłowych. Użyj tej flagi, jeśli źródła w czasie wykonywania muszą znajdować się w innej lokalizacji niż lokalizacja w czasie projektowania. Określona lokalizacja jest osadzona na mapie źródłowej, aby skierować debuger do miejsca, w którym znajdują się pliki źródłowe.

Aby uzyskać więcej informacji na temat opcji kompilatora, sprawdź [opcje kompilatora](https://www.typescriptlang.org/docs/handbook/compiler-options.html) stron w podręczniku TypeScript.

### <a name="configure-source-maps-using-project-settings-typescript-project"></a>Konfigurowanie map źródłowych przy użyciu ustawień projektu (projekt TypeScript)

Ustawienia mapy źródłowej można również skonfigurować przy użyciu właściwości projektu, klikając prawym przyciskiem myszy projekt, a następnie wybierając **polecenie Właściwości > projektu > Kompilacja > Debugowania w języku TypeScript.**

Te ustawienia projektu są dostępne.

* **Generowanie map źródłowych** (odpowiednik **sourceMap** w *tsconfig.json):* Generuje odpowiedni plik *.map.*
* **Określ katalog główny map źródłowych** (odpowiednik **mapRoot** in *tsconfig.json):* Określa lokalizację, w której debuger powinien znajdować pliki map zamiast generowanych lokalizacji. Użyj tej flagi, jeśli pliki *.map* w czasie wykonywania muszą znajdować się w innej lokalizacji niż pliki .js. Określona lokalizacja jest osadzona na mapie źródłowej, aby skierować debuger do miejsca, w którym znajdują się pliki mapy.
* **Określ katalog główny plików TypeScript** (odpowiednik **sourceRoot** in *tsconfig.json):* Określa lokalizację, w której debuger powinien znajdować pliki TypeScript zamiast lokalizacji źródłowych. Użyj tej flagi, jeśli pliki źródłowe w czasie wykonywania muszą znajdować się w innej lokalizacji niż lokalizacja w czasie projektowania. Określona lokalizacja jest osadzona na mapie źródłowej, aby skierować debuger do miejsca, w którym znajdują się pliki źródłowe.

## <a name="debug-javascript-in-dynamic-files-using-razor-aspnet"></a>Debugowanie języka JavaScript w plikach dynamicznych przy użyciu razor (ASP.NET)

::: moniker range=">=vs-2019"
Począwszy od programu Visual Studio 2019 program Visual Studio zapewnia obsługę debugowania tylko dla Chrome i Microsoft Edge (Chromium).
::: moniker-end
::: moniker range="vs-2017"
Program Visual Studio zapewnia obsługę debugowania tylko dla Chrome i Internet Explorer.
::: moniker-end

Nie można jednak automatycznie trafić punktów przerwania w plikach generowanych za pomocą składni Razor (cshtml, vbhtml). Istnieją dwa podejścia, których można użyć do debugowania tego rodzaju pliku:

* **Umieść `debugger;` instrukcję, w której chcesz przerwać:** Powoduje to, że skrypt dynamiczny zatrzymuje wykonywanie i natychmiast rozpoczyna debugowanie podczas jego tworzenia.
* **Załaduj stronę i otwórz dokument dynamiczny w programie Visual Studio:** Musisz otworzyć plik dynamiczny podczas debugowania, ustawić punkt przerwania i odświeżyć stronę, aby ta metoda działała. W zależności od tego, czy korzystasz z Chrome, czy Internet Explorera, plik zostanie odnalezieny przy użyciu jednej z następujących strategii:

   W chrome przejdź do **Programu Solution Explorer > Script Documents > YourPageName**.

    > [!NOTE]
    > Podczas korzystania z Chrome, może pojawić się komunikat **nie źródło jest dostępne między \<tagami skryptu>**. To jest OK, po prostu kontynuuj debugowanie.

   ::: moniker range=">=vs-2019"
   W przypadku przeglądarki Microsoft Edge (Chromium) należy stosować tę samą procedurę co Chrome.
   ::: moniker-end

   ::: moniker range="vs-2017"
   W programie Internet Explorer przejdź do programu **> Dokumenty skryptów Eksploratora rozwiązań > programie Windows Internet Explorer > Aplikacji Twoja StronaName**.
   ::: moniker-end

Aby uzyskać więcej informacji, zobacz [Debugowanie po stronie klienta projektów ASP.NET w Google Chrome](https://devblogs.microsoft.com/aspnet/client-side-debugging-of-asp-net-projects-in-google-chrome/).
