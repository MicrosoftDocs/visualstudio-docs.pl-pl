---
title: Omówienie dla Visual Basic deweloperów
description: Dowiedz się więcej o Visual Studio do edytowania, debugowania i kompilowania kodu, a następnie publikowania aplikacji jako Visual Basic dewelopera.
ms.date: 03/02/2021
ms.technology: vs-ide-general
ms.custom:
- vs-acquisition
- get-started
- SEO-VS-2020
ms.topic: conceptual
author: TerryGLee
ms.author: tglee
manager: jmartens
dev_langs:
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 486201d61f6bd2d149c9aea66efee1814ce667e7
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112386634"
---
# <a name="welcome-to-the-visual-studio-ide--visual-basic"></a>Witamy w Visual Studio IDE | Visual Basic

Zintegrowane Visual Studio *deweloperska* to kreatywna wersja, która umożliwia edytowanie, debugowanie i kompilowanie kodu, a następnie publikowanie aplikacji. Zintegrowane środowisko projektowe (IDE) to bogaty w funkcje program, który może być używany w wielu aspektach tworzenia oprogramowania. Ponad standardowym edytorem i debugerem zapewnianym przez większość interfejsów VISUAL STUDIO są kompilatory, narzędzia do uzupełniania kodu, projektanci graficzni i wiele innych funkcji, które ułatwiają proces tworzenia oprogramowania.

::: moniker range="vs-2017"

![W Visual Studio IDE](../media/visual-studio-ide.png)

::: moniker-end

::: moniker range=">=vs-2019"

