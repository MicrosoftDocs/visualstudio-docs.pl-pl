---
ms.date: 03/19/2019
ms.technology: vs-ide-general
ms.custom: vs-get-started
ms.author: tglee
author: TerryGLee
manager: jillfra
ms.topic: include
ms.openlocfilehash: 69b1bccf20c242965462b807b2a1b64d3c60d671
ms.sourcegitcommit: 2ae2436dc3484b9dfa10e0483afba1e5a02a52eb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/25/2020
ms.locfileid: "77590807"
---
*Zintegrowane środowisko programistyczne* programu Visual Studio to twórczy pad do uruchamiania, który umożliwia edytowanie, debugowanie i kompilowanie kodu, a następnie publikowanie aplikacji. Zintegrowanym środowisku programistycznym (IDE) to program bogate, który może służyć do wielu aspektów programowania. Podniesienia standardowy edytor i debugera, większości środowisk IDE podać, program Visual Studio obejmuje kompilatory, narzędzia uzupełniania kodu, projektanci graficzni i wiele innych funkcji, do jej obsługi ułatwiają realizację procesu tworzenia oprogramowania.

::: moniker range="vs-2017"

![Środowisko IDE programu Visual Studio 2017](../media/visual-studio-ide.png)

::: moniker-end

::: moniker range="vs-2019"

[![środowiska IDE programu Visual Studio 2019](../media/vs-2019/ide-overview.png)](../media/vs-2019/ide-overview.png#lightbox)

::: moniker-end

Ten obraz pokazuje programu Visual Studio Otwórz projekt i kilka okien narzędzi klucza, które będą prawdopodobnie używane:

- [Eksplorator rozwiązań](../../ide/solutions-and-projects-in-visual-studio.md) (prawy górny) umożliwia wyświetlanie plików kodu i nawigowanie w nich oraz zarządzanie nimi. **Eksplorator rozwiązań** może pomóc organizować kod przez zgrupowanie plików na [rozwiązania i projekty](../tutorial-projects-solutions.md).

- [Okno edytora](../../ide/writing-code-in-the-code-and-text-editor.md) (środkowe), w którym najprawdopodobniej będzie można spędzać większość czasu, zostanie wyświetlona zawartość pliku. Jest to, który umożliwia edytowanie kodu lub projektować interfejs użytkownika, takie jak okna przy użyciu przycisków i pola tekstowe.

::: moniker range="vs-2017"

- W [oknie danych wyjściowych](../../ide/reference/output-window.md) (u dołu) jest miejsce, gdzie program Visual Studio wysyła powiadomienia, takie jak debugowanie i komunikaty o błędach, ostrzeżenia kompilatora, publikowanie komunikatów o stanie itd. Każde źródło komunikatu ma osobnej karcie.

::: moniker-end

- [Team Explorer](/azure/devops/user-guide/work-team-explorer?view=vsts) (prawy dolny) umożliwia śledzenie elementów roboczych i udostępnianie kodu innym osobom korzystającym z technologii kontroli wersji, takich jak [git](https://git-scm.com/) i [Kontrola wersji serwera Team Foundation (TFVC)](/azure/devops/repos/tfvc/overview?view=vsts).

## <a name="editions"></a>Wersje

::: moniker range="vs-2017"

Program Visual Studio jest dostępna dla Windows i Mac. [Visual Studio dla komputerów Mac](/visualstudio/mac/) ma wiele takich samych funkcji, jak program Visual Studio 2017 i jest zoptymalizowany pod kątem opracowywania aplikacji mobilnych i międzyplatformowych. Ten artykuł dotyczy programu Visual Studio 2017 w wersji Windows.

Istnieją trzy wersje programu Visual Studio 2017: Community, Professional i Enterprise. Zobacz [porównanie programu Visual Studio 2017 środowisk IDE](https://visualstudio.microsoft.com/vs/compare/) , aby dowiedzieć się, jakie funkcje są obsługiwane w poszczególnych wersjach.

::: moniker-end

::: moniker range="vs-2019"

Program Visual Studio jest dostępna dla Windows i Mac. [Visual Studio dla komputerów Mac](/visualstudio/mac/) ma wiele takich samych funkcji, jak program Visual Studio 2019 i jest zoptymalizowany pod kątem opracowywania aplikacji mobilnych i międzyplatformowych. Ten artykuł koncentruje się na wersji systemu Windows programu Visual Studio 2019.

Istnieją trzy wersje programu Visual Studio 2019: Community, Professional i Enterprise. Zobacz [porównanie programu Visual Studio środowisk IDE](https://visualstudio.microsoft.com/vs/compare/) , aby dowiedzieć się, jakie funkcje są obsługiwane w poszczególnych wersjach.

::: moniker-end

## <a name="popular-productivity-features"></a>Funkcje zwiększające produktywność popularne funkcje

Oto niektóre z najpopularniejszych funkcji w programie Visual Studio, które ułatwiają mu bardziej wydajnej pracy, podczas opracowywania oprogramowania:

- Zygzaki i [szybkie akcje](../../ide/quick-actions.md)

   Zygzaki są faliste linie, które alertów dotyczących błędów lub potencjalnych problemów w kodzie podczas wpisywania. Te wskazówki visual umożliwiają rozwiązywanie problemów z natychmiast bez oczekiwania na błąd, które mają zostać odnalezione, podczas kompilacji lub po uruchomieniu programu. Po umieszczeniu wskaźnika myszy nad wężyk, zobaczysz dodatkowe informacje o tym błędzie. Żarówka może również wystąpić na lewym marginesie z akcjami, znane jako szybkich akcji, aby naprawić błąd.

   ![Faliste linie w programie Visual Studio](../media/squiggles-error.png)

::: moniker range=">=vs-2019"

- Czyszczenie kodu

   Po kliknięciu przycisku sformatuj kod i Zastosuj wszelkie poprawki kodu sugerowane przez [Ustawienia stylu kodu](../../ide/reference/options-text-editor-csharp-formatting.md), [konwencje editorconfig](../../ide/create-portable-custom-editor-options.md)i [analizatory Roslyn](../../code-quality/roslyn-analyzers-overview.md). **Czyszczenie kodu** ułatwia rozwiązywanie problemów w kodzie przed przekazaniem ich do przeglądu kodu. (Obecnie dostępne tylko C# dla kodu).

   ![Przycisk czyszczenia kodu w programie Visual Studio](../media/vs-2019/code-cleanup.png)

::: moniker-end

- [Refaktoryzacja](../../ide/refactoring-in-visual-studio.md)

   Refaktoryzacja obejmuje operacje, takie jak inteligentne zmiana nazwy zmiennych, wyodrębnianie jeden lub więcej wierszy kodu do nowej metody zmiany kolejności parametrów metod i inne.

   ![Refaktoryzacja w programie Visual Studio](../media/refactoring-menu.png)

- [IntelliSense](../../ide/using-intellisense.md)

   Funkcja IntelliSense jest okres zestaw funkcji, który wyświetla informacje o kodzie bezpośrednio w edytorze, a w niektórych przypadkach zapisu małe fragmenty kodu dla Ciebie. To, jak podstawowa dokumentacja wbudowanego w edytorze, co pozwala uniknąć konieczności wyszukiwania informacji o typie w innym miejscu. Funkcje IntelliSense, zależy od języka. Aby uzyskać więcej informacji, zobacz [ C# IntelliSense](../../ide/visual-csharp-intellisense.md), [ C++ Visual IntelliSense](../../ide/visual-cpp-intellisense.md), [JavaScript IntelliSense](../../ide/javascript-intellisense.md)i [Visual Basic IntelliSense](../../ide/visual-basic-specific-intellisense.md). Na poniższej ilustracji przedstawiono, jak technologia IntelliSense wyświetla listę elementu członkowskiego dla typu:

   ![Lista elementów członkowskich programu Visual Studio](../media/intellisense-list-members.png)

- Pole wyszukiwania

   Program Visual Studio może wydawać się trudne w czasie za pomocą menu tak wiele, opcje i właściwości. Pole wyszukiwania to doskonały sposób na szybkie znajdowanie potrzebnych informacji w programie Visual Studio. Po uruchomieniu, wpisując nazwę coś, czego szukasz, program Visual Studio wyświetla wyniki, które przyjmują dokładnie miejscu należy przejść. Aby dodać funkcję do programu Visual Studio, na przykład w celu dodania obsługi dodatkowego języka programowania, w polu wyszukiwania znajdują się wyniki otwierające Instalator programu Visual Studio w celu zainstalowania obciążenia lub pojedynczego składnika.

   > [!TIP]
   > Naciśnij klawisz **Ctrl**+**Q** jako skrót do pola wyszukiwania.

   ::: moniker range="vs-2017"

   ![Pole wyszukiwania szybkiego uruchamiania w programie Visual Studio 2017](../media/quick-launch-nuget.png)

   Aby uzyskać więcej informacji, zobacz [Szybki Start](../../ide/reference/quick-launch-environment-options-dialog-box.md).

   ::: moniker-end

   ::: moniker range="vs-2019"

   ![Pole wyszukiwania w programie Visual Studio 2019](../media/vs-2019/quick-launch-nuget.png)

   ::: moniker-end

- [Live Share](/visualstudio/liveshare/)

   Współpracuj z innymi osobami w czasie rzeczywistym, niezależnie od typu aplikacji lub języka programowania. Możesz natychmiast i bezpiecznie udostępnić projekt oraz, w razie konieczności, debugowanie sesji, wystąpienia terminala, aplikacje sieci Web, połączenia głosowe i inne.

- [Hierarchia wywołań](../../ide/reference/call-hierarchy.md)

   W oknie **Hierarchia wywołań** są wyświetlane metody wywołujące wybraną metodę. Może to być przydatne informacje, jeśli myślisz o zmienić lub usunąć metodę lub podczas próby znalezienia błędu.

   ![Okno hierarchii wywołań](../../ide/reference/media/call-hierarchy-csharp-expanded.png)

- [CodeLens](../../ide/find-code-changes-and-other-history-with-codelens.md)

   Funkcja CodeLens pomoże Ci znaleźć odwołania do kodu, zmiany kodu, połączone usterki, elementy robocze, przeglądy kodu i testów jednostkowych, wszystko to bez zamykania edytora.

   ![CodeLens](../media/codelens-overview.png)

- [Przejdź do definicji](../../ide/go-to-and-peek-definition.md)

   Funkcja przejdź do definicji umożliwia przejście bezpośrednio do lokalizacji, w którym funkcja lub typ jest zdefiniowany.

   ![Przejdź do definicji](../media/go-to-definition-menu.png)

- [Definicja wglądu](../../ide/how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12.md)

   Okno **Definicja wglądu** pokazuje definicję metody lub typu bez faktycznego otwierania osobnego pliku.

   ![Wgląd do definicji](../media/peek-definition.png)

## <a name="install-the-visual-studio-ide"></a>Zainstaluj program Visual Studio IDE

W tej sekcji utworzysz prosty projekt, aby wypróbować niektóre elementy, które można wykonać za pomocą programu Visual Studio. Użyjesz funkcji [IntelliSense](../../ide/using-intellisense.md) jako pomocy dotyczącej kodowania, Debuguj aplikację, aby wyświetlić wartość zmiennej podczas wykonywania programu, i Zmień motyw kolorów.

::: moniker range="vs-2017"

Aby rozpocząć, [Pobierz program Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) i zainstaluj go w systemie. Modułowy Instalator umożliwia wybieranie i instalowanie *obciążeń*, które są grupami funkcji wymaganych przez preferowany język programowania lub platformę. Aby postępować zgodnie z instrukcjami dotyczącymi [tworzenia programu](#create-a-program), należy wybrać **środowisko programistyczne dla wielu platform .NET Core** podczas instalacji.

::: moniker-end

::: moniker range=">=vs-2019"

Aby rozpocząć, [Pobierz program Visual Studio](https://visualstudio.microsoft.com/downloads) i zainstaluj go w systemie. Modułowy Instalator umożliwia wybieranie i instalowanie *obciążeń*, które są grupami funkcji wymaganych przez preferowany język programowania lub platformę. Aby postępować zgodnie z instrukcjami dotyczącymi [tworzenia programu](#create-a-program), należy wybrać **środowisko programistyczne dla wielu platform .NET Core** podczas instalacji.

::: moniker-end

![Obciążenia programowanie dla wielu platform .NET core w Instalatorze programu Visual Studio](../media/dotnet-core-cross-platform-workload.png)

Po otwarciu programu Visual Studio po raz pierwszy możesz [zalogować się](../../ide/signing-in-to-visual-studio.md) przy użyciu konto Microsoft lub konta służbowego.

## <a name="create-a-program"></a>Utwórz program

Przyjrzyjmy się temu bliżej i Utwórz prosty program.

::: moniker range="vs-2017"

1. Otwórz program Visual Studio.

1. Na pasku menu wybierz kolejno pozycje **plik** > **Nowy** > **projekt**.

   ![Plik > Nowy projekt na pasku menu](../media/file-new-project-menu.png)

   Okno dialogowe **Nowy projekt** zawiera kilka *szablonów*projektów. Szablon zawiera podstawowe pliki i ustawienia wymagane dla typu danego projektu.

1. Wybierz kategorię szablon **.NET Core** w obszarze **Wizualizacja C#** , a następnie wybierz szablon **Aplikacja konsolowa (.NET Core)** . W polu tekstowym **Nazwa** wpisz **HelloWorld**, a następnie wybierz przycisk **OK** .

   ![Szablon aplikacji .NET core](../media/overview-new-project-dialog.png)

   > [!NOTE]
   > Jeśli nie widzisz kategorii **.NET Core** , musisz zainstalować **środowisko programistyczne dla wielu platform .NET Core** . Aby to zrobić, wybierz link **otwórz Instalator programu Visual Studio** w lewym dolnym rogu okna dialogowego **Nowy projekt** . Po otwarciu Instalator programu Visual Studio przewiń w dół i wybierz pozycję **.NET Core Międzyplatformowe** obciążenie dla deweloperów, a następnie wybierz polecenie **Modyfikuj**.

   Program Visual Studio tworzy projekt. Jest to prosta aplikacja "Hello world", która wywołuje metodę <xref:System.Console.WriteLine?displayProperty=nameWithType> w celu wyświetlenia ciągu literału "Hello world!" w oknie konsoli (dane wyjściowe programu).

   Wkrótce powinny zostać wyświetlone, podobny do poniższego:

   ![Visual Studio IDE](../media/overview-ide-console-app.png)

   Zawiera kodu C# dla swojej aplikacji w oknie edytora, która zajmuje większość miejsca. Należy zauważyć, że tekst jest automatycznie w trybie kolorowym do wskazania różnych części kodu, takich jak słów kluczowych i typów. Ponadto małe, pionowe linie przerywane, w kodzie wskazują, które nawiasy klamrowe zgodne siebie nawzajem, a później zlokalizować kod pomocy numery wierszy. Możesz wybrać znaków minus małe, spakowany, aby zwinąć lub rozwinąć bloków kodu. Ten kod funkcji konspektu można ukrywać kod, który nie jest konieczne, pozwala zminimalizować bałaganu na ekranie. Pliki projektu są wymienione po prawej stronie w oknie o nazwie **Eksplorator rozwiązań**.

   ![Visual Studio IDE z czerwone pola](../media/overview-ide-console-app-red-boxes.png)

   Brak dostępnych inne menu i okien narzędzi, ale Przejdźmy teraz.

1. Teraz uruchom aplikację. Można to zrobić, wybierając pozycję **Uruchom bez debugowania** z menu **Debuguj** na pasku menu. Możesz również nacisnąć klawisz **Ctrl**+**F5**.

   ![Debuguj > Uruchom bez debugowania menu](../media/overview-start-without-debugging.png)

   Program Visual Studio kompiluje aplikację i zostanie otwarte okno konsoli z komunikatem **Hello World!** . Masz teraz uruchomionej aplikacji.

   ![Okno konsoli](../media/overview-console-window.png)

1. Aby zamknąć okno konsoli, naciśnij dowolny klawisz na klawiaturze.

1. Dodajmy dodatkowy kod do aplikacji. Dodaj następujący C# kod przed wierszem, który brzmi `Console.WriteLine("Hello World!");`:

   ```csharp
   Console.WriteLine("\nWhat is your name?");
   var name = Console.ReadLine();
   ```

   Ten kod wyświetla **nazwę użytkownika** w oknie konsoli, a następnie czeka, aż użytkownik wprowadzi jakiś tekst, a następnie klawisz **Enter** .

1. Zmień wiersz, który brzmi `Console.WriteLine("Hello World!");`, do następującego kodu:

   ```csharp
   Console.WriteLine($"\nHello {name}!");
   ```

1. Uruchom aplikację ponownie, wybierając pozycję **debuguj** > **Rozpocznij bez debugowania** lub naciskając klawisz **Ctrl**+**F5**.

   Program Visual Studio ponownie kompiluje aplikację, a okno konsoli otworzy i wyświetli monit o podanie nazwy.

1. Wprowadź swoją nazwę w oknie konsoli i naciśnij klawisz **Enter**.

   ![Dane wejściowe z okna konsoli](../media/overview-console-input.png)

1. Naciśnij dowolny klawisz, aby zamknąć okno konsoli i zatrzymać uruchomionego programu.

::: moniker-end

::: moniker range=">=vs-2019"

1. Otwórz program Visual Studio.

   Zostanie wyświetlone okno uruchamiania z różnymi opcjami klonowania repozytorium, otwarciem ostatniego projektu lub utworzeniem nowego projektu.

1. Wybierz pozycję **Utwórz nowy projekt**.

   ![Okno uruchamiania programu Visual Studio — Tworzenie nowego projektu](../media/vs-2019/start-window-create-new-project.png)

   Zostanie otwarte okno **Utwórz nowy projekt** zawierające kilka *szablonów*projektów. Szablon zawiera podstawowe pliki i ustawienia wymagane dla typu danego projektu.

1. Aby znaleźć żądany szablon, wpisz lub wprowadź w polu wyszukiwania **konsolę .NET Core** . Lista dostępnych szablonów jest automatycznie filtrowana na podstawie wprowadzonych słów kluczowych. Można bardziej filtrować wyniki szablonu, wybierając **C#** z listy rozwijanej **Język** . Wybierz szablon **Aplikacja konsolowa (.NET Core)** , a następnie wybierz przycisk **dalej**.

    ![Tworzenie nowego projektu w programie Visual Studio](../media/vs-2019/create-new-project.png)

1. W oknie **Konfigurowanie nowego projektu** wprowadź **HelloWorld** w polu **Nazwa projektu** , opcjonalnie Zmień lokalizację katalogu dla plików projektu, a następnie wybierz pozycję **Utwórz**.

   ![Konfigurowanie nowego projektu w programie Visual Studio](../media/vs-2019/configure-new-project.png)

   Program Visual Studio tworzy projekt. Jest to prosta aplikacja "Hello world", która wywołuje metodę <xref:System.Console.WriteLine?displayProperty=nameWithType> w celu wyświetlenia ciągu literału "Hello world!" w oknie konsoli (dane wyjściowe programu).

   Wkrótce powinny zostać wyświetlone, podobny do poniższego:

   ![Visual Studio IDE](../media/vs-2019/overview-ide-console-app.png)

   Zawiera kodu C# dla swojej aplikacji w oknie edytora, która zajmuje większość miejsca. Należy zauważyć, że tekst jest automatycznie w trybie kolorowym do wskazania różnych części kodu, takich jak słów kluczowych i typów. Ponadto małe, pionowe linie przerywane, w kodzie wskazują, które nawiasy klamrowe zgodne siebie nawzajem, a później zlokalizować kod pomocy numery wierszy. Możesz wybrać znaków minus małe, spakowany, aby zwinąć lub rozwinąć bloków kodu. Ten kod funkcji konspektu można ukrywać kod, który nie jest konieczne, pozwala zminimalizować bałaganu na ekranie. Pliki projektu są wymienione po prawej stronie w oknie o nazwie **Eksplorator rozwiązań**.

   ![Visual Studio IDE z czerwone pola](../media/vs-2019/overview-ide-console-app-red-boxes.png)

   Brak dostępnych inne menu i okien narzędzi, ale Przejdźmy teraz.

1. Teraz uruchom aplikację. Można to zrobić, wybierając pozycję **Uruchom bez debugowania** z menu **Debuguj** na pasku menu. Możesz również nacisnąć klawisz **Ctrl**+**F5**.

   ![Debuguj > Uruchom bez debugowania menu](../media/overview-start-without-debugging.png)

   Program Visual Studio kompiluje aplikację i zostanie otwarte okno konsoli z komunikatem **Hello World!** . Masz teraz uruchomionej aplikacji.

   ![Okno konsoli](../media/vs-2019/overview-console-window.png)

1. Aby zamknąć okno konsoli, naciśnij dowolny klawisz na klawiaturze.

1. Dodajmy dodatkowy kod do aplikacji. Dodaj następujący C# kod przed wierszem, który brzmi `Console.WriteLine("Hello World!");`:

   ```csharp
   Console.WriteLine("\nWhat is your name?");
   var name = Console.ReadLine();
   ```

   Ten kod wyświetla **nazwę użytkownika** w oknie konsoli, a następnie czeka, aż użytkownik wprowadzi jakiś tekst, a następnie klawisz **Enter** .

1. Zmień wiersz, który brzmi `Console.WriteLine("Hello World!");`, do następującego kodu:

   ```csharp
   Console.WriteLine($"\nHello {name}!");
   ```

1. Uruchom aplikację ponownie, wybierając pozycję **debuguj** > **Rozpocznij bez debugowania** lub naciskając klawisz **Ctrl**+**F5**.

   Program Visual Studio ponownie kompiluje aplikację, a okno konsoli otworzy i wyświetli monit o podanie nazwy.

1. Wprowadź swoją nazwę w oknie konsoli i naciśnij klawisz **Enter**.

   ![Okno konsoli](../media/vs-2019/overview-console-input.png)

1. Naciśnij dowolny klawisz, aby zamknąć okno konsoli i zatrzymać uruchomionego programu.

::: moniker-end

## <a name="use-refactoring-and-intellisense"></a>Refaktoryzacja i technologii IntelliSense

Przyjrzyjmy się kilku sposobom, które [Refaktoryzacja](../../ide/refactoring-in-visual-studio.md) i [technologia IntelliSense](../../ide/using-intellisense.md) mogą pomóc w bardziej wydajnym kodzie.

Najpierw Zmień nazwę zmiennej `name`:

1. Kliknij dwukrotnie zmienną `name`, aby ją zaznaczyć.

2. Wpisz nową nazwę zmiennej, **username**.

   Należy zauważyć, że szare pole pojawia się wokół zmienną i żarówka pojawia się na marginesie.

::: moniker range="vs-2017"

3. Wybierz ikonę żarówki, aby wyświetlić dostępne [szybkie akcje](../../ide/quick-actions.md). Wybierz pozycję **Zmień nazwę na "username"** .

   ![Zmień nazwę akcji w programie Visual Studio](../media/rename-quick-action.png)

   Zmienna została zmieniona w projekcie, czyli w tym przypadku tylko dwa miejsca.

   ![Animowany obraz gif przedstawiający Refaktoryzacja zmiany nazwy w programie Visual Studio](../media/rename-refactoring.gif)

::: moniker-end

::: moniker range=">=vs-2019"

3. Wybierz ikonę żarówki, aby wyświetlić dostępne [szybkie akcje](../../ide/quick-actions.md). Wybierz pozycję **Zmień nazwę na "username"** .

   ![Zmień nazwę akcji w programie Visual Studio](../media/vs-2019/rename-quick-action.png)

   Zmienna została zmieniona w projekcie, czyli w tym przypadku tylko dwa miejsca.

::: moniker-end

4. Teraz Przyjrzyjmy się w technologii IntelliSense. Poniżej wiersza, który brzmi `Console.WriteLine($"\nHello {username}!");`, wpisz `DateTime now = DateTime.`.

   W polu są wyświetlane elementy członkowskie klasy <xref:System.DateTime>. Ponadto opis aktualnie zaznaczonego elementu członkowskiego, wyświetla się w osobnym oknie.

   ![Funkcja IntelliSense członków listy w programie Visual Studio](../media/intellisense-list-members.png)

5. Wybierz element członkowski o nazwie **Now**, który jest właściwością klasy, klikając ją dwukrotnie lub naciskając klawisz **Tab**. Wypełnij wiersz kodu, dodając średnik do końca.

6. Poniżej wpisz lub Wklej następujące wiersze kodu:

   ```csharp
   int dayOfYear = now.DayOfYear;

   Console.Write("Day of year: ");
   Console.WriteLine(dayOfYear);
   ```

   > [!TIP]
   > <xref:System.Console.Write%2A?displayProperty=nameWithType> jest nieco inna dla <xref:System.Console.WriteLine%2A?displayProperty=nameWithType>, ponieważ nie dodaje terminatora wiersza po wydrukowaniu. Oznacza to, że w następnej części tekst, który jest wysyłany do danych wyjściowych zostanie wydrukowany na tym samym wierszu. Możesz umieścić kursor każda z tych metod w kodzie, aby wyświetlić jego opis.

7. Następnie użyjemy refaktoryzacji ponownie się nieco bardziej zwięzły widok kodu. Kliknij zmienną `now` w wierszu `DateTime now = DateTime.Now;`.

   Należy zauważyć, że mała ikona śrubokręt pojawia się na marginesie w danym wierszu.

8. Kliknij ikonę śrubokręt, aby zobaczyć, jakie sugestie dotyczące programu Visual Studio jest dostępny. W tym przypadku jest wyświetlana [wbudowana zmienna tymczasowa](../../ide/reference/inline-temporary-variable.md) Refaktoryzacja w celu usunięcia wiersza kodu bez zmiany ogólnego zachowania kodu:

   ![Wbudowane tymczasowej zmiennej Refaktoryzacja w programie Visual Studio](../media/inline-temporary-variable-refactoring.png)

9. Kliknij przycisk **wbudowana zmienna tymczasowa** , aby refaktoryzacji kodu.

::: moniker range="vs-2017"

10. Ponownie uruchom program, naciskając klawisz **Ctrl**+**F5**. Dane wyjściowe wyglądają następująco:

    ![Okno konsoli z danych wyjściowych programu](../media/overview-console-final.png)

::: moniker-end

::: moniker range=">=vs-2019"

10. Ponownie uruchom program, naciskając klawisz **Ctrl**+**F5**. Dane wyjściowe wyglądają następująco:

    ![Okno konsoli z danych wyjściowych programu](../media/vs-2019/overview-console-final.png)

::: moniker-end

## <a name="debug-code"></a>Możliwe jest debugowanie kodu

Podczas pisania kodu, musisz go uruchomić i przetestować go dla błędów. System debugowania programu Visual Studio pozwala krokowo jedną instrukcję kodu w czasie, aby zbadać zmienne, zgodnie z rzeczywistym. Można ustawić *punkty przerwania* , które zatrzymują wykonywanie kodu w konkretnym wierszu. Można zaobserwować, jak wartości zmiennych zmian jako kod jest wykonywany i nie tylko.

Ustawmy punkt przerwania, aby widział wartość zmiennej `username`, gdy program jest "w locie".

1. Znajdź wiersz kodu, który mówi `Console.WriteLine($"\nHello {username}!");`. Aby ustawić punkt przerwania w tym wierszu kodu, oznacza to, aby program wstrzymać wykonanie w tym wierszu kliknij na marginesie po lewej stronie edytora. Możesz również kliknąć dowolne miejsce w wierszu kodu, a następnie nacisnąć klawisz **F9**.

   Czerwony okrąg pojawia się na marginesie po lewej stronie, a kod zostanie wyróżniony czerwonym kolorem.

   ![Punkt przerwania w wierszu kodu w programie Visual Studio](../media/breakpoint.png)

1. Rozpocznij debugowanie, wybierając pozycję **debuguj** > **rozpocząć debugowanie** lub naciskając klawisz **F5**.

1. Gdy zostanie wyświetlone okno konsoli i zostanie wyświetlony monit o podanie nazwy, wpisz ją w i naciśnij klawisz **Enter**.

   Fokus wraca do edytora kodu programu Visual Studio, a wiersz kodu z punktem przerwania zostanie wyróżniony kolorem żółtym. Oznacza to, że jest następnego wiersza kodu, które spowodują wykonanie programu.

1. Przesuń wskaźnik myszy nad zmienną `username`, aby zobaczyć jej wartość. Alternatywnie możesz kliknąć prawym przyciskiem myszy `username` i wybrać polecenie **Dodaj czujkę** , aby dodać zmienną do okna **czujki** , gdzie można także zobaczyć jego wartość.

   ![Wartość zmiennej podczas debugowania w programie Visual Studio](../media/debugging-variable-value.png)

1. Aby pozwolić programowi na zakończenie pracy, naciśnij ponownie klawisz **F5** .

Aby uzyskać więcej informacji na temat debugowania w programie Visual Studio, zobacz [Przewodnik po funkcjach debugera](../../debugger/debugger-feature-tour.md).

## <a name="customize-visual-studio"></a>Dostosuj program Visual Studio

Możesz dostosować interfejsu użytkownika programu Visual Studio, w tym zmiany domyślnego motywu kolorów. Aby przejść do **ciemnego** motywu:

1. Na pasku menu wybierz polecenie **narzędzia** > **Opcje** , aby otworzyć okno dialogowe **Opcje** .

::: moniker range="vs-2017"

2. Na stronie opcje **środowiska** > **Ogólne** Zmień wybór **motywu koloru** na **ciemny**, a następnie wybierz przycisk **OK**.

   Motyw kolorów dla całego środowiska IDE zmieni się na **ciemny**.

   ![Visual Studio z motywu ciemny](../media/dark-theme.png)

::: moniker-end

::: moniker range=">=vs-2019"

2. Na stronie opcje **środowiska** > **Ogólne** Zmień wybór **motywu koloru** na **ciemny**, a następnie wybierz przycisk **OK**.

   Motyw kolorów dla całego środowiska IDE zmieni się na **ciemny**.

   ![Visual Studio z motywu ciemny](../media/vs-2019/dark-theme.png)

::: moniker-end

Aby dowiedzieć się więcej na temat innych sposobów personalizowania środowiska IDE, zobacz [Personalizowanie programu Visual Studio](../../ide/personalizing-the-visual-studio-ide.md).