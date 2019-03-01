---
title: Debugowanie aplikacji w języku JavaScript lub TypeScript
description: Program Visual Studio zapewnia obsługę debugowania aplikacji JavaScript i TypeScript w programie Visual Studio
ms.date: 12/03/2018
ms.topic: conceptual
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jillfra
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: af11a16c94f50c5d7614d8d630534433332a4d91
ms.sourcegitcommit: 87d7123c09812534b7b08743de4d11d6433eaa13
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/01/2019
ms.locfileid: "57223393"
---
# <a name="debug-a-javascript-or-typescript-app-in-visual-studio"></a>Debugowanie aplikacji w języku JavaScript lub TypeScript w programie Visual Studio

Możesz debugować kod JavaScript i TypeScript za pomocą programu Visual Studio. Można ustawić i identyfikować punkty przerwania, Dołącz debuger, sprawdzanie zmiennych, przejrzyj stos wywołań i korzystanie z innych funkcji debugowania.

> [!TIP]
> Jeśli jeszcze nie zainstalowano programu Visual Studio, przejdź do strony [program Visual Studio pobiera](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) strony, aby zainstalować go za darmo. W zależności od typu tworzenia aplikacji, które wykonujesz, użytkownik może być konieczne zainstalowanie **pakiet roboczy programowania Node.js** z programem Visual Studio.

## <a name="debug-server-side-script"></a>Debugowanie skryptu po stronie serwera

1. Za pomocą projektu Otwórz w programie Visual Studio, otwórz plik języka JavaScript po stronie serwera (takich jak *server.js*), kliknij na marginesie na oprawę po lewej stronie, można ustawić punktu przerwania:

    ![Ustaw punkt przerwania](../javascript/media/tutorial-nodejs-react-set-breakpoint.png)

    Punkty przerwania są najbardziej podstawowa i podstawowych funkcji niezawodne debugowanie. Punkt przerwania wskazuje, gdzie programu Visual Studio powinny zawiesić uruchamianie kodu, dzięki czemu możesz zapoznaj się z wartości zmiennych lub zachowanie pamięci lub czy gałąź kodu wprowadzenie uruchomieniu.

1. Aby uruchomić aplikację, naciśnij klawisz **F5** (**debugowania** > **Rozpocznij debugowanie**).

    Debuger zatrzymuje się w punkcie przerwania zestawu (bieżąca instrukcja jest oznaczona kolorem żółtym). Teraz możesz sprawdzić stan swojej aplikacji, ustawiając kursor nad zmiennych, które obecnie znajdują się w zakresie, za pomocą okna debugera, takie jak **lokalne** i **Obejrzyj** systemu windows.

1. Naciśnij klawisz **F5** kontynuowanie działania aplikacji.

1. Jeśli chcesz użyć narzędzia deweloperskie przeglądarki Chrome lub F12 Tools, naciśnij klawisz **F12**. Można użyć tych narzędzi do badania modelu DOM i interakcji z aplikacją przy użyciu konsoli języka JavaScript.

## <a name="debug-client-side-script"></a>Debugowanie skryptu po stronie klienta

Visual Studio zawiera obsługę debugowania dla programu Chrome i Internet Explorer tylko. W niektórych scenariuszach debuger uderza automatycznie punktów przerwania w kodzie JavaScript i TypeScript i osadzonych skryptów dla plików HTML.

Jeśli źródło jest zminimalizowany lub utworzone przez transpiler TypeScript lub Babel, użycie [źródła mapy](#generate_sourcemaps) jest wymagana dla najlepsze środowisko debugowania. Bez mapy źródła nadal można dołączyć debuger do skryptu uruchomiona po stronie klienta. Jednak tylko można ustawić i identyfikować punkty przerwania w pliku zminimalizowany lub transpiled, a nie oryginalnego pliku źródłowego. Na przykład w aplikacji Vue.js zminimalizowany skryptu przekazywane jako parametry do `eval` instrukcji, a nie istnieje sposób do wykonania kroków tego kodu, które skutecznie za pomocą debugera programu Visual Studio, chyba że używasz mapy źródła. W przypadku niektórych złożonych scenariuszy debugowania mogą także używać narzędzia deweloperskie przeglądarki Chrome lub F12 Tools dla programu Microsoft Edge.

Aby dołączyć debuger programu Visual Studio i trafień punktów przerwania w kodzie po stronie klienta, debuger zwykle potrzebuje pomocy, aby zidentyfikować korygowania procesu. Oto jeden ze sposobów, aby je włączyć za pomocą przeglądarki Chrome.

### <a name="attach-the-debugger-to-client-side-script-using-chrome"></a>Dołącz debuger do skryptu po stronie klienta za pomocą przeglądarki Chrome

1. Zamknij wszystkie okna przeglądarki Chrome.

    Ta akcja jest to konieczne, zanim będzie można uruchomić przeglądarki Chrome w trybie debugowania.

2. Otwórz **Uruchom** polecenia Windows **Start** przycisk (kliknij prawym przyciskiem myszy i wybierz polecenie **Uruchom**), a następnie wprowadź następujące polecenie:

    `chrome.exe --remote-debugging-port=9222`

    To polecenie uruchamia dla programu Chrome z włączonym debugowaniem.

3. Przełącz się do programu Visual Studio i ustaw punkt przerwania w kodzie źródłowym. (Ustaw punkt przerwania w wierszu kodu, który umożliwia punkty przerwania, takich jak `return` instrukcji lub `var` deklaracji).

    ![Ustaw punkt przerwania](../javascript/media/tutorial-nodejs-react-set-breakpoint-client-code.png)

    Jeśli trzeba znaleźć określonego kodu w dużych, wygenerowany plik, użyj **Ctrl**+**F** (**Edytuj** > **Znajdź i Zamień**  >  **Szybkiego wyszukiwania**).

4. Za pomocą przeglądarki Chrome wybrany jako cel debugowania w programie Visual Studio, naciśnij klawisz **Ctrl**+**F5** (**debugowania** > **Rozpocznij bez debugowania** ) do uruchomienia aplikacji w przeglądarce.

    Aplikacja zostanie otwarta nowa karta przeglądarki.

    Jeśli dla programu Chrome jest dostępne na danym komputerze, ale nie są wyświetlane jako opcja, wybierz opcję **przeglądanie za pomocą** z listy rozwijanej docelowego debugowania i wybierz opcję dla programu Chrome jako domyślny element docelowy przeglądarki (wybierz **Ustaw jako domyślny**).

5. Wybierz **debugowania** > **dołączyć do procesu**.

6. W **dołączyć do procesu** okna dialogowego wybierz **kodu aparatu WebKit** w **dołączyć do** wpisz **chrome** w polu filtru, aby filtrować wyniki wyszukiwania.

    **Kod aparatu WebKit** jest wymaganą wartością dla programu Chrome, czyli na podstawie aparatu Webkit przeglądarki.

7. Wybierz proces dla programu Chrome przy użyciu właściwy host port (1337 na tej ilustracji), a następnie wybierz pozycję **Dołącz**.

    ![Dołącz do procesu](../javascript/media/tutorial-nodejs-react-attach-to-process.png)

    Wiesz, że debuger został dołączony poprawnie otwieraniu konsoli języka JavaScript i narzędzia DOM Explorer w programie Visual Studio. Te narzędzia do debugowania są podobne do narzędzia programistyczne dla programu Chrome i F12 Tools dla Microsoft Edge.

    > [!NOTE]
    > Jeśli debuger nie dołączy i zostanie wyświetlony komunikat "nie można dołączyć do procesu. Operacja jest niedozwolona w bieżącym stanie", zamknij wszystkie wystąpienia programu Chrome, przed rozpoczęciem Chrome w trybie debugowania za pomocą Menedżera zadań. Rozszerzenia dla programu Chrome może być uruchomiony i zapobieganie tryb pełnego debugowania.

8. Jeśli kod za pomocą punktu przerwania zostały już wykonane, Odśwież stronę przeglądarki w taki sposób, aby trafiony punkt przerwania.

    Gdy wstrzymaniu w debugerze, można sprawdzić stan swojej aplikacji, przenosząc kursor myszy nad zmienne okien i korzystanie z debugera. Debuger może przejść przez krokowe wykonywanie kodu (**F5**, **F10**, i **F11**).

    Dla zminimalizowany lub transpiled JavaScript, można napotkać punkt przerwania w albo transpiled JavaScript lub lokalizacja zamapowanych w pliku TypeScript (przy użyciu map źródeł), w zależności od stanu usługi środowisko i przeglądarki. W obu przypadkach możesz przejść przez kod i Sprawdź zmienne.

    * Jeśli potrzebujesz wszedł do kodu w pliku TypeScript i nie można to zrobić, użyj **dołączyć do procesu** zgodnie z opisem w poprzednich krokach, aby dołączyć debuger. Następnie otwórz dynamicznie generowanych plików TypeScript za pomocą Eksploratora rozwiązań, otwierając **dokumenty skryptów** > **filename.tsx**, a następnie ustaw punkt przerwania i Odśwież stronę w przeglądarce (Ustaw punkt przerwania w wierszu kodu, który umożliwia punkty przerwania, takich jak `return` instrukcji lub `var` deklaracji).

        Alternatywnie, jeśli zachodzi potrzeba Wejdź do kodu w pliku TypeScript i nie mogą to zrobić, użyj `debugger;` instrukcji w TypeScript pliku lub zamiast tego ustawić punkty przerwania w Developer Tools dla programu Chrome.

    * Jeśli musisz Wejdź do kodu w pliku JavaScript transpiled (na przykład *bundle.js aplikacji*) i nie można to zrobić, usuń plik mapy źródłowej *filename.js.map*.

     > [!TIP]
     > Po dołączeniu do procesu po raz pierwszy wykonać następujące kroki, możesz szybko dołączyć do tego samego procesu w programie Visual Studio 2017, wybierając **debugowania** > **ponownie Dołącz do procesu**.

## <a name="generate_sourcemaps"></a> Generuj mapy źródeł w celu debugowania

Visual Studio ma możliwość użycia i Generuj mapy źródeł w plikach źródłowych języka JavaScript. Jest to często wymagane, jeśli źródło jest zminimalizowany lub utworzone przez transpiler TypeScript lub Babel. Dostępne opcje zależą od typu projektu.

* Domyślnie projekt TypeScript w programie Visual Studio generuje map źródeł dla Ciebie.

* W projekcie w języku JavaScript, musisz wygenerować mapy źródła przy użyciu narzędzia bundler, takich jak webpack i kompilatora takie jak kompilator (lub w Babel) TypeScript, które mogą zostać dodane do projektu. Dla kompilatora TypeScript, musisz również dodać *tsconfig.json* pliku. Na przykład, który pokazuje, jak to zrobić za pomocą konfiguracji webpack podstawowe, zobacz [tworzenie aplikacji Node.js na platformie React](../javascript/tutorial-nodejs-with-react-and-jsx.md).

> [!NOTE]
> Jeśli dopiero zaczynasz korzystać z mapy źródła, przeczytaj [wprowadzenie do mapy źródła JavaScript](https://www.html5rocks.com/en/tutorials/developertools/sourcemaps/) przed kontynuowaniem.

Aby skonfigurować ustawienia zaawansowane mapy źródła, należy użyć *tsconfig.json* lub w ustawieniach projektu w projekt TypeScript, ale nie oba.

### <a name="configure-source-maps-using-a-tsconfigjson-file"></a>Konfigurowanie map źródeł przy użyciu pliku tsconfig.json

Jeśli dodasz *tsconfig.json* plik do projektu programu Visual Studio traktuje katalog główny jako projekt TypeScript. Aby dodać plik, kliknij prawym przyciskiem myszy projekt w Eksploratorze rozwiązań, a następnie wybierz **Dodaj > Nowy element > sieci Web > Skrypty > pliku konfiguracji JSON TypeScript**. A *tsconfig.json* plików, takich jak pobiera dodaje do projektu.

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

* **inlineSourceMap**: Emituj pojedynczy plik z mapami źródeł zamiast tworzenia map oddzielne źródło dla każdego pliku źródłowego.
* **inlineSources**: Emituj źródło razem map źródeł w pojedynczym pliku; wymaga *inlineSourceMap* lub *mapy źródła* do ustawienia.
* **mapRoot**: Określa lokalizację, w której debuger powinien znajdować się w mapę źródłową (*.map*) zamiast domyślnej lokalizacji. Użyj tej flagi, jeśli środowiska wykonawczego *.map* pliki muszą znajdować się w innej lokalizacji niż *js* plików. Określona lokalizacja jest osadzony w mapę źródłową do kierowania debugera do lokalizacji *.map* plików.
* **mapy źródła**: Generuje odpowiadający *.map* pliku.
* **sourceRoot**: Określa lokalizację, gdzie debuger powinien znaleźć plików TypeScript zamiast szukania w lokalizacjach źródłowych. Jeśli źródła czasu wykonywania muszą znajdować się w innej lokalizacji niż lokalizacja, w czasie projektowania, należy użyć tej flagi. Określona lokalizacja jest osadzony w mapę źródłową do kierowania debugera, na którym znajdują się pliki źródłowe.

Aby uzyskać więcej informacji na temat opcji kompilatora, sprawdź stronę [opcje kompilatora](https://www.typescriptlang.org/docs/handbook/compiler-options.html) w podręczniku TypeScript.

### <a name="configure-source-maps-using-project-settings"></a>Konfigurowanie map źródeł przy użyciu ustawień projektu

Można również skonfigurować ustawienia mapy źródła, korzystanie z właściwości projektu, kliknij prawym przyciskiem myszy projekt, a następnie wybierając **projektu > Właściwości > kompilacji TypeScript > debugowanie**.

Te ustawienia projektu są dostępne.

* **Generuj mapy źródeł** (równoważne **mapy źródła** w *tsconfig.json*): Generuje odpowiadający *.map* pliku.
* **Określ katalog główny map źródeł** (równoważne **mapRoot** w *tsconfig.json*): Określa lokalizację, gdzie debuger powinien znaleźć plików map zamiast szukania w wygenerowanych lokalizacjach. Użyj tej flagi, jeśli środowiska wykonawczego *.map* pliki muszą znajdować się w innej lokalizacji niż pliki js. Określona lokalizacja jest osadzony w mapę źródłową do kierowania debugera, na którym znajdują się pliki mapy.
* **Określ katalog główny plików TypeScript** (równoważne **sourceRoot** w *tsconfig.json*): Określa lokalizację, gdzie debuger powinien znaleźć plików TypeScript zamiast szukania w lokalizacjach źródłowych. Jeśli pliki źródłowe w czasie wykonywania muszą znajdować się w innej lokalizacji niż lokalizacja, w czasie projektowania, należy użyć tej flagi. Określona lokalizacja jest osadzony w mapę źródłową do kierowania debugera, na którym znajdują się pliki źródłowe.

## <a name="debug-javascript-in-dynamic-files-using-razor-aspnet"></a>Debugowanie kodu JavaScript w dynamicznych plikach za pomocą programu Razor (ASP.NET)

Visual Studio zawiera obsługę debugowania dla programu Chrome i Internet Explorer tylko. Będzie automatycznie dołączać punktów przerwania do języka JavaScript/TypeScript i osadzonych skryptów dla plików HTML.

Debugowanie dynamicznie generowanych plików nie jest automatyczna. Nie można automatycznie identyfikować punkty przerwania na pliki wygenerowane ze składnią Razor (cshtml, vbhtml). Istnieją dwie metody używane do debugowania tego typu plików:

* **Miejsce `debugger;` instrukcji, w którym chcesz przerwać**: Powoduje to dynamiczny skrypt, aby zatrzymać wykonywanie, a następnie rozpocząć debugowanie natychmiast, gdy jest tworzona.
* **Załadowanie strony, a następnie otwórz dokument dynamicznych w programie Visual Studio**: Można będzie muszą otworzyć dynamiczny plik podczas debugowania, ustaw punkt przerwania i Odśwież stronę dla tej metody do pracy. W zależności od tego, czy używasz przeglądarki Chrome lub Internet Explorer można znaleźć pliku przy użyciu jednej z następujących strategii:

   Dla programu Chrome, przejdź do **Eksploratora rozwiązań > dokumenty skryptów > YourPageName**.

    > [!NOTE]
    > Korzystając z przeglądarki Chrome, może zostać wyświetlony komunikat **źródło nie jest dostępne między \<skryptu > Znaczniki**. Stanowi to problemu, po prostu kontynuować debugowanie.

   Dla programu Internet Explorer przejdź do **Eksploratora rozwiązań > dokumenty skryptów > Windows Internet Explorer > YourPageName**.

Aby uzyskać więcej informacji, zobacz [klienta debugowania projektów programu ASP.NET w przeglądarce Google Chrome](https://devblogs.microsoft.com/aspnet/client-side-debugging-of-asp-net-projects-in-google-chrome/).