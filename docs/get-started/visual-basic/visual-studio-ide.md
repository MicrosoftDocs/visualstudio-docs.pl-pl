---
title: Przegląd dla deweloperów Visual Basic
description: Dowiedz się więcej o używaniu programu Visual Studio do edytowania, debugowania i kompilowania kodu, a następnie publikowania aplikacji jako dewelopera Visual Basic.
ms.date: 03/02/2021
ms.technology: vs-ide-general
ms.custom:
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
ms.openlocfilehash: 398070e0214e36f696bb69614bb6a51b3462a551
ms.sourcegitcommit: 5654b7a57a9af111a6f29239212d76086bc745c9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/03/2021
ms.locfileid: "101682985"
---
# <a name="welcome-to-the-visual-studio-ide--visual-basic"></a>Witamy w programie Visual Studio IDE | Visual Basic

*Zintegrowane środowisko programistyczne* programu Visual Studio to twórczy pad do uruchamiania, który umożliwia edytowanie, debugowanie i kompilowanie kodu, a następnie publikowanie aplikacji. Zintegrowane środowisko programistyczne (IDE) to program bogaty w funkcje, który może być używany w wielu aspektach tworzenia oprogramowania. W porównaniu z standardowym edytorem i debugerem, który środowisk IDE zapewnia, program Visual Studio obejmuje kompilatory, narzędzia do uzupełniania kodu, graficzne projektanci i wiele innych funkcji, które ułatwiają proces tworzenia oprogramowania.

::: moniker range="vs-2017"

![Środowisko IDE programu Visual Studio](../media/visual-studio-ide.png)

::: moniker-end

::: moniker range=">=vs-2019"

[![Środowisko IDE programu Visual Studio 2019](media/vs-2019/ide-overview.png)](media/vs-2019/ide-overview.png#lightbox)

::: moniker-end

Ten obraz przedstawia program Visual Studio z otwartym projektem i kilkoma oknami narzędzi kluczowych, których prawdopodobnie używasz:

- [Eksplorator rozwiązań](../../ide/solutions-and-projects-in-visual-studio.md) (prawy górny) umożliwia wyświetlanie plików kodu i nawigowanie w nich oraz zarządzanie nimi. **Eksplorator rozwiązań** może pomóc organizować kod przez zgrupowanie plików na [rozwiązania i projekty](tutorial-projects-solutions.md).

- [Okno edytora](../../ide/writing-code-in-the-code-and-text-editor.md) (środkowe), w którym najprawdopodobniej będzie można spędzać większość czasu, zostanie wyświetlona zawartość pliku. Jest to miejsce, w którym można edytować kod lub zaprojektować interfejs użytkownika, taki jak okno z przyciskami i polami tekstowymi.

- W [oknie danych wyjściowych](../../ide/reference/output-window.md) (u dołu) jest miejsce, gdzie program Visual Studio wysyła powiadomienia, takie jak debugowanie i komunikaty o błędach, ostrzeżenia kompilatora, publikowanie komunikatów o stanie itd. Każde źródło wiadomości ma własną kartę.

- [Team Explorer](/azure/devops/user-guide/work-team-explorer?view=vsts&preserve-view=true) (prawy dolny) umożliwia śledzenie elementów roboczych i udostępnianie kodu innym osobom korzystającym z technologii kontroli wersji, takich jak [git](https://git-scm.com/) i [Kontrola wersji serwera Team Foundation (TFVC)](/azure/devops/repos/tfvc/overview?view=vsts&preserve-view=true).

## <a name="editions"></a>Wersje

Program Visual Studio jest dostępny dla systemów Windows i Mac. [Visual Studio dla komputerów Mac](/visualstudio/mac/) ma wiele takich samych funkcji, jak program Visual Studio 2017 i jest zoptymalizowany pod kątem opracowywania aplikacji mobilnych i międzyplatformowych. Ten artykuł koncentruje się na wersji systemu Windows programu Visual Studio 2017.

Istnieją trzy wersje programu Visual Studio 2017: Community, Professional i Enterprise. Zobacz [porównanie programu Visual Studio 2017 środowisk IDE](https://visualstudio.microsoft.com/vs/compare/) , aby dowiedzieć się, jakie funkcje są obsługiwane w poszczególnych wersjach.

## <a name="popular-productivity-features"></a>Popularne funkcje produktywności

Niektóre popularne funkcje programu Visual Studio, które ułatwiają wydajniejszą pracę podczas opracowywania oprogramowania, obejmują:

- Zygzaki i [szybkie akcje](../../ide/quick-actions.md)

   Zygzaki to faliste podkreślenia, które wysyłają alerty do błędów lub potencjalnych problemów w kodzie podczas wpisywania. Te wizualne wskazówki umożliwiają natychmiastowe Rozwiązywanie problemów bez oczekiwania na odnalezienie błędu podczas kompilacji lub podczas uruchamiania programu. Po umieszczeniu wskaźnika myszy na zygzaku pojawią się dodatkowe informacje o błędzie. Żarówka może również pojawić się na lewym marginesie z akcjami, znanymi jako szybkie akcje, aby naprawić błąd.

   ::: moniker range="vs-2017"

   ![Zygzaky w programie Visual Studio](media/squiggles-error.png)

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   ![Zygzaky w programie Visual Studio](media/vs-2019/squiggles-error.png)

   ::: moniker-end

- [Refaktoryzacja](../../ide/refactoring-in-visual-studio.md)

   Refaktoryzacja obejmuje operacje, takie jak inteligentne Zmienianie nazw zmiennych, wyodrębnianie jednego lub większej liczby wierszy kodu do nowej metody, zmiana kolejności parametrów metody i nie tylko.

   ::: moniker range="vs-2017"

   ![Menu refaktoryzacji w programie Visual Studio](media/refactoring-menu.png)

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   ![Menu refaktoryzacji w programie Visual Studio](media/vs-2019/refactorings-menu.png)

   ::: moniker-end

- [Technologia](../../ide/using-intellisense.md)

   Technologia IntelliSense to termin dla zestawu funkcji, który wyświetla informacje o kodzie bezpośrednio w edytorze, a w niektórych przypadkach zapisuje małe bity kodu. Jest tak jak w przypadku, gdy podstawowa dokumentacja jest wbudowana w edytorze, co umożliwia zaoszczędzenie informacji o typie w innym miejscu. Funkcje IntelliSense różnią się w zależności od języka. Aby uzyskać więcej informacji, zobacz [C# IntelliSense](../../ide/visual-csharp-intellisense.md), [Visual C++ IntelliSense](../../ide/visual-cpp-intellisense.md), [JavaScript IntelliSense](../../ide/javascript-intellisense.md)i [Visual Basic IntelliSense](../../ide/visual-basic-specific-intellisense.md). Na poniższej ilustracji przedstawiono, w jaki sposób technologia IntelliSense wyświetla listę elementów członkowskich typu:

   ::: moniker range="vs-2017"

   ![Lista elementów członkowskich programu Visual Studio](media/intellisense-list-members.png)

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   ![Lista elementów członkowskich programu Visual Studio](media/vs-2019/intellisense-list-members.png)

   ::: moniker-end

- Pole wyszukiwania

   Program Visual Studio może pozornie przeciążać, tak jak wiele menu, opcji i właściwości. Pole wyszukiwania to doskonały sposób na szybkie znajdowanie potrzebnych informacji w programie Visual Studio. Po rozpoczęciu wpisywania nazwy szukanego elementu program Visual Studio Wyświetla listę wyników, które dokładnie zapoznają się z tym, co należy zrobić. Aby dodać funkcję do programu Visual Studio, na przykład w celu dodania obsługi dodatkowego języka programowania, w polu wyszukiwania znajdują się wyniki otwierające Instalator programu Visual Studio w celu zainstalowania obciążenia lub pojedynczego składnika.

   > [!TIP]
   > Naciśnij klawisz **Ctrl** + **Q** jako skrót do pola wyszukiwania.

   ::: moniker range="vs-2017"

   ![Pole wyszukiwania szybkiego uruchamiania w programie Visual Studio 2017](../media/quick-launch-nuget.png)

   Aby uzyskać więcej informacji, zobacz [Szybki Start](../../ide/reference/quick-launch-environment-options-dialog-box.md).

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   ![Pole wyszukiwania w programie Visual Studio 2019](media/vs-2019/quick-launch.png)

   ::: moniker-end

- [Live Share](/visualstudio/liveshare/)

   Współpracuj z innymi osobami w czasie rzeczywistym, niezależnie od typu aplikacji lub języka programowania. Możesz natychmiast i bezpiecznie udostępnić projekt oraz, w razie konieczności, debugowanie sesji, wystąpienia terminala, aplikacje sieci Web, połączenia głosowe i inne.

- [Hierarchia wywołań](../../ide/reference/call-hierarchy.md)

   W oknie **Hierarchia wywołań** są wyświetlane metody wywołujące wybraną metodę. Te informacje mogą być przydatne, gdy myślisz o zmianie lub usunięciu metody lub podczas próby śledzenia błędu.

   ::: moniker range="vs-2017"

   ![Okno hierarchii wywołań w programie Visual Studio](media/call-hierarchy.png)

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   ![Okno hierarchii wywołań w programie Visual Studio](media/vs-2019/call-hierarchy.png)

   ::: moniker-end

- [CodeLens](../../ide/find-code-changes-and-other-history-with-codelens.md)

   CodeLens pomaga znaleźć odwołania do kodu, zmiany w kodzie, połączone błędy, elementy robocze, przeglądy kodu i testy jednostkowe, bez opuszczania edytora.

   ::: moniker range="vs-2017"

   ![CodeLens w programie Visual Studio](media/codelens.png)

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   ![CodeLens w programie Visual Studio](media/vs-2019/codelens.png)

   ::: moniker-end

- [Przejdź do definicji](../../ide/go-to-and-peek-definition.md)

   Funkcja przejdź do definicji przenosi bezpośrednio do lokalizacji, w której zdefiniowana jest funkcja lub typ.

   ::: moniker range="vs-2017"

   ![Przejdź do definicji w programie Visual Studio 2017](media/go-to-definition-menu.png)

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   ![Przejdź do definicji w programie Visual Studio 2019](media/vs-2019/go-to-definition-menu.png)

   ::: moniker-end

- [Podejrzyj definicję](../../ide/how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12.md)

   Okno **Definicja wglądu** pokazuje definicję metody lub typu bez faktycznego otwierania osobnego pliku.

   ::: moniker range="vs-2017"

   ![Wgląd do definicji w programie Visual Studio](media/peek-definition.png)

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   ![Wgląd do definicji w programie Visual Studio](media/vs-2019/peek-definition.png)

   ::: moniker-end

## <a name="install-the-visual-studio-ide"></a>Instalowanie środowiska IDE programu Visual Studio

W tej sekcji utworzysz prosty projekt, aby wypróbować niektóre elementy, które można wykonać za pomocą programu Visual Studio. Zmienisz motyw kolorów, użyjesz funkcji [IntelliSense](../../ide/using-intellisense.md) jako pomocy dotyczącej kodowania i debugujesz aplikację, aby zobaczyć wartość zmiennej podczas wykonywania programu.

::: moniker range="vs-2017"

Aby rozpocząć, [Pobierz program Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) i zainstaluj go w systemie. Modułowy Instalator umożliwia wybieranie i instalowanie *obciążeń*, które są grupami funkcji wymaganych przez preferowany język programowania lub platformę. Aby postępować zgodnie z instrukcjami dotyczącymi [tworzenia programu](#create-a-program), należy wybrać **środowisko programistyczne dla wielu platform .NET Core** podczas instalacji.

::: moniker-end

::: moniker range=">=vs-2019"

Aby rozpocząć, [Pobierz program Visual Studio](https://visualstudio.microsoft.com/downloads) i zainstaluj go w systemie. Modułowy Instalator umożliwia wybieranie i instalowanie *obciążeń*, które są grupami funkcji wymaganych przez preferowany język programowania lub platformę. Aby postępować zgodnie z instrukcjami dotyczącymi [tworzenia programu](#create-a-program), należy wybrać **środowisko programistyczne dla wielu platform .NET Core** podczas instalacji.

::: moniker-end

![Obciążenie Międzyplatformowe dla platformy .NET Core w Instalator programu Visual Studio](../media/dotnet-core-cross-platform-workload.png)

Po otwarciu programu Visual Studio po raz pierwszy możesz [zalogować się](../../ide/signing-in-to-visual-studio.md) przy użyciu konto Microsoft lub konta służbowego.

## <a name="customize-visual-studio"></a>Dostosuj program Visual Studio

Możesz spersonalizować interfejs użytkownika programu Visual Studio, w tym zmiany domyślnego motywu kolorów.

### <a name="change-the-color-theme"></a>Zmień motyw kolorów

Aby przejść do **ciemnego** motywu:

::: moniker range="vs-2017"

1. Otwórz program Visual Studio.

::: moniker-end

::: moniker range=">=vs-2019"

1. Otwórz program Visual Studio. W oknie uruchamiania wybierz pozycję **Kontynuuj bez kodu**.


    :::image type="content" source="media/vs-2019/continue-without-code.png" alt-text="Zrzut ekranu okna uruchamiania w programie Visual Studio 2019 z wyróżnionym linkiem &quot;Kontynuuj bez kodu&quot;.":::

   Zostanie otwarte środowisko IDE.

::: moniker-end

2. Na pasku menu wybierz **Narzędzia**  >  **Opcje** , aby otworzyć okno dialogowe **Opcje** .

3. Na stronie   >  **Ogólne** opcje środowiska Zmień wybór **motywu koloru** na **ciemny**, a następnie kliknij przycisk **OK**.

   ![Zmień motyw kolorów na ciemny w programie Visual Studio](media/change-color-theme.png)

   Motyw kolorów dla całego środowiska IDE zmieni się na **ciemny**.

   ::: moniker range="vs-2017"

   ![Visual Studio w ciemnym motywie](../../ide/media/quickstart-personalize-dark-theme.png)

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   ![Visual Studio w ciemnym motywie](media/vs-2019/dark-theme.png)

   ::: moniker-end

### <a name="select-environment-settings"></a>Wybierz ustawienia środowiska

Następnie skonfigurujemy program Visual Studio do korzystania z ustawień środowiska dostosowanych do Visual Basic deweloperów.

1. Na pasku menu wybierz kolejno opcje **Narzędzia**  >  **Importuj i Eksportuj ustawienia**.

2. W **Kreatorze importowania i eksportowania ustawień** wybierz opcję **Zresetuj wszystkie ustawienia** na pierwszej stronie, a następnie kliknij przycisk **dalej**.

3. Na stronie **Zapisywanie bieżących ustawień** wybierz opcję zapisania bieżących ustawień lub nie, a następnie kliknij przycisk **dalej**. (Jeśli nie dostosowano żadnych ustawień, wybierz pozycję **nie, po prostu Zresetuj ustawienia, zastępując Moje bieżące ustawienia**).

4. Na stronie **Wybierz domyślną kolekcję ustawień** wybierz **Visual Basic**, a następnie kliknij przycisk **Zakończ**.

5. Na stronie **Resetowanie ukończone** kliknij przycisk **Zamknij**.

Aby dowiedzieć się więcej na temat innych sposobów personalizowania środowiska IDE, zobacz [Personalizowanie programu Visual Studio](../../ide/personalizing-the-visual-studio-ide.md).

## <a name="create-a-program"></a>Tworzenie programu

Szczegółowemy i utworzysz prosty program.

::: moniker range="vs-2017"

1. Na pasku menu programu Visual Studio wybierz pozycję **plik** > **Nowy projekt**.

   ![Plik > nowy projekt na pasku menu](media/file-new-project-menu.png)

   Okno dialogowe **Nowy projekt** zawiera kilka *szablonów* projektów. Szablon zawiera podstawowe pliki i ustawienia, które są zbędne dla danego typu projektu.

1. Wybierz kategorię **.NET Core** w obszarze **Visual Basic**, a następnie wybierz szablon **Aplikacja konsolowa (.NET Core)** . W polu tekstowym **Nazwa** wpisz **HelloWorld**, a następnie wybierz przycisk **OK** .

   ![Szablon aplikacji .NET Core](media/overview-npd.png)

   > [!NOTE]
   > Jeśli nie widzisz kategorii **.NET Core** , musisz zainstalować **środowisko programistyczne dla wielu platform .NET Core** . Aby to zrobić, wybierz link **otwórz Instalator programu Visual Studio** w lewym dolnym rogu okna dialogowego **Nowy projekt** . Po otwarciu Instalator programu Visual Studio przewiń w dół i wybierz pozycję **.NET Core Międzyplatformowe** obciążenie dla deweloperów, a następnie wybierz polecenie **Modyfikuj**.

   Program Visual Studio tworzy projekt. Jest to prosta aplikacja "Hello world", która wywołuje <xref:System.Console.WriteLine?displayProperty=nameWithType> metodę w celu wyświetlenia ciągu literału "Hello World!" w oknie Konsola (dane wyjściowe programu).

   Wkrótce powinna zostać wyświetlona następująca zawartość:

   ![Visual Studio IDE](media/overview-ide-console-app.png)

   Kod Visual Basic aplikacji pojawia się w oknie edytora, co powoduje najwięcej miejsca. Zauważ, że tekst jest automatycznie kolorowy, aby wskazać różne części kodu, takie jak słowa kluczowe i typy. Ponadto małe, pionowe linie kreskowane w kodzie wskazują, które nawiasy są zgodne ze sobą, a numery wierszy ułatwiają znalezienie kodu później. Możesz wybrać małe, opakowane znaki minus, aby zwinąć lub rozwinąć bloki kodu. Ta funkcja tworzenia konspektu kodu umożliwia ukrycie kodu, który nie jest potrzebny, pomagając na zminimalizowanie bałaganu na ekranie. Pliki projektu są wymienione po prawej stronie w oknie o nazwie **Eksplorator rozwiązań**.

   ![Środowisko IDE programu Visual Studio z czerwonymi polami](media/overview-ide-console-app-red-boxes.png)

   Dostępne są inne menu i okna narzędzi, ale teraz przyjrzyjmy się.

1. Teraz uruchom aplikację. Można to zrobić, wybierając pozycję **Uruchom bez debugowania** z menu **Debuguj** na pasku menu. Możesz również nacisnąć klawisz **Ctrl** + **F5**.

   ![Debuguj > Rozpocznij bez debugowania menu](../media/overview-start-without-debugging.png)

   Program Visual Studio kompiluje aplikację i zostanie otwarte okno konsoli z komunikatem **Hello World!**. Masz teraz działającą aplikację.

   ![Okno konsoli](../media/overview-console-window.png)

1. Aby zamknąć okno konsoli, naciśnij dowolny klawisz na klawiaturze.

1. Dodajmy do aplikacji dodatkowy kod. Dodaj następujący kod Visual Basic przed wierszem, który brzmi `Console.WriteLine("Hello World!")` :

   ```vb
   Console.WriteLine("What is your name?")
   Dim name = Console.ReadLine()
   ```

   Ten kod wyświetla **nazwę użytkownika** w oknie konsoli, a następnie czeka, aż użytkownik wprowadzi jakiś tekst, a następnie klawisz **Enter** .

1. Zmień wiersz wyświetlany w `Console.WriteLine("Hello World!")` następującym kodzie:

   ```vb
   Console.WriteLine("Hello " + name + "!")
   ```

1. Uruchom aplikację ponownie, naciskając klawisz **Ctrl** + **F5**.

   Program Visual Studio ponownie kompiluje aplikację i zostanie otwarte okno konsoli z prośbą o wprowadzenie nazwy.

1. Wprowadź swoją nazwę w oknie konsoli i naciśnij klawisz **Enter**.

   ![Dane wejściowe okna konsoli](../media/overview-console-input.png)

1. Naciśnij dowolny klawisz, aby zamknąć okno konsoli i zatrzymać uruchomiony program.

::: moniker-end

::: moniker range=">=vs-2019"

1. Na pasku menu programu Visual Studio wybierz pozycję **plik**  >  **Nowy**  >  **projekt**. (Alternatywnie naciśnij klawisz **Ctrl** + **SHIFT** + **N**.)

    :::image type="content" source="media/vs-2019/file-new-project.png" alt-text="Zrzut ekranu przedstawiający plik > nowy > wybór projektu z paska menu programu Visual Studio 2019.":::

   Zostanie otwarte okno **Utwórz nowy projekt** zawierające kilka *szablonów* projektów. Szablon zawiera podstawowe pliki i ustawienia wymagane dla danego typu projektu.

1. Aby znaleźć żądany szablon, wpisz lub wprowadź w polu wyszukiwania **konsolę .NET Core** . Lista dostępnych szablonów jest automatycznie filtrowana na podstawie wprowadzonych słów kluczowych. Możesz dodatkowo filtrować wyniki szablonu, wybierając pozycję **Visual Basic** z listy rozwijanej **wszystkie języki** , **Windows** z listy **wszystkie platformy** **, a następnie** z listy **wszystkie typy projektów** .

   Wybierz szablon **Aplikacja konsolowa** , a następnie kliknij przycisk **dalej**.

    :::image type="content" source="media/vs-2019/create-new-project.png" alt-text="Zrzut ekranu przedstawiający okno &quot;Tworzenie nowego projektu&quot; w programie Visual Studio 2019, w którym wybierasz szablon, którego chcesz użyć.":::

1. W oknie **Konfigurowanie nowego projektu** wprowadź **HelloWorld** w polu **Nazwa projektu** , opcjonalnie Zmień lokalizację katalogu dla plików projektu (domyślne ustawienia regionalne to `C:\Users\<name>\source\repos` ), a następnie kliknij przycisk **dalej**.

    :::image type="content" source="media/vs-2019/configure-new-project.png" alt-text="Zrzut ekranu przedstawiający okno &quot;Konfigurowanie nowego projektu&quot; w programie Visual Studio 2019, w którym wprowadzana jest nazwa projektu.":::

1. W oknie **Informacje dodatkowe** Sprawdź, czy program **.NET Core 3,1** pojawia się w menu rozwijanym **platforma docelowa** , a następnie kliknij przycisk **Utwórz**.

    :::image type="content" source="media/vs-2019/create-project-additional-info.png" alt-text="Zrzut ekranu przedstawiający okno &quot;dodatkowe informacje&quot; w programie Visual Studio 2019, w którym wybierasz żądaną wersję platformy .NET Core.":::

   Program Visual Studio tworzy projekt. Jest to prosta aplikacja "Hello world", która wywołuje <xref:System.Console.WriteLine?displayProperty=nameWithType> metodę w celu wyświetlenia ciągu literału "Hello World!" w oknie Konsola (dane wyjściowe programu).

   Wkrótce powinna zostać wyświetlona następująca zawartość:

   ![Visual Studio IDE](media/overview-ide-console-app.png)

   Kod Visual Basic aplikacji pojawia się w oknie edytora, co powoduje najwięcej miejsca. Zauważ, że tekst jest automatycznie kolorowy, aby wskazać różne części kodu, takie jak słowa kluczowe i typy. Ponadto małe, pionowe linie kreskowane w kodzie wskazują, które nawiasy są zgodne ze sobą, a numery wierszy ułatwiają znalezienie kodu później. Możesz wybrać małe, opakowane znaki minus, aby zwinąć lub rozwinąć bloki kodu. Ta funkcja tworzenia konspektu kodu umożliwia ukrycie kodu, który nie jest potrzebny, pomagając na zminimalizowanie bałaganu na ekranie. Pliki projektu są wymienione po prawej stronie w oknie o nazwie **Eksplorator rozwiązań**.

   ![Środowisko IDE programu Visual Studio z czerwonymi polami](media/overview-ide-console-app-red-boxes.png)

   Dostępne są inne menu i okna narzędzi, ale teraz przyjrzyjmy się.

1. Teraz uruchom aplikację. Można to zrobić, wybierając pozycję **Uruchom bez debugowania** z menu **Debuguj** na pasku menu. Możesz również nacisnąć klawisz **Ctrl** + **F5**.

   ![Debuguj > Rozpocznij bez debugowania menu](media/vs-2019/start-without-debugging.png)

   Program Visual Studio kompiluje aplikację i zostanie otwarte okno konsoli z komunikatem **Hello World!**. Masz teraz działającą aplikację.

   ![Zrzut ekranu przedstawiający okno konsoli z komunikatem Hello world.](../media/vs-2019/overview-console-window.png)

1. Aby zamknąć okno konsoli, naciśnij dowolny klawisz na klawiaturze.

1. Dodajmy do aplikacji dodatkowy kod. Dodaj następujący kod Visual Basic przed wierszem, który brzmi `Console.WriteLine("Hello World!")` :

   ```vb
   Console.WriteLine("What is your name?")
   Dim name = Console.ReadLine()
   ```

   Ten kod wyświetla **nazwę użytkownika** w oknie konsoli, a następnie czeka, aż użytkownik wprowadzi jakiś tekst, a następnie klawisz **Enter** .

1. Zmień wiersz wyświetlany w `Console.WriteLine("Hello World!")` następującym kodzie:

   ```vb
   Console.WriteLine("Hello " + name + "!")
   ```

1. Uruchom aplikację ponownie, naciskając klawisz **Ctrl** + **F5**.

   Program Visual Studio ponownie kompiluje aplikację i zostanie otwarte okno konsoli z prośbą o wprowadzenie nazwy.

1. Wprowadź swoją nazwę w oknie konsoli i naciśnij klawisz **Enter**.

   ![Zrzut ekranu przedstawiający okno konsoli z pytaniami dotyczącymi Twojej nazwy i odpowiedzi aplikacji.](../media/vs-2019/overview-console-input.png)

1. Naciśnij dowolny klawisz, aby zamknąć okno konsoli i zatrzymać uruchomiony program.

::: moniker-end

## <a name="use-refactoring-and-intellisense"></a>Używanie refaktoryzacji i technologii IntelliSense

Przyjrzyjmy się kilku sposobom, które [Refaktoryzacja](../../ide/refactoring-in-visual-studio.md) i [technologia IntelliSense](../../ide/using-intellisense.md) mogą pomóc w bardziej wydajnym kodzie.

Najpierw Zmień nazwę `name` zmiennej:

1. Kliknij dwukrotnie zmienną, `name` Aby ją zaznaczyć.

2. Wpisz nową nazwę zmiennej, **username**.

   Zauważ, że wokół zmiennej pojawia się szare pole, a żarówka pojawia się na marginesie.

3. Wybierz ikonę żarówki, aby wyświetlić dostępne [szybkie akcje](../../ide/quick-actions.md). Wybierz pozycję **Zmień nazwę na "username"**.

   ![Zmień nazwę akcji w programie Visual Studio](media/rename-quick-action.png)

   Zmienna została zmieniona na projekt, który w naszym przypadku ma tylko dwa miejsca.

4. Teraz przyjrzyjmy się technologii IntelliSense. Poniżej wiersza, który brzmi `Console.WriteLine("Hello " + username + "!")` , wpisz następujący fragment kodu:

    ```vb
   Dim now = Date.
   ```

   W polu są wyświetlane elementy członkowskie <xref:System.DateTime> klasy. Ponadto w osobnym polu jest wyświetlany opis aktualnie wybranego elementu członkowskiego.

   ![Elementy członkowskie listy IntelliSense w programie Visual Studio](media/intellisense-list-members.png)

5. Wybierz element członkowski o nazwie **Now**, który jest właściwością klasy, klikając ją dwukrotnie lub wybierając ją przy użyciu klawiszy strzałek w górę lub w dół, a następnie naciskając klawisz **Tab**.

6. Poniżej wpisz lub Wklej następujące wiersze kodu:

   ```vb
   Dim dayOfYear = now.DayOfYear
   Console.Write("Day of year: ")
   Console.WriteLine(dayOfYear)
   ```

   > [!TIP]
   > <xref:System.Console.Write%2A?displayProperty=nameWithType> jest nieco inna dla <xref:System.Console.WriteLine%2A?displayProperty=nameWithType> programu, ponieważ nie dodaje terminatora wiersza po wydrukowaniu. Oznacza to, że Następny fragment tekstu, który jest wysyłany do danych wyjściowych, będzie drukowany w tym samym wierszu. Możesz umieścić wskaźnik myszy nad każdą z tych metod w kodzie, aby zobaczyć ich opis.

7. Następnie użyjemy ponownie refaktoryzacji, aby kod był nieco bardziej zwięzły. Kliknij zmienną `now` w wierszu `Dim now = Date.Now` .

   Zauważ, że na marginesie w tym wierszu pojawia się ikona małego śrubokrętu.

8. Kliknij ikonę śrubokrętu, aby zobaczyć, jakie sugestie są dostępne dla programu Visual Studio. W tym przypadku jest wyświetlana [wbudowana zmienna tymczasowa](../../ide/reference/inline-temporary-variable.md) Refaktoryzacja w celu usunięcia wiersza kodu bez zmiany ogólnego zachowania kodu:

   ![Refaktoryzacja wbudowanej zmiennej tymczasowej w programie Visual Studio](media/inline-temporary-variable-refactoring.png)

9. Kliknij przycisk **wbudowana zmienna tymczasowa** , aby refaktoryzacji kodu.

::: moniker range="vs-2017"

10. Ponownie uruchom program, naciskając klawisz **Ctrl** + **F5**. Dane wyjściowe wyglądają następująco:

    ![Okno konsoli z danymi wyjściowymi programu](../media/overview-console-final.png)

::: moniker-end

::: moniker range=">=vs-2019"

10. Ponownie uruchom program, naciskając klawisz **Ctrl** + **F5**. Dane wyjściowe wyglądają następująco:

    ![Okno konsoli z danymi wyjściowymi programu](../media/vs-2019/overview-console-final.png)

::: moniker-end

## <a name="debug-code"></a>Debugowanie kodu

Podczas pisania kodu należy go uruchomić i przetestować pod kątem błędów. System debugowania programu Visual Studio umożliwia przechodzenie przez kod jednej instrukcji w czasie i sprawdzanie zmiennych w miarę rzeczywistym. Można ustawić *punkty przerwania* , które zatrzymują wykonywanie kodu w konkretnym wierszu. Można obserwować, jak zmienia się wartość zmiennej w miarę uruchamiania kodu i nie tylko.

Ustaw teraz punkt przerwania, aby zobaczyć wartość zmiennej, `username` gdy program jest "w locie".

1. Znajdź wiersz kodu, który jest wyświetlany `Console.WriteLine("Hello " + username + "!")` . Aby ustawić punkt przerwania w tym wierszu kodu, czyli w celu wstrzymania wykonywania programu w tym wierszu, kliknij górny lewy margines edytora. Możesz również kliknąć dowolne miejsce w wierszu kodu, a następnie nacisnąć klawisz **F9**.

   Czerwony okrąg pojawia się na marginesie po lewej stronie, a kod zostanie wyróżniony kolorem czerwonym.

   ![Punkt przerwania w wierszu kodu w programie Visual Studio](media/breakpoint.png)

1. Rozpocznij debugowanie, wybierając **Debuguj**  >  **Rozpocznij debugowanie** lub naciskając klawisz **F5**.

1. Gdy zostanie wyświetlone okno konsoli i zostanie wyświetlony monit o podanie nazwy, wpisz ją w i naciśnij klawisz **Enter**.

   Fokus wraca do edytora kodu programu Visual Studio, a wiersz kodu z punktem przerwania zostanie wyróżniony kolorem żółtym. Oznacza to, że jest to kolejny wiersz kodu, który zostanie wykonany przez program.

1. Przesuń wskaźnik myszy nad `username` zmienną, aby zobaczyć jej wartość. Alternatywnie możesz kliknąć prawym przyciskiem myszy `username` i wybrać polecenie **Dodaj czujkę** , aby dodać zmienną do okna **czujki** , gdzie można także zobaczyć jego wartość.

   ![Wartość zmiennej podczas debugowania w programie Visual Studio](media/debugging-variable-value.png)

1. Aby pozwolić programowi na zakończenie pracy, naciśnij ponownie klawisz **F5** .

Aby uzyskać więcej informacji na temat debugowania w programie Visual Studio, zobacz [Przewodnik po funkcjach debugera](../../debugger/debugger-feature-tour.md).

## <a name="next-steps"></a>Następne kroki

Poznanie programu Visual Studio w następujący sposób wraz z jednym z następujących artykułów wprowadzających:

> [!div class="nextstepaction"]
> [Dowiedz się, jak używać edytora kodu](tutorial-editor.md)

> [!div class="nextstepaction"]
> [Informacje o projektach i rozwiązaniach](tutorial-projects-solutions.md)

## <a name="see-also"></a>Zobacz też

- Odkryj [więcej funkcji programu Visual Studio](../../ide/advanced-feature-overview.md)
- Odwiedź witrynę [VisualStudio.Microsoft.com](https://visualstudio.microsoft.com/vs/)
- Przeczytaj [Blog programu Visual Studio](https://devblogs.microsoft.com/visualstudio/)