[![The Visual Studio 2019 IDE](media/vs-2019/ide-overview.png)](media/vs-2019/ide-overview.png#lightbox)

::: moniker-end

Ten obraz Visual Studio z otwartym projektem i kilkoma kluczowymi oknami narzędzi, których prawdopodobnie będziesz używać:

- [Eksplorator rozwiązań](../../ide/solutions-and-projects-in-visual-studio.md) (w prawym górnym rogu) umożliwia wyświetlanie i nawigowanie po plikach kodu oraz zarządzanie nimi. **Eksplorator rozwiązań** może pomóc w organizowaniu kodu przez grupowanie plików w [rozwiązania i projekty.](tutorial-projects-solutions.md)

- W [oknie edytora](../../ide/writing-code-in-the-code-and-text-editor.md) (w środku), w którym prawdopodobnie będziesz spędzać większość czasu, jest wyświetlana zawartość pliku. W tym miejscu można edytować kod lub zaprojektować interfejs użytkownika, taki jak okno z przyciskami i polami tekstowymi.

- Okno [Dane wyjściowe](../../ide/reference/output-window.md) (dolne centrum) to miejsce, w którym Visual Studio powiadomienia, takie jak debugowanie i komunikaty o błędach, ostrzeżenia kompilatora, publikowanie komunikatów o stanie i nie tylko. Każde źródło komunikatu ma własną kartę.

- [Team Explorer](/azure/devops/user-guide/work-team-explorer?view=vsts&preserve-view=true) (w prawym dolnym rogu) umożliwia śledzenie elementów roboczych i udostępnianie kodu innym osobom przy użyciu technologii kontroli wersji, takich jak [Git](https://git-scm.com/) [i Kontrola wersji serwera Team Foundation (TFVC).](/azure/devops/repos/tfvc/overview?view=vsts&preserve-view=true)

## <a name="editions"></a>Wersje

Visual Studio jest dostępna dla systemów Windows i Mac. [Visual Studio dla komputerów Mac](/visualstudio/mac/) ma wiele takich samych funkcji jak Visual Studio 2017 i jest zoptymalizowany pod kątem tworzenia aplikacji międzyplatformowych i mobilnych. Ten artykuł koncentruje się na wersji systemu Windows Visual Studio 2017.

Istnieją trzy wersje programu Visual Studio 2017: Community, Professional i Enterprise. Zobacz [Porównanie Visual Studio 2017,](https://visualstudio.microsoft.com/vs/compare/) aby dowiedzieć się, które funkcje są obsługiwane w poszczególnych wersjach.

## <a name="popular-productivity-features"></a>Popularne funkcje zwiększające produktywność

Niektóre z popularnych funkcji w Visual Studio, które pomagają wydajniej tworzyć oprogramowanie, obejmują:

- Zygki i [szybkie akcje](../../ide/quick-actions.md)

   Zygzyki są falistymi podkreśleniami, które ostrzegają o błędach lub potencjalnych problemach w kodzie podczas wpisywania. Te wizualne wskazówki umożliwiają natychmiastowe rozwiązywanie problemów bez oczekiwania na wykryte błędy podczas kompilacji lub podczas uruchamiania programu. Jeśli najedziesz kursorem na zygki, zobaczysz dodatkowe informacje o błędzie. Żarówka może również pojawić się na lewym marginesie z akcjami, nazywanymi szybkimi akcjami, aby naprawić błąd.

   ::: moniker range="vs-2017"

   ![Zygniaki w Visual Studio](media/squiggles-error.png)

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   ![Zygniaki w Visual Studio](media/vs-2019/squiggles-error.png)

   ::: moniker-end

- [Refaktoryzacja](../../ide/refactoring-in-visual-studio.md)

   Refaktoryzacja obejmuje operacje, takie jak inteligentna zmiana nazw zmiennych, wyodrębnianie co najmniej jednego wiersza kodu do nowej metody, zmienianie kolejności parametrów metody i nie tylko.

   ::: moniker range="vs-2017"

   ![Menu refaktoryzacji w Visual Studio](media/refactoring-menu.png)

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   ![Menu refaktoryzacji w Visual Studio](media/vs-2019/refactorings-menu.png)

   ::: moniker-end

- [Intellisense](../../ide/using-intellisense.md)

   IntelliSense to termin dla zestawu funkcji, które wyświetla informacje o kodzie bezpośrednio w edytorze i, w niektórych przypadkach, piszą za Ciebie małe części kodu. Przypomina to podstawową dokumentację w tekście w edytorze, dzięki której nie trzeba szukać informacji o typie w innym miejscu. Funkcje IntelliSense różnią się w zależności od języka. Aby uzyskać więcej informacji, zobacz [C# IntelliSense,](../../ide/visual-csharp-intellisense.md) [Visual C++ IntelliSense,](../../ide/visual-cpp-intellisense.md) [JavaScript IntelliSense](../../ide/javascript-intellisense.md)i [Visual Basic IntelliSense.](../../ide/visual-basic-specific-intellisense.md) Na poniższej ilustracji przedstawiono sposób, w jaki funkcja IntelliSense wyświetla listę elementów członkowskich dla typu:

   ::: moniker range="vs-2017"

   ![Visual Studio członkowskie](media/intellisense-list-members.png)

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   ![Visual Studio członkowskie](media/vs-2019/intellisense-list-members.png)

   ::: moniker-end

- Pole wyszukiwania

   Visual Studio czasami może wydawać się przytłaczające przy użyciu tak wielu menu, opcji i właściwości. Pole wyszukiwania to doskonały sposób na szybkie znalezienie tego, czego potrzebujesz w Visual Studio. Gdy zaczniesz wpisywać nazwę szukanych danych, Visual Studio wyniki, które zabierzą Cię dokładnie do miejsca, w którym musisz przejść. Jeśli musisz dodać funkcje do usługi Visual Studio, na przykład aby dodać obsługę dodatkowego języka programowania, pole wyszukiwania zawiera wyniki, które otwierają Instalator programu Visual Studio instalowania obciążenia lub pojedynczego składnika.

   > [!TIP]
   > Naciśnij **klawisze Ctrl** + **Q** jako skrót do pola wyszukiwania.

   ::: moniker range="vs-2017"

   ![Szybkie uruchamianie wyszukiwania w programie Visual Studio 2017](../media/quick-launch-nuget.png)

   Aby uzyskać więcej informacji, [zobacz Szybkie uruchamianie](../../ide/reference/quick-launch-environment-options-dialog-box.md).

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   ![Pole wyszukiwania w Visual Studio 2019 r.](media/vs-2019/quick-launch.png)

   ::: moniker-end

- [Live Share](/visualstudio/liveshare/)

   Wspólne edytowanie i debugowanie z innymi osobami w czasie rzeczywistym, niezależnie od typu aplikacji lub języka programowania. Możesz natychmiast i bezpiecznie udostępniać projekt oraz, w razie potrzeby, debugowanie sesji, wystąpień terminali, aplikacji internetowych hosta lokalnego, połączeń głosowych i nie tylko.

- [Hierarchia wywołań](../../ide/reference/call-hierarchy.md)

   Okno **Hierarchia** wywołań zawiera metody, które wywołują wybraną metodę. Mogą to być przydatne informacje, gdy myślisz o zmianie lub usunięciu metody albo gdy próbujesz śledzić usterkę.

   ::: moniker range="vs-2017"

   ![Okno Hierarchia wywołań w Visual Studio](media/call-hierarchy.png)

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   ![Okno Hierarchia wywołań w Visual Studio](media/vs-2019/call-hierarchy.png)

   ::: moniker-end

- [CodeLens](../../ide/find-code-changes-and-other-history-with-codelens.md)

   CodeLens ułatwia znajdowanie odwołań do kodu, zmian w kodzie, połączonych usterek, elementów roboczych, przeglądów kodu i testów jednostkowych bez opuszczania edytora.

   ::: moniker range="vs-2017"

   ![CodeLens w Visual Studio](media/codelens.png)

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   ![CodeLens w Visual Studio](media/vs-2019/codelens.png)

   ::: moniker-end

- [Przejdź do definicji](../../ide/go-to-and-peek-definition.md)

   Funkcja Przejdź do definicji pozwala przejść bezpośrednio do lokalizacji, w której zdefiniowano funkcję lub typ.

   ::: moniker range="vs-2017"

   ![Przejdź do definicji w Visual Studio 2017 r.](media/go-to-definition-menu.png)

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   ![Przejdź do definicji w Visual Studio 2019 r.](media/vs-2019/go-to-definition-menu.png)

   ::: moniker-end

- [Podejrzyj definicję](../../ide/how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12.md)

   W **oknie Podgląd definicji** jest przedstawiana definicja metody lub typu bez konieczności otwierania oddzielnego pliku.

   ::: moniker range="vs-2017"

   ![Podgląd definicji w Visual Studio](media/peek-definition.png)

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   ![Podgląd definicji w Visual Studio](media/vs-2019/peek-definition.png)

   ::: moniker-end

## <a name="install-the-visual-studio-ide"></a>Instalowanie środowiska IDE Visual Studio

W tej sekcji utworzysz prosty projekt, aby wypróbować niektóre czynności, które można wykonać za pomocą Visual Studio. Zmienisz motyw kolorów, użyjesz funkcji [IntelliSense](../../ide/using-intellisense.md) jako pomocy w kodowaniu i zdebugujesz aplikację, aby zobaczyć wartość zmiennej podczas wykonywania programu.

::: moniker range="vs-2017"

Aby rozpocząć, [pobierz Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) i zainstaluj go w systemie. Instalator modułowy umożliwia wybieranie i instalowanie obciążeń *,* które są grupami funkcji wymaganymi dla preferowanego języka lub platformy programowania. Aby wykonać kroki tworzenia [programu](#create-a-program), pamiętaj, aby podczas instalacji wybrać międzyplatformowe obciążenie tworzenia aplikacji na platformie **.NET Core.**

::: moniker-end

::: moniker range=">=vs-2019"

Aby rozpocząć, [pobierz Visual Studio](https://visualstudio.microsoft.com/downloads) i zainstaluj go w systemie. Instalator modułowy umożliwia wybieranie i instalowanie obciążeń *,* które są grupami funkcji wymaganymi dla preferowanego języka lub platformy programowania. Aby wykonać kroki tworzenia [programu](#create-a-program), pamiętaj, aby podczas instalacji wybrać międzyplatformowe obciążenie tworzenia aplikacji na platformie **.NET Core.**

::: moniker-end

![Międzyplatformowe obciążenie programowe platformy .NET Core w Instalator programu Visual Studio](../media/dotnet-core-cross-platform-workload.png)

Po pierwszym otwarciu Visual Studio możesz opcjonalnie zalogować się przy użyciu konta konto Microsoft lub konta służbowego. [](../../ide/signing-in-to-visual-studio.md)

## <a name="customize-visual-studio"></a>Dostosowywanie Visual Studio

Możesz spersonalizować Visual Studio interfejsu użytkownika, w tym zmienić domyślny motyw kolorów.

### <a name="change-the-color-theme"></a>Zmienianie motywu kolorów

Aby zmienić motyw **na ciemny:**

::: moniker range="vs-2017"

1. Otwórz program Visual Studio.

::: moniker-end

::: moniker range=">=vs-2019"

1. Otwórz program Visual Studio. W oknie uruchamiania wybierz pozycję **Kontynuuj bez kodu**.


    :::image type="content" source="media/vs-2019/continue-without-code.png" alt-text="Zrzut ekranu przedstawiający okno uruchamiania w Visual Studio 2019 r. z wyróżnionym linkiem &quot;Kontynuuj bez kodu&quot;.":::

   Zostanie otwarte idee.

::: moniker-end

2. Na pasku menu wybierz pozycję **Opcje**  >  **narzędzi,** aby otworzyć **okno dialogowe** Opcje.

3. Na stronie **Opcje** ogólne środowiska zmień wybór opcji  >   **Motyw kolorów** na **Ciemny,** a następnie kliknij przycisk **OK.**

   ![Zmień kolor motywu na ciemny w Visual Studio](media/change-color-theme.png)

   Motyw kolorów dla całego środowiska IDE zmieni się na **Ciemny.**

   ::: moniker range="vs-2017"

   ![Visual Studio w motywie ciemnym](../../ide/media/quickstart-personalize-dark-theme.png)

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   ![Visual Studio w motywie ciemnym](media/vs-2019/dark-theme.png)

   ::: moniker-end

### <a name="select-environment-settings"></a>Wybieranie ustawień środowiska

Następnie skonfigurujemy środowisko Visual Studio do używania ustawień środowiska dostosowanych do Visual Basic deweloperów.

1. Na pasku menu wybierz pozycję **Narzędzia**  >  **Importuj i Eksportuj ustawienia.**

2. W **Kreatorze importowania i eksportowania** ustawień wybierz pozycję **Resetuj wszystkie ustawienia** na pierwszej stronie, a następnie kliknij przycisk **Dalej.**

3. Na stronie **Zapisz bieżące ustawienia** wybierz opcję zapisania bieżących ustawień, a następnie kliknij przycisk **Dalej.** (Jeśli nie dostosowano żadnych ustawień, wybierz pozycję Nie, po prostu zresetuj **ustawienia, nadpisując moje bieżące ustawienia).**

4. Na stronie **Wybierz domyślną kolekcję ustawień** wybierz pozycję **Visual Basic**, a następnie kliknij przycisk **Zakończ.**

5. Na stronie **Resetuj zakończone** kliknij przycisk **Zamknij**.

Aby dowiedzieć się więcej o innych sposobach personalizowania środowiska IDE, zobacz [Personalizuj Visual Studio](../../ide/personalizing-the-visual-studio-ide.md).

## <a name="create-a-program"></a>Tworzenie programu

Przyjrzyjmy się temu i utwórzmy prosty program.

::: moniker range="vs-2017"

1. Na pasku Visual Studio menu wybierz pozycję **File** > **New Project (Nowy projekt pliku).**

   ![Plik > Nowy projekt na pasku menu](media/file-new-project-menu.png)

   W **oknie dialogowym** Nowy projekt jest wyświetlane kilka szablonów *projektu.* Szablon zawiera podstawowe pliki i ustawienia wymagane dla danego typu projektu.

1. Wybierz **kategorię .NET Core** w **Visual Basic**, a następnie wybierz szablon **Aplikacja konsolowa (.NET Core).** W polu **tekstowym** Nazwa wpisz **HelloWorld**, a następnie wybierz **przycisk OK.**

   ![Szablon aplikacji .NET Core](media/overview-npd.png)

   > [!NOTE]
   > Jeśli nie widzisz kategorii **.NET Core,** musisz zainstalować obciążenie tworzenie aplikacji **dla wielu platform.** W tym celu wybierz link **Otwórz Instalator programu Visual Studio** u dołu po lewej stronie okna **dialogowego Nowy** projekt. Po Instalator programu Visual Studio przewiń w dół i wybierz obciążenie Tworzenie aplikacji dla wielu platform dla platformy **.NET Core,** a następnie wybierz pozycję **Modyfikuj.**

   Visual Studio tworzy projekt. Jest to prosta aplikacja typu "Hello world", która wywołuje metodę w celu wyświetlenia <xref:System.Console.WriteLine?displayProperty=nameWithType> ciągu literału "Hello world!" w oknie konsoli (dane wyjściowe programu).

   Wkrótce powinien zostać wyświetlony następujący kod:

   ![Visual Studio IDE](media/overview-ide-console-app.png)

   Kod Visual Basic aplikacji jest wyświetlany w oknie edytora, które zajmuje większość miejsca. Zwróć uwagę, że tekst jest automatycznie pokolorowany w celu wskazania różnych części kodu, takich jak słowa kluczowe i typy. Ponadto małe, pionowe linie kreskowane w kodzie wskazują, które nawiasy klamrowe są ze sobą zgodne, a numery wierszy ułatwiają późniejsze lokalizowanie kodu. Możesz wybrać małe, boxed minus znaki, aby zwinąć lub rozwinąć bloki kodu. Ta funkcja wyekslinowania kodu pozwala ukryć kod, który nie jest potrzebny, co pomaga zminimalizować nieład ekranu. Pliki projektu są wyświetlane po prawej stronie okna o nazwie **Eksplorator rozwiązań**.

   ![Visual Studio IDE z czerwonymi polami](media/overview-ide-console-app-red-boxes.png)

   Dostępne są inne menu i okna narzędzi, ale na razie przejdźmy dalej.

1. Teraz uruchom aplikację. Możesz to zrobić, wybierając pozycję **Uruchom bez** debugowania z menu **Debugowanie** na pasku menu. Możesz również nacisnąć klawisz **Ctrl** + **F5.**

   ![Debugowanie > start bez menu debugowania](../media/overview-start-without-debugging.png)

   Visual Studio aplikację i zostanie otwarte okno konsoli z komunikatem **Hello world!**. Masz teraz uruchamianą aplikację.

   ![Okno konsoli](../media/overview-console-window.png)

1. Aby zamknąć okno konsoli, naciśnij dowolny klawisz na klawiaturze.

1. Dodajmy dodatkowy kod do aplikacji. Dodaj następujący kod Visual Basic przed wierszem o treści `Console.WriteLine("Hello World!")` :

   ```vb
   Console.WriteLine("What is your name?")
   Dim name = Console.ReadLine()
   ```

   Ten kod wyświetla komunikat What is your name? (Jaka jest Twoja **nazwa?)** w oknie konsoli, a następnie czeka, aż użytkownik wprowadzi tekst, po którym następuje **klawisz Enter.**

1. Zmień wiersz, który `Console.WriteLine("Hello World!")` mówi, na następujący kod:

   ```vb
   Console.WriteLine("Hello " + name + "!")
   ```

1. Uruchom aplikację ponownie, naciskając klawisz **Ctrl** + **F5**.

   Visual Studio aplikacja zostanie ponownie skompilowana, a zostanie otwarte okno konsoli z monitem o twoją nazwę.

1. Wprowadź swoją nazwę w oknie konsoli i naciśnij **klawisz Enter**.

   ![Wejście okna konsoli](../media/overview-console-input.png)

1. Naciśnij dowolny klawisz, aby zamknąć okno konsoli i zatrzymać uruchomiony program.

::: moniker-end

::: moniker range=">=vs-2019"

1. Na pasku Visual Studio wybierz pozycję **File** New Project  >  **(Nowy projekt**  >  **pliku).** (Ewentualnie naciśnij klawisze **Ctrl** + **Shift (Przesunięcie)** + **N**).

    :::image type="content" source="media/vs-2019/file-new-project.png" alt-text="Zrzut ekranu przedstawiający wybór > Nowy > Project na pasku menu Visual Studio 2019.":::

   Zostanie **otwarte okno Tworzenie nowego** projektu z kilkoma *szablonami projektów.* Szablon zawiera podstawowe pliki i ustawienia wymagane dla danego typu projektu.

1. Aby znaleźć szablon, którego potrzebujemy, wpisz lub wprowadź **konsolę .net core** w polu wyszukiwania. Lista dostępnych szablonów jest automatycznie filtrowana na podstawie wprowadzonych słów kluczowych. Możesz dalej filtrować wyniki szablonu, wybierając opcję  Visual Basic z listy rozwijanej **Wszystkie** języki, system **Windows** z listy **Wszystkie** platformy i opcję **Konsola** z listy Wszystkie **typy projektów.**

   Wybierz szablon **Aplikacja konsolowa,** a następnie kliknij przycisk **Dalej.**

    :::image type="content" source="media/vs-2019/create-new-project.png" alt-text="Zrzut ekranu przedstawiający okno &quot;Tworzenie nowego projektu&quot; Visual Studio 2019 r., w którym można wybrać szablon.":::

1. W **oknie** Configure your new project (Konfigurowanie nowego projektu) wprowadź **helloworld** w polu **Project name** (Nazwa projektu), opcjonalnie zmień lokalizację katalogu dla plików projektu (domyślne ustawienia lokalne to ), a następnie kliknij przycisk `C:\Users\<name>\source\repos` Next **(Dalej).**

    :::image type="content" source="media/vs-2019/configure-new-project.png" alt-text="Zrzut ekranu przedstawiający okno &quot;Konfigurowanie nowego projektu&quot; Visual Studio 2019 r., w którym wprowadzasz nazwę projektu.":::

1. W **oknie Dodatkowe informacje** sprawdź, czy program **.NET Core 3.1** jest wyświetlany w menu rozwijaym **Target Framework,** a następnie kliknij pozycję **Utwórz.**

    :::image type="content" source="media/vs-2019/create-project-additional-info.png" alt-text="Zrzut ekranu przedstawiający okno &quot;Dodatkowe informacje&quot; w programie Visual Studio 2019, w którym wybierasz wersję programu .NET Core Framework.":::

   Visual Studio tworzy projekt. Jest to prosta aplikacja typu "Hello world", która wywołuje metodę w celu wyświetlenia <xref:System.Console.WriteLine?displayProperty=nameWithType> ciągu literału "Hello world!" w oknie konsoli (dane wyjściowe programu).

   Wkrótce powinien zostać wyświetlony następujący kod:

   ![Visual Studio IDE](media/overview-ide-console-app.png)

   Kod Visual Basic aplikacji jest wyświetlany w oknie edytora, które zajmuje większość miejsca. Zwróć uwagę, że tekst jest automatycznie pokolorowany w celu wskazania różnych części kodu, takich jak słowa kluczowe i typy. Ponadto małe, pionowe linie kreskowane w kodzie wskazują, które nawiasy klamrowe są ze sobą zgodne, a numery wierszy ułatwiają późniejsze lokalizowanie kodu. Możesz wybrać małe, boxed minus znaki, aby zwinąć lub rozwinąć bloki kodu. Ta funkcja wyekslinowania kodu pozwala ukryć kod, który nie jest potrzebny, co pomaga zminimalizować nieład ekranu. Pliki projektu są wyświetlane po prawej stronie okna o nazwie **Eksplorator rozwiązań**.

   ![Visual Studio IDE z czerwonymi polami](media/overview-ide-console-app-red-boxes.png)

   Dostępne są inne menu i okna narzędzi, ale na razie przejdźmy dalej.

1. Teraz uruchom aplikację. Możesz to zrobić, wybierając pozycję **Uruchom bez** debugowania z menu **Debugowanie** na pasku menu. Możesz również nacisnąć klawisz **Ctrl** + **F5.**

   ![Debugowanie > start bez menu debugowania](media/vs-2019/start-without-debugging.png)

   Visual Studio aplikację i zostanie otwarte okno konsoli z komunikatem **Hello world!**. Masz teraz uruchamianą aplikację.

   ![Zrzut ekranu przedstawiający okno konsoli z wyświetlonym Hello world komunikatu.](../media/vs-2019/overview-console-window.png)

1. Aby zamknąć okno konsoli, naciśnij dowolny klawisz na klawiaturze.

1. Dodajmy dodatkowy kod do aplikacji. Dodaj następujący kod Visual Basic przed wierszem o treści `Console.WriteLine("Hello World!")` :

   ```vb
   Console.WriteLine("What is your name?")
   Dim name = Console.ReadLine()
   ```

   Ten kod wyświetla komunikat What is your name? (Jaka jest Twoja **nazwa?)** w oknie konsoli, a następnie czeka, aż użytkownik wprowadzi tekst, po którym następuje **klawisz Enter.**

1. Zmień wiersz, który `Console.WriteLine("Hello World!")` mówi, na następujący kod:

   ```vb
   Console.WriteLine("Hello " + name + "!")
   ```

1. Uruchom aplikację ponownie, naciskając klawisz **Ctrl** + **F5**.

   Visual Studio aplikacja zostanie ponownie skompilowana, a zostanie otwarte okno konsoli z monitem o twoją nazwę.

1. Wprowadź swoją nazwę w oknie konsoli i naciśnij **klawisz Enter**.

   ![Zrzut ekranu przedstawiający okno konsoli z pytaniem What is your name (Jakie jest Twoje imię i odpowiedź aplikacji).](../media/vs-2019/overview-console-input.png)

1. Naciśnij dowolny klawisz, aby zamknąć okno konsoli i zatrzymać uruchomiony program.

::: moniker-end

## <a name="use-refactoring-and-intellisense"></a>Używanie refaktoryzacji i funkcji IntelliSense

Przyjrzyjmy się kilku sposobom, [](../../ide/refactoring-in-visual-studio.md) na które refaktoryzacja i [funkcja IntelliSense](../../ide/using-intellisense.md) mogą pomóc w wydajniejszym kodowanie.

Najpierw zmieńmy nazwę `name` zmiennej:

1. Kliknij dwukrotnie `name` zmienną, aby ją zaznaczyć.

2. Wpisz nową nazwę zmiennej, **username**.

   Zwróć uwagę, że wokół zmiennej pojawia się szare pole, a na marginesie pojawi się żarówka.

3. Wybierz ikonę żarówki, aby wyświetlić dostępne [szybkie akcje](../../ide/quick-actions.md). Wybierz **pozycję Zmień nazwę "name" na "username".**

   ![Akcja zmiany nazwy w Visual Studio](media/rename-quick-action.png)

   Nazwa zmiennej jest zmieniana w projekcie. W naszym przypadku jest to tylko dwa miejsca.

4. Teraz przyjrzyjmy się funkcji IntelliSense. Poniżej wiersza z następującą `Console.WriteLine("Hello &quot; + username + &quot;!")` wartością wpisz następujący fragment kodu:

    ```vb
   Dim now = Date.
   ```

   Pole zawiera składowe <xref:System.DateTime> klasy. Ponadto opis aktualnie wybranego członka jest wyświetlany w osobnym polu.

   ![Elementy członkowskie listy funkcji IntelliSense w Visual Studio](media/intellisense-list-members.png)

5. Wybierz członka o nazwie **Now**, który jest właściwością klasy , klikając ją dwukrotnie lub wybierając ją za pomocą klawiszy strzałek w górę lub w dół, a następnie naciskając klawisz **Tab**.

6. Poniżej wpisz lub wklej następujące wiersze kodu:

   ```vb
   Dim dayOfYear = now.DayOfYear
   Console.Write("Day of year: ")
   Console.WriteLine(dayOfYear)
   ```

   > [!TIP]
   > <xref:System.Console.Write%2A?displayProperty=nameWithType> Jest nieco inny niż w tym, że nie <xref:System.Console.WriteLine%2A?displayProperty=nameWithType> dodaje terminatora wiersza po wydrukowaniu. Oznacza to, że następny fragment tekstu, który zostanie wysłany do danych wyjściowych, zostanie wydrukowany w tym samym wierszu. Możesz zatrzymać wskaźnik myszy na każdej z tych metod w kodzie, aby wyświetlić ich opis.

7. Następnie ponownie użyjemy refaktoryzacji, aby kod był nieco zwięzły. Kliknij zmienną `now` w wierszu `Dim now = Date.Now` .

   Zwróć uwagę, że na marginesie w tym wierszu pojawia się mała ikona śrubokręta.

8. Kliknij ikonę śrubokręta, aby zobaczyć, jakie sugestie Visual Studio dostępne. W tym przypadku jest pokazywana refaktoryzacja zmiennej tymczasowej Wbudowane w celu usunięcia wiersza kodu bez zmiany ogólnego zachowania kodu: [](../../ide/reference/inline-temporary-variable.md)

   ![Refaktoryzacja wbudowanej zmiennej tymczasowej w Visual Studio](media/inline-temporary-variable-refactoring.png)

9. Kliknij **pozycję Inline temporary variable (W** tekście zmiennej tymczasowej), aby refaktoryzować kod.

::: moniker range="vs-2017"

10. Uruchom ponownie program, naciskając klawisz **Ctrl** + **F5**. Dane wyjściowe wyglądają następująco:

    ![Okno konsoli z wyjściem programu](../media/overview-console-final.png)

::: moniker-end

::: moniker range=">=vs-2019"

10. Uruchom ponownie program, naciskając klawisz **Ctrl** + **F5**. Dane wyjściowe wyglądają następująco:

    ![Okno konsoli z wyjściem programu](../media/vs-2019/overview-console-final.png)

::: moniker-end

## <a name="debug-code&quot;></a>Debugowanie kodu

Podczas pisania kodu musisz go uruchomić i przetestować pod podpowiedem usterek. Visual Studio debugowania systemu pozwala przechodzić przez kod po jednej instrukcji na raz i sprawdzać zmienne w każdym momencie. Można ustawić punkty *przerwania, które* zatrzymają wykonywanie kodu w określonym wierszu. Możesz obserwować, jak wartość zmiennej zmienia się podczas pracy kodu i nie tylko.

Ustawmy punkt przerwania, aby zobaczyć wartość zmiennej, gdy `username` program jest &quot;w locie&quot;.

1. Znajdź wiersz kodu o treści `Console.WriteLine(&quot;Hello &quot; + username + &quot;!")` . Aby ustawić punkt przerwania w tym wierszu kodu, czyli aby program wstrzymał wykonywanie w tym wierszu, kliknij lewy margines edytora. Możesz również kliknąć dowolne miejsce w wierszu kodu, a następnie nacisnąć **klawisz F9**.

   Na marginesie po lewej stronie pojawi się czerwone kółko, a kod zostanie wyróżniony na czerwono.

   ![Punkt przerwania w wierszu kodu w Visual Studio](media/breakpoint.png)

1. Rozpocznij debugowanie, wybierając pozycję   >  **Debuguj rozpocznij debugowanie** lub naciskając **klawisz F5**.

1. Gdy zostanie wyświetlone okno konsoli z prośbą o podanie twojej nazwy, wpisz ją i naciśnij klawisz **Enter**.

   Fokus powraca do Visual Studio kodu, a wiersz kodu z punktem przerwania jest wyróżniony żółtym kolorem. Oznacza to, że jest to następny wiersz kodu, który zostanie wykonany przez program.

1. Umieść wskaźnik myszy na `username` zmiennej, aby wyświetlić jej wartość. Alternatywnie możesz kliknąć prawym przyciskiem myszy i wybrać pozycję Dodaj czujkę, aby dodać zmienną do okna Czujka, w którym `username` można również zobaczyć jej wartość.  

   ![Wartość zmiennej podczas debugowania w Visual Studio](media/debugging-variable-value.png)

1. Aby pozwolić programowi na ukończenie, naciśnij **ponownie klawisz F5.**

Aby uzyskać więcej informacji na temat debugowania w programie Visual Studio, zobacz [Debugger feature tour (Przewodnik po funkcji debugera).](../../debugger/debugger-feature-tour.md)

## <a name="next-steps"></a>Następne kroki

Zapoznaj Visual Studio dalej, korzystając z jednego z następujących artykułów wprowadzających:

> [!div class="nextstepaction"]
> [Dowiedz się, jak używać edytora kodu](tutorial-editor.md)

> [!div class="nextstepaction"]
> [Dowiedz się więcej o projektach i rozwiązaniach](tutorial-projects-solutions.md)

## <a name="see-also"></a>Zobacz też

- Odkryj [więcej Visual Studio funkcji](../../ide/advanced-feature-overview.md)
- Odwiedź [visualstudio.microsoft.com](https://visualstudio.microsoft.com/vs/)
- Przeczytaj [blog Visual Studio bloga](https://devblogs.microsoft.com/visualstudio/)
