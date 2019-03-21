---
title: Omówienie dla deweloperów programu Visual Basic
ms.date: 11/15/2018
ms.technology: vs-ide-general
ms.custom: get-started
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 2bba6a290e8d34b2f809916341e9258ae5d36fa9
ms.sourcegitcommit: 3d37c2460584f6c61769be70ef29c1a67397cf14
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/21/2019
ms.locfileid: "58324084"
---
# <a name="welcome-to-the-visual-studio-ide--visual-basic"></a>Witamy w środowisku IDE programu Visual Studio | Visual Basic

Visual Studio *zintegrowanego środowiska programistycznego* to twórczych Konsola uruchamianie służy do edytowania, debugowania i kompilowanie kodu, a następnie opublikować aplikację. Zintegrowanym środowisku programistycznym (IDE) to program bogate, który może służyć do wielu aspektów programowania. Podniesienia standardowy edytor i debugera, większości środowisk IDE podać, program Visual Studio obejmuje kompilatory, narzędzia uzupełniania kodu, projektanci graficzni i wiele innych funkcji, do jej obsługi ułatwiają realizację procesu tworzenia oprogramowania.

::: moniker range="vs-2017"

![Visual Studio IDE](../media/visual-studio-ide.png)

::: moniker-end

::: moniker range=">=vs-2019"

