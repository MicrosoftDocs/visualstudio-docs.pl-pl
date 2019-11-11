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
ms.openlocfilehash: 0405488f6f456f22711498e81789881ffc5a0a8a
ms.sourcegitcommit: 308a2bdbea81df78bffc3a01afce4ab13131fabc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/11/2019
ms.locfileid: "73912997"
---
# <a name="debug-a-javascript-or-typescript-app-in-visual-studio"></a>Debugowanie aplikacji JavaScript lub TypeScript w programie Visual Studio

Program Visual Studio umożliwia debugowanie kodu JavaScript i języka TypeScript. Można ustawiać i trafiać punkty przerwania, dołączać debuger, sprawdzać zmienne, wyświetlać stos wywołań i korzystać z innych funkcji debugowania.

> [!TIP]
> Jeśli program Visual Studio nie został jeszcze zainstalowany, przejdź do strony [plików do pobrania programu Visual Studio](https://visualstudio.microsoft.com/downloads/) , aby zainstalować ją bezpłatnie. W zależności od typu opracowywanej aplikacji może być konieczne zainstalowanie **obciążenia programowania Node. js** w programie Visual Studio.

## <a name="debug-server-side-script"></a>Debugowanie skryptu po stronie serwera

1. Gdy projekt jest otwarty w programie Visual Studio, Otwórz plik JavaScript po stronie serwera (na przykład *Server. js*), kliknij przycisk odstępu w lewym marginesie, aby ustawić punkt przerwania:

    ![Ustawianie punktu przerwania](../javascript/media/tutorial-nodejs-react-set-breakpoint.png)

    Punkty przerwania są najbardziej podstawową i istotną funkcją niezawodnego debugowania. Punkt przerwania wskazuje, gdzie program Visual Studio powinien zawiesić uruchomiony kod, aby można było przyjrzeć się wartościom zmiennych lub działaniu pamięci lub niezależnie od tego, czy gałąź kodu jest uruchamiana.

1. Aby uruchomić aplikację, naciśnij klawisz **F5** (**Debuguj**  > **Rozpocznij debugowanie**).

    Debuger wstrzymuje się w ustawionym punkcie przerwania (Bieżąca instrukcja jest oznaczona kolorem żółtym). Teraz można sprawdzić stan aplikacji, umieszczając kursor na zmiennych, które znajdują się obecnie w zakresie, korzystając **z okien debugera** , takich jak **lokalne** i kontrolki okien.

1. Naciśnij klawisz **F5** , aby kontynuować aplikację.

1. Jeśli chcesz użyć narzędzi Chrome Narzędzia deweloperskie lub F12, naciśnij klawisz **F12**. Za pomocą tych narzędzi można przeanalizować DOM i korzystać z aplikacji za pomocą konsoli JavaScript.

## <a name="debug-client-side-script"></a>Debugowanie skryptu po stronie klienta

::: moniker range=">=vs-2019"
Program Visual Studio zapewnia obsługę debugowania po stronie klienta dla przeglądarki Chrome i programu Microsoft Edge (chrom). W niektórych scenariuszach debuger automatycznie trafi punkty przerwania w języku JavaScript i kodzie TypeScript oraz w osadzonych skryptach w plikach HTML. Aby debugować skrypt po stronie klienta w aplikacjach ASP.NET, zobacz wpis w blogu [debugowanie JavaScript w przeglądarce Microsoft Edge](https://devblogs.microsoft.com/visualstudio/debug-javascript-in-microsoft-edge-from-visual-studio/) i ten [wpis dla Google Chrome](https://devblogs.microsoft.com/aspnet/client-side-debugging-of-asp-net-projects-in-google-chrome).
::: moniker-end
::: moniker range="vs-2017"
Program Visual Studio zapewnia obsługę debugowania po stronie klienta dla przeglądarki Chrome i programu Internet Explorer. W niektórych scenariuszach debuger automatycznie trafi punkty przerwania w języku JavaScript i kodzie TypeScript oraz w osadzonych skryptach w plikach HTML. Debugowanie skryptu po stronie klienta w aplikacjach ASP.NET można znaleźć w blogu [debugowanie po stronie klienta projektów ASP.NET w Google Chrome](https://devblogs.microsoft.com/aspnet/client-side-debugging-of-asp-net-projects-in-google-chrome/).
::: moniker-end

W przypadku aplikacji innych niż ASP.NET wykonaj kroki opisane tutaj.

### <a name="prepare-your-app-for-debugging"></a>Przygotowywanie aplikacji do debugowania

Jeśli źródło jest zminimalizowanego lub utworzone przez transstertę, taką jak TypeScript lub Babel, do najlepszego środowiska debugowania jest wymagane użycie [map źródła](#generate_source_maps) . Bez map źródła można nadal dołączyć debuger do uruchomionego skryptu po stronie klienta. Można jednak tylko ustawiać i trafiać punkty przerwania w pliku zminimalizowanego lub z możliwością presterty, a nie z oryginalnego pliku źródłowego. Na przykład w aplikacji Vue. js skrypt zminimalizowanego jest przenoszona jako ciąg do instrukcji `eval` i nie ma sposobu na efektywne przechodzenie przez ten kod przy użyciu debugera programu Visual Studio, chyba że są używane mapy źródłowe. W złożonych scenariuszach debugowania można także użyć narzędzi Chrome Narzędzia deweloperskie lub F12 dla przeglądarki Microsoft Edge.

Aby uzyskać pomoc dotyczącą generowania map źródeł, zobacz [Generuj mapy źródeł na potrzeby debugowania](#generate_source_maps).

### <a name="prepare_the_browser_for_debugging"></a>Przygotowanie przeglądarki do debugowania

::: moniker range=">=vs-2019"
W tym scenariuszu należy użyć przeglądarki Microsoft Edge (chrom), obecnie o nazwie **Microsoft Edge beta** w środowisku IDE lub w przeglądarce Chrome.
::: moniker-end
::: moniker range="vs-2017"
W tym scenariuszu należy użyć programu Chrome.
::: moniker-end

1. Zamknij wszystkie okna dla przeglądarki docelowej.

   Inne wystąpienia przeglądarki mogą uniemożliwiać otwarcie przeglądarki z włączonym debugowaniem. (Mogą być uruchomione rozszerzenia przeglądarki i uniemożliwiać tryb pełnego debugowania, więc może być konieczne otwarcie Menedżera zadań w celu znalezienia nieoczekiwanych wystąpień programu Chrome).

   ::: moniker range=">=vs-2019"
   Dla przeglądarki Microsoft Edge (chrom) Zamknij również wszystkie wystąpienia programu Chrome. Ponieważ obie przeglądarki używają bazy kodu chromu, daje to najlepsze wyniki.
   ::: moniker-end

2. Uruchom przeglądarkę z włączonym debugowaniem.

    ::: moniker range=">=vs-2019"
    Począwszy od programu Visual Studio 2019, można ustawić flagę `--remote-debugging-port=9222` podczas uruchamiania przeglądarki, wybierając pozycję **Przeglądaj za pomocą..** . > na pasku narzędzi **debugowania** , a następnie wybierając pozycję **Dodaj**, a następnie ustawiając flagę w polu **argumenty** . Użyj innej przyjaznej nazwy dla przeglądarki, takiej jak **Edge z debugowaniem** lub **Chrome z debugowaniem**. Aby uzyskać szczegółowe informacje, zobacz [Informacje o wersji](/visualstudio/releases/2019/release-notes-v16.2).

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

Aby dołączyć debuger z programu Visual Studio i trafić punkty przerwania w kodzie po stronie klienta, debuger musi pomóc w zidentyfikowaniu prawidłowego procesu. Aby to umożliwić, należy wykonać jedną z tych metod.

1. Przejdź do programu Visual Studio, a następnie ustaw punkt przerwania w kodzie źródłowym, który może być plikiem JavaScript, plikiem TypeScript lub plikiem JSX. (Ustaw punkt przerwania w wierszu kodu, który umożliwia używanie punktów przerwania, takich jak instrukcja return lub Deklaracja wariancji).

    ![Ustawianie punktu przerwania](../javascript/media/tutorial-nodejs-react-set-breakpoint-client-code.png)

    Aby znaleźć konkretny kod w profilowanym pliku, użyj **klawiszy Ctrl**+**F** (**edytuj** > **Znajdź i Zamień** > **szybkie wyszukiwanie**).

    W przypadku kodu po stronie klienta, aby napotkać punkt przerwania w pliku TypeScript lub plik JSX zazwyczaj wymaga użycia [map źródła](#generate_source_maps). Mapa źródłowa musi być poprawnie skonfigurowana do obsługi debugowania w programie Visual Studio.

2. Wybierz docelową przeglądarkę jako element docelowy debugowania w programie Visual Studio, a następnie naciśnij klawisz **Ctrl**+**F5** (**Debuguj** > **Rozpocznij bez debugowania**), aby uruchomić aplikację w przeglądarce.

    ::: moniker range=">=vs-2019"
    Jeśli utworzono konfigurację przeglądarki z przyjazną nazwą, wybierz ją jako element docelowy debugowania.
    ::: moniker-end

    Aplikacja zostanie otwarta na nowej karcie przeglądarki.

3. Wybierz  >  debugowania**dołączanie do procesu**.

    > [!TIP]
    > Począwszy od programu Visual Studio 2017, po dołączeniu do procesu po raz pierwszy, wykonując poniższe kroki, można szybko ponownie dołączyć do tego samego procesu, wybierając **debuguj** > **ponownie dołączyć do procesu**.

4. W oknie dialogowym **Dołącz do procesu** Pobierz przefiltrowaną listę wystąpień przeglądarki, do których można dołączać.

    ::: moniker range=">=vs-2019"
    W programie Visual Studio 2019 wybierz poprawny debuger dla docelowej przeglądarki, **JavaScript (Chrome)** lub **JavaScript (Microsoft Edge-chrom)** w polu **Dołącz do** wpisz **Chrome** lub **Edge** w polu Filtr, aby odfiltrować Wyniki wyszukiwania.
    ::: moniker-end
    ::: moniker range="vs-2017"
    W programie Visual Studio 2017 wybierz pozycję **kod WebKit** w polu **Dołącz do** , wpisz **Chrome** w polu Filtr, aby odfiltrować wyniki wyszukiwania.
    ::: moniker-end

5. Wybierz proces przeglądarki z właściwym portem hosta (localhost w tym przykładzie) i wybierz pozycję **Dołącz**.

    Port (na przykład 1337) może również pojawić się w polu **title** , aby ułatwić wybranie prawidłowego wystąpienia przeglądarki.

    ::: moniker range=">=vs-2019"
    Poniższy przykład pokazuje, jak wygląda wyszukiwanie w przeglądarce Microsoft Edge (chrom).

    ![Dołącz do procesu](../javascript/media/tutorial-nodejs-react-attach-to-process-edge.png)
    ::: moniker-end
    ::: moniker range="vs-2017"
    ![Dołącz do procesu](../javascript/media/tutorial-nodejs-react-attach-to-process.png)

    Wiadomo, że debuger został prawidłowo dołączony, gdy DOM Explorer i konsola JavaScript zostanie otwarta w programie Visual Studio. Te narzędzia debugowania są podobne do narzędzi Chrome Narzędzia deweloperskie i F12 dla przeglądarki Microsoft Edge.
    ::: moniker-end

    > [!TIP]
    > Jeśli debuger nie zostanie dołączony i zostanie wyświetlony komunikat "nie można uruchomić adaptera debugowania" lub "nie można dołączyć do procesu. Operacja nie jest dozwolona w bieżącym stanie ". przed uruchomieniem przeglądarki w trybie debugowania należy zamknąć wszystkie wystąpienia przeglądarki docelowej za pomocą Menedżera zadań systemu Windows. Mogą działać rozszerzenia przeglądarki i uniemożliwiać tryb pełnego debugowania.

6. Ponieważ kod z punktem przerwania mógł już zostać wykonany, Odśwież stronę przeglądarki. W razie potrzeby podejmij działanie, aby spowodować wykonanie kodu z punktem przerwania.

    W debugerze można przeanalizować stan aplikacji, umieszczając kursor nad zmiennymi i korzystając z okien debugera. Debuger można uzyskać, przechodząc przez kod (**F5**, **F10**i **F11**). Aby uzyskać więcej informacji na temat podstawowych funkcji debugowania, zobacz [pierwsze spojrzenie na debuger](../debugger/debugger-feature-tour.md).

    Punkt przerwania może zostać trafiony w pliku *. js* lub pliku źródłowym, w zależności od typu aplikacji, które wykonane wcześniej, oraz innych czynników, takich jak stan przeglądarki. W obu przypadkach możesz przejść przez kod i przeanalizować zmienne.

   * Jeśli musisz przerwać kod w pliku źródłowym TypeScript, JSX lub *. Vue* i nie można tego zrobić, upewnij się, że środowisko jest prawidłowo skonfigurowane, zgodnie z opisem w sekcji [Rozwiązywanie problemów](#troubleshooting_source_maps) .

   * Jeśli trzeba podzielić na kod w przekształconym pliku JavaScript (na przykład *App-Bundle. js*) i nie można tego zrobić, usuń plik mapy źródłowej o *nazwie filename. js. map*.

### <a name="troubleshooting_source_maps"></a>Rozwiązywanie problemów z punktami przerwania i mapy źródeł

Jeśli musisz przerwać kod w pliku źródłowym TypeScript lub JSX i nie można go wykonać, użyj **dołączenia do procesu** , jak opisano w poprzednich krokach, aby dołączyć debuger. Upewnij się, że środowisko zostało prawidłowo skonfigurowane:

* Zamknięto wszystkie wystąpienia przeglądarki, w tym rozszerzenia programu Chrome (przy użyciu Menedżera zadań), dzięki czemu można uruchomić przeglądarkę w trybie debugowania.
      
* Upewnij się [, że przeglądarka została uruchomiona w trybie debugowania](#prepare_the_browser_for_debugging).

* Upewnij się, że plik mapy źródłowej zawiera poprawną ścieżkę względną do pliku źródłowego i że nie zawiera nieobsługiwanych prefiksów, takich jak *WebPack:///* , co uniemożliwia debugerowi programu Visual Studio lokalizowanie pliku źródłowego. Na przykład odwołanie, takie jak *WebPack:///.app.TSX* , może zostać poprawione na *./app.TSX*. Można to zrobić ręcznie w pliku mapy źródłowej (który jest przydatny do testowania) lub za pomocą niestandardowej konfiguracji kompilacji. Aby uzyskać więcej informacji, zobacz [Generuj mapy źródeł na potrzeby debugowania](#generate_source_maps).

Alternatywnie, jeśli trzeba podzielić na kod w pliku źródłowym (na przykład *App. TSX*) i nie można go wykonać, spróbuj użyć instrukcji `debugger;` w pliku źródłowym lub ustawić punkty przerwania w narzędzia deweloperskie programu Chrome (lub F12 narzędzia dla przeglądarki Microsoft Edge).

## <a name="generate_source_maps"></a>Generuj mapy źródeł na potrzeby debugowania

Program Visual Studio oferuje możliwość używania i generowania map źródeł w plikach źródłowych JavaScript. Jest to często wymagane, jeśli źródło jest zminimalizowanego lub utworzone przez transstertę, taką jak TypeScript lub Babel. Dostępne opcje zależą od typu projektu.

* Projekt TypeScript w programie Visual Studio domyślnie generuje mapy źródłowe. Aby uzyskać więcej informacji, zobacz [Konfigurowanie map źródła przy użyciu pliku tsconfig. JSON](#configure_source_maps).

* W projekcie JavaScript można generować mapy źródeł przy użyciu pakietu, takiego jak WebPack, oraz kompilatora, takiego jak kompilator języka TypeScript (lub Babel), który można dodać do projektu. Dla kompilatora języka TypeScript należy również dodać plik *tsconfig. JSON* i ustawić opcję kompilatora `sourceMap`. Aby zapoznać się z przykładem, który pokazuje, jak to zrobić przy użyciu podstawowej konfiguracji pakietu WebPack, zobacz [Tworzenie aplikacji node. js z reagowaniem](../javascript/tutorial-nodejs-with-react-and-jsx.md).

> [!NOTE]
> Jeśli jesteś nowym mapowaniem źródeł, Przeczytaj [wprowadzenie do map źródłowych JavaScript](https://www.html5rocks.com/en/tutorials/developertools/sourcemaps/) przed kontynuowaniem. 

Aby skonfigurować ustawienia zaawansowane dla map źródeł, Użyj ustawień *tsconfig. JSON* lub projektu w projekcie TypeScript, ale nie obu.

Aby włączyć debugowanie przy użyciu programu Visual Studio, należy się upewnić, że odwołania do pliku źródłowego na wygenerowanej mapie źródłowej są poprawne (może to wymagać testowania). Na przykład jeśli używasz pakietu WebPack, odwołania w pliku mapy źródłowej zawierają prefiks *WebPack:///* , co uniemożliwia programowi Visual Studio znalezienie pliku źródłowego TYPESCRIPT lub JSX. W związku z tym, gdy poprawisz ten element do celów debugowania, odwołanie do pliku źródłowego (na przykład *App. TSX*) musi zostać zmienione z dowolnego elementu, takiego jak *WebPack:///./app.TSX* *./app.TSX*, co umożliwia debugowanie ( ścieżka jest względna dla pliku źródłowego. Poniższy przykład pokazuje, jak można skonfigurować mapy źródłowe w pakiecie WebPack, który jest jednym z najbardziej popularnych pakietów, dzięki czemu współpracują z programem Visual Studio.

(Tylko pakiet WebPack) Jeśli ustawiasz punkt przerwania w pliku JSX (a nie w pliku JavaScript), musisz zaktualizować konfigurację pakietu WebPack. Na przykład w *WebPack-config. js*może zajść potrzeba zastąpienia następującego kodu:

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

Jest to ustawienie tylko do programowania, które umożliwia debugowanie kodu po stronie klienta w programie Visual Studio.

W przypadku skomplikowanych scenariuszy narzędzia przeglądarki (**F12**) czasami działają najlepiej do debugowania, ponieważ nie wymagają zmiany niestandardowych prefiksów.

### <a name="configure_source_maps"></a>Skonfiguruj mapy źródłowe przy użyciu pliku tsconfig. JSON

Jeśli dodasz plik *tsconfig. JSON* do projektu, program Visual Studio traktuje katalog główny katalogu jako projekt TypeScript. Aby dodać plik, kliknij prawym przyciskiem myszy projekt w Eksplorator rozwiązań, a następnie wybierz polecenie **dodaj > nowy element > pliku konfiguracji języka TYPESCRIPT JSON**. Plik *tsconfig. JSON* , podobny do następującego, zostanie dodany do projektu.

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

#### <a name="compiler-options-for-tsconfigjson"></a>Opcje kompilatora dla tsconfig. JSON

* **inlineSourceMap**: Emituj pojedynczy plik z mapami źródłowymi zamiast tworzenia oddzielnej mapy źródłowej dla każdego pliku źródłowego.
* **inlineSources**: Emituj Źródło obok mapowań źródłowych w pojedynczym pliku; wymaga ustawienia *inlineSourceMap* lub *mapy źródła* .
* **mapRoot**: określa lokalizację, w której debuger powinien znaleźć pliki mapy źródłowej (*map*) zamiast domyślnej lokalizacji. Tej flagi należy użyć, jeśli pliki *map* czasu wykonywania muszą znajdować się w innej lokalizacji niż pliki *. js* . Określona lokalizacja jest osadzona na mapie źródłowej, aby skierować debuger do lokalizacji plików *map* .
* **mapy źródła**: generuje odpowiadający plik *. map* .
* **sourceRoot**: określa lokalizację, w której debuger powinien znaleźć pliki TypeScript zamiast lokalizacji źródłowych. Tej flagi należy użyć, jeśli źródła czasu wykonywania muszą znajdować się w innej lokalizacji niż lokalizacja w czasie projektowania. Określona lokalizacja jest osadzona na mapie źródłowej, aby skierować debuger do miejsca, w którym znajdują się pliki źródłowe.

Aby uzyskać więcej informacji na temat opcji kompilatora, zaznacz [Opcje kompilatora](https://www.typescriptlang.org/docs/handbook/compiler-options.html) strony w podręczniku języka TypeScript.

### <a name="configure-source-maps-using-project-settings-typescript-project"></a>Skonfiguruj mapy źródłowe za pomocą ustawień projektu (projekt TypeScript)

Możesz również skonfigurować ustawienia mapy źródłowej przy użyciu właściwości projektu, klikając prawym przyciskiem myszy projekt, a następnie wybierając pozycję **project > właściwości > > kompilacji języka TypeScript**.

Te ustawienia projektu są dostępne.

* **Generuj mapy źródeł** (równoważne **mapy źródła** w *tsconfig. JSON*): generuje odpowiadający plik *. map* .
* **Określ katalog główny map źródeł** (odpowiednik **mapRoot** w *tsconfig. JSON*): określa lokalizację, w której debuger powinien znaleźć pliki map zamiast wygenerowanych lokalizacji. Tej flagi należy użyć, jeśli pliki *map* czasu wykonywania muszą znajdować się w innej lokalizacji niż pliki. js. Określona lokalizacja jest osadzona na mapie źródłowej, aby skierować debuger do miejsca, w którym znajdują się pliki mapy.
* **Określ katalog główny plików TypeScript** (odpowiednik **sourceRoot** w *tsconfig. JSON*): określa lokalizację, w której debuger powinien znaleźć pliki TypeScript zamiast lokalizacji źródłowych. Tej flagi należy użyć, jeśli pliki źródłowe czasu wykonywania muszą znajdować się w innej lokalizacji niż lokalizacja w czasie projektowania. Określona lokalizacja jest osadzona na mapie źródłowej, aby skierować debuger do miejsca, w którym znajdują się pliki źródłowe.

## <a name="debug-javascript-in-dynamic-files-using-razor-aspnet"></a>Debugowanie kodu JavaScript w plikach dynamicznych przy użyciu Razor (ASP.NET)

::: moniker range=">=vs-2019"
Począwszy od programu Visual Studio 2019, program Visual Studio zapewnia obsługę debugowania tylko dla przeglądarki Chrome i programu Microsoft Edge (chrom).
::: moniker-end
::: moniker range="vs-2017"
Program Visual Studio zapewnia obsługę debugowania tylko dla przeglądarki Chrome i programu Internet Explorer.
::: moniker-end

Nie można jednak automatycznie trafiać punktów przerwania dla plików generowanych za pomocą składnia Razor (cshtml, VBHTML). Istnieją dwie metody, których można użyć do debugowania tego rodzaju pliku:

* **Umieść instrukcję `debugger;`, która ma zostać przerwana**: spowoduje to zatrzymanie wykonywania skryptu dynamicznego i natychmiastowe rozpoczęcie debugowania podczas jego tworzenia.
* **Załaduj stronę i Otwórz dokument dynamiczny w programie Visual Studio**: musisz otworzyć plik dynamiczny podczas debugowania, ustawić punkt przerwania i odświeżyć stronę, aby ta metoda działała. W zależności od tego, czy korzystasz z przeglądarki Chrome, czy programu Internet Explorer, możesz znaleźć plik przy użyciu jednej z następujących strategii:

   Dla programu Chrome przejdź do **Eksplorator rozwiązań > dokumenty skryptu > YourPageName**.

    > [!NOTE]
    > W przypadku korzystania z programu Chrome może zostać wyświetlony komunikat nie można uzyskać **dostępu do tagów > \<script**. To OK, po prostu Kontynuuj debugowanie.

   ::: moniker range=">=vs-2019"
   W przypadku programu Microsoft Edge (chrom) Użyj tej samej procedury jak Chrome.
   ::: moniker-end

   ::: moniker range="vs-2017"
   W przypadku programu Internet Explorer przejdź do **Eksplorator rozwiązań > dokumenty skryptu > Windows Internet Explorer > YourPageName**.
   ::: moniker-end

Aby uzyskać więcej informacji, zobacz [debugowanie po stronie klienta projektów ASP.NET w przeglądarce Google Chrome](https://devblogs.microsoft.com/aspnet/client-side-debugging-of-asp-net-projects-in-google-chrome/).
