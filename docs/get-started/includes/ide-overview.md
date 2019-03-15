---
ms.date: 03/19/2019
ms.technology: vs-ide-general
ms.custom: vs-get-started
ms.author: gewarren
author: gewarren
manager: jillfra
ms.topic: include
ms.openlocfilehash: c411df964d0f0ffb6a96484f6ad4d245d561410c
ms.sourcegitcommit: 4ffb7be5384ad566ce46538032bf8561754c61a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2019
ms.locfileid: "58070337"
---
Visual Studio *zintegrowanego środowiska programistycznego* to twórczych Konsola uruchamianie służy do edytowania, debugowania i kompilowanie kodu, a następnie opublikować aplikację. Zintegrowanym środowisku programistycznym (IDE) to program bogate, który może służyć do wielu aspektów programowania. Podniesienia standardowy edytor i debugera, większości środowisk IDE podać, program Visual Studio obejmuje kompilatory, narzędzia uzupełniania kodu, projektanci graficzni i wiele innych funkcji, do jej obsługi ułatwiają realizację procesu tworzenia oprogramowania.

::: moniker range="vs-2017"

![Program Visual Studio 2017 IDE](../media/visual-studio-ide.png)

::: moniker-end

::: moniker range="vs-2019"

[![](../media/vs-2019/ide-overview.png "Visual Studio IDE")](../media/vs-2019/ide-overview.png#lightbox)

::: moniker-end

Ten obraz pokazuje programu Visual Studio Otwórz projekt i kilka okien narzędzi klucza, które będą prawdopodobnie używane:

- [Eksplorator rozwiązań](../../ide/solutions-and-projects-in-visual-studio.md) (prawym górnym rogu) umożliwia wyświetlanie, przejść i zarządzanie plikami kodu. **Eksplorator rozwiązań** ułatwiają organizowanie kodu za pomocą tych plików do grupowania [rozwiązania i projekty](../tutorial-projects-solutions.md).

- [Okna edytora](../../ide/writing-code-in-the-code-and-text-editor.md) (center), gdzie prawdopodobnie spędzisz większość czasu, wyświetla zawartość pliku. Jest to, który umożliwia edytowanie kodu lub projektować interfejs użytkownika, takie jak okna przy użyciu przycisków i pola tekstowe.

::: moniker range="vs-2017"

- [Okno danych wyjściowych](../../ide/reference/output-window.md) (na dole na środku) jest, gdzie Visual Studio wysyła powiadomienia, takich jak debugowanie i komunikaty o błędach, ostrzeżenia kompilatora, publikowania komunikatów o stanie i inne. Każde źródło komunikatu ma osobnej karcie.

::: moniker-end

- [Team Explorer](/azure/devops/user-guide/work-team-explorer?view=vsts) (prawy dolny róg) umożliwia śledzenie elementów roboczych i udostępnianie kodu z innymi osobami przy użyciu technologii kontroli wersji, takich jak [Git](https://git-scm.com/) i [Team Foundation Version Control (TFVC)](/azure/devops/repos/tfvc/overview?view=vsts).

## <a name="editions"></a>Wersje

::: moniker range="vs-2017"

Program Visual Studio jest dostępna dla Windows i Mac. [Program Visual Studio for Mac](/visualstudio/mac/) zawiera wiele same funkcje co program Visual Studio 2017 i jest zoptymalizowany pod kątem tworzenia aplikacji dla wielu platform i na urządzeniach przenośnych. Ten artykuł dotyczy programu Visual Studio 2017 w wersji Windows.

Istnieją trzy wersje programu Visual Studio 2017: Community, Professional i Enterprise. Zobacz [porównanie programu Visual Studio 2017 IDE](https://visualstudio.microsoft.com/vs/compare/) Aby dowiedzieć się więcej o funkcji, które są obsługiwane w poszczególnych wydaniach.

::: moniker-end

::: moniker range="vs-2019"

Program Visual Studio jest dostępna dla Windows i Mac. [Program Visual Studio for Mac](/visualstudio/mac/) ma wiele z tych samych funkcji, jak Visual Studio 2019 r i jest zoptymalizowany pod kątem tworzenia aplikacji dla wielu platform i na urządzeniach przenośnych. Ten artykuł koncentruje się na Windows wersję programu Visual Studio 2019 r.

Istnieją trzy wersje programu Visual Studio 2019 r.: Community, Professional i Enterprise. Zobacz [porównanie środowiska IDE programu Visual Studio](https://visualstudio.microsoft.com/vs/compare/) Aby dowiedzieć się więcej o funkcji, które są obsługiwane w poszczególnych wydaniach.

::: moniker-end

## <a name="popular-productivity-features"></a>Funkcje zwiększające produktywność popularne funkcje

Oto niektóre z najpopularniejszych funkcji w programie Visual Studio, które ułatwiają mu bardziej wydajnej pracy, podczas opracowywania oprogramowania:

- Zygzaki i [szybkie akcje](../../ide/quick-actions.md)

   Zygzaki są faliste linie, które alertów dotyczących błędów lub potencjalnych problemów w kodzie podczas wpisywania. Te wskazówki visual umożliwiają rozwiązywanie problemów z natychmiast bez oczekiwania na błąd, które mają zostać odnalezione, podczas kompilacji lub po uruchomieniu programu. Po umieszczeniu wskaźnika myszy nad wężyk, zobaczysz dodatkowe informacje o tym błędzie. Żarówka może również wystąpić na lewym marginesie z akcjami, znane jako szybkich akcji, aby naprawić błąd.

   ![Faliste linie w programie Visual Studio](../media/squiggles-error.png)

::: moniker range=">=vs-2019"

- Oczyszczanie kodu

   Za pomocą kliknięcia przycisku formatowanie kodu i stosować wszelkie poprawki kodu zaproponowana przez Twoje [ustawienia stylu kodu](../../ide/reference/options-text-editor-csharp-formatting.md), [konwencje .editorconfig](../../ide/create-portable-custom-editor-options.md), i [analizatorów Roslyn](../../code-quality/roslyn-analyzers-overview.md). **Kod czyszczenia** pomaga rozwiązać problemy występujące w kodzie, zanim przejdzie do przeglądu kodu. (Obecnie dostępna dla C# tylko kodu.)

   ![Przycisk Wyczyść kod w programie Visual Studio](../media/vs-2019/code-cleanup.png)

::: moniker-end

- [Refaktoryzacja](../../ide/refactoring-in-visual-studio.md)

   Refaktoryzacja obejmuje operacje, takie jak inteligentne zmiana nazwy zmiennych, wyodrębnianie jeden lub więcej wierszy kodu do nowej metody zmiany kolejności parametrów metod i inne.

   ![Refaktoryzacja w programie Visual Studio](../media/refactoring-menu.png)

- [Funkcja IntelliSense](../../ide/using-intellisense.md)

   Funkcja IntelliSense jest okres zestaw funkcji, który wyświetla informacje o kodzie bezpośrednio w edytorze, a w niektórych przypadkach zapisu małe fragmenty kodu dla Ciebie. To, jak podstawowa dokumentacja wbudowanego w edytorze, co pozwala uniknąć konieczności wyszukiwania informacji o typie w innym miejscu. Funkcje IntelliSense, zależy od języka. Aby uzyskać więcej informacji, zobacz [IntelliSense w języku C#](../../ide/visual-csharp-intellisense.md), [Visual C++ IntelliSense](../../ide/visual-cpp-intellisense.md), [JavaScript IntelliSense](../../ide/javascript-intellisense.md), i [Visual Basic IntelliSense](../../ide/visual-basic-specific-intellisense.md). Na poniższej ilustracji przedstawiono, jak technologia IntelliSense wyświetla listę elementu członkowskiego dla typu:

   ![Lista elementów członkowskich programu Visual Studio](../media/intellisense-list-members.png)

- [Szybkie uruchamianie](../../ide/reference/quick-launch-environment-options-dialog-box.md)

   Program Visual Studio może wydawać się trudne w czasie za pomocą menu tak wiele, opcje i właściwości. **Szybkie uruchamianie** pole wyszukiwania jest doskonałym sposobem na szybkie znajdowanie potrzebnej w programie Visual Studio. Po uruchomieniu, wpisując nazwę coś, czego szukasz, program Visual Studio wyświetla wyniki, które przyjmują dokładnie miejscu należy przejść. Jeśli chcesz dodać funkcje do programu Visual Studio, na przykład aby dodać obsługę dodatkowych języka programowania, **Szybkie uruchamianie** zapewnia wyniki, które Otwórz Instalator programu Visual Studio do zainstalowania obciążeń lub poszczególnych składników.

   > [!TIP]
   > Naciśnij klawisz **Ctrl**+**Q** jako skrót do **Szybkie uruchamianie** pola wyszukiwania.

   ::: moniker range="vs-2017"

   ![Szybkie uruchamianie pola wyszukiwania w programie Visual Studio 2017](../media/quick-launch-nuget.png)

   ::: moniker-end

   ::: moniker range="vs-2019"

   ![Szybkiego uruchamiania pola wyszukiwania w programie Visual Studio 2019 r.](../media/vs-2019/quick-launch-nuget.png)

   ::: moniker-end

- [Udostępnianie na żywo](/visualstudio/liveshare/)

   Zespołowe przeprowadzanie edytowania i debugowania z innymi osobami w czasie rzeczywistym, niezależnie od tego, jakie usługi typu aplikacji lub języka programowania. Szybko i bezpiecznie Udostępnij swój projekt, a następnie zgodnie z potrzebami, w sesji debugowania terminalu przypadkach localhost sieci web, aplikacje, połączenia głosowe i inne.

- [Hierarchia wywołań](../../ide/reference/call-hierarchy.md)

   **Hierarchię wywołań** okno zawiera metody, które wywołują wybranej metody. Może to być przydatne informacje, jeśli myślisz o zmienić lub usunąć metodę lub podczas próby znalezienia błędu.

   ![Okno hierarchii wywołań](../../ide/reference/media/call-hierarchy-csharp-expanded.png)

- [Funkcja CodeLens](../../ide/find-code-changes-and-other-history-with-codelens.md)

   Funkcja CodeLens pomoże Ci znaleźć odwołania do kodu, zmiany kodu, połączone usterki, elementy robocze, przeglądy kodu i testów jednostkowych, wszystko to bez zamykania edytora.

   ![Funkcja CodeLens](../media/codelens-overview.png)

- [Przejdź do definicji](../../ide/go-to-and-peek-definition.md)

   Funkcja przejdź do definicji umożliwia przejście bezpośrednio do lokalizacji, w którym funkcja lub typ jest zdefiniowany.

   ![Przejdź do definicji](../media/go-to-definition-menu.png)

- [Zobacz definicję](../../ide/how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12.md)

   **Peek Definition** okno zawiera definicję metody lub typu, bez konieczności otwierania pliku.

   ![Wgląd do definicji](../media/peek-definition.png)

## <a name="install-the-visual-studio-ide"></a>Zainstaluj program Visual Studio IDE

W tej sekcji utworzysz prosty projekt, aby wypróbować kilka rzeczy, które można wykonać za pomocą programu Visual Studio. Użyjesz [IntelliSense](../../ide/using-intellisense.md) jak kodowanie pomocy, debugować aplikację, aby wyświetlić wartość zmiennej podczas wykonywania programu i Zmień motyw kolorów.

::: moniker range="vs-2017"

Aby rozpocząć pracę, [Pobierz program Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) i zainstaluj go na system. Instalator modułowej umożliwia wybierz i zainstaluj *obciążeń*, służą do grup funkcje potrzebne do programowania języka lub platformy, użytkownik sobie tego życzy. Wykonaj kroki dla [tworzenie programu](#create-a-program), pamiętaj o wybraniu **programowanie dla wielu platform .NET Core** obciążenie podczas instalacji.

::: moniker-end

::: moniker range=">=vs-2019"

Aby rozpocząć pracę, [Pobierz program Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) i zainstaluj go na system. Instalator modułowej umożliwia wybierz i zainstaluj *obciążeń*, służą do grup funkcje potrzebne do programowania języka lub platformy, użytkownik sobie tego życzy. Wykonaj kroki dla [tworzenie programu](#create-a-program), pamiętaj o wybraniu **programowanie dla wielu platform .NET Core** obciążenie podczas instalacji.

::: moniker-end

![Obciążenia programowanie dla wielu platform .NET core w Instalatorze programu Visual Studio](../media/dotnet-core-cross-platform-workload.png)

Po otwarciu programu Visual Studio po raz pierwszy, można opcjonalnie [Zaloguj](../../ide/signing-in-to-visual-studio.md) przy użyciu swojego konta Microsoft albo konta służbowego lub szkolnego.

## <a name="create-a-program"></a>Utwórz program

Przyjrzyjmy się temu bliżej i Utwórz prosty program.

::: moniker range="vs-2017"

1. Otwórz program Visual Studio.

1. Na pasku menu wybierz **pliku** > **New** > **projektu**.

   ![Plik > Nowy projekt na pasku menu](../media/file-new-project-menu.png)

   **Nowy projekt** okno dialogowe zawiera kilka projektu *szablony*. Szablon zawiera podstawowe pliki i ustawienia wymagane dla typu danego projektu.

1. Wybierz **platformy .NET Core** kategorii szablonu w ramach **Visual C#** , a następnie wybierz **Aplikacja konsoli (.NET Core)** szablonu. W **nazwa** polu tekstowym **HelloWorld**, a następnie wybierz pozycję **OK** przycisku.

   ![Szablon aplikacji .NET core](../media/overview-new-project-dialog.png)

   > [!NOTE]
   > Jeśli nie widzisz **platformy .NET Core** kategorii, musisz zainstalować **programowanie dla wielu platform .NET Core** obciążenia. Aby to zrobić, wybierz **Otwórz Instalator programu Visual Studio** łącza w lewym dolnym rogu **nowy projekt** okna dialogowego. Po otwarciu Instalatora programu Visual Studio, przewiń w dół i wybierz **programowanie dla wielu platform .NET Core** obciążenia, a następnie wybierz **Modyfikuj**.

   Program Visual Studio tworzy projekt. Jest prostą aplikację "Hello World", która wywołuje <xref:System.Console.WriteLine?displayProperty=nameWithType> metodę w celu wyświetlenia literału ciągu "Hello World!" w oknie konsoli (dane wyjściowe programu).

   Wkrótce powinny zostać wyświetlone, podobny do poniższego:

   ![Visual Studio IDE](../media/overview-ide-console-app.png)

   Zawiera kodu C# dla swojej aplikacji w oknie edytora, która zajmuje większość miejsca. Należy zauważyć, że tekst jest automatycznie w trybie kolorowym do wskazania różnych części kodu, takich jak słów kluczowych i typów. Ponadto małe, pionowe linie przerywane, w kodzie wskazują, które nawiasy klamrowe zgodne siebie nawzajem, a później zlokalizować kod pomocy numery wierszy. Możesz wybrać znaków minus małe, spakowany, aby zwinąć lub rozwinąć bloków kodu. Ten kod funkcji konspektu można ukrywać kod, który nie jest konieczne, pozwala zminimalizować bałaganu na ekranie. Pliki projektu są wyświetlane po prawej stronie w oknie o nazwie **Eksploratora rozwiązań**.

   ![Visual Studio IDE z czerwone pola](../media/overview-ide-console-app-red-boxes.png)

   Brak dostępnych inne menu i okien narzędzi, ale Przejdźmy teraz.

1. Teraz uruchom aplikację. Można to zrobić, wybierając **Rozpocznij bez debugowania** z **debugowania** menu na pasku menu. Można również nacisnąć klawisz **Ctrl**+**F5**.

   ![Debuguj > Uruchom bez debugowania menu](../media/overview-start-without-debugging.png)

   Program Visual Studio tworzy aplikację, a komunikat zostanie otwarte okno konsoli **Hello World!**. Masz teraz uruchomionej aplikacji.

   ![Okno konsoli](../media/overview-console-window.png)

1. Aby zamknąć okno konsoli, naciśnij dowolny klawisz na klawiaturze.

1. Dodajmy dodatkowy kod do aplikacji. Dodaj następujący kod C# przed wierszem, który jest wyświetlany komunikat `Console.WriteLine("Hello World!");`:

   ```csharp
   Console.WriteLine("\nWhat is your name?");
   var name = Console.ReadLine();
   ```

   Ten kod wyświetla **jak się Nazywasz?** w oknie konsoli, a następnie czeka, aż użytkownik wprowadza jakiś tekst, a następnie **Enter** klucza.

1. Zmień wiersz, który jest wyświetlany komunikat `Console.WriteLine("Hello World!");` z następującym kodem:

   ```csharp
   Console.WriteLine($"\nHello {name}!");
   ```

1. Ponownie uruchom aplikację, wybierając **debugowania** > **Rozpocznij bez debugowania** lub naciskając **Ctrl**+**F5**.

   Program Visual Studio ponownie kompiluje aplikację, a okno konsoli otworzy i wyświetli monit o podanie nazwy.

1. Wprowadź nazwę w oknie konsoli, a następnie naciśnij klawisz **Enter**.

   ![Dane wejściowe z okna konsoli](../media/overview-console-input.png)

1. Naciśnij dowolny klawisz, aby zamknąć okno konsoli i zatrzymać uruchomionego programu.

::: moniker-end

::: moniker range=">=vs-2019"

1. Otwórz program Visual Studio.

   W oknie uruchamiania pojawia się z różnymi opcjami klonowanie repozytorium, otwieranie projektu zawierającego najnowsze lub tworzenia nowego projektu.

1. Wybierz **Utwórz nowy projekt**.

   ![Visual Studio Uruchom okno Utwórz nowy projekt](../media/vs-2019/start-window-create-new-project.png)

   **Utwórz nowy projekt** okna otwiera i pokazuje kilka projektów *szablony*. Szablon zawiera podstawowe pliki i ustawienia wymagane dla typu danego projektu.

1. Aby znaleźć szablonu firma Microsoft, wpisz lub wprowadź **konsolowa .net core** w polu wyszukiwania. Lista dostępnych szablonów jest automatycznie filtrowany według słów kluczowych, wprowadzony. Rezultaty szablonu można dalej filtrować, wybierając **C#** z **języka** listy rozwijanej. Wybierz **Aplikacja konsoli (.NET Core)** szablonu, a następnie wybierz **dalej**.

    ![Utwórz nowy projekt w programie Visual Studio](../media/vs-2019/create-new-project.png)

1. W **konfigurowania nowego projektu** oknie wprowadź **HelloWorld** w **Nazwa projektu** opcjonalnie Zmień lokalizację plików projektu, a następnie Wybierz **Utwórz**.

   ![Skonfiguruj nowy projekt w programie Visual Studio](../media/vs-2019/configure-new-project.png)

   Program Visual Studio tworzy projekt. Jest prostą aplikację "Hello World", która wywołuje <xref:System.Console.WriteLine?displayProperty=nameWithType> metodę w celu wyświetlenia literału ciągu "Hello World!" w oknie konsoli (dane wyjściowe programu).

   Wkrótce powinny zostać wyświetlone, podobny do poniższego:

   ![Visual Studio IDE](../media/vs-2019/overview-ide-console-app.png)

   Zawiera kodu C# dla swojej aplikacji w oknie edytora, która zajmuje większość miejsca. Należy zauważyć, że tekst jest automatycznie w trybie kolorowym do wskazania różnych części kodu, takich jak słów kluczowych i typów. Ponadto małe, pionowe linie przerywane, w kodzie wskazują, które nawiasy klamrowe zgodne siebie nawzajem, a później zlokalizować kod pomocy numery wierszy. Możesz wybrać znaków minus małe, spakowany, aby zwinąć lub rozwinąć bloków kodu. Ten kod funkcji konspektu można ukrywać kod, który nie jest konieczne, pozwala zminimalizować bałaganu na ekranie. Pliki projektu są wyświetlane po prawej stronie w oknie o nazwie **Eksploratora rozwiązań**.

   ![Visual Studio IDE z czerwone pola](../media/vs-2019/overview-ide-console-app-red-boxes.png)

   Brak dostępnych inne menu i okien narzędzi, ale Przejdźmy teraz.

1. Teraz uruchom aplikację. Można to zrobić, wybierając **Rozpocznij bez debugowania** z **debugowania** menu na pasku menu. Można również nacisnąć klawisz **Ctrl**+**F5**.

   ![Debuguj > Uruchom bez debugowania menu](../media/overview-start-without-debugging.png)

   Program Visual Studio tworzy aplikację, a komunikat zostanie otwarte okno konsoli **Hello World!**. Masz teraz uruchomionej aplikacji.

   ![Okno konsoli](../media/vs-2019/overview-console-window.png)

1. Aby zamknąć okno konsoli, naciśnij dowolny klawisz na klawiaturze.

1. Dodajmy dodatkowy kod do aplikacji. Dodaj następujący kod C# przed wierszem, który jest wyświetlany komunikat `Console.WriteLine("Hello World!");`:

   ```csharp
   Console.WriteLine("\nWhat is your name?");
   var name = Console.ReadLine();
   ```

   Ten kod wyświetla **jak się Nazywasz?** w oknie konsoli, a następnie czeka, aż użytkownik wprowadza jakiś tekst, a następnie **Enter** klucza.

1. Zmień wiersz, który jest wyświetlany komunikat `Console.WriteLine("Hello World!");` z następującym kodem:

   ```csharp
   Console.WriteLine($"\nHello {name}!");
   ```

1. Ponownie uruchom aplikację, wybierając **debugowania** > **Rozpocznij bez debugowania** lub naciskając **Ctrl**+**F5**.

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

::: moniker range="vs-2017"

3. Wybierz ikonę żarówki, aby wyświetlić dostępnych [szybkie akcje](../../ide/quick-actions.md). Wybierz **Zmień nazwę "name" do "username"**.

   ![Zmień nazwę akcji w programie Visual Studio](../media/rename-quick-action.png)

   Zmienna została zmieniona w projekcie, czyli w tym przypadku tylko dwa miejsca.

   ![Animowany obraz gif przedstawiający Refaktoryzacja zmiany nazwy w programie Visual Studio](../media/rename-refactoring.gif)

::: moniker-end

::: moniker range=">=vs-2019"

3. Wybierz ikonę żarówki, aby wyświetlić dostępnych [szybkie akcje](../../ide/quick-actions.md). Wybierz **Zmień nazwę "name" do "username"**.

   ![Zmień nazwę akcji w programie Visual Studio](../media/vs-2019/rename-quick-action.png)

   Zmienna została zmieniona w projekcie, czyli w tym przypadku tylko dwa miejsca.

::: moniker-end

4. Teraz Przyjrzyjmy się w technologii IntelliSense. Poniżej wiersza, który jest wyświetlany komunikat `Console.WriteLine($"\nHello {username}!");`, typ `DateTime now = DateTime.`.

   Wyświetlone elementy członkowskie <xref:System.DateTime> klasy. Ponadto opis aktualnie zaznaczonego elementu członkowskiego, wyświetla się w osobnym oknie.

   ![Funkcja IntelliSense członków listy w programie Visual Studio](../media/intellisense-list-members.png)

5. Wybierz element członkowski o nazwie **teraz**, który jest właściwością klasy, klikając je dwukrotnie lub naciskając **kartę**. Wykonaj w wierszu kodu, dodając je średnikiem na końcu.

6. Poniżej wpisz lub wklej następujące wiersze kodu:

   ```csharp
   int dayOfYear = now.DayOfYear;

   Console.Write("Day of year: ");
   Console.WriteLine(dayOfYear);
   ```

   > [!TIP]
   > <xref:System.Console.Write%2A?displayProperty=nameWithType> różni się nieco się <xref:System.Console.WriteLine%2A?displayProperty=nameWithType> się po wydrukowaniu terminator wiersza nie jest dodawany. Oznacza to, że w następnej części tekst, który jest wysyłany do danych wyjściowych zostanie wydrukowany na tym samym wierszu. Możesz umieścić kursor każda z tych metod w kodzie, aby wyświetlić jego opis.

7. Następnie użyjemy refaktoryzacji ponownie się nieco bardziej zwięzły widok kodu. Kliknij na zmiennej `now` w wierszu `DateTime now = DateTime.Now;`.

   Należy zauważyć, że mała ikona śrubokręt pojawia się na marginesie w danym wierszu.

8. Kliknij ikonę śrubokręt, aby zobaczyć, jakie sugestie dotyczące programu Visual Studio jest dostępny. W tym przypadku jest wyświetlane [wstawiona zmienna tymczasowa](../../ide/reference/inline-temporary-variable.md) refaktoryzacji, aby usunąć wiersz kodu bez wprowadzania zmian w ogólnym zachowaniom kodu:

   ![Wbudowane tymczasowej zmiennej Refaktoryzacja w programie Visual Studio](../media/inline-temporary-variable-refactoring.png)

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

1. Znajdź wiersz kodu, który jest wyświetlany komunikat `Console.WriteLine($"\nHello {username}!");`. Aby ustawić punkt przerwania w tym wierszu kodu, oznacza to, aby program wstrzymać wykonanie w tym wierszu kliknij na marginesie po lewej stronie edytora. Możesz również kliknąć dowolne miejsce na wiersz kodu, a następnie naciśnij klawisz **F9**.

   Czerwony okrąg pojawia się na marginesie po lewej stronie, a kod zostanie wyróżniony czerwonym kolorem.

   ![Punkt przerwania w wierszu kodu w programie Visual Studio](../media/breakpoint.png)

1. Rozpocznij debugowanie wybierając **debugowania** > **Rozpocznij debugowanie** lub naciskając **F5**.

1. W oknie konsoli zostanie wyświetlony i poprosi o podanie nazwy użytkownika, wpisz go w i naciśnij klawisz **Enter**.

   Powrót do edytora kodu programu Visual Studio oraz wiersza kodu, punkt przerwania jest wyróżniony na żółto. Oznacza to, że jest następnego wiersza kodu, które spowodują wykonanie programu.

1. Umieść kursor myszy nad `username` zmiennej, aby zobaczyć jej wartość. Alternatywnie możesz kliknąć prawym przyciskiem myszy na `username` i wybierz **Dodaj czujkę** można dodać zmienną **Obejrzyj** okna, w którym widać również jego wartość.

   ![Wartość zmiennej podczas debugowania w programie Visual Studio](../media/debugging-variable-value.png)

1. Aby umożliwić programu zostało ukończone, naciśnij klawisz **F5** ponownie.

Aby uzyskać więcej informacji o debugowaniu w programie Visual Studio, zobacz [Przewodnik po funkcjach debugera](../../debugger/debugger-feature-tour.md).

## <a name="customize-visual-studio"></a>Dostosuj program Visual Studio

Możesz dostosować interfejsu użytkownika programu Visual Studio, w tym zmiany domyślnego motywu kolorów. Aby zmienić **ciemny** motywu:

1. Na pasku menu wybierz **narzędzia** > **opcje** otworzyć **opcje** okna dialogowego.

::: moniker range="vs-2017"

2. Na **środowiska** > **ogólne** Strona opcji, zmień **motyw kolorów** wyboru, aby **ciemny**, a następnie wybierz pozycję **OK**.

   Motyw kolorów dla całej IDE zmieni się na **ciemny**.

   ![Visual Studio z motywu ciemny](../media/dark-theme.png)

::: moniker-end

::: moniker range=">=vs-2019"

2. Na **środowiska** > **ogólne** Strona opcji, zmień **motyw kolorów** wyboru, aby **ciemny**, a następnie wybierz pozycję **OK**.

   Motyw kolorów dla całej IDE zmieni się na **ciemny**.

   ![Visual Studio z motywu ciemny](../media/vs-2019/dark-theme.png)

::: moniker-end

Aby dowiedzieć się więcej o innych metodach, które można spersonalizować środowisko IDE, zobacz [Personalizowanie programu Visual Studio](../../ide/personalizing-the-visual-studio-ide.md).