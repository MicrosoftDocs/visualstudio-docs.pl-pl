---
ms.date: 05/28/2021
ms.technology: vs-ide-general
ms.custom: vs-get-started
ms.author: tglee
author: TerryGLee
manager: jmartens
ms.topic: include
ms.openlocfilehash: 128a09500aaa326fad717efcade9040496452963
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/17/2021
ms.locfileid: "112362502"
---
Zintegrowane Visual Studio *deweloperska* to kreatywna wersja, która umożliwia edytowanie, debugowanie i kompilowanie kodu, a następnie publikowanie aplikacji. Zintegrowane środowisko projektowe (IDE) to bogaty w funkcje program, który może być używany w wielu aspektach tworzenia oprogramowania. Ponad standardowym edytorem i debugerem zapewnianym przez większość interfejsów VISUAL STUDIO są kompilatory, narzędzia do uzupełniania kodu, projektanci graficzni i wiele innych funkcji, które ułatwiają proces tworzenia oprogramowania.

::: moniker range="vs-2017"

![The Visual Studio 2017 IDE](../media/visual-studio-ide.png)

::: moniker-end

::: moniker range=">=vs-2019"

:::image type="content" source="../media/vs-2019/ide-overview.png" alt-text="Zrzut ekranu przedstawiający Visual Studio IDE, który zawiera objaśnienia wskazujące, gdzie znajdują się kluczowe funkcje i funkcje." lightbox="../media/vs-2019/ide-overview.png":::

::: moniker-end

Ten obraz Visual Studio z otwartym projektem i kilkoma kluczowymi oknami narzędzi, których prawdopodobnie będziesz używać:

- [Eksplorator rozwiązań](../../ide/solutions-and-projects-in-visual-studio.md) (w prawym górnym rogu) umożliwia wyświetlanie i nawigowanie po plikach kodu oraz zarządzanie nimi. **Eksplorator rozwiązań** może pomóc w organizowaniu kodu przez grupowanie plików w [rozwiązania i projekty.](../tutorial-projects-solutions.md)

- W [oknie edytora](../../ide/writing-code-in-the-code-and-text-editor.md) (w środku), w którym prawdopodobnie będziesz spędzać większość czasu, jest wyświetlana zawartość pliku. W tym miejscu można edytować kod lub zaprojektować interfejs użytkownika, taki jak okno z przyciskami i polami tekstowymi.

::: moniker range="vs-2017"

- Okno [Dane wyjściowe](../../ide/reference/output-window.md) (dolne centrum) to miejsce, w którym Visual Studio powiadomienia, takie jak debugowanie i komunikaty o błędach, ostrzeżenia kompilatora, publikowanie komunikatów o stanie i nie tylko. Każde źródło komunikatu ma własną kartę.

::: moniker-end

