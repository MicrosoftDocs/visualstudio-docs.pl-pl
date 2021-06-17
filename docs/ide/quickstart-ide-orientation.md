---
title: 'Szybki start: przewodnik po Visual Studio IDE'
description: Dowiedz się więcej o niektórych oknach, menu i innych funkcjach interfejsu użytkownika Visual Studio zintegrowanym środowisku projektowym (IDE).
ms.custom: acquisition
titleSuffix: ''
ms.date: 03/02/2021
ms.topic: quickstart
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 1f10c3fcca5d87f8371d1373314406cf4aa47ec3
ms.sourcegitcommit: 1f27f33852112702ee35fbc0c02fba37899e4cf5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/15/2021
ms.locfileid: "112113225"
---
# <a name="quickstart-first-look-at-the-visual-studio-ide"></a>Szybki start: pierwsze spojrzenie na Visual Studio IDE

W tym 5-10-minutowym wprowadzeniu do zintegrowanego środowiska projektowego (IDE) usługi Visual Studio zajmiemy się niektórymi oknami, menu i innymi funkcjami interfejsu użytkownika.

::: moniker range="vs-2017"

Jeśli jeszcze nie zainstalowano programu Visual Studio, przejdź do strony [pobierania](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) Visual Studio, aby zainstalować ją bezpłatnie.

::: moniker-end

::: moniker range=">=vs-2019"

Jeśli jeszcze nie zainstalowano programu Visual Studio, przejdź do strony [pobierania](https://visualstudio.microsoft.com/downloads) Visual Studio, aby zainstalować ją bezpłatnie.

::: moniker-end

::: moniker range="vs-2017"

## <a name="start-page"></a>Strona początkowa

Pierwszą rzeczą, którą zobaczysz po otwarciu Visual Studio jest najprawdopodobniej **strona startowa**. Strona **startowa została** zaprojektowana jako "centrum", aby ułatwić szybsze znajdowanie potrzebnych poleceń i plików projektu. W **sekcji** Ostatnie są wyświetlane projekty i foldery, nad których ostatnio pracowaliśmy. W **obszarze Nowy** projekt możesz kliknąć link, aby otworzyć okno dialogowe Nowy projekt, lub w obszarze Otwórz możesz otworzyć istniejący projekt kodu lub folder.  Po prawej stronie znajduje się kanał informacyjny z najnowszymi wiadomościami dla deweloperów.

![Strona startowa w Visual Studio](media/start-page.png)

Jeśli zamkniesz **stronę startową i** chcesz zobaczyć ją ponownie, możesz otworzyć ją ponownie z menu **Plik.**

![Menu Plik w Visual Studio](media/quickstart-IDE-file-menu-large.png)

::: moniker-end

::: moniker range=">=vs-2019"

## <a name="start-window"></a> Okno uruchamiania

Pierwszą rzeczą, którą zobaczysz po otwarciu okna Visual Studio jest okno uruchamiania. Okno uruchamiania zostało zaprojektowane tak, aby ułatwić szybsze "uzyskiwanie dostępu do kodu". Oferuje on opcje klonowania lub wyewidencjiowania kodu, otwierania istniejącego projektu lub rozwiązania, tworzenia nowego projektu lub po prostu otwierania folderu zawierającego niektóre pliki kodu.

[![Okno uruchamiania w Visual Studio 2019 r.](media/vs-2019/start-window-labeled.png)](media/vs-2019/start-window-labeled.png#lightbox)

Jeśli używasz listy Visual Studio po raz pierwszy, lista ostatnich projektów będzie pusta.

Jeśli pracujesz z bazami kodu nie opartymi na programie MSBuild, użyjesz opcji Otwórz **folder** lokalny, aby otworzyć kod w Visual Studio. Aby uzyskać więcej informacji, zobacz Develop code in Visual Studio without projects or solutions (Tworzenie kodu w Visual Studio [bez projektów i rozwiązań).](develop-code-in-visual-studio-without-projects-or-solutions.md) W przeciwnym razie możesz utworzyć nowy projekt lub sklonować projekt od dostawcy źródłowego, takiego jak GitHub lub Azure DevOps.

Opcja **Kontynuuj bez kodu** po prostu otwiera Visual Studio dewelopera bez żadnego załadowanego konkretnego projektu lub kodu. Możesz wybrać tę opcję, aby dołączyć do [Live Share](/visualstudio/liveshare/) lub dołączyć do procesu debugowania. Możesz również nacisnąć klawisz **Esc,** aby zamknąć okno uruchamiania i otworzyć ideę .

::: moniker-end

## <a name="create-a-project"></a>Tworzenie projektu

Aby kontynuować eksplorowanie Visual Studio funkcji, utwórzmy nowy projekt.

::: moniker range="vs-2017"

1. Na **stronie startowej** w polu wyszukiwania w  obszarze Nowy projekt wpisz w konsoli , aby filtrować listę typów projektów do tych, które zawierają w nazwie "console".

   ![Wyszukiwanie szablonów projektów na Visual Studio startowej](media/start-page-search-templates.png)

   Visual Studio udostępnia różne rodzaje szablonów projektów, które ułatwiają szybkie rozpoczynanie kodowania. Wybierz szablon projektu Aplikacja konsolowa w języku C# **(.NET Core).** (Alternatywnie, jeśli jesteś deweloperem języka Visual Basic, C++, JavaScript lub innym deweloperem języka, możesz utworzyć projekt w jednym z tych języków. Interfejs użytkownika, którego będziemy się przyglądać, jest podobny dla wszystkich języków programowania).

1. W **wyświetlonym oknie** dialogowym Nowy projekt zaakceptuj domyślną nazwę projektu i wybierz przycisk **OK.**

::: moniker-end

::: moniker range=">=vs-2019"

1. W oknie uruchamiania wybierz pozycję **Utwórz nowy projekt.**

    :::image type="content" source="../get-started/media/vs-2019/start-window-create-new-project.png" alt-text="Zrzut ekranu przedstawiający okno &quot;Tworzenie nowego projektu&quot; w Visual Studio 2019 r.":::

   Zostanie **otwarte okno Tworzenie nowego** projektu z kilkoma *szablonami projektów.* Szablon zawiera podstawowe pliki i ustawienia wymagane dla danego typu projektu.

   W tym miejscu możesz wyszukiwać, filtrować i wybierać szablon projektu. Zostanie również wyświetlona lista ostatnio używanych szablonów projektów.

1. W polu wyszukiwania u góry  wpisz w konsoli, aby filtrować listę typów projektów do tych, które zawierają w nazwie "console". Dodatkowo uściślij wyniki wyszukiwania, wybierając język **C#**  (lub inny język) z listy rozwijanej Wszystkie języki.

    :::image type="content" source="media/vs-2019/create-new-project.png" alt-text="Zrzut ekranu przedstawiający okno &quot;Tworzenie nowego projektu&quot; w programie Visual Studio 2019, w którym wybierasz szablon.":::

1. Jeśli jako język wybrano język C#, Visual Basic lub F#, wybierz szablon **Aplikacja konsolowa,** a następnie wybierz **przycisk Dalej.** (Jeśli wybrano inny język, po prostu wybierz dowolny szablon. Interfejs użytkownika, którego będziemy się przyglądać, jest podobny dla wszystkich języków programowania).

1. W **oknie Konfigurowanie nowego** projektu zaakceptuj domyślną nazwę i lokalizację projektu, a następnie wybierz pozycję **Dalej.**

    :::image type="content" source="media/vs-2019/configure-new-project-console.png" alt-text="Zrzut ekranu przedstawiający okno &quot;Konfigurowanie nowego projektu&quot; Visual Studio 2019 r., w którym wprowadzasz nazwę projektu.":::

1. W **oknie Dodatkowe informacje** sprawdź, czy program **.NET Core 3.1** jest wyświetlany w menu rozwijanych **Target Framework,** a następnie kliknij pozycję **Utwórz.**

    :::image type="content" source="../get-started/media/vs-2019/create-project-additional-info.png" alt-text="Zrzut ekranu przedstawiający okno &quot;Dodatkowe informacje&quot; w programie Visual Studio 2019, w którym wybierasz wersję programu .NET Core Framework.":::

::: moniker-end

   Projekt zostanie utworzony, a w oknie edytora zostanie otwarty **plik** o nazwie *Program.cs.* Edytor **pokazuje** zawartość plików i jest to miejsce, w którym większość pracy z kodowaniem będziesz robić w Visual Studio.

   ![Edytor w Visual Studio](media/editor.png)

## <a name="solution-explorer"></a>Eksplorator rozwiązań

**Eksplorator rozwiązań**, która zazwyczaj znajduje się po prawej stronie witryny Visual Studio, przedstawia graficzną reprezentację hierarchii plików i folderów w projekcie, rozwiązaniu lub folderze kodu. Możesz przeglądać hierarchię i przechodzić do pliku w **Eksplorator rozwiązań**.

![Eksplorator rozwiązań w Visual Studio](media/quickstart-IDE-solution-explorer.png)

## <a name="menus"></a>Menu

Pasek menu w górnej części menu Visual Studio grupuje polecenia w kategorie. Na przykład menu **Projekt** zawiera polecenia związane z projektem, nad który pracujesz. W menu **Narzędzia** możesz dostosować sposób zachowania Visual Studio, wybierając pozycję Opcje **lub** dodaj funkcje do instalacji, wybierając pozycję Pobierz narzędzia i **funkcje.**

::: moniker range="vs-2017"

![Pasek menu w programie Visual Studio 2017](media/quickstart-IDE-menu-bar.png)

::: moniker-end

::: moniker range=">=vs-2019"

![Pasek menu w programie Visual Studio 2019](media/vs-2019/menu-bar.png)

::: moniker-end

## <a name="error-list"></a>Lista błędów

Otwórz okno **Lista błędów,** wybierając menu **Widok,** a następnie pozycję **Lista błędów**.

Lista **błędów zawiera** błędy, ostrzeżenia i komunikaty dotyczące bieżącego stanu kodu. Jeśli w pliku lub w dowolnym miejscu projektu występują błędy (na przykład brak nawiasu klamrowego lub średnika), są one wyświetlane w tym miejscu.

![Lista błędów w Visual Studio](media/quickstart-IDE-error-list.png)

## <a name="output-window"></a>Okno wyniku

W **oknie** Dane wyjściowe są wyświetlane komunikaty wyjściowe z budowania projektu i od dostawcy kontroli źródła.

Skompilowajmy projekt, aby wyświetlić dane wyjściowe kompilacji. W menu **Kompilacja** wybierz pozycję **Build Solution (Skompilowanie rozwiązania).** Okno **Dane wyjściowe** automatycznie uzyskuje fokus i wyświetla komunikat o pomyślnej kompilacji.

![Okno danych wyjściowych w Visual Studio](media/build-output-minimal.png)

## <a name="search-box"></a>Pole wyszukiwania

Pole wyszukiwania to szybki i łatwy sposób nawigowania do niemal wszystkich Visual Studio. Możesz wprowadzić tekst związany z tym, co chcesz zrobić. Zostanie wyświetlona lista opcji, które odnoszą się do tekstu. Załóżmy na przykład, że chcesz zwiększyć poziom szczegółowości danych wyjściowych kompilacji, aby wyświetlić dodatkowe szczegóły dotyczące tego, co dokładnie robi kompilacja. Oto jak możesz to zrobić:

::: moniker range="vs-2017"

1. Znajdź **Szybkie uruchamianie** wyszukiwania w prawym górnym rogu środowiska IDE. (Ewentualnie naciśnij klawisze **Ctrl** + **Q,** aby uzyskać do niego dostęp).

2. W **polu wyszukiwania** wpisz szczegółowość. Z wyświetlonych wyników wybierz pozycję **Projekty i rozwiązania — > skompilować i uruchomić w** **kategorii** Opcje.

   ![Szybkie uruchamianie pola wyszukiwania w Visual Studio 2017 r.](media/quickstart-IDE-quick-launch.png)

   Opcje **zostanie** otwarte okno dialogowe opcje **kompilacji i** uruchamiania strony.

::: moniker-end

::: moniker range=">=vs-2019"

1. Naciśnij **klawisze Ctrl** + **Q,** aby aktywować pole wyszukiwania w górnej części środowiska IDE.

2. W **polu wyszukiwania** wpisz szczegółowość. Z wyświetlonych wyników wybierz pozycję Zmień poziom **szczegółowości programu MSBuild.**

   ![Pole wyszukiwania w Visual Studio 2019 r.](media/vs-2019/quick-launch-verbosity.png)

   Opcje **zostanie** otwarte okno dialogowe opcje **kompilacji i** uruchamiania strony.

::: moniker-end

3. W **obszarze Szczegółowość danych wyjściowych kompilacji projektu MSBuild** wybierz pozycję **Normalna,** a następnie kliknij przycisk **OK.**

4. Skompilować projekt ponownie, klikając prawym przyciskiem myszy projekt **ConsoleApp1** w Eksplorator rozwiązań **i** wybierając polecenie **Rebuild** (Skompilowanie) z menu kontekstowego.

   Tym razem w **oknie Dane** wyjściowe jest bardziej szczegółowe rejestrowanie z procesu kompilacji, w tym informacje o plikach, które zostały skopiowane do miejsca.

   ![Pełne dane wyjściowe kompilacji w Visual Studio](media/build-output-verbose.png)

## <a name="send-feedback-menu"></a>Menu Wyślij opinię

Jeśli podczas korzystania z usługi Visual Studio wystąpią jakiekolwiek problemy lub jeśli masz sugestie dotyczące sposobu ulepszenia produktu, możesz użyć **menu** Wyślij opinię w górnej części Visual Studio aplikacji.

::: moniker range="vs-2017"

![Menu Wyślij opinię w programie Visual Studio 2017](media/quickstart-IDE-send-feedback.png)

::: moniker-end

::: moniker range=">=vs-2019"

![Menu Wyślij opinię w Visual Studio 2019 r.](media/vs-2019/send-feedback-menu.png)

::: moniker-end

## <a name="next-steps"></a>Następne kroki

Przyjrzeliśmy się zaledwie kilku funkcji interfejsu Visual Studio, aby zapoznać się z interfejsem użytkownika. Aby poznać więcej informacji:

> [!div class="nextstepaction"]
> [Dowiedz się więcej o edytorze kodu](../get-started/tutorial-editor.md)

> [!div class="nextstepaction"]
> [Dowiedz się więcej o projektach i rozwiązaniach](../get-started/tutorial-projects-solutions.md)

## <a name="see-also"></a>Zobacz też

- [Omówienie środowiska IDE Visual Studio projektowego](../get-started/visual-studio-ide.md)
- [Więcej funkcji Visual Studio](../ide/advanced-feature-overview.md)
- [Zmienianie motywu i kolorów czcionek](../ide/quickstart-personalize-the-ide.md)
