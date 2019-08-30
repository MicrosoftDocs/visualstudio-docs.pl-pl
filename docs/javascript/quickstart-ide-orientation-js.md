---
title: Przewodnik po środowisku IDE programu Visual Studio
titleSuffix: ''
ms.date: 02/05/2019
ms.topic: quickstart
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 677dddbde5e90117dc19acfaf54a941c304ae7f1
ms.sourcegitcommit: 44e9b1d9230fcbbd081ee81be9d4be8a485d8502
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/30/2019
ms.locfileid: "70180056"
---
# <a name="first-look-at-the-visual-studio-ide"></a>Pierwsze spojrzenie na środowisko IDE programu Visual Studio

W ramach tego wprowadzenia do programu Visual Studio zintegrowane środowisko programistyczne (IDE) 5 – 10 minut przeniesiemy się części okna, menu i inne funkcje interfejsu użytkownika.

::: moniker range="vs-2017"

Jeśli jeszcze nie zainstalowano programu Visual Studio, przejdź do strony [program Visual Studio pobiera](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) strony, aby zainstalować go za darmo.

::: moniker-end

::: moniker range="vs-2019"

Jeśli jeszcze nie zainstalowano programu Visual Studio, przejdź do strony [program Visual Studio pobiera](https://visualstudio.microsoft.com/downloads) strony, aby zainstalować go za darmo.

::: moniker-end

::: moniker range=">=vs-2019"

## <a name="start-window"></a>Okno uruchamiania

Pierwsze czynności, które zobaczysz po uruchomieniu programu Visual Studio jest oknem startowym. Okno Start zostało zaprojektowane z założeniami, aby ułatwić szybkie rozpoczęcie pracy z kodem. Dostępne są opcje zamykania lub wyewidencjonowywania kodu, otwierania istniejącego projektu lub rozwiązania, tworzenia nowego projektu lub po prostu otwierania folderu zawierającego niektóre pliki kodu.

[![Okno uruchamiania w programie Visual Studio 2019](media/vs-2019/start-window.png)](media/vs-2019/start-window.png)

Jeśli używasz programu Visual Studio po raz pierwszy, lista ostatnio używanych projektów będzie pusta.

Jeśli pracujesz z bazami danych spoza programu MSBuild, użyj opcji **Otwórz folder lokalny** , aby otworzyć swój kod w programie Visual Studio. Aby uzyskać więcej informacji, zobacz [tworzenie kodu w programie Visual Studio bez projektów ani rozwiązań](develop-javascript-code-without-solutions-projects.md). W przeciwnym razie można utworzyć nowy projekt lub sklonować projekt od dostawcy źródłowego, takiego jak GitHub lub Azure DevOps.

Opcja **Kontynuuj bez kodu** po prostu otwiera środowisko programistyczne programu Visual Studio bez żadnego załadowanego projektu lub kodu. Możesz wybrać tę opcję, aby przyłączyć się do sesji [Live Share](/visualstudio/liveshare/) lub dołączyć do procesu debugowania. Możesz również nacisnąć klawisz **ESC** , aby zamknąć okno Start i otworzyć środowisko IDE.

::: moniker-end

::: moniker range="vs-2017"

## <a name="start-page"></a>Strona początkowa

Pierwszą rzeczą, zostaną wyświetlone po uruchomieniu programu Visual Studio jest najprawdopodobniej **strona startowa**. **Strona startowa** został zaprojektowany jako "Centrum", aby pomóc Ci znaleźć polecenia i projektu pliki potrzebne Ci szybciej. **Ostatnie** sekcja wyświetla projektów i foldery pracuje ostatnio. W obszarze **nowy projekt**, możesz kliknąć link, aby wyświetlić **nowy projekt** okno dialogowe, lub w obszarze **Otwórz**, możesz otworzyć istniejący projekt kodu lub folderu. Po prawej stronie jest źródło danych z najnowszymi informacjami dla programistów.

![Strona początkowa w programie Visual Studio](media/start-page.png)

Jeśli zamkniesz **strona startowa** i chcesz zobaczyć ją ponownie, możesz uruchomić go z **pliku** menu.

![Menu Plik w programie Visual Studio](media/quickstart-IDE-file-menu-large.png)

::: moniker-end

## <a name="create-a-project"></a>Tworzenie projektu

Aby kontynuować poznawanie funkcji programu Visual Studio, Utwórzmy nowy projekt.

::: moniker range=">=vs-2019"

1. W oknie uruchamiania wybierz pozycję **Utwórz nowy projekt**, a następnie w polu wyszukiwania wpisz **kod JavaScript** , aby odfiltrować listę typów projektu do tych, które zawierają ciąg "JavaScript" w nazwie lub w typie języka.

   Program Visual Studio zawiera różne rodzaje szablony projektów, które ułatwiają rozpoczęcie pracy, szybko kodowania. (Alternatywnie, jeśli jesteś deweloperem języka TypeScript, możesz utworzyć projekt w tym języku. Interfejs użytkownika, które firma Microsoft będzie spojrzenie na jest podobny dla wszystkich języków programowania.)

   ![Wyszukaj szablony projektów w oknie uruchamiania programu Visual Studio](media/vs-2019/create-new-project.png)

1. Wybierz pusty szablon projektu **aplikacji sieci Web w języku Node. js** , a następnie kliknij przycisk **dalej**.

1. W wyświetlonym oknie dialogowym **Konfigurowanie nowego projektu** zaakceptuj domyślną nazwę projektu i wybierz pozycję **Utwórz**.

::: moniker-end

::: moniker range="vs-2017"

1. Na **stronie Start**w polu wyszukiwania w obszarze **Nowy projekt**wpisz **JavaScript** , aby odfiltrować listę typów projektu do tych, które zawierają ciąg "JavaScript" w nazwie lub w typie języka.

   ![Wyszukaj szablony projektów w programie Visual Studio strony początkowej](media/start-page-search-templates.png)

   Program Visual Studio zawiera różne rodzaje szablony projektów, które ułatwiają rozpoczęcie pracy, szybko kodowania. Wybierz pusty szablon projektu **aplikacji sieci Web w języku Node. js** . (Alternatywnie, jeśli jesteś deweloperem języka TypeScript, możesz utworzyć projekt w tym języku. Interfejs użytkownika, które firma Microsoft będzie spojrzenie na jest podobny dla wszystkich języków programowania.)

1. W **nowy projekt** okno dialogowe, które zostanie wyświetlone, zaakceptuj domyślną nazwę projektu i wybierz polecenie **OK**.
::: moniker-end

   Projekt zostanie utworzony, a plik o nazwie *Server.cs* zostanie otwarty w oknie **edytora** . **Edytora** pokazuje zawartość plików, a to, gdzie wykonasz większość swojej pracy kodowania w programie Visual Studio.

   ![Edytor programu Visual Studio](media/editor.png)

## <a name="solution-explorer"></a>Eksplorator rozwiązań

**Eksplorator rozwiązań**, który jest zazwyczaj po prawej stronie programu Visual Studio, dowiesz się, graficzną reprezentację hierarchii plików i folderów w projekcie, rozwiązania lub katalogu z kodem. Możesz przeglądać hierarchii i przejdź do pliku w **Eksploratora rozwiązań**.

![Eksplorator rozwiązań w programie Visual Studio](media/quickstart-IDE-solution-explorer.png)

## <a name="menus"></a>Menu

Na pasku menu, wzdłuż górnej części programu Visual Studio grupy poleceń na kategorie. Na przykład **projektu** menu zawiera polecenia związane z projektem, w której pracujesz. Na **narzędzia** menu, można dostosować sposób działania programu Visual Studio, wybierając **opcje**, lub Dodaj funkcje do instalacji, wybierając **Pobierz narzędzia i funkcje**.

![Pasek menu w programie Visual Studio](media/quickstart-IDE-menu-bar.png)

Teraz Otwórz **lista błędów** okna, wybierając **widoku** menu, a następnie **lista błędów**.

## <a name="error-list"></a>Lista błędów

**Lista błędów** dowiesz się błędy, ostrzeżenia i komunikaty dotyczące bieżącego stanu w kodzie. Jeśli występują błędy (np. Brak nawiasu klamrowego lub średnika) w pliku lub dowolnego miejsca w projekcie, są one wymienione w tym miejscu.

![Lista błędów w programie Visual Studio](media/quickstart-IDE-error-list.png)

## <a name="output-window"></a>Okno wyniku

**Dane wyjściowe** Pokazuje okno danych wyjściowych wiadomości z kompilowania projektu i Twój dostawca kontroli źródła.

Utwórzmy projekt, aby wyświetlić niektóre dane wyjściowe kompilacji. Z **kompilacji** menu, wybierz **Kompiluj rozwiązanie**. **Dane wyjściowe** okno uzyskuje fokus i automatycznie wyświetli komunikat pomyślnej kompilacji.

![Okno danych wyjściowych w programie Visual Studio](media/build-output-minimal.png)

## <a name="search-box"></a>Pole wyszukiwania

Pole wyszukiwania jest szybkim i łatwym sposobem wykonywania całkiem wielu elementów w programie Visual Studio. Można wprowadzić tekst powiązany co chcesz zrobić, a jego pokazano listę opcji, które odnoszą się do tekstu. Na przykład Wyobraź sobie, że chcesz zwiększyć szczegółowość dane wyjściowe kompilacji, aby wyświetlić dodatkowe informacje o tym, co dokładnie kompilacji robi. Poniżej przedstawiono, jak może to zrobić:

1. Wpisz **szczegółowość** w polu wyszukiwania. Z wyświetlane wyniki, wybierz **projekty i rozwiązania--> Kompilowanie i uruchamianie** w obszarze **opcje** kategorii.

   ![Pole wyszukiwania w programie Visual Studio](media/quickstart-IDE-quick-launch.png)

   **Opcje** zostanie wyświetlone okno dialogowe **kompilowanie i uruchamianie** Strona opcji.

1. W obszarze **poziom szczegółowości danych wyjściowych kompilacji projektu programu MSBuild**, wybierz **normalny**, a następnie kliknij przycisk **OK**.

1. Ponownie skompiluj projekt, klikając prawym przyciskiem myszy projekt **NodejsWebApp1** w **Eksplorator rozwiązań** i wybierając polecenie **Kompiluj ponownie** z menu kontekstowego.

   Tym razem **dane wyjściowe** okno pokazuje pełniejsze rejestrowanie z procesu kompilacji, w tym pliki, które zostały skopiowane where.

   ![Dane wyjściowe kompilacji pełne w programie Visual Studio](media/build-output-verbose.png)

## <a name="send-feedback-menu"></a>Wyślij opinię menu

Jeśli podczas korzystania z programu Visual Studio wystąpią jakiekolwiek problemy lub jeśli masz sugestie dotyczące ulepszania produktu, możesz użyć menu **Wyślij opinię** w górnej części okna programu Visual Studio.

![Wyślij opinię menu w programie Visual Studio](../ide/media/quickstart-ide-send-feedback.png)

## <a name="next-steps"></a>Następne kroki

Opisaliśmy kilka funkcji programu Visual Studio, aby korzystały z interfejsem użytkownika. Aby dokładniej:

> [!div class="nextstepaction"]
> [Dowiedz się więcej o Edytorze kodu](write-and-edit-code.md)

> [!div class="nextstepaction"]
> [Dowiedz się więcej o projekty i rozwiązania](../get-started/tutorial-projects-solutions.md)

## <a name="see-also"></a>Zobacz także

- [Omówienie środowiska IDE programu Visual Studio](../get-started/visual-studio-ide.md)
- [Więcej funkcji programu Visual Studio 2017](../ide/advanced-feature-overview.md)
- [Zmienianie motywu i kolory czcionek](../ide/quickstart-personalize-the-ide.md)
