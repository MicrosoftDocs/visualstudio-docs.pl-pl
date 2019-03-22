---
title: Przewodnik po środowisku IDE programu Visual Studio
titleSuffix: ''
ms.date: 02/21/2019
ms.topic: quickstart
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8cb1b18488eaf9ddf3308e74d583fd1b92fc2563
ms.sourcegitcommit: 3201da3499051768ab59f492699a9049cbc5c3c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2019
ms.locfileid: "58354752"
---
# <a name="quickstart-first-look-at-the-visual-studio-ide"></a>Szybki start: Pierwsze spojrzenie na środowisko IDE programu Visual Studio

W ramach tego wprowadzenia do programu Visual Studio zintegrowane środowisko programistyczne (IDE) 5 – 10 minut przeniesiemy się części okna, menu i inne funkcje interfejsu użytkownika.

Jeśli jeszcze nie zainstalowano programu Visual Studio, przejdź do strony [program Visual Studio pobiera](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) strony, aby zainstalować go za darmo.

::: moniker range="vs-2017"

## <a name="start-page"></a>Strona początkowa

Pierwszą rzeczą, zostaną wyświetlone po otwarciu programu Visual Studio jest najprawdopodobniej **strona startowa**. **Strona startowa** został zaprojektowany jako "Centrum", aby pomóc Ci znaleźć polecenia i projektu pliki potrzebne Ci szybciej. **Ostatnie** sekcja wyświetla projektów i foldery pracuje ostatnio. W obszarze **nowy projekt**, możesz kliknąć link, aby wyświetlić **nowy projekt** okno dialogowe, lub w obszarze **Otwórz**, możesz otworzyć istniejący projekt kodu lub folderu. Po prawej stronie jest źródło danych z najnowszymi informacjami dla programistów.

![Strona początkowa w programie Visual Studio](media/start-page.png)

Jeśli zamkniesz **strona startowa** i chcesz zobaczyć ją ponownie, możesz uruchomić go z **pliku** menu.

![Menu Plik w programie Visual Studio](media/quickstart-IDE-file-menu-large.png)

::: moniker-end

::: moniker range=">=vs-2019"

## <a name="start-window"></a>Okno uruchamiania

Pierwszą rzeczą, jaką zobaczysz po otwarciu programu Visual Studio jest oknem rozpoczęcia. W oknie uruchamiania zaprojektowano w celu ułatwienia Ci "kod" szybciej. Ma funkcje umożliwiające klonowanie lub zapoznaj się z kodu, otwórz istniejący projekt lub rozwiązanie, Utwórz nowy projekt lub po prostu otwórz folder, który zawiera kilka plików kodu.

[![](media/vs-2019/start-window-labeled.png "Okno uruchamiania w programie Visual Studio 2019 r.")](media/vs-2019/start-window-labeled.png#lightbox)

Jeśli używasz programu Visual Studio po raz pierwszy, listy ostatnich projektów jest pusta.

Jeśli pracujesz z niekorzystających z programu MSBuild na podstawie ścieżek bazowych kodów, użyjesz **Otwórz folder lokalny** opcję, aby otworzyć kod w programie Visual Studio. Aby uzyskać więcej informacji, zobacz [tworzenie kodu w programie Visual Studio bez projektów ani rozwiązań](develop-code-in-visual-studio-without-projects-or-solutions.md). W przeciwnym razie możesz utworzyć nowy projekt lub klonowanie projektu od dostawcy źródła, takich jak GitHub lub DevOps platformy Azure.

**Kontynuuj bez konieczności pisania kodu** opcja po prostu otwiera środowiska programistycznego Visual Studio bez określonego projektu lub kodu załadowanego. Możesz wybrać tę opcję, aby dołączyć [udostępniania na żywo](/visualstudio/liveshare/) sesji lub dołączyć do procesu debugowania. Można również nacisnąć klawisz **Esc** aby zamknąć okno uruchamiania i otworzyć IDE.

::: moniker-end

## <a name="create-a-project"></a>Tworzenie projektu

Aby kontynuować poznawanie funkcji programu Visual Studio, Utwórzmy nowy projekt.

::: moniker range="vs-2017"

1. Na **strona startowa**, w polu wyszukiwania w obszarze **nowy projekt**, wpisz w **konsoli** do filtrowania listy typów projektów, które zawierają "konsoli" w nazwie.

   ![Wyszukaj szablony projektów w programie Visual Studio strony początkowej](media/start-page-search-templates.png)

   Program Visual Studio zawiera różne rodzaje szablony projektów, które ułatwiają rozpoczęcie pracy, szybko kodowania. Wybieranie języka C# **Aplikacja konsoli (.NET Framework)** szablonu projektu. (Również w przypadku języka Visual Basic, C++, Javascript lub innych deweloperów języka, możesz tworzenia projektu w jednym z tych języków. Interfejs użytkownika, które firma Microsoft będzie spojrzenie na jest podobny dla wszystkich języków programowania.)

1. W **nowy projekt** okno dialogowe, które zostanie wyświetlone, zaakceptuj domyślną nazwę projektu i wybierz polecenie **OK**.

::: moniker-end

::: moniker range=">=vs-2019"

1. W oknie rozpoczęcia wybierz **Utwórz nowy projekt**.

   Zostanie otwarte okno dialogowe, które mówi **Utwórz nowy projekt**. W tym miejscu można wyszukiwać, filtrować, a następnie wybierz szablon projektu. Zawiera również listę szablonów niedawno używanych projektów.

1. W polu wyszukiwania u góry wpisz **konsoli** do filtrowania listy typów projektów, które zawierają "konsoli" w nazwie. Dalej zawęzić wyniki wyszukiwania przez pobrania **C#** (lub innego języka) z **języka** selektora.

   ![Okno dialogowe nowego projektu w programie Visual Studio 2019 r.](media/vs-2019/create-a-new-project.png)

1. W przypadku wybrania C#, Visual Basic lub F# języka, wybierz **Aplikacja konsoli (.NET Framework)** szablonu, a następnie wybierz **dalej**. (Jeśli wybrano inny język, wystarczy wybrać dowolny szablon. Interfejs użytkownika, które firma Microsoft będzie spojrzenie na jest podobny dla wszystkich języków programowania.)

1. Na **konfigurowania nowego projektu** strony, zaakceptuj domyślną nazwę projektu i lokalizację, a następnie wybierz **Utwórz**.

::: moniker-end

   Projekt zostanie utworzony i plik o nazwie *Program.cs* zostanie otwarty w **edytora** okna. **Edytora** pokazuje zawartość plików, a to, gdzie wykonasz większość swojej pracy kodowania w programie Visual Studio.

   ![Edytor programu Visual Studio](media/editor.png)

## <a name="solution-explorer"></a>Eksplorator rozwiązań

**Eksplorator rozwiązań**, który jest zazwyczaj po prawej stronie programu Visual Studio, dowiesz się, graficzną reprezentację hierarchii plików i folderów w projekcie, rozwiązania lub katalogu z kodem. Możesz przeglądać hierarchii i przejdź do pliku w **Eksploratora rozwiązań**.

![Eksplorator rozwiązań w programie Visual Studio](media/quickstart-IDE-solution-explorer.png)

## <a name="menus"></a>Menu

Na pasku menu, wzdłuż górnej części programu Visual Studio grupy poleceń na kategorie. Na przykład **projektu** menu zawiera polecenia związane z projektem, w której pracujesz. Na **narzędzia** menu, można dostosować sposób działania programu Visual Studio, wybierając **opcje**, lub Dodaj funkcje do instalacji, wybierając **Pobierz narzędzia i funkcje**.

::: moniker range="vs-2017"

![Pasek menu programu Visual Studio 2017](media/quickstart-IDE-menu-bar.png)

::: moniker-end

::: moniker range=">=vs-2019"

![Pasek menu w Visual Studio 2019 r.](media/vs-2019/menu-bar.png)

::: moniker-end

## <a name="error-list"></a>Lista błędów

Otwórz **lista błędów** okna, wybierając **widoku** menu, a następnie **lista błędów**.

**Lista błędów** dowiesz się błędy, ostrzeżenia i komunikaty dotyczące bieżącego stanu w kodzie. Jeśli występują błędy (np. Brak nawiasu klamrowego lub średnika) w pliku lub dowolnego miejsca w projekcie, są one wymienione w tym miejscu.

![Lista błędów w programie Visual Studio](media/quickstart-IDE-error-list.png)

## <a name="output-window"></a>Okno wyniku

**Dane wyjściowe** Pokazuje okno danych wyjściowych wiadomości z kompilowania projektu i Twój dostawca kontroli źródła.

Utwórzmy projekt, aby wyświetlić niektóre dane wyjściowe kompilacji. Z **kompilacji** menu, wybierz **Kompiluj rozwiązanie**. **Dane wyjściowe** okno uzyskuje fokus i automatycznie wyświetli komunikat pomyślnej kompilacji.

![Okno danych wyjściowych w programie Visual Studio](media/build-output-minimal.png)

## <a name="quick-launch"></a>Szybkie uruchamianie

**Szybkie uruchamianie** pole wyszukiwania jest szybki i łatwy sposób przechodzenia do zasadzie dowolny rodzaj danych w programie Visual Studio. Można wprowadzić tekst powiązany co chcesz zrobić, a jego pokazano listę opcji, które odnoszą się do tekstu. Na przykład Wyobraź sobie, że chcesz zwiększyć szczegółowość dane wyjściowe kompilacji, aby wyświetlić dodatkowe informacje o tym, co dokładnie kompilacji robi. Poniżej przedstawiono, jak może to zrobić:

::: moniker range="vs-2017"

1. Znajdź **Szybkie uruchamianie** pola wyszukiwania w prawym górnym rogu środowiska IDE. (Też nacisnąć klawisz **Ctrl**+**Q** do niego dostęp.)

2. Typ **szczegółowości** do **Szybkie uruchamianie** pola wyszukiwania. Z wyświetlane wyniki, wybierz **projekty i rozwiązania--> Kompilowanie i uruchamianie** w obszarze **opcje** kategorii.

   ![Pole wyszukiwania szybkiego uruchamiania w programie Visual Studio 2017](media/quickstart-IDE-quick-launch.png)

   **Opcje** zostanie wyświetlone okno dialogowe **kompilowanie i uruchamianie** Strona opcji.

::: moniker-end

::: moniker range=">=vs-2019"

1. Znajdź **Szybkie uruchamianie** pola wyszukiwania w górnej części IDE, prawo menu. (Też nacisnąć klawisz **Ctrl**+**Q** do niego dostęp.)

2. Typ **szczegółowości** do **Szybkie uruchamianie** pola wyszukiwania. Z wyświetlane wyniki, wybierz **szczegółowość MSBuild zmiany**.

   ![Pole wyszukiwania Szybkie uruchamianie w Visual Studio 2019 r.](media/vs-2019/quick-launch-verbosity.png)

   **Opcje** zostanie wyświetlone okno dialogowe **kompilowanie i uruchamianie** Strona opcji.

::: moniker-end

3. W obszarze **poziom szczegółowości danych wyjściowych kompilacji projektu programu MSBuild**, wybierz **normalny**, a następnie kliknij przycisk **OK**.

4. Ponownie skompiluj projekt, klikając prawym przyciskiem myszy **ConsoleApp1** projektu w **Eksploratora rozwiązań** i wybierając pozycję **odbudować** z menu kontekstowego.

   Tym razem **dane wyjściowe** okno pokazuje pełniejsze rejestrowanie z procesu kompilacji, w tym pliki, które zostały skopiowane where.

   ![Dane wyjściowe kompilacji pełne w programie Visual Studio](media/build-output-verbose.png)

## <a name="send-feedback-menu"></a>Wyślij opinię menu

Należy napotykasz problemy podczas korzystania z programu Visual Studio, lub jeśli masz sugestie dotyczące poprawy produktu, możesz użyć **Wyślij opinię** menu w górnej części okna programu Visual Studio obok **szybki Uruchom** pole.

::: moniker range="vs-2017"

![Wyślij opinię menu w programie Visual Studio 2017](media/quickstart-IDE-send-feedback.png)

::: moniker-end

::: moniker range=">=vs-2019"

![Wysyłanie opinii menu w Visual Studio 2019 r.](media/vs-2019/send-feedback-menu.png)

::: moniker-end

## <a name="next-steps"></a>Następne kroki

Opisaliśmy kilka funkcji programu Visual Studio, aby korzystały z interfejsem użytkownika. Aby dokładniej:

> [!div class="nextstepaction"]
> [Dowiedz się więcej o Edytorze kodu](../get-started/tutorial-editor.md)

> [!div class="nextstepaction"]
> [Dowiedz się więcej o projekty i rozwiązania](../get-started/tutorial-projects-solutions.md)

## <a name="see-also"></a>Zobacz także

- [Omówienie środowiska IDE programu Visual Studio](../get-started/visual-studio-ide.md)
- [Więcej funkcji programu Visual Studio](../ide/advanced-feature-overview.md)
- [Zmienianie motywu i kolory czcionek](../ide/quickstart-personalize-the-ide.md)
