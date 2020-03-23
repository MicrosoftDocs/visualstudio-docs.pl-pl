---
ms.date: 03/19/2019
ms.technology: vs-ide-general
ms.custom: vs-get-started
ms.author: tglee
author: TerryGLee
manager: jillfra
ms.topic: include
ms.openlocfilehash: c6e715602d0157f52109d7d0bedf25fbd25a23a0
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "79082307"
---
*Zintegrowane środowisko programistyczne* programu Visual Studio to kreatywna klawiatura uruchamiania, której można używać do edytowania, debugowania i tworzenia kodu, a następnie publikowania aplikacji. Zintegrowane środowisko programistyczne (IDE) to bogaty w funkcje program, który może być używany do wielu aspektów tworzenia oprogramowania. Poza standardowym edytorem i debugerem, które zapewnia większość edytorów IDE, program Visual Studio zawiera kompilatory, narzędzia do uzupełniania kodu, projektantów graficznych i wiele innych funkcji ułatwiających proces tworzenia oprogramowania.

::: moniker range="vs-2017"

![Środowisko IDE programu Visual Studio 2017](../media/visual-studio-ide.png)

::: moniker-end

::: moniker range="vs-2019"

[![Środowisko IDE programu Visual Studio 2019](../media/vs-2019/ide-overview.png)](../media/vs-2019/ide-overview.png#lightbox)

::: moniker-end

Ten obraz przedstawia program Visual Studio z otwartym projektem i kilkoma kluczowymi oknami narzędzi, których prawdopodobnie użyjesz:

- [Eksplorator rozwiązań](../../ide/solutions-and-projects-in-visual-studio.md) (w prawym górnym rogu) umożliwia wyświetlanie, nawigację i zarządzanie plikami kodu. **Eksplorator rozwiązań** może pomóc w zorganizowaniu kodu, grupując pliki w [rozwiązania i projekty.](../tutorial-projects-solutions.md)

- [Okno edytora](../../ide/writing-code-in-the-code-and-text-editor.md) (w środku), w którym prawdopodobnie spędzisz większość czasu, wyświetla zawartość pliku. W tym miejscu można edytować kod lub zaprojektować interfejs użytkownika, taki jak okno z przyciskami i polami tekstowymi.

::: moniker range="vs-2017"

- [Okno Dane wyjściowe](../../ide/reference/output-window.md) (centrum dolnego rogu) jest, gdzie Visual Studio wysyła powiadomienia, takie jak debugowanie i komunikaty o błędach, ostrzeżenia kompilatora, publikowanie komunikatów o stanie i więcej. Każde źródło wiadomości ma własną kartę.

::: moniker-end

- [Team Explorer](/azure/devops/user-guide/work-team-explorer?view=vsts) (w prawym dolnym rogu) umożliwia śledzenie elementów roboczych i udostępnianie kodu innym osobom przy użyciu technologii kontroli wersji, takich jak [Git](https://git-scm.com/) i [Team Foundation Version Control (TFVC).](/azure/devops/repos/tfvc/overview?view=vsts)

## <a name="editions"></a>Wersje

::: moniker range="vs-2017"

Program Visual Studio jest dostępny dla systemów Windows i Mac. [Visual Studio dla komputerów Mac](/visualstudio/mac/) ma wiele takich samych funkcji jak Visual Studio 2017 i jest zoptymalizowany pod kątem tworzenia aplikacji wieloplatformowych i mobilnych. W tym artykule skupiono się na wersji programu Visual Studio 2017 dla systemu Windows.

Istnieją trzy wersje programu Visual Studio: Community, Professional i Enterprise. Zobacz [Porównanie wersji programu Visual Studio,](https://visualstudio.microsoft.com/vs/compare/) aby dowiedzieć się, które funkcje są obsługiwane w każdej wersji.

::: moniker-end

::: moniker range="vs-2019"

Program Visual Studio jest dostępny dla systemów Windows i Mac. [Visual Studio dla komputerów Mac](/visualstudio/mac/) ma wiele takich samych funkcji jak Visual Studio 2019 i jest zoptymalizowany pod kątem tworzenia aplikacji wieloplatformowych i mobilnych. W tym artykule skupiono się na wersji programu Visual Studio 2019 dla systemu Windows.

Istnieją trzy wersje programu Visual Studio 2019: Community, Professional i Enterprise. Zobacz [Porównanie wersji programu Visual Studio,](https://visualstudio.microsoft.com/vs/compare/) aby dowiedzieć się, które funkcje są obsługiwane w każdej wersji.

::: moniker-end

## <a name="popular-productivity-features"></a>Popularne funkcje zwiększające produktywność

Niektóre z popularnych funkcji w programie Visual Studio, które pomagają być bardziej wydajne w miarę tworzenia oprogramowania obejmują:

- Squiggles i [szybkie akcje](../../ide/quick-actions.md)

   Squiggles są faliste podkreśla, że alerty o błędach lub potencjalnych problemów w kodzie podczas pisania. Te wskazówki wizualne umożliwiają natychmiastowe rozwiązywanie problemów bez oczekiwania na wykrycie błędu podczas kompilacji lub po uruchomieniu programu. Po umieszczeniu wskaźnika myszy na fali, zostaną wyświetlene dodatkowe informacje o błędzie. Żarówka może również pojawić się na lewym marginesie z akcjami, znanymi jako Szybkie akcje, aby naprawić błąd.

   ![Squiggles w programie Visual Studio](../media/squiggles-error.png)

::: moniker range=">=vs-2019"

- Oczyszczanie kodu

   Za pomocą kliknięcia przycisku sformatuj kod i zastosuj wszelkie poprawki kodu sugerowane przez [ustawienia stylu kodu](../../ide/reference/options-text-editor-csharp-formatting.md), [.editorconfig conventions](../../ide/create-portable-custom-editor-options.md)i [Roslyn analyzers](../../code-quality/roslyn-analyzers-overview.md). **Oczyszczanie kodu** pomaga rozwiązać problemy w kodzie, zanim przejdzie do przeglądu kodu. (Obecnie dostępne tylko dla kodu języka C#).

   ![Przycisk Oczyszczanie kodu w programie Visual Studio](../media/vs-2019/code-cleanup.png)

::: moniker-end

- [Refaktoryzacja](../../ide/refactoring-in-visual-studio.md)

   Refaktoryzowanie obejmuje operacje, takie jak inteligentna zmiana nazwy zmiennych, wyodrębnianie jednego lub więcej wierszy kodu do nowej metody, zmiana kolejności parametrów metody i inne.

   ![Refaktoryzacja w programie Visual Studio](../media/refactoring-menu.png)

- [IntelliSense](../../ide/using-intellisense.md)

   IntelliSense to termin dla zestawu funkcji, który wyświetla informacje o kodzie bezpośrednio w edytorze i, w niektórych przypadkach, zapis małych fragmentów kodu dla Ciebie. To tak, jakby mieć podstawową dokumentację w edytorze, co pozwala zaoszczędzić od konieczności wyszukiwania informacji o typie w innym miejscu. Funkcje IntelliSense różnią się w zależności od języka. Aby uzyskać więcej informacji, zobacz [C# IntelliSense](../../ide/visual-csharp-intellisense.md), [Visual C++ IntelliSense](../../ide/visual-cpp-intellisense.md), [JavaScript IntelliSense](../../ide/javascript-intellisense.md)i [Visual Basic IntelliSense](../../ide/visual-basic-specific-intellisense.md). Na poniższej ilustracji pokazano, jak intellisense wyświetla listę członków dla danego typu:

   ![Lista członków programu Visual Studio](../media/intellisense-list-members.png)

- Pole wyszukiwania

   Visual Studio może wydawać się przytłaczające czasami z tak wielu menu, opcje i właściwości. Pole wyszukiwania to świetny sposób na szybkie znalezienie potrzebnych w programie Visual Studio. Po rozpoczęciu wpisywania nazwy czegoś, czego szukasz, Visual Studio wyświetla wyniki, które zajmą Cię dokładnie tam, gdzie musisz się udać. Jeśli chcesz dodać funkcje do programu Visual Studio, na przykład, aby dodać obsługę dodatkowego języka programowania, pole wyszukiwania zawiera wyniki, które otwierają Instalatora programu Visual Studio, aby zainstalować obciążenie lub pojedynczy składnik.

   > [!TIP]
   > Naciśnij **klawisz Ctrl**+**Q** jako skrót do pola wyszukiwania.

   ::: moniker range="vs-2017"

   ![Pole wyszukiwania Szybkie uruchamianie w programie Visual Studio 2017](../media/quick-launch-nuget.png)

   Aby uzyskać więcej informacji, zobacz [Szybkie uruchamianie](../../ide/reference/quick-launch-environment-options-dialog-box.md).

   ::: moniker-end

   ::: moniker range="vs-2019"

   ![Pole wyszukiwania w programie Visual Studio 2019](../media/vs-2019/quick-launch-nuget.png)

   ::: moniker-end

- [Live Share](/visualstudio/liveshare/)

   Wspólnie edytuj i debuguj z innymi osobami w czasie rzeczywistym, niezależnie od typu aplikacji lub języka programowania. Możesz natychmiast i bezpiecznie udostępniać swój projekt i, w razie potrzeby, debugowanie sesji, wystąpień terminali, aplikacji sieci web localhost, połączeń głosowych i innych.

- [Hierarchia wywołań](../../ide/reference/call-hierarchy.md)

   Okno **Hierarchia wywołań** pokazuje metody, które wywołują wybraną metodę. Może to być przydatne informacje, gdy myślisz o zmianie lub usunięciu metody lub gdy próbujesz wyśledzić błąd.

   ![Okno Hierarchia połączeń](../../ide/reference/media/call-hierarchy-csharp-expanded.png)

- [CodeLens](../../ide/find-code-changes-and-other-history-with-codelens.md)

   CodeLens pomaga znaleźć odwołania do kodu, zmiany w kodzie, połączone błędy, elementy robocze, przeglądy kodu i testy jednostkowe, wszystko bez opuszczania edytora.

   ![CodeLens](../media/codelens-overview.png)

- [Przejdź do definicji](../../ide/go-to-and-peek-definition.md)

   Funkcja Przejdź do definicji prowadzi bezpośrednio do lokalizacji, w której zdefiniowano funkcję lub typ.

   ![Przejdź do definicji](../media/go-to-definition-menu.png)

- [Podejrzyj definicję](../../ide/how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12.md)

   Okno **Definicja wglądu** zawiera definicję metody lub typu bez otwierania oddzielnego pliku.

   ![Wgląd do definicji](../media/peek-definition.png)

## <a name="install-the-visual-studio-ide"></a>Instalowanie środowiska IDE programu Visual Studio

W tej sekcji utworzysz prosty projekt, aby wypróbować niektóre czynności, które można wykonać za pomocą programu Visual Studio. Użyjesz [IntelliSense](../../ide/using-intellisense.md) jako pomocy kodowania, debugować aplikację, aby zobaczyć wartość zmiennej podczas wykonywania programu i zmienić motyw kolorów.

::: moniker range="vs-2017"

Aby rozpocząć, [pobierz program Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) i zainstaluj go w systemie. Modułowy instalator umożliwia wybór i *zainstalowanie obciążeń,* które są grupami funkcji potrzebnych do preferowanego języka programowania lub platformy. Aby wykonać kroki dotyczące [tworzenia programu,](#create-a-program)należy wybrać obciążenie **programowe .NET Core podczas** instalacji.

::: moniker-end

::: moniker range=">=vs-2019"

Aby rozpocząć, [pobierz program Visual Studio](https://visualstudio.microsoft.com/downloads) i zainstaluj go w systemie. Modułowy instalator umożliwia wybór i *zainstalowanie obciążeń,* które są grupami funkcji potrzebnych do preferowanego języka programowania lub platformy. Aby wykonać kroki dotyczące [tworzenia programu,](#create-a-program)należy wybrać obciążenie **programowe .NET Core podczas** instalacji.

::: moniker-end

![Wieloplatformowe obciążenie programowe .NET Core w Instalatorze programu Visual Studio](../media/dotnet-core-cross-platform-workload.png)

Po otwarciu programu Visual Studio po raz pierwszy można opcjonalnie [zalogować się](../../ide/signing-in-to-visual-studio.md) przy użyciu konta Microsoft lub konta służbowego.

## <a name="create-a-program"></a>Tworzenie programu

Zanurkujmy i stwórzmy prosty program.

::: moniker range="vs-2017"

1. Otwórz program Visual Studio.

1. Na pasku menu wybierz pozycję **Plik** > **nowego** > **projektu**.

   ![Plik > nowy projekt na pasku menu](../media/file-new-project-menu.png)

   W oknie dialogowym **Nowy projekt** przedstawiono kilka *szablonów*projektów . Szablon zawiera podstawowe pliki i ustawienia potrzebne dla danego typu projektu.

1. Wybierz kategorię szablonu **.NET Core** w obszarze **Visual C#**, a następnie wybierz szablon **Aplikacji konsoli (net core).** W polu tekstowym **Nazwa** wpisz **HelloWorld**, a następnie wybierz przycisk **OK.**

   ![Szablon aplikacji .NET Core](../media/overview-new-project-dialog.png)

   > [!NOTE]
   > Jeśli nie widzisz kategorii **.NET Core,** musisz zainstalować obciążenie **programistyczne .NET Core na różnych platformach.** Aby to zrobić, wybierz łącze **Instalatora programu Visual Visual Studio** w lewym dolnym rogu okna dialogowego Nowy **projekt.** Po otwarciu Instalatora programu Visual Studio przewiń w dół i wybierz **wieloplatformowe obciążenie programowe .NET Core,** a następnie wybierz pozycję **Modyfikuj**.

   Visual Studio tworzy projekt. Jest to prosta aplikacja "Hello World", <xref:System.Console.WriteLine?displayProperty=nameWithType> która wywołuje metodę wyświetlania dosłownego ciągu "Hello World!" w oknie konsoli (dane wyjściowe programu).

   Wkrótce powinieneś zobaczyć coś następującego:

   ![Visual Studio IDE](../media/overview-ide-console-app.png)

   Kod języka C# dla aplikacji pokazuje w oknie edytora, który zajmuje większość miejsca. Należy zauważyć, że tekst jest automatycznie kolorowane, aby wskazać różne części kodu, takich jak słowa kluczowe i typy. Ponadto małe, pionowe linie przerywane w kodzie wskazują, które nawiasy klamrowe są do siebie zgodne, a numery wierszy ułatwiają późniejsze zlokalizowanie kodu. Można wybrać małe, pudełkowe znaki minus do zwinięcia lub rozwinięcia bloków kodu. Ta funkcja tworzenia kodu umożliwia ukrycie kodu, którego nie potrzebujesz, co pomaga zminimalizować bałagan na ekranie. Pliki projektu są wyświetlane po prawej stronie w oknie o nazwie **Eksplorator rozwiązań**.

   ![Środowiska IDE programu Visual Studio z czerwonymi polami](../media/overview-ide-console-app-red-boxes.png)

   Dostępne są inne menu i okna narzędzi, ale przejdźmy dalej.

1. Teraz uruchom aplikację. Można to zrobić, wybierając **przycisk Start bez debugowania** z menu **Debugowania** na pasku menu. Można również nacisnąć **klawisz Ctrl**+**F5**.

   ![Debugowanie > Start bez menu debugowania](../media/overview-start-without-debugging.png)

   Visual Studio tworzy aplikację, a okno konsoli otwiera się z komunikatem **Hello World!**. Masz teraz aplikację do biegania!

   ![Okno konsoli](../media/overview-console-window.png)

1. Aby zamknąć okno konsoli, naciśnij dowolny klawisz na klawiaturze.

1. Dodajmy dodatkowy kod do aplikacji. Dodaj następujący kod C# przed `Console.WriteLine("Hello World!");`wierszem, który mówi:

   ```csharp
   Console.WriteLine("\nWhat is your name?");
   var name = Console.ReadLine();
   ```

   Ten kod wyświetla **nazwę użytkownika** w oknie konsoli, a następnie poczeka, aż użytkownik wprowadzi tekst, po którym następuje klawisz **Enter.**

1. Zmień wiersz, `Console.WriteLine("Hello World!");` który jest zgodny z następującym kodem:

   ```csharp
   Console.WriteLine($"\nHello {name}!");
   ```

1. Uruchom aplikację ponownie, wybierając **debugowanie** > **start bez debugowania** lub naciskając klawisz **Ctrl**+**F5**.

   Visual Studio odbudowuje aplikację, a okno konsoli otwiera się i monituje o nazwę.

1. Wpisz swoje imię i nazwisko w oknie konsoli i naciśnij klawisz **Enter**.

   ![Wejście okna konsoli](../media/overview-console-input.png)

1. Naciśnij dowolny klawisz, aby zamknąć okno konsoli i zatrzymać uruchomiony program.

::: moniker-end

::: moniker range=">=vs-2019"

1. Otwórz program Visual Studio.

   Okno startowe jest wyświetlane z różnymi opcjami klonowania repozytorium, otwierania najnowszego projektu lub tworzenia zupełnie nowego projektu.

1. Wybierz **pozycję Utwórz nowy projekt**.

   ![Okno startowe programu Visual Studio tworzy nowy projekt](../media/vs-2019/start-window-create-new-project.png)

   Zostanie otwarte okno **Utwórz nowy projekt** i zostanie wyświetleń kilka *szablonów*projektu . Szablon zawiera podstawowe pliki i ustawienia potrzebne dla danego typu projektu.

1. Aby znaleźć szablon, który chcemy, wpisz lub wpisz **konsolę .net core** w polu wyszukiwania. Lista dostępnych szablonów jest automatycznie filtrowana na podstawie wprowadzonych słów kluczowych. Można dodatkowo filtrować wyniki szablonu, wybierając **C#** z listy rozwijanej **Język.** Wybierz szablon **Aplikacji konsoli (.NET Core),** a następnie wybierz pozycję **Dalej**.

    ![Utworzenie nowego projektu w Visual Studio](../media/vs-2019/create-new-project.png)

1. W oknie **Konfigurowanie nowego projektu** wprowadź **helloworld** w polu **Nazwa projektu,** opcjonalnie zmień lokalizację katalogu dla plików projektu, a następnie wybierz pozycję **Utwórz**.

   ![Konfigurowanie nowego projektu w programie Visual Studio](../media/vs-2019/configure-new-project.png)

   Visual Studio tworzy projekt. Jest to prosta aplikacja "Hello World", <xref:System.Console.WriteLine?displayProperty=nameWithType> która wywołuje metodę wyświetlania dosłownego ciągu "Hello World!" w oknie konsoli (dane wyjściowe programu).

   Wkrótce powinieneś zobaczyć coś następującego:

   ![Visual Studio IDE](../media/vs-2019/overview-ide-console-app.png)

   Kod języka C# dla aplikacji pokazuje w oknie edytora, który zajmuje większość miejsca. Należy zauważyć, że tekst jest automatycznie kolorowane, aby wskazać różne części kodu, takich jak słowa kluczowe i typy. Ponadto małe, pionowe linie przerywane w kodzie wskazują, które nawiasy klamrowe są do siebie zgodne, a numery wierszy ułatwiają późniejsze zlokalizowanie kodu. Można wybrać małe, pudełkowe znaki minus do zwinięcia lub rozwinięcia bloków kodu. Ta funkcja tworzenia kodu umożliwia ukrycie kodu, którego nie potrzebujesz, co pomaga zminimalizować bałagan na ekranie. Pliki projektu są wyświetlane po prawej stronie w oknie o nazwie **Eksplorator rozwiązań**.

   ![Środowiska IDE programu Visual Studio z czerwonymi polami](../media/vs-2019/overview-ide-console-app-red-boxes.png)

   Dostępne są inne menu i okna narzędzi, ale przejdźmy dalej.

1. Teraz uruchom aplikację. Można to zrobić, wybierając **przycisk Start bez debugowania** z menu **Debugowania** na pasku menu. Można również nacisnąć **klawisz Ctrl**+**F5**.

   ![Debugowanie > Start bez menu debugowania](../media/overview-start-without-debugging.png)

   Visual Studio tworzy aplikację, a okno konsoli otwiera się z komunikatem **Hello World!**. Masz teraz aplikację do biegania!

   ![Okno konsoli](../media/vs-2019/overview-console-window.png)

1. Aby zamknąć okno konsoli, naciśnij dowolny klawisz na klawiaturze.

1. Dodajmy dodatkowy kod do aplikacji. Dodaj następujący kod C# przed `Console.WriteLine("Hello World!");`wierszem, który mówi:

   ```csharp
   Console.WriteLine("\nWhat is your name?");
   var name = Console.ReadLine();
   ```

   Ten kod wyświetla **nazwę użytkownika** w oknie konsoli, a następnie poczeka, aż użytkownik wprowadzi tekst, po którym następuje klawisz **Enter.**

1. Zmień wiersz, `Console.WriteLine("Hello World!");` który jest zgodny z następującym kodem:

   ```csharp
   Console.WriteLine($"\nHello {name}!");
   ```

1. Uruchom aplikację ponownie, wybierając **debugowanie** > **start bez debugowania** lub naciskając klawisz **Ctrl**+**F5**.

   Visual Studio odbudowuje aplikację, a okno konsoli otwiera się i monituje o nazwę.

1. Wpisz swoje imię i nazwisko w oknie konsoli i naciśnij klawisz **Enter**.

   ![Okno konsoli](../media/vs-2019/overview-console-input.png)

1. Naciśnij dowolny klawisz, aby zamknąć okno konsoli i zatrzymać uruchomiony program.

::: moniker-end

## <a name="use-refactoring-and-intellisense"></a>Korzystanie z refaktoryzacji i technologii IntelliSense

Przyjrzyjmy się kilku sposobom [refaktoryzacji](../../ide/refactoring-in-visual-studio.md) i [intellisense](../../ide/using-intellisense.md) może pomóc w bardziej efektywnym kodowaniu.

Najpierw zmieńmy nazwę zmiennej: `name`

1. Kliknij dwukrotnie `name` zmienną, aby ją zaznaczyć.

2. Wpisz nową nazwę zmiennej, **nazwę użytkownika**.

   Zwróć uwagę, że wokół zmiennej pojawia się szare pole, a na marginesie pojawi się żarówka.

::: moniker range="vs-2017"

3. Wybierz ikonę żarówki, aby wyświetlić dostępne [szybkie akcje](../../ide/quick-actions.md). Wybierz **zmień nazwę "name" na "username".**

   ![Zmienianie nazwy akcji w programie Visual Studio](../media/rename-quick-action.png)

   Zmiana zmiennej jest zmieniana w całym projekcie, który w naszym przypadku jest tylko dwa miejsca.

   ![Animowany gif z poleceniem zmiany nazwy refaktoryzacji w programie Visual Studio](../media/rename-refactoring.gif)

::: moniker-end

::: moniker range=">=vs-2019"

3. Wybierz ikonę żarówki, aby wyświetlić dostępne [szybkie akcje](../../ide/quick-actions.md). Wybierz **zmień nazwę "name" na "username".**

   ![Zmienianie nazwy akcji w programie Visual Studio](../media/vs-2019/rename-quick-action.png)

   Zmiana zmiennej jest zmieniana w całym projekcie, który w naszym przypadku jest tylko dwa miejsca.

::: moniker-end

4. Teraz rówmy się na IntelliSense. Poniżej linii, `Console.WriteLine($"\nHello {username}!");`która `DateTime now = DateTime.`mówi , wpisz .

   W polu są wyświetlane <xref:System.DateTime> elementy członkowskie klasy. Ponadto opis aktualnie wybranego elementu członkowskiego jest wyświetlany w osobnym polu.

   ![Członkowie listy IntelliSense w programie Visual Studio](../media/intellisense-list-members.png)

5. Wybierz element członkowski o nazwie **Teraz**, który jest właściwością klasy, klikając dwukrotnie na nią lub naciskając **klawisz Tab**. Uzupełnij wiersz kodu, dodając średnik na końcu.

6. Poniżej wpisz lub wklej następujące wiersze kodu:

   ```csharp
   int dayOfYear = now.DayOfYear;

   Console.Write("Day of year: ");
   Console.WriteLine(dayOfYear);
   ```

   > [!TIP]
   > <xref:System.Console.Write%2A?displayProperty=nameWithType>jest trochę inny, <xref:System.Console.WriteLine%2A?displayProperty=nameWithType> ponieważ nie dodaje terminatora linii po wydrukowaniu. Oznacza to, że następny fragment tekstu, który jest wysyłany do danych wyjściowych zostanie wydrukowany w tym samym wierszu. Możesz najechać kursorem na każdą z tych metod w kodzie, aby wyświetlić ich opis.

7. Następnie użyjemy refaktoryzacji ponownie, aby kod był nieco bardziej zwięzły. Kliknij zmienną `now` w `DateTime now = DateTime.Now;`wierszu .

   Zwróć uwagę, że na marginesie w tej linii pojawia się mała ikona śrubokręta.

8. Kliknij ikonę śrubokręta, aby zobaczyć, jakie sugestie visual studio ma dostępne. W takim przypadku jest pokazano [inline tymczasowej zmiennej](../../ide/reference/inline-temporary-variable.md) refaktoryzacji, aby usunąć wiersz kodu bez zmiany ogólnego zachowania kodu:

   ![Wbudowana tymczasowa refaktoryzatoring zmiennej w programie Visual Studio](../media/inline-temporary-variable-refactoring.png)

9. Kliknij **inline zmienną tymczasową,** aby refaktoryzuje kod.

::: moniker range="vs-2017"

10. Uruchom program ponownie, naciskając **klawisz Ctrl**+**F5**. Dane wyjściowe wyglądają mniej więcej tak:

    ![Okno konsoli z wyjściem programu](../media/overview-console-final.png)

::: moniker-end

::: moniker range=">=vs-2019"

10. Uruchom program ponownie, naciskając **klawisz Ctrl**+**F5**. Dane wyjściowe wyglądają mniej więcej tak:

    ![Okno konsoli z wyjściem programu](../media/vs-2019/overview-console-final.png)

::: moniker-end

## <a name="debug-code"></a>Kod debugowania

Podczas pisania kodu, należy go uruchomić i przetestować go pod kątem błędów. System debugowania programu Visual Studio umożliwia przechodzenie przez kod po jednej instrukcji naraz i sprawdzanie zmiennych w trakcie podróży. Można ustawić *punkty przerwania,* które zatrzymują wykonywanie kodu w określonym wierszu. Można zaobserwować, jak zmienia się wartość zmiennej w miarę działania kodu i nie tylko.

Ustawmy punkt przerwania, aby zobaczyć `username` wartość zmiennej, gdy program jest "w locie".

1. Znajdź wiersz kodu, `Console.WriteLine($"\nHello {username}!");`który mówi . Aby ustawić punkt przerwania w tym wierszu kodu, to znaczy, aby program wstrzymał wykonanie w tym wierszu, kliknij na lewym marginesie edytora. Można również kliknąć w dowolnym miejscu w wierszu kodu, a następnie nacisnąć **klawisz F9**.

   Czerwony okrąg pojawia się na lewym marginesie, a kod jest wyróżniony na czerwono.

   ![Punkt przerwania w wierszu kodu w programie Visual Studio](../media/breakpoint.png)

1. Rozpocznij debugowanie, wybierając **debugowanie** > **startowe debugowanie** lub naciskając **klawisz F5**.

1. Gdy pojawi się okno konsoli i pojawi się pytanie o podanie imienia i nazwiska, wpisz ją i naciśnij klawisz **Enter**.

   Fokus powraca do edytora kodu programu Visual Studio, a wiersz kodu z punktem przerwania jest wyróżniony na żółto. Oznacza to, że jest to następny wiersz kodu, który program zostanie wykonany.

1. Najedź kursorem myszy na zmienną, `username` aby zobaczyć jej wartość. Możesz też kliknąć prawym `username` przyciskiem myszy i wybrać pozycję **Dodaj zegarek,** aby dodać zmienną do okna **Czujka,** w którym można również zobaczyć jej wartość.

   ![Wartość zmiennej podczas debugowania w programie Visual Studio](../media/debugging-variable-value.png)

1. Aby program został ukończony, naciśnij ponownie klawisz **F5.**

Aby uzyskać więcej informacji na temat debugowania w programie Visual Studio, zobacz [Przewodnik funkcji debugera](../../debugger/debugger-feature-tour.md).

## <a name="customize-visual-studio"></a>Dostosowywanie programu Visual Studio

Można spersonalizować interfejs użytkownika programu Visual Studio, w tym zmienić domyślny motyw kolorów. Aby zmienić motyw **Ciemny:**

1. Na pasku menu wybierz pozycję**Opcje** **narzędzi,** > aby otworzyć okno dialogowe **Opcje.**

::: moniker range="vs-2017"

2. Na stronie Opcje **ogólne** **środowiska** > zmień wybór **motywu Kolor** na **Ciemny**, a następnie wybierz przycisk **OK**.

   Motyw kolorów dla całego IDE zmienia się na **Ciemny**.

   ![Visual Studio w ciemnym motywie](../media/dark-theme.png)

::: moniker-end

::: moniker range=">=vs-2019"

2. Na stronie Opcje **ogólne** **środowiska** > zmień wybór **motywu Kolor** na **Ciemny**, a następnie wybierz przycisk **OK**.

   Motyw kolorów dla całego IDE zmienia się na **Ciemny**.

   ![Visual Studio w ciemnym motywie](../media/vs-2019/dark-theme.png)

::: moniker-end

Aby dowiedzieć się więcej o innych sposobach personalizowania ide, zobacz [Personalizuj program Visual Studio](../../ide/personalizing-the-visual-studio-ide.md).