[![](media/vs-2019/ide-overview.png "Visual Studio IDE")](media/vs-2019/ide-overview.png#lightbox)

::: moniker-end

Ten obraz pokazuje programu Visual Studio Otwórz projekt i kilka okien narzędzi klucza, które będą prawdopodobnie używane:

- [Eksplorator rozwiązań](../../ide/solutions-and-projects-in-visual-studio.md) (prawym górnym rogu) umożliwia wyświetlanie, przejść i zarządzanie plikami kodu. **Eksplorator rozwiązań** ułatwiają organizowanie kodu za pomocą tych plików do grupowania [rozwiązania i projekty](tutorial-projects-solutions.md).

- [Okna edytora](../../ide/writing-code-in-the-code-and-text-editor.md) (center), gdzie prawdopodobnie spędzisz większość czasu, wyświetla zawartość pliku. Jest to, który umożliwia edytowanie kodu lub projektować interfejs użytkownika, takie jak okna przy użyciu przycisków i pola tekstowe.

- [Okno danych wyjściowych](../../ide/reference/output-window.md) (na dole na środku) jest, gdzie Visual Studio wysyła powiadomienia, takich jak debugowanie i komunikaty o błędach, ostrzeżenia kompilatora, publikowania komunikatów o stanie i inne. Każde źródło komunikatu ma osobnej karcie.

- [Team Explorer](/azure/devops/user-guide/work-team-explorer?view=vsts) (prawy dolny róg) umożliwia śledzenie elementów roboczych i udostępnianie kodu z innymi osobami przy użyciu technologii kontroli wersji, takich jak [Git](https://git-scm.com/) i [Team Foundation Version Control (TFVC)](/azure/devops/repos/tfvc/overview?view=vsts).

## <a name="editions"></a>Wersje

Program Visual Studio jest dostępna dla Windows i Mac. [Program Visual Studio for Mac](/visualstudio/mac/) zawiera wiele same funkcje co program Visual Studio 2017 i jest zoptymalizowany pod kątem tworzenia aplikacji dla wielu platform i na urządzeniach przenośnych. Ten artykuł dotyczy programu Visual Studio 2017 w wersji Windows.

Istnieją trzy wersje programu Visual Studio 2017: Community, Professional i Enterprise. Zobacz [porównanie programu Visual Studio 2017 IDE](https://visualstudio.microsoft.com/vs/compare/) Aby dowiedzieć się więcej o funkcji, które są obsługiwane w poszczególnych wydaniach.

## <a name="popular-productivity-features"></a>Funkcje zwiększające produktywność popularne funkcje

Oto niektóre z najpopularniejszych funkcji w programie Visual Studio, które ułatwiają mu bardziej wydajnej pracy, podczas opracowywania oprogramowania:

- Zygzaki i [szybkie akcje](../../ide/quick-actions.md)

   Zygzaki są faliste linie, które alertów dotyczących błędów lub potencjalnych problemów w kodzie podczas wpisywania. Te wskazówki visual umożliwiają rozwiązywanie problemów z natychmiast bez oczekiwania na błąd, które mają zostać odnalezione, podczas kompilacji lub po uruchomieniu programu. Po umieszczeniu wskaźnika myszy nad wężyk, zobaczysz dodatkowe informacje o tym błędzie. Żarówka może również wystąpić na lewym marginesie z akcjami, znane jako szybkich akcji, aby naprawić błąd.

   ::: moniker range="vs-2017"

   ![Faliste linie w programie Visual Studio](media/squiggles-error.png)

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   ![Faliste linie w programie Visual Studio](media/vs-2019/squiggles-error.png)

   ::: moniker-end

- [Refaktoryzacja](../../ide/refactoring-in-visual-studio.md)

   Refaktoryzacja obejmuje operacje, takie jak inteligentne zmiana nazwy zmiennych, wyodrębnianie jeden lub więcej wierszy kodu do nowej metody zmiany kolejności parametrów metod i inne.

   ::: moniker range="vs-2017"

   ![Refaktoryzacja menu w programie Visual Studio](media/refactoring-menu.png)

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   ![Refaktoryzacja menu w programie Visual Studio](media/vs-2019/refactorings-menu.png)

   ::: moniker-end

- [Funkcja IntelliSense](../../ide/using-intellisense.md)

   Funkcja IntelliSense jest okres zestaw funkcji, który wyświetla informacje o kodzie bezpośrednio w edytorze, a w niektórych przypadkach zapisu małe fragmenty kodu dla Ciebie. To, jak podstawowa dokumentacja wbudowanego w edytorze, co pozwala uniknąć konieczności wyszukiwania informacji o typie w innym miejscu. Funkcje IntelliSense, zależy od języka. Aby uzyskać więcej informacji, zobacz [IntelliSense w języku C#](../../ide/visual-csharp-intellisense.md), [Visual C++ IntelliSense](../../ide/visual-cpp-intellisense.md), [JavaScript IntelliSense](../../ide/javascript-intellisense.md), i [Visual Basic IntelliSense](../../ide/visual-basic-specific-intellisense.md). Na poniższej ilustracji przedstawiono, jak technologia IntelliSense wyświetla listę elementu członkowskiego dla typu:

   ::: moniker range="vs-2017"

   ![Lista elementów członkowskich programu Visual Studio](media/intellisense-list-members.png)

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   ![Lista elementów członkowskich programu Visual Studio](media/vs-2019/intellisense-list-members.png)

   ::: moniker-end

- [Szybkie uruchamianie](../../ide/reference/quick-launch-environment-options-dialog-box.md)

   Program Visual Studio może wydawać się trudne w czasie za pomocą menu tak wiele, opcje i właściwości. **Szybkie uruchamianie** pole wyszukiwania jest doskonałym sposobem na szybkie znajdowanie potrzebnej w programie Visual Studio. Po uruchomieniu, wpisując nazwę coś, czego szukasz, program Visual Studio wyświetla wyniki, które przyjmują dokładnie miejscu należy przejść. Jeśli chcesz dodać funkcje do programu Visual Studio, na przykład aby dodać obsługę dodatkowych języka programowania, **Szybkie uruchamianie** zapewnia wyniki, które Otwórz Instalator programu Visual Studio do zainstalowania obciążeń lub poszczególnych składników.

   > [!TIP]
   > Naciśnij klawisz **Ctrl**+**Q** jako skrót do **Szybkie uruchamianie** pola wyszukiwania.

   ::: moniker range="vs-2017"

   ![Szybkie uruchamianie pola wyszukiwania w programie Visual Studio 2017](../media/quick-launch-nuget.png)

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   ![Szybkiego uruchamiania pola wyszukiwania w programie Visual Studio 2019 r.](media/vs-2019/quick-launch.png)

   ::: moniker-end

- [Udostępnianie na żywo](/visualstudio/liveshare/)

   Zespołowe przeprowadzanie edytowania i debugowania z innymi osobami w czasie rzeczywistym, niezależnie od tego, jakie usługi typu aplikacji lub języka programowania. Szybko i bezpiecznie Udostępnij swój projekt, a następnie zgodnie z potrzebami, w sesji debugowania terminalu przypadkach localhost sieci web, aplikacje, połączenia głosowe i inne.

- [Hierarchia wywołań](../../ide/reference/call-hierarchy.md)

   **Hierarchię wywołań** okno zawiera metody, które wywołują wybranej metody. Może to być przydatne informacje, jeśli myślisz o zmienić lub usunąć metodę lub podczas próby znalezienia błędu.

   ::: moniker range="vs-2017"

   ![Okno hierarchii wywołań w programie Visual Studio](media/call-hierarchy.png)

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   ![Okno hierarchii wywołań w programie Visual Studio](media/vs-2019/call-hierarchy.png)

   ::: moniker-end

- [Funkcja CodeLens](../../ide/find-code-changes-and-other-history-with-codelens.md)

   Funkcja CodeLens pomoże Ci znaleźć odwołania do kodu, zmiany kodu, połączone usterki, elementy robocze, przeglądy kodu i testów jednostkowych, wszystko to bez zamykania edytora.

   ::: moniker range="vs-2017"

   ![Funkcja CodeLens w programie Visual Studio](media/codelens.png)

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   ![Funkcja CodeLens w programie Visual Studio](media/vs-2019/codelens.png)

   ::: moniker-end

- [Przejdź do definicji](../../ide/go-to-and-peek-definition.md)

   Funkcja przejdź do definicji umożliwia przejście bezpośrednio do lokalizacji, w którym funkcja lub typ jest zdefiniowany.

   ::: moniker range="vs-2017"

   ![Przejdź do definicji w programie Visual Studio 2017](media/go-to-definition-menu.png)

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   ![Przejdź do definicji w programie Visual Studio 2019 r.](media/vs-2019/go-to-definition-menu.png)

   ::: moniker-end

- [Zobacz definicję](../../ide/how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12.md)

   **Peek Definition** okno zawiera definicję metody lub typu, bez konieczności otwierania pliku.

   ::: moniker range="vs-2017"

   ![Zobacz definicję w programie Visual Studio](media/peek-definition.png)

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   ![Zobacz definicję w programie Visual Studio](media/vs-2019/peek-definition.png)

   ::: moniker-end

## <a name="install-the-visual-studio-ide"></a>Zainstaluj program Visual Studio IDE

W tej sekcji utworzysz prosty projekt, aby wypróbować kilka rzeczy, które można wykonać za pomocą programu Visual Studio. Będzie zmienić motyw kolorów, użyj [IntelliSense](../../ide/using-intellisense.md) jak kodowanie pomocy i Debuguj aplikację, aby wyświetlić wartość zmiennej podczas wykonywania programu.

::: moniker range="vs-2017"

Aby rozpocząć pracę, [Pobierz program Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) i zainstaluj go na system. Instalator modułowej umożliwia wybierz i zainstaluj *obciążeń*, służą do grup funkcje potrzebne do programowania języka lub platformy, użytkownik sobie tego życzy. Wykonaj kroki dla [tworzenie programu](#create-a-program), pamiętaj o wybraniu **programowanie dla wielu platform .NET Core** obciążenie podczas instalacji.

::: moniker-end

::: moniker range=">=vs-2019"

Aby rozpocząć pracę, [Pobierz program Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) i zainstaluj go na system. Instalator modułowej umożliwia wybierz i zainstaluj *obciążeń*, służą do grup funkcje potrzebne do programowania języka lub platformy, użytkownik sobie tego życzy. Wykonaj kroki dla [tworzenie programu](#create-a-program), pamiętaj o wybraniu **programowanie dla wielu platform .NET Core** obciążenie podczas instalacji.

::: moniker-end

![Obciążenia programowanie dla wielu platform .NET core w Instalatorze programu Visual Studio](../media/dotnet-core-cross-platform-workload.png)

Po otwarciu programu Visual Studio po raz pierwszy, można opcjonalnie [Zaloguj](../../ide/signing-in-to-visual-studio.md) przy użyciu swojego konta Microsoft albo konta służbowego lub szkolnego.

## <a name="customize-visual-studio"></a>Dostosuj program Visual Studio

Możesz dostosować interfejsu użytkownika programu Visual Studio, w tym zmiany domyślnego motywu kolorów.

### <a name="change-the-color-theme"></a>Zmień motyw kolorów

Aby zmienić **ciemny** motywu:

::: moniker range="vs-2017"

1. Otwórz program Visual Studio.

::: moniker-end

::: moniker range=">=vs-2019"

1. Otwórz program Visual Studio. W oknie rozpoczęcia wybierz **Kontynuuj bez konieczności pisania kodu**.

   ![Okno uruchamiania w programie Visual Studio 2019 r.](media/vs-2019/continue-without-code.png)

   Otwiera IDE.

::: moniker-end

2. Na pasku menu wybierz **narzędzia** > **opcje** otworzyć **opcje** okna dialogowego.

3. Na **środowiska** > **ogólne** Strona opcji, zmień **motyw kolorów** wyboru, aby **ciemny**, a następnie wybierz pozycję **OK**.

   ![Zmień motyw kolorów na ciemny w programie Visual Studio](media/change-color-theme.png)

   Motyw kolorów dla całej IDE zmieni się na **ciemny**.

   ::: moniker range="vs-2017"

   ![Visual Studio z motywu ciemny](../../ide/media/quickstart-personalize-dark-theme.png)

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   ![Visual Studio z motywu ciemny](media/vs-2019/dark-theme.png)

   ::: moniker-end

### <a name="select-environment-settings"></a>Wybierz ustawienia środowiska

Następnie skonfigurujemy Visual Studio, aby użyć ustawienia środowiska dostosowane do deweloperów programu Visual Basic.

1. Na pasku menu wybierz **narzędzia** > **Import i eksport ustawień**.

2. W **Kreatora importowania i eksportowania ustawień**, wybierz opcję **Resetuj wszystkie ustawienia** na pierwszej stronie, a następnie wybierz **dalej**.

3. Na **zapisać bieżące ustawienia** stronie, wybierz opcję, aby zapisać bieżące ustawienia lub nie, a następnie wybierz **dalej**. (Jeśli nie zostały dostosowane ustawienia, wybierz opcję **nie, tylko Zresetuj ustawienia, zastępując Moje bieżące ustawienia**.)

4. Na **wybierz domyślnej kolekcji ustawień** wybierz **języka Visual Basic**, a następnie wybierz **Zakończ**.

5. Na **resetowania pełną** wybierz **Zamknij**.

Aby dowiedzieć się więcej o innych metodach, które można spersonalizować środowisko IDE, zobacz [Personalizowanie programu Visual Studio](../../ide/personalizing-the-visual-studio-ide.md).

## <a name="create-a-program"></a>Utwórz program

Przyjrzyjmy się temu bliżej i Utwórz prosty program.

::: moniker range="vs-2017"

1. Na pasku menu programu Visual Studio, wybierz **pliku** > **nowy projekt**.

   ![Plik > Nowy projekt na pasku menu](media/file-new-project-menu.png)

   **Nowy projekt** okno dialogowe zawiera kilka projektu *szablony*. Szablon zawiera podstawowe pliki i ustawienia wymagane dla typu danego projektu.

1. Wybierz **platformy .NET Core** kategorię w obszarze **języka Visual Basic**, a następnie wybierz **Aplikacja konsoli (.NET Core)** szablonu. W **nazwa** polu tekstowym **HelloWorld**, a następnie wybierz pozycję **OK** przycisku.

   ![Szablon aplikacji .NET core](media/overview-npd.png)

   > [!NOTE]
   > Jeśli nie widzisz **platformy .NET Core** kategorii, musisz zainstalować **programowanie dla wielu platform .NET Core** obciążenia. Aby to zrobić, wybierz **Otwórz Instalator programu Visual Studio** łącza w lewym dolnym rogu **nowy projekt** okna dialogowego. Po otwarciu Instalatora programu Visual Studio, przewiń w dół i wybierz **programowanie dla wielu platform .NET Core** obciążenia, a następnie wybierz **Modyfikuj**.

   Program Visual Studio tworzy projekt. Jest prostą aplikację "Hello World", która wywołuje <xref:System.Console.WriteLine?displayProperty=nameWithType> metodę w celu wyświetlenia literału ciągu "Hello World!" w oknie konsoli (dane wyjściowe programu).

   Wkrótce powinny zostać wyświetlone, podobny do poniższego:

   ![Visual Studio IDE](media/overview-ide-console-app.png)

   Kod Visual Basic dla aplikacji zostanie wyświetlony w oknie edytora, która zajmuje większość miejsca. Należy zauważyć, że tekst jest automatycznie w trybie kolorowym do wskazania różnych części kodu, takich jak słów kluczowych i typów. Ponadto małe, pionowe linie przerywane, w kodzie wskazują, które nawiasy klamrowe zgodne siebie nawzajem, a później zlokalizować kod pomocy numery wierszy. Możesz wybrać znaków minus małe, spakowany, aby zwinąć lub rozwinąć bloków kodu. Ten kod funkcji konspektu można ukrywać kod, który nie jest konieczne, pozwala zminimalizować bałaganu na ekranie. Pliki projektu są wyświetlane po prawej stronie w oknie o nazwie **Eksploratora rozwiązań**.

   ![Visual Studio IDE z czerwone pola](media/overview-ide-console-app-red-boxes.png)

   Brak dostępnych inne menu i okien narzędzi, ale Przejdźmy teraz.

1. Teraz uruchom aplikację. Można to zrobić, wybierając **Rozpocznij bez debugowania** z **debugowania** menu na pasku menu. Można również nacisnąć klawisz **Ctrl**+**F5**.

   ![Debuguj > Uruchom bez debugowania menu](../media/overview-start-without-debugging.png)

   Program Visual Studio tworzy aplikację, a komunikat zostanie otwarte okno konsoli **Hello World!**. Masz teraz uruchomionej aplikacji.

   ![Okno konsoli](../media/overview-console-window.png)

1. Aby zamknąć okno konsoli, naciśnij dowolny klawisz na klawiaturze.

1. Dodajmy dodatkowy kod do aplikacji. Dodaj następujący kod języka Visual Basic przed wierszem, który jest wyświetlany komunikat `Console.WriteLine("Hello World!")`:

   ```vb
   Console.WriteLine("What is your name?")
   Dim name = Console.ReadLine()
   ```

   Ten kod wyświetla **jak się Nazywasz?** w oknie konsoli, a następnie czeka, aż użytkownik wprowadza jakiś tekst, a następnie **Enter** klucza.

1. Zmień wiersz, który jest wyświetlany komunikat `Console.WriteLine("Hello World!")` z następującym kodem:

   ```vb
   Console.WriteLine("Hello " + name + "!")
   ```

1. Ponownie uruchom aplikację, naciskając klawisz **Ctrl**+**F5**.

   Program Visual Studio ponownie kompiluje aplikację, a okno konsoli otworzy i wyświetli monit o podanie nazwy.

1. Wprowadź nazwę w oknie konsoli, a następnie naciśnij klawisz **Enter**.

   ![Dane wejściowe z okna konsoli](../media/overview-console-input.png)

1. Naciśnij dowolny klawisz, aby zamknąć okno konsoli i zatrzymać uruchomionego programu.

::: moniker-end

::: moniker range=">=vs-2019"

1. Na pasku menu programu Visual Studio, wybierz **pliku** > **nowy projekt**.

   ![Plik > Nowy projekt na pasku menu](media/vs-2019/file-new-project.png)

   **Utwórz nowy projekt** okna otwiera i pokazuje kilka projektów *szablony*. Szablon zawiera podstawowe pliki i ustawienia wymagane dla typu danego projektu.

1. Aby znaleźć szablonu firma Microsoft, wpisz lub wprowadź **konsolowa .net core** w polu wyszukiwania. Lista dostępnych szablonów jest automatycznie filtrowany według słów kluczowych, wprowadzony. Rezultaty szablonu można dalej filtrować, wybierając **języka Visual Basic** z **języka** listy rozwijanej.

1. Wybierz **Aplikacja konsoli (.NET Core)** szablonu, a następnie wybierz **dalej**.

   ![Utwórz nowy projekt w programie Visual Studio](media/vs-2019/create-new-project.png)

1. W **konfigurowania nowego projektu** oknie wprowadź **HelloWorld** w **Nazwa projektu** opcjonalnie Zmień lokalizację plików projektu, a następnie Wybierz **Utwórz**.

   ![Skonfiguruj nowy projekt w programie Visual Studio](media/vs-2019/configure-new-project.png)

   Program Visual Studio tworzy projekt. Jest prostą aplikację "Hello World", która wywołuje <xref:System.Console.WriteLine?displayProperty=nameWithType> metodę w celu wyświetlenia literału ciągu "Hello World!" w oknie konsoli (dane wyjściowe programu).

   Wkrótce powinny zostać wyświetlone, podobny do poniższego:

   ![Visual Studio IDE](media/overview-ide-console-app.png)

   Kod Visual Basic dla aplikacji zostanie wyświetlony w oknie edytora, która zajmuje większość miejsca. Należy zauważyć, że tekst jest automatycznie w trybie kolorowym do wskazania różnych części kodu, takich jak słów kluczowych i typów. Ponadto małe, pionowe linie przerywane, w kodzie wskazują, które nawiasy klamrowe zgodne siebie nawzajem, a później zlokalizować kod pomocy numery wierszy. Możesz wybrać znaków minus małe, spakowany, aby zwinąć lub rozwinąć bloków kodu. Ten kod funkcji konspektu można ukrywać kod, który nie jest konieczne, pozwala zminimalizować bałaganu na ekranie. Pliki projektu są wyświetlane po prawej stronie w oknie o nazwie **Eksploratora rozwiązań**.

   ![Visual Studio IDE z czerwone pola](media/overview-ide-console-app-red-boxes.png)

   Brak dostępnych inne menu i okien narzędzi, ale Przejdźmy teraz.

1. Teraz uruchom aplikację. Można to zrobić, wybierając **Rozpocznij bez debugowania** z **debugowania** menu na pasku menu. Można również nacisnąć klawisz **Ctrl**+**F5**.

   ![Debuguj > Uruchom bez debugowania menu](media/vs-2019/start-without-debugging.png)

   Program Visual Studio tworzy aplikację, a komunikat zostanie otwarte okno konsoli **Hello World!**. Masz teraz uruchomionej aplikacji.

   ![Okno konsoli](../media/vs-2019/overview-console-window.png)

1. Aby zamknąć okno konsoli, naciśnij dowolny klawisz na klawiaturze.

1. Dodajmy dodatkowy kod do aplikacji. Dodaj następujący kod języka Visual Basic przed wierszem, który jest wyświetlany komunikat `Console.WriteLine("Hello World!")`:

   ```vb
   Console.WriteLine("What is your name?")
   Dim name = Console.ReadLine()
   ```

   Ten kod wyświetla **jak się Nazywasz?** w oknie konsoli, a następnie czeka, aż użytkownik wprowadza jakiś tekst, a następnie **Enter** klucza.

1. Zmień wiersz, który jest wyświetlany komunikat `Console.WriteLine("Hello World!")` z następującym kodem:

   ```vb
   Console.WriteLine("Hello " + name + "!")
   ```

1. Ponownie uruchom aplikację, naciskając klawisz **Ctrl**+**F5**.

   Program Visual Studio ponownie kompiluje aplikację, a okno konsoli otworzy i wyświetli monit o podanie nazwy.

1. Wprowadź nazwę w oknie konsoli, a następnie naciśnij klawisz **Enter**.

   ![Okno konsoli](../media/vs-2019/overview-console-input.png)

1. Naciśnij dowolny klawisz, aby zamknąć okno konsoli i zatrzymać uruchomionego programu.

::: moniker-end

## <a name="use-refactoring-and-intellisense"></a>Refaktoryzacja i technologii IntelliSense

Spójrzmy na kilka sposobów, [refaktoryzacji](../../ide/refactoring-in-visual-studio.md) i [IntelliSense](../../ide/using-intellisense.md) może pomóc w bardziej efektywnie kodu.

Po pierwsze możemy zmienić nazwę `name` zmiennej:

1. Kliknij dwukrotnie `name` zmiennej, aby go zaznaczyć.

2. Wpisz nową nazwę zmiennej, **username**.

   Należy zauważyć, że szare pole pojawia się wokół zmienną i żarówka pojawia się na marginesie.

3. Wybierz ikonę żarówki, aby wyświetlić dostępnych [szybkie akcje](../../ide/quick-actions.md). Wybierz **Zmień nazwę "name" do "username"**.

   ![Zmień nazwę akcji w programie Visual Studio](media/rename-quick-action.png)

   Zmienna została zmieniona w projekcie, czyli w tym przypadku tylko dwa miejsca.

4. Teraz Przyjrzyjmy się w technologii IntelliSense. Poniżej wiersza, który jest wyświetlany komunikat `Console.WriteLine("Hello " + username + "!")`, wpisz poniższy fragment kodu:

    ```vb
   Dim now = Date.
   ```

   Wyświetlone elementy członkowskie <xref:System.DateTime> klasy. Ponadto opis aktualnie zaznaczonego elementu członkowskiego, wyświetla się w osobnym oknie.

   ![Funkcja IntelliSense członków listy w programie Visual Studio](media/intellisense-list-members.png)

5. Wybierz element członkowski o nazwie **teraz**, który jest właściwością klasy, klikając dwukrotnie na nim lub wybierając go za pomocą w górę lub w dół klawiszy strzałek, a następnie naciskając klawisz **kartę**.

6. Poniżej wpisz lub wklej następujące wiersze kodu:

   ```vb
   Dim dayOfYear = now.DayOfYear
   Console.Write("Day of year: ")
   Console.WriteLine(dayOfYear)
   ```

   > [!TIP]
   > <xref:System.Console.Write%2A?displayProperty=nameWithType> różni się nieco się <xref:System.Console.WriteLine%2A?displayProperty=nameWithType> się po wydrukowaniu terminator wiersza nie jest dodawany. Oznacza to, że w następnej części tekst, który jest wysyłany do danych wyjściowych zostanie wydrukowany na tym samym wierszu. Możesz umieścić kursor każda z tych metod w kodzie, aby wyświetlić jego opis.

7. Następnie użyjemy refaktoryzacji ponownie się nieco bardziej zwięzły widok kodu. Kliknij na zmiennej `now` w wierszu `Dim now = Date.Now`.

   Należy zauważyć, że mała ikona śrubokręt pojawia się na marginesie w danym wierszu.

8. Kliknij ikonę śrubokręt, aby zobaczyć, jakie sugestie dotyczące programu Visual Studio jest dostępny. W tym przypadku jest wyświetlane [wstawiona zmienna tymczasowa](../../ide/reference/inline-temporary-variable.md) refaktoryzacji, aby usunąć wiersz kodu bez wprowadzania zmian w ogólnym zachowaniom kodu:

   ![Wbudowane tymczasowej zmiennej Refaktoryzacja w programie Visual Studio](media/inline-temporary-variable-refactoring.png)

9. Kliknij przycisk **wstawiona zmienna tymczasowa** Refaktoryzacja kodu.

::: moniker range="vs-2017"

10. Uruchom program ponownie, naciskając klawisz **Ctrl**+**F5**. Dane wyjściowe wyglądają następująco:

    ![Okno konsoli z danych wyjściowych programu](../media/overview-console-final.png)

::: moniker-end

::: moniker range=">=vs-2019"

10. Uruchom program ponownie, naciskając klawisz **Ctrl**+**F5**. Dane wyjściowe wyglądają następująco:

    ![Okno konsoli z danych wyjściowych programu](../media/vs-2019/overview-console-final.png)

::: moniker-end

## <a name="debug-code"></a>Możliwe jest debugowanie kodu

Podczas pisania kodu, musisz go uruchomić i przetestować go dla błędów. System debugowania programu Visual Studio pozwala krokowo jedną instrukcję kodu w czasie, aby zbadać zmienne, zgodnie z rzeczywistym. Możesz ustawić *punktów przerwania* , Zatrzymaj wykonywanie kodu w określonej linii. Można zaobserwować, jak wartości zmiennych zmian jako kod jest wykonywany i nie tylko.

Teraz Ustaw punkt przerwania, aby zobaczyć wartość `username` zmiennej, podczas gdy program jest "w locie".

1. Znajdź wiersz kodu, który jest wyświetlany komunikat `Console.WriteLine("Hello " + username + "!")`. Aby ustawić punkt przerwania w tym wierszu kodu, oznacza to, aby program wstrzymać wykonanie w tym wierszu kliknij na marginesie po lewej stronie edytora. Możesz również kliknąć dowolne miejsce na wiersz kodu, a następnie naciśnij klawisz **F9**.

   Czerwony okrąg pojawia się na marginesie po lewej stronie, a kod zostanie wyróżniony czerwonym kolorem.

   ![Punkt przerwania w wierszu kodu w programie Visual Studio](media/breakpoint.png)

1. Rozpocznij debugowanie wybierając **debugowania** > **Rozpocznij debugowanie** lub naciskając **F5**.

1. W oknie konsoli zostanie wyświetlony i poprosi o podanie nazwy użytkownika, wpisz go w i naciśnij klawisz **Enter**.

   Powrót do edytora kodu programu Visual Studio oraz wiersza kodu, punkt przerwania jest wyróżniony na żółto. Oznacza to, że jest następnego wiersza kodu, które spowodują wykonanie programu.

1. Umieść kursor myszy nad `username` zmiennej, aby zobaczyć jej wartość. Alternatywnie możesz kliknąć prawym przyciskiem myszy na `username` i wybierz **Dodaj czujkę** można dodać zmienną **Obejrzyj** okna, w którym widać również jego wartość.

   ![Wartość zmiennej podczas debugowania w programie Visual Studio](media/debugging-variable-value.png)

1. Aby umożliwić programu zostało ukończone, naciśnij klawisz **F5** ponownie.

Aby uzyskać więcej informacji o debugowaniu w programie Visual Studio, zobacz [Przewodnik po funkcjach debugera](../../debugger/debugger-feature-tour.md).

## <a name="next-steps"></a>Następne kroki

Zapoznaj się dodatkowo program Visual Studio, wykonując wraz z jednym niniejsze artykuły wprowadzające zawierają:

> [!div class="nextstepaction"]
> [Dowiedz się, jak za pomocą edytora kodu](tutorial-editor.md)

> [!div class="nextstepaction"]
> [Dowiedz się więcej o projekty i rozwiązania](tutorial-projects-solutions.md)

## <a name="see-also"></a>Zobacz także

- Odkryj [więcej funkcji programu Visual Studio](../../ide/advanced-feature-overview.md)
- Odwiedź stronę [visualstudio.microsoft.com](https://visualstudio.microsoft.com/vs/)
- Odczyt [blog Visual Studio](https://devblogs.microsoft.com/visualstudio/)