- [Usługa Git Changes](/visualstudio/version-control/) (w prawym dolnym rogu) umożliwia śledzenie elementów roboczych i udostępnianie kodu innym osobom przy użyciu technologii kontroli wersji, takich jak [Git](https://git-scm.com/) i [GitHub.](https://docs.github.com/github)

## <a name="editions"></a>Wersje

::: moniker range="vs-2017"

Visual Studio jest dostępna dla systemów Windows i Mac. [Visual Studio dla komputerów Mac](/visualstudio/mac/) ma wiele takich samych funkcji jak Visual Studio 2017 i jest zoptymalizowany pod kątem tworzenia aplikacji międzyplatformowych i mobilnych. Ten artykuł koncentruje się na wersji systemu Windows Visual Studio 2017.

Dostępne są trzy wersje Visual Studio: Community, Professional i Enterprise. Zobacz [Porównanie Visual Studio,](https://visualstudio.microsoft.com/vs/compare/) aby dowiedzieć się, które funkcje są obsługiwane w poszczególnych wersjach.

::: moniker-end

::: moniker range=">=vs-2019"

Visual Studio jest dostępna dla systemów Windows i Mac. [Visual Studio dla komputerów Mac](/visualstudio/mac/) ma wiele takich samych funkcji jak Visual Studio 2019 i jest zoptymalizowany pod kątem tworzenia aplikacji międzyplatformowych i mobilnych. Ten artykuł koncentruje się na wersji systemu Windows Visual Studio 2019.

Istnieją trzy wersje programu Visual Studio 2019: Community, Professional i Enterprise. Zobacz [Porównanie Visual Studio,](https://visualstudio.microsoft.com/vs/compare/) aby dowiedzieć się, które funkcje są obsługiwane w poszczególnych wersjach.

::: moniker-end

## <a name="popular-productivity-features"></a>Popularne funkcje zwiększające produktywność

Niektóre z popularnych funkcji w Visual Studio, które pomagają wydajniej tworzyć oprogramowanie, obejmują:

- Zygki i [szybkie akcje](../../ide/quick-actions.md)

   Zygzyki są falistymi podkreśleniami, które ostrzegają o błędach lub potencjalnych problemach w kodzie podczas wpisywania. Te wizualne wskazówki umożliwiają natychmiastowe rozwiązywanie problemów bez oczekiwania na wykryte błędy podczas kompilacji lub podczas uruchamiania programu. Jeśli najedziesz kursorem na zygki, zobaczysz dodatkowe informacje o błędzie. Żarówka może również pojawić się na lewym marginesie z akcjami, nazywanymi szybkimi akcjami, aby naprawić błąd.

   ![Zygniaki w Visual Studio](../media/squiggles-error.png)

::: moniker range=">=vs-2019"

- Oczyszczanie kodu

   Po kliknięciu przycisku sformatuj kod i zastosuj wszelkie poprawki kodu sugerowane przez ustawienia stylu [kodu,](../../ide/reference/options-text-editor-csharp-formatting.md)konwencje [editorconfig](../../ide/create-portable-custom-editor-options.md)i [analizatory Roslyn.](../../code-quality/roslyn-analyzers-overview.md) **Oczyszczanie kodu** pomaga w rozwiązywaniu problemów z kodem, zanim przejdzie on do przeglądu kodu. (Obecnie dostępne tylko dla kodu C#).

   ![Przycisk Oczyszczanie kodu w Visual Studio](../media/vs-2019/code-cleanup.png)

::: moniker-end

- [Refaktoryzacja](../../ide/refactoring-in-visual-studio.md)

   Refaktoryzacja obejmuje operacje, takie jak inteligentna zmiana nazw zmiennych, wyodrębnianie co najmniej jednego wiersza kodu do nowej metody, zmienianie kolejności parametrów metody i nie tylko.

   ![Refaktoryzacja w programie Visual Studio](../media/refactoring-menu.png)

- [Intellisense](../../ide/using-intellisense.md)

   IntelliSense to termin dla zestawu funkcji, które wyświetla informacje o kodzie bezpośrednio w edytorze i, w niektórych przypadkach, piszą za Ciebie małe części kodu. Przypomina to podstawową dokumentację w tekście w edytorze, dzięki której nie trzeba szukać informacji o typie w innym miejscu. Funkcje IntelliSense różnią się w zależności od języka. Aby uzyskać więcej informacji, zobacz [C# IntelliSense,](../../ide/visual-csharp-intellisense.md) [Visual C++ IntelliSense,](../../ide/visual-cpp-intellisense.md) [JavaScript IntelliSense](../../ide/javascript-intellisense.md)i [Visual Basic IntelliSense.](../../ide/visual-basic-specific-intellisense.md) Na poniższej ilustracji przedstawiono sposób, w jaki funkcja IntelliSense wyświetla listę elementów członkowskich dla typu:

   ![Visual Studio członkowskie](../media/intellisense-list-members.png)

- [Visual Studio wyszukiwania](../../ide/visual-studio-search.md)

   Visual Studio czasami może wydawać się przytłaczające przy użyciu tak wielu menu, opcji i właściwości. Visual Studio wyszukiwania **(Ctrl** Q ) to doskonały sposób szybkiego wyszukiwania funkcji i kodu + środowiska IDE w jednym miejscu.

   ::: moniker range="vs-2017"

   ![Szybkie uruchamianie wyszukiwania w programie Visual Studio 2017](../media/quick-launch-nuget.png)

   Aby uzyskać więcej informacji, [zobacz Szybkie uruchamianie](../../ide/reference/quick-launch-environment-options-dialog-box.md).

   ::: moniker-end

   ::: moniker range="vs-2019"

   ![Pole wyszukiwania w Visual Studio 2019 r.](../media/vs-2019/quick-launch-nuget.png)

    Aby uzyskać informacje i porady dotyczące produktywności, [zobacz Jak używać Visual Studio wyszukiwania](../../ide/visual-studio-search.md).

   ::: moniker-end

- [Live Share](/visualstudio/liveshare/)

   Wspólne edytowanie i debugowanie z innymi osobami w czasie rzeczywistym, niezależnie od typu aplikacji lub języka programowania. Możesz natychmiast i bezpiecznie udostępniać projekt oraz, w razie potrzeby, debugowanie sesji, wystąpień terminali, aplikacji internetowych hosta lokalnego, połączeń głosowych i nie tylko.

- [Hierarchia wywołań](../../ide/reference/call-hierarchy.md)

   Okno **Hierarchia** wywołań zawiera metody, które wywołują wybraną metodę. Mogą to być przydatne informacje, gdy myślisz o zmianie lub usunięciu metody albo gdy próbujesz śledzić usterkę.

   ![Okno Hierarchia wywołań](../../ide/reference/media/call-hierarchy-csharp-expanded.png)

- [CodeLens](../../ide/find-code-changes-and-other-history-with-codelens.md)

   CodeLens ułatwia znajdowanie odwołań do kodu, zmian w kodzie, połączonych usterek, elementów roboczych, przeglądów kodu i testów jednostkowych bez opuszczania edytora.

   ![CodeLens](../media/codelens-overview.png)

- [Przejdź do definicji](../../ide/go-to-and-peek-definition.md)

   Funkcja Przejdź do definicji pozwala przejść bezpośrednio do lokalizacji, w której zdefiniowano funkcję lub typ.

   ![Przejdź do definicji](../media/go-to-definition-menu.png)

- [Podejrzyj definicję](../../ide/how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12.md)

   W **oknie Podgląd definicji** jest przedstawiana definicja metody lub typu bez konieczności otwierania oddzielnego pliku.

   ![Wgląd w definicję](../media/peek-definition.png)

## <a name="install-the-visual-studio-ide"></a>Instalowanie środowiska IDE Visual Studio

W tej sekcji utworzysz prosty projekt, aby wypróbować niektóre czynności, które można wykonać za pomocą Visual Studio. Użyjesz funkcji [IntelliSense](../../ide/using-intellisense.md) jako pomocy w kodowaniu, debuguj aplikację, aby zobaczyć wartość zmiennej podczas wykonywania programu, i zmienisz motyw kolorów.

::: moniker range="vs-2017"

Aby rozpocząć, [pobierz Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) i zainstaluj go w systemie. Instalator modułowy umożliwia wybieranie i instalowanie obciążeń *,* które są grupami funkcji wymaganymi dla preferowanego języka lub platformy programowania. Aby wykonać kroki tworzenia [programu](#create-a-program), pamiętaj, aby podczas instalacji wybrać międzyplatformowe obciążenie tworzenia aplikacji na platformie **.NET Core.**

::: moniker-end

::: moniker range=">=vs-2019"

Aby rozpocząć, [pobierz Visual Studio](https://visualstudio.microsoft.com/downloads) i zainstaluj go w systemie. Instalator modułowy umożliwia wybieranie i instalowanie obciążeń *,* które są grupami funkcji wymaganymi dla preferowanego języka lub platformy programowania. Aby wykonać kroki tworzenia [programu](#create-a-program), pamiętaj, aby podczas instalacji wybrać międzyplatformowe obciążenie tworzenia aplikacji na platformie **.NET Core.**

::: moniker-end

![Międzyplatformowe obciążenie programowe platformy .NET Core w Instalator programu Visual Studio](../media/dotnet-core-cross-platform-workload.png)

Po pierwszym otwarciu Visual Studio możesz opcjonalnie zalogować się przy użyciu konta konto Microsoft lub konta służbowego. [](../../ide/signing-in-to-visual-studio.md)

## <a name="create-a-program"></a>Tworzenie programu

Przyjrzyjmy się temu i utwórzmy prosty program.

::: moniker range="vs-2017"

1. Otwórz program Visual Studio.

1. Na pasku menu wybierz pozycję **File** New Project > **(Plik nowy** > **projekt).**

   ![Plik > nowy projekt na pasku menu](../media/file-new-project-menu.png)

   W **oknie dialogowym** Nowy projekt jest wyświetlane kilka szablonów *projektów.* Szablon zawiera podstawowe pliki i ustawienia wymagane dla danego typu projektu.

1. Wybierz **kategorię szablonów .NET Core** w obszarze **Visual C#,** a następnie wybierz szablon **Aplikacja konsolowa (.NET Core).** W polu **tekstowym** Nazwa wpisz **HelloWorld,** a następnie wybierz **przycisk OK.**

   ![Szablon aplikacji .NET Core](../media/overview-new-project-dialog.png)

   > [!NOTE]
   > Jeśli nie widzisz kategorii **.NET Core,** musisz zainstalować międzyplatformowe obciążenie **programowe .NET Core.** W tym celu wybierz link **Otwórz Instalator programu Visual Studio** w lewym dolnym rogu okna **dialogowego Nowy** projekt. Po Instalator programu Visual Studio przewiń w dół i wybierz obciążenie Tworzenie aplikacji dla wielu platform na platformie **.NET Core,** a następnie wybierz pozycję **Modyfikuj.**

   Visual Studio tworzy projekt. Jest to prosta aplikacja "Hello world", która wywołuje metodę w celu wyświetlenia <xref:System.Console.WriteLine?displayProperty=nameWithType> ciągu literału "Hello world!" w oknie konsoli (dane wyjściowe programu).

   Wkrótce powinien zostać wyświetlony kod podobny do następującego:

   ![Visual Studio IDE](../media/overview-ide-console-app.png)

   Kod języka C# dla aplikacji jest wyświetlany w oknie edytora, które zajmuje większość miejsca. Zwróć uwagę, że tekst jest automatycznie kolorowany w celu wskazania różnych części kodu, takich jak słowa kluczowe i typy. Ponadto małe, pionowe linie kreskowane w kodzie wskazują, które nawiasy klamrowe są ze sobą zgodne, a numery wierszy ułatwiają późniejsze lokalizowanie kodu. Aby zwinąć lub rozwinąć bloki kodu, możesz wybrać małe, zwinięte i zwinięte znaki minus. Ta funkcja wyekscyplinowania kodu pozwala ukryć kod, który nie jest potrzebny, co pomaga zminimalizować nieład wyświetlany na ekranie. Pliki projektu są wyświetlane po prawej stronie okna o nazwie **Eksplorator rozwiązań**.

   ![Visual Studio IDE z czerwonymi polami](../media/overview-ide-console-app-red-boxes.png)

   Dostępne są inne menu i okna narzędzi, ale na razie przejdźmy dalej.

1. Teraz uruchom aplikację. Możesz to zrobić, wybierając pozycję **Uruchom bez** debugowania z menu **Debugowanie** na pasku menu. Możesz również nacisnąć klawisz **Ctrl** + **F5.**

   ![Debugowanie > start bez menu debugowania](../media/overview-start-without-debugging.png)

   Visual Studio aplikację, a zostanie otwarte okno konsoli z komunikatem **Hello world!**. Masz teraz uruchamianą aplikację.

   ![Zrzut ekranu przedstawiający cmd.exe konsoli z danych wyjściowych "Hello Word!". i "Naciśnij dowolny klawisz, aby kontynuować".](../media/overview-console-window.png)

1. Aby zamknąć okno konsoli, naciśnij dowolny klawisz na klawiaturze.

1. Dodajmy dodatkowy kod do aplikacji. Dodaj następujący kod C# przed wierszem o treści `Console.WriteLine("Hello World!");` :

   ```csharp
   Console.WriteLine("\nWhat is your name?");
   var name = Console.ReadLine();
   ```

   Ten kod wyświetla wartość What is your name? (Jaka jest Twoja **nazwa?)** w oknie konsoli, a następnie czeka, aż użytkownik wprowadzi jakiś tekst, a następnie klawisz **Enter.**

1. Zmień wiersz polecenia na `Console.WriteLine("Hello World!");` następujący kod:

   ```csharp
   Console.WriteLine($"\nHello {name}!");
   ```

1. Uruchom aplikację ponownie, wybierając pozycję **Rozpocznij** > **debugowanie bez** debugowania lub naciskając **klawisz Ctrl** + **F5.**

   Visual Studio aplikacja zostanie ponownie skompilowana, a zostanie otwarte okno konsoli z monitem o twoją nazwę.

1. Wprowadź swoją nazwę w oknie konsoli i naciśnij klawisz **Enter**.

   ![Dane wejściowe okna konsoli](../media/overview-console-input.png)

1. Naciśnij dowolny klawisz, aby zamknąć okno konsoli i zatrzymać uruchomiony program.

::: moniker-end

::: moniker range=">=vs-2019"

1. Otwórz program Visual Studio.

   Zostanie wyświetlone okno uruchamiania z różnymi opcjami klonowania repo, otwierania ostatniego projektu lub tworzenia zupełnie nowego projektu.

1. Wybierz **pozycję Utwórz nowy projekt.**

    :::image type="content" source="../media/vs-2019/start-window-create-new-project.png" alt-text="Zrzut ekranu przedstawiający okno &quot;Tworzenie nowego projektu&quot; w Visual Studio 2019 r.":::

   Zostanie **otwarte okno Tworzenie nowego** projektu z kilkoma *szablonami projektów.* Szablon zawiera podstawowe pliki i ustawienia wymagane dla danego typu projektu.

1. Aby znaleźć szablon, którego potrzebujemy, wpisz lub wprowadź **konsolę .net core** w polu wyszukiwania. Lista dostępnych szablonów jest automatycznie filtrowana na podstawie wprowadzonych słów kluczowych. Wyniki szablonu można dodatkowo filtrować, wybierając  język **C#** z listy rozwijanej Wszystkie  języki, system **Windows** z listy **Wszystkie** platformy i konsolę z listy **Wszystkie typy projektów.**

    Wybierz szablon **Aplikacja konsolowa,** a następnie kliknij przycisk **Dalej.**

    :::image type="content" source="../media/vs-2019/create-new-project.png" alt-text="Zrzut ekranu przedstawiający okno &quot;Tworzenie nowego projektu&quot; w programie Visual Studio 2019, w którym wybierasz szablon.":::

1. W **oknie** Konfigurowanie nowego projektu wprowadź **helloworld** w polu **Nazwa** projektu, opcjonalnie zmień lokalizację katalogu dla plików projektu (domyślne ustawienia lokalne to ), a `C:\Users\<name>\source\repos` następnie kliknij przycisk **Dalej.**

    :::image type="content" source="../media/vs-2019/configure-new-project.png" alt-text="Zrzut ekranu przedstawiający okno &quot;Konfigurowanie nowego projektu&quot; w Visual Studio 2019 r., w którym wprowadzasz nazwę projektu.":::

1. W **oknie Dodatkowe informacje** sprawdź, czy program **.NET Core 3.1** jest wyświetlany w menu rozwijanych **Target Framework,** a następnie kliknij pozycję **Utwórz.**

    :::image type="content" source="../media/vs-2019/create-project-additional-info.png" alt-text="Zrzut ekranu przedstawiający okno &quot;Dodatkowe informacje&quot; w programie Visual Studio 2019, w którym wybierasz wersję programu .NET Core Framework.":::

   Visual Studio tworzy projekt. Jest to prosta aplikacja "Hello world", która wywołuje metodę w celu wyświetlenia <xref:System.Console.WriteLine?displayProperty=nameWithType> ciągu literału "Hello world!" w oknie konsoli (dane wyjściowe programu).

   Wkrótce powinien zostać wyświetlony kod podobny do następującego:

   ![Visual Studio IDE](../media/vs-2019/overview-ide-console-app.png)

   Kod języka C# dla aplikacji jest wyświetlany w oknie edytora, które zajmuje większość miejsca. Zwróć uwagę, że tekst jest automatycznie kolorowany w celu wskazania różnych części kodu, takich jak słowa kluczowe i typy. Ponadto małe, pionowe linie kreskowane w kodzie wskazują, które nawiasy klamrowe są ze sobą zgodne, a numery wierszy ułatwiają późniejsze lokalizowanie kodu. Aby zwinąć lub rozwinąć bloki kodu, możesz wybrać małe, zwinięte i zwinięte znaki minus. Ta funkcja wyekscyplinowania kodu pozwala ukryć kod, który nie jest potrzebny, co pomaga zminimalizować nieład wyświetlany na ekranie. Pliki projektu są wyświetlane po prawej stronie okna o nazwie **Eksplorator rozwiązań**.

   ![Visual Studio IDE z czerwonymi polami](../media/vs-2019/overview-ide-console-app-red-boxes.png)

   Dostępne są inne menu i okna narzędzi, ale na razie przejdźmy dalej.

1. Teraz uruchom aplikację. Możesz to zrobić, wybierając pozycję **Uruchom bez** debugowania z menu **Debugowanie** na pasku menu. Możesz również nacisnąć klawisz **Ctrl** + **F5.**

   ![Debugowanie > start bez menu debugowania](../media/overview-start-without-debugging.png)

   Visual Studio aplikację, a zostanie otwarte okno konsoli z komunikatem **Hello world!**. Masz teraz uruchamianą aplikację.

   ![Zrzut ekranu przedstawiający Microsoft Visual Studio konsoli debugowania z danych wyjściowych "Hello Word!". i "Naciśnij dowolny klawisz, aby zamknąć to okno".](../media/vs-2019/overview-console-window.png)

1. Aby zamknąć okno konsoli, naciśnij dowolny klawisz na klawiaturze.

1. Dodajmy dodatkowy kod do aplikacji. Dodaj następujący kod C# przed wierszem o treści `Console.WriteLine("Hello World!");` :

   ```csharp
   Console.WriteLine("\nWhat is your name?");
   var name = Console.ReadLine();
   ```

   Ten kod wyświetla wartość What is your name? (Jaka jest Twoja **nazwa?)** w oknie konsoli, a następnie czeka, aż użytkownik wprowadzi jakiś tekst, a następnie klawisz **Enter.**

1. Zmień wiersz polecenia na `Console.WriteLine("Hello World!");` następujący kod:

   ```csharp
   Console.WriteLine($"\nHello {name}!");
   ```

1. Uruchom aplikację ponownie, wybierając pozycję **Rozpocznij** > **debugowanie bez** debugowania lub naciskając **klawisz Ctrl** + **F5.**

   Visual Studio aplikacja zostanie ponownie skompilowana, a zostanie otwarte okno konsoli z monitem o twoją nazwę.

1. Wprowadź swoją nazwę w oknie konsoli i naciśnij klawisz **Enter**.

   ![Zrzut ekranu Microsoft Visual Studio konsoli debugowania przedstawiający monit o nazwę, dane wejściowe i dane wyjściowe "HelloTte!".](../media/vs-2019/overview-console-input.png)

1. Naciśnij dowolny klawisz, aby zamknąć okno konsoli i zatrzymać uruchomiony program.

::: moniker-end

## <a name="use-refactoring-and-intellisense"></a>Korzystanie z refaktoryzacji i funkcji IntelliSense

Przyjrzyjmy się kilku sposobom [](../../ide/refactoring-in-visual-studio.md) refaktoryzacji i funkcji [IntelliSense,](../../ide/using-intellisense.md) które mogą pomóc w wydajniejszym kodowanie.

Najpierw zmieńmy nazwę `name` zmiennej:

1. Kliknij dwukrotnie `name` zmienną, aby ją wybrać.

2. Wpisz nową nazwę zmiennej, **username**.

   Zwróć uwagę, że wokół zmiennej pojawia się szare pole, a na marginesie pojawi się żarówka.

::: moniker range="vs-2017"

3. Wybierz ikonę żarówki, aby wyświetlić dostępne [szybkie akcje](../../ide/quick-actions.md). Wybierz **pozycję Zmień nazwę "name" na "username".**

   ![Zmienianie nazwy akcji w Visual Studio](../media/rename-quick-action.png)

   Nazwa zmiennej jest zmieniana w całym projekcie, co w naszym przypadku jest tylko dwoma miejscami.

   ![Animowany plik GIF przedstawiający refaktoryzowanie zmiany nazwy w Visual Studio](../media/rename-refactoring.gif)

::: moniker-end

::: moniker range=">=vs-2019"

3. Wybierz ikonę żarówki, aby wyświetlić dostępne [szybkie akcje](../../ide/quick-actions.md). Wybierz **pozycję Zmień nazwę "name" na "username".**

   ![Zmienianie nazwy akcji w Visual Studio](../media/vs-2019/rename-quick-action.png)

   Nazwa zmiennej jest zmieniana w całym projekcie, co w naszym przypadku jest tylko dwoma miejscami.

::: moniker-end

4. Teraz przyjrzyjmy się funkcji IntelliSense. Pod wierszem , który mówi `Console.WriteLine($"\nHello {username}!");` , wpisz `DateTime now = DateTime.` .

   Pole wyświetla składowe <xref:System.DateTime> klasy. Ponadto opis aktualnie wybranego członka jest wyświetlany w osobnym polu.

   ![Elementy członkowskie listy funkcji IntelliSense w Visual Studio](../media/intellisense-list-members.png)

5. Wybierz członka o nazwie **Now**, który jest właściwością klasy, klikając ją dwukrotnie lub naciskając klawisz **Tab**. Ukończ wiersz kodu, dodając średnik na końcu.

6. Poniżej wpisz lub wklej następujące wiersze kodu:

   ```csharp
   int dayOfYear = now.DayOfYear;

   Console.Write("Day of year: ");
   Console.WriteLine(dayOfYear);
   ```

   > [!TIP]
   > <xref:System.Console.Write%2A?displayProperty=nameWithType> jest nieco inny niż w tym, że nie dodaje <xref:System.Console.WriteLine%2A?displayProperty=nameWithType> terminatora wiersza po wydrukowaniu. Oznacza to, że następny fragment tekstu, który jest wysyłany do danych wyjściowych, zostanie wydrukowany w tym samym wierszu. Możesz zatrzymać wskaźnik myszy na każdej z tych metod w kodzie, aby wyświetlić ich opis.

7. Następnie ponownie użyjemy refaktoryzacji, aby kod był nieco bardziej zwięzły. Kliknij zmienną `now` w wierszu `DateTime now = DateTime.Now;` .

   Zwróć uwagę, że na marginesie w tym wierszu pojawia się mała ikona śrubokręta.

8. Kliknij ikonę śrubokręta, aby zobaczyć, jakie sugestie Visual Studio dostępne. W tym przypadku pokazuje refaktoryzowanie zmiennej tymczasowej w tekście w celu usunięcia wiersza kodu bez zmiany ogólnego zachowania kodu: [](../../ide/reference/inline-temporary-variable.md)

   ![Refaktoryzacja wbudowanej zmiennej tymczasowej w Visual Studio](../media/inline-temporary-variable-refactoring.png)

9. Kliknij **pozycję Inline temporary variable (W** tekście zmiennej tymczasowej), aby refaktoryzować kod.

::: moniker range="vs-2017"

10. Uruchom ponownie program, naciskając **klawisz Ctrl** + **F5.** Dane wyjściowe wyglądają następująco:

    ! Zrzut ekranu przedstawiający cmd.exe konsoli z monitem o nazwę, dane wejściowe i dane wyjściowe "HelloTte! Dzień roku: 151".] (.. /media/overview-console-final.png)

::: moniker-end

::: moniker range=">=vs-2019"

10. Uruchom ponownie program, naciskając **klawisz Ctrl** + **F5.** Dane wyjściowe wyglądają następująco:

    ![Zrzut ekranu przedstawiający Microsoft Visual Studio konsoli debugowania z wyświetlonym monitem o nazwę, dane wejściowe i dane wyjściowe "HelloTte! Dzień roku: 43".](../media/vs-2019/overview-console-final.png)

::: moniker-end

## <a name="debug-code&quot;></a>Debugowanie kodu

Podczas pisania kodu należy go uruchomić i przetestować pod względu na błędy. Visual Studio debugowania pozwala przechodzić przez kod po jednej instrukcji na raz i sprawdzać zmienne w kolejnych krokach. Punkty *przerwania, które zatrzymają* wykonywanie kodu, można ustawić w określonym wierszu. Możesz obserwować, jak wartość zmiennej zmienia się podczas pracy kodu i nie tylko.

Ustawmy punkt przerwania, aby zobaczyć wartość zmiennej, gdy `username` program jest &quot;w locie&quot;.

1. Znajdź wiersz kodu z kodem `Console.WriteLine($&quot;\nHello {username}!");` . Aby ustawić punkt przerwania w tym wierszu kodu, czyli aby program wstrzymał wykonywanie w tym wierszu, kliknij lewy margines edytora. Możesz również kliknąć dowolne miejsce w wierszu kodu, a następnie nacisnąć **klawisz F9**.

   Na lewym marginesie pojawi się czerwone kółko, a kod zostanie wyróżniony na czerwono.

   ![Punkt przerwania w wierszu kodu w Visual Studio](../media/breakpoint.png)

1. Rozpocznij debugowanie, wybierając pozycję   >  **Debuguj rozpocznij debugowanie** lub naciskając **klawisz F5.**

1. Gdy zostanie wyświetlone okno konsoli z pytaniem o Twoją nazwę, wpisz je i naciśnij klawisz **Enter**.

   Fokus powraca do Visual Studio kodu, a wiersz kodu z punktem przerwania jest wyróżniony kolorem żółtym. Oznacza to, że jest to następny wiersz kodu, który zostanie wykonany przez program.

1. Umieść wskaźnik myszy na `username` zmiennej, aby wyświetlić jej wartość. Alternatywnie możesz kliknąć prawym przyciskiem myszy i wybrać pozycję Dodaj czujkę, aby dodać zmienną do okna Czujka, w którym `username` można również zobaczyć jej wartość.  

   ![Wartość zmiennej podczas debugowania w Visual Studio](../media/debugging-variable-value.png)

1. Aby pozwolić programowi na ukończenie, naciśnij **ponownie klawisz F5.**

Aby uzyskać więcej szczegółów na temat debugowania w Visual Studio, zobacz [Debugger feature tour (Przewodnik po funkcji debugera).](../../debugger/debugger-feature-tour.md)

## <a name="customize-visual-studio"></a>Dostosowywanie Visual Studio

Możesz spersonalizować Visual Studio interfejsu użytkownika, w tym zmienić domyślny motyw kolorów. Aby zmienić motyw **na ciemny:**

1. Na pasku menu wybierz pozycję **Opcje**  >  **narzędzi,** aby otworzyć **okno dialogowe** Opcje.

::: moniker range="vs-2017"

2. Na stronie **Opcje** ogólne środowiska zmień wybór opcji >  **Motyw kolorów** na **Ciemny,** a następnie wybierz przycisk **OK.**

   Motyw kolorów dla całego środowiska IDE zmieni się na **Ciemny.**

   ![Visual Studio w motywie ciemnym](../media/dark-theme.png)

::: moniker-end

::: moniker range=">=vs-2019"

2. Na stronie **Opcje** ogólne środowiska zmień wybór opcji >  **Motyw kolorów** na **Ciemny,** a następnie wybierz przycisk **OK.**

   Motyw kolorów dla całego środowiska IDE zmieni się na **Ciemny.**

   ![Visual Studio w motywie ciemnym](../media/vs-2019/dark-theme.png)

::: moniker-end

Aby dowiedzieć się więcej o innych sposobach personalizowania środowiska IDE, zobacz [Personalizuj Visual Studio](../../ide/personalizing-the-visual-studio-ide.md).