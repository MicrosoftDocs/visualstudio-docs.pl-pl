---
title: Debugowanie aplikacji JavaScript lub TypeScript
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
ms.openlocfilehash: ec2b93d212f9a9485f6e817d00b06cccfec47a93
ms.sourcegitcommit: 978df2feb5e64228d2e3dd430b299a5c234cda17
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2019
ms.locfileid: "72888699"
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

Program Visual Studio zapewnia obsługę debugowania tylko dla przeglądarki Chrome i programu Internet Explorer. W niektórych scenariuszach debuger automatycznie trafi punkty przerwania w języku JavaScript i kodzie TypeScript oraz w osadzonych skryptach w plikach HTML.

Jeśli źródło jest zminimalizowanego lub utworzone przez transstertę, taką jak TypeScript lub Babel, do najlepszego środowiska debugowania jest wymagane użycie [map źródła](#generate_sourcemaps) . Bez map źródła można nadal dołączyć debuger do uruchomionego skryptu po stronie klienta. Można jednak tylko ustawiać i trafiać punkty przerwania w pliku zminimalizowanego lub z możliwością presterty, a nie z oryginalnego pliku źródłowego. Na przykład w aplikacji Vue. js skrypt zminimalizowanego jest przenoszona jako ciąg do instrukcji `eval` i nie ma sposobu na efektywne przechodzenie przez ten kod przy użyciu debugera programu Visual Studio, chyba że są używane mapy źródłowe. W niektórych złożonych scenariuszach debugowania można także użyć narzędzi Chrome Narzędzia deweloperskie lub F12 dla przeglądarki Microsoft Edge.

W celu dołączenia debugera z programu Visual Studio i trafień punktów przerwania w kodzie po stronie klienta debuger zwykle potrzebuje pomocy, aby zidentyfikować właściwy proces. Oto jeden ze sposobów na włączenie tego przy użyciu programu Chrome.

### <a name="attach-the-debugger-to-client-side-script-using-chrome"></a>Dołącz debuger do skryptu po stronie klienta za pomocą programu Chrome

1. Zamknij wszystkie okna programu Chrome.

    Ta akcja jest wymagana, aby można było uruchomić program Chrome w trybie debugowania.

2. Otwórz polecenie **Uruchom** z przycisku **Start** systemu Windows (kliknij prawym przyciskiem myszy i wybierz polecenie **Uruchom**), a następnie wprowadź następujące polecenie:

    `chrome.exe --remote-debugging-port=9222`

    To polecenie uruchamia program Chrome z włączonym debugowaniem.

    ::: moniker range=">=vs-2019"

    > [!NOTE]
    > Możesz również ustawić flagę `--remote-debugging-port` podczas uruchamiania przeglądarki, wybierając pozycję **Przeglądaj za pomocą..** . > na pasku narzędzi **debugowania** , a następnie wybierając pozycję **Dodaj**, a następnie ustawiając flagę w polu **argumenty** . Użyj innej przyjaznej nazwy dla przeglądarki, takiej jak **Chrome z debugowaniem**. Aby uzyskać szczegółowe informacje, zobacz [Informacje o wersji](/visualstudio/releases/2019/release-notes-preview).

    ::: moniker-end

3. Przejdź do programu Visual Studio i ustaw punkt przerwania w kodzie źródłowym. (Ustaw punkt przerwania w wierszu kodu, który umożliwia używanie punktów przerwania, takich jak instrukcja `return` lub Deklaracja `var`).

    ![Ustawianie punktu przerwania](../javascript/media/tutorial-nodejs-react-set-breakpoint-client-code.png)

    Jeśli chcesz znaleźć konkretny kod w dużym, wygenerowanym pliku, użyj **klawiszy Ctrl** +**F** (**Edytuj**  > **Znajdź i Zastąp**  > **szybkie wyszukiwanie**).

4. Gdy w programie Visual Studio wybrano element Chrome, naciśnij klawisz **Ctrl** +**F5** (**Debuguj**  > **Uruchom bez debugowania**), aby uruchomić aplikację w przeglądarce.

    Aplikacja zostanie otwarta na nowej karcie przeglądarki.

    Jeśli program Chrome jest dostępny na komputerze, ale nie jest wyświetlany jako opcja, wybierz pozycję **Przeglądaj z** listy rozwijanej element docelowy debugowania, a następnie wybierz pozycję Chrome jako domyślny element docelowy przeglądarki (wybierz pozycję **Ustaw jako domyślny**).

5. Wybierz  >  debugowania**dołączanie do procesu**.

6. W oknie dialogowym **Dołącz do procesu** wybierz pozycję **kod WebKit** w polu **Dołącz do** , wpisz **Chrome** w polu Filtr, aby odfiltrować wyniki wyszukiwania.

    **Kod WebKit** jest wartością wymaganą dla programu Chrome, która jest przeglądarką opartą na WebKit.

7. Wybierz proces Chrome z prawidłowym portem hosta (1337 na tej ilustracji) i wybierz pozycję **Dołącz**.

    ![Dołącz do procesu](../javascript/media/tutorial-nodejs-react-attach-to-process.png)

    ::: moniker range="vs-2017"
    Wiadomo, że debuger został prawidłowo dołączony, gdy DOM Explorer i konsola JavaScript zostanie otwarta w programie Visual Studio. Te narzędzia debugowania są podobne do narzędzi Chrome Narzędzia deweloperskie i F12 dla przeglądarki Microsoft Edge.
    ::: moniker-end

    > [!NOTE]
    > Jeśli debuger nie zostanie dołączony i zostanie wyświetlony komunikat "nie można dołączyć do procesu. Operacja nie jest dozwolona w bieżącym stanie ", należy użyć Menedżera zadań, aby zamknąć wszystkie wystąpienia elementu Chrome przed uruchomieniem programu Chrome w trybie debugowania. Rozszerzenia programu Chrome mogą być uruchomione i uniemożliwiać tryb pełnego debugowania.

8. Jeśli kod z punktem przerwania został już wykonany, Odśwież stronę przeglądarki, aby trafić punkt przerwania.

    W debugerze można przeanalizować stan aplikacji, umieszczając kursor nad zmiennymi i korzystając z okien debugera. Debuger można uzyskać, przechodząc przez kod (**F5**, **F10**i **F11**).

    W przypadku zminimalizowanego lub z transstertą języka JavaScript można napotkać punkt przerwania w postaci kodu JavaScript lub jego zamapowanej lokalizacji w pliku TypeScript (przy użyciu map źródła), w zależności od środowiska i stanu przeglądarki. W obu przypadkach możesz przejść przez kod i przeanalizować zmienne.

    * Jeśli musisz przerwać kod w pliku TypeScript i nie można go wykonać, użyj **dołączenia do procesu** , jak opisano w poprzednich krokach, aby dołączyć debuger. Następnie otwórz dynamicznie wygenerowany plik TypeScript z Eksplorator rozwiązań, otwierając **dokumenty skryptu**  > **filename. TSX**, ustaw punkt przerwania i Odśwież stronę w przeglądarce (Ustaw punkt przerwania w wierszu kodu, który umożliwia używanie punktów przerwania, takie jak instrukcja `return` lub Deklaracja `var`).

        Alternatywnie, jeśli konieczne jest przerwanie w kodzie w pliku TypeScript i nie można tego zrobić, spróbuj użyć instrukcji `debugger;` w pliku TypeScript lub ustaw punkty przerwania w Narzędzia deweloperskie Chrome.

    * Jeśli trzeba podzielić na kod w przekształconym pliku JavaScript (na przykład *App-Bundle. js*) i nie można go wykonać, usuń plik mapy źródłowej o *nazwie filename. js. map*.

     > [!TIP]
     > Po dołączeniu do procesu po raz pierwszy, wykonując poniższe kroki, można szybko ponownie dołączyć do tego samego procesu, wybierając **debuguj**  > **ponownie dołączyć do procesu**.

## <a name="generate_sourcemaps"></a>Generuj mapy źródeł na potrzeby debugowania

Program Visual Studio oferuje możliwość używania i generowania map źródeł w plikach źródłowych JavaScript. Jest to często wymagane, jeśli źródło jest zminimalizowanego lub utworzone przez transstertę, taką jak TypeScript lub Babel. Dostępne opcje zależą od typu projektu.

* Projekt TypeScript w programie Visual Studio domyślnie generuje mapy źródłowe.

* W projekcie JavaScript musisz generować mapy źródłowe za pomocą pakietu, takiego jak WebPack, oraz kompilatora, takiego jak kompilator języka TypeScript (lub Babel), który można dodać do projektu. Dla kompilatora języka TypeScript należy również dodać plik *tsconfig. JSON* . Aby zapoznać się z przykładem, który pokazuje, jak to zrobić przy użyciu podstawowej konfiguracji pakietu WebPack, zobacz [Tworzenie aplikacji node. js z reagowaniem](../javascript/tutorial-nodejs-with-react-and-jsx.md).

> [!NOTE]
> Jeśli jesteś nowym mapowaniem źródeł, Przeczytaj [wprowadzenie do map źródłowych JavaScript](https://www.html5rocks.com/en/tutorials/developertools/sourcemaps/) przed kontynuowaniem.

Aby skonfigurować ustawienia zaawansowane dla map źródeł, Użyj ustawień *tsconfig. JSON* lub projektu w projekcie TypeScript, ale nie obu.

### <a name="configure-source-maps-using-a-tsconfigjson-file"></a>Skonfiguruj mapy źródłowe przy użyciu pliku tsconfig. JSON

Jeśli dodasz plik *tsconfig. JSON* do projektu, program Visual Studio traktuje katalog główny katalogu jako projekt TypeScript. Aby dodać plik, kliknij prawym przyciskiem myszy projekt w Eksplorator rozwiązań, a następnie wybierz polecenie **dodaj > nowy element > Web > skrypty > plik konfiguracji JSON języka TypeScript**. Plik *tsconfig. JSON* , podobny do następującego, zostanie dodany do projektu.

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

### <a name="configure-source-maps-using-project-settings"></a>Skonfiguruj mapy źródłowe przy użyciu ustawień projektu

Możesz również skonfigurować ustawienia mapy źródłowej przy użyciu właściwości projektu, klikając prawym przyciskiem myszy projekt, a następnie wybierając pozycję **project > właściwości > > kompilacji języka TypeScript**.

Te ustawienia projektu są dostępne.

* **Generuj mapy źródeł** (równoważne **mapy źródła** w *tsconfig. JSON*): generuje odpowiadający plik *. map* .
* **Określ katalog główny map źródeł** (odpowiednik **mapRoot** w *tsconfig. JSON*): określa lokalizację, w której debuger powinien znaleźć pliki map zamiast wygenerowanych lokalizacji. Tej flagi należy użyć, jeśli pliki *map* czasu wykonywania muszą znajdować się w innej lokalizacji niż pliki. js. Określona lokalizacja jest osadzona na mapie źródłowej, aby skierować debuger do miejsca, w którym znajdują się pliki mapy.
* **Określ katalog główny plików TypeScript** (odpowiednik **sourceRoot** w *tsconfig. JSON*): określa lokalizację, w której debuger powinien znaleźć pliki TypeScript zamiast lokalizacji źródłowych. Tej flagi należy użyć, jeśli pliki źródłowe czasu wykonywania muszą znajdować się w innej lokalizacji niż lokalizacja w czasie projektowania. Określona lokalizacja jest osadzona na mapie źródłowej, aby skierować debuger do miejsca, w którym znajdują się pliki źródłowe.

## <a name="debug-javascript-in-dynamic-files-using-razor-aspnet"></a>Debugowanie kodu JavaScript w plikach dynamicznych przy użyciu Razor (ASP.NET)

Program Visual Studio zapewnia obsługę debugowania tylko dla przeglądarki Chrome i programu Internet Explorer. Spowoduje to automatyczne dołączenie punktów przerwania do języka JavaScript/TypeScript i skryptów osadzonych w plikach HTML.

Debugowanie dynamicznie generowanych plików nie jest automatyczne. Nie można automatycznie trafiać punktów przerwania dla plików generowanych za pomocą składnia Razor (cshtml, VBHTML). Istnieją dwie metody, których można użyć do debugowania tego rodzaju pliku:

* **Umieść instrukcję `debugger;`, która ma zostać przerwana**: spowoduje to zatrzymanie wykonywania skryptu dynamicznego i natychmiastowe rozpoczęcie debugowania podczas jego tworzenia.
* **Załaduj stronę i Otwórz dokument dynamiczny w programie Visual Studio**: musisz otworzyć plik dynamiczny podczas debugowania, ustawić punkt przerwania i odświeżyć stronę, aby ta metoda działała. W zależności od tego, czy korzystasz z przeglądarki Chrome, czy programu Internet Explorer, możesz znaleźć plik przy użyciu jednej z następujących strategii:

   Dla programu Chrome przejdź do **Eksplorator rozwiązań > dokumenty skryptu > YourPageName**.

    > [!NOTE]
    > W przypadku korzystania z programu Chrome może zostać wyświetlony komunikat nie można uzyskać **dostępu do tagów > \<script**. To OK, po prostu Kontynuuj debugowanie.

   W przypadku programu Internet Explorer przejdź do **Eksplorator rozwiązań > dokumenty skryptu > Windows Internet Explorer > YourPageName**.

Aby uzyskać więcej informacji, zobacz [debugowanie po stronie klienta projektów ASP.NET w przeglądarce Google Chrome](https://devblogs.microsoft.com/aspnet/client-side-debugging-of-asp-net-projects-in-google-chrome/).