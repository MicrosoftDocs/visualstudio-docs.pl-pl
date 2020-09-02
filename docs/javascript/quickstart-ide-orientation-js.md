---
title: Pierwsze spojrzenie na środowisko IDE programu Visual Studio
titleSuffix: ''
ms.date: 02/05/2019
ms.topic: quickstart
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 41d5d40cc7951f09a8106426f603d42628c61846
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "88238871"
---
# <a name="first-look-at-the-visual-studio-ide"></a>Pierwsze spojrzenie na środowisko IDE programu Visual Studio

W tym 5-10 minutowym wprowadzeniu do zintegrowanego środowiska programistycznego (IDE) programu Visual Studio zajmiemy się tworzeniem niektórych okien, menu i innych funkcji interfejsu użytkownika.

::: moniker range="vs-2017"

Jeśli program Visual Studio nie został jeszcze zainstalowany, przejdź do strony [plików do pobrania programu Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) , aby zainstalować ją bezpłatnie.

::: moniker-end

::: moniker range=">=vs-2019"

Jeśli program Visual Studio nie został jeszcze zainstalowany, przejdź do strony [plików do pobrania programu Visual Studio](https://visualstudio.microsoft.com/downloads) , aby zainstalować ją bezpłatnie.

::: moniker-end

::: moniker range=">=vs-2019"

## <a name="start-window"></a>Okno uruchamiania

Pierwsze czynności, które zobaczysz po uruchomieniu programu Visual Studio jest oknem startowym. Okno Start zostało zaprojektowane z założeniami, aby ułatwić szybkie rozpoczęcie pracy z kodem. Dostępne są opcje zamykania lub wyewidencjonowywania kodu, otwierania istniejącego projektu lub rozwiązania, tworzenia nowego projektu lub po prostu otwierania folderu zawierającego niektóre pliki kodu.

[![Okno uruchamiania w programie Visual Studio 2019](media/vs-2019/start-window.png)](media/vs-2019/start-window.png)

Jeśli używasz programu Visual Studio po raz pierwszy, lista ostatnio używanych projektów będzie pusta.

Jeśli pracujesz z bazami danych spoza programu MSBuild, użyj opcji **Otwórz folder lokalny** , aby otworzyć swój kod w programie Visual Studio. Aby uzyskać więcej informacji, zobacz [Programowanie kodu w programie Visual Studio bez projektów i rozwiązań](develop-javascript-code-without-solutions-projects.md). W przeciwnym razie można utworzyć nowy projekt lub sklonować projekt od dostawcy źródłowego, takiego jak GitHub lub Azure DevOps.

Opcja **Kontynuuj bez kodu** po prostu otwiera środowisko programistyczne programu Visual Studio bez żadnego załadowanego projektu lub kodu. Możesz wybrać tę opcję, aby przyłączyć się do sesji [Live Share](/visualstudio/liveshare/) lub dołączyć do procesu debugowania. Możesz również nacisnąć klawisz **ESC** , aby zamknąć okno Start i otworzyć środowisko IDE.

::: moniker-end

::: moniker range="vs-2017"

## <a name="start-page"></a>Strona początkowa

Pierwsze czynności, które zobaczysz po uruchomieniu programu Visual Studio, prawdopodobnie na **stronie początkowej**. **Strona startowa** jest zaprojektowana jako "centrum", aby pomóc w znalezieniu poleceń i plików projektu, które są potrzebne szybciej. W sekcji ostatnie są wyświetlane ostatnio **używane** projekty i foldery. W obszarze **Nowy projekt**można kliknąć link, aby wyświetlić okno dialogowe **Nowy projekt** lub w obszarze **Otwórz**, można otworzyć istniejący projekt lub folder kodu. Po prawej stronie znajduje się źródło najnowszych wiadomości dla deweloperów.

![Strona początkowa w programie Visual Studio](media/start-page.png)

Jeśli zamkniesz **stronę początkową** i chcesz ją ponownie zobaczyć, możesz ją otworzyć z menu **plik** .

![Menu plik w programie Visual Studio](media/quickstart-IDE-file-menu-large.png)

::: moniker-end

## <a name="create-a-project"></a>Tworzenie projektu

Aby kontynuować Eksplorowanie funkcji programu Visual Studio, Utwórz nowy projekt.

::: moniker range=">=vs-2019"

1. W oknie uruchamiania wybierz pozycję **Utwórz nowy projekt**, a następnie w polu wyszukiwania wpisz **kod JavaScript** , aby odfiltrować listę typów projektu do tych, które zawierają ciąg "JavaScript" w nazwie lub w typie języka.

   Program Visual Studio oferuje różne rodzaje szablonów projektów, które ułatwiają szybkie rozpoczęcie tworzenia kodu. (Alternatywnie, jeśli jesteś deweloperem języka TypeScript, możesz utworzyć projekt w tym języku. Interfejs użytkownika, który sprawdzimy, jest podobny dla wszystkich języków programowania.)

   ![Wyszukaj szablony projektów w oknie uruchamiania programu Visual Studio](media/vs-2019/create-new-project.png)

1. Wybierz pusty szablon projektu **aplikacji sieci Web Node.js** i kliknij przycisk **dalej**.

1. W wyświetlonym oknie dialogowym **Konfigurowanie nowego projektu** zaakceptuj domyślną nazwę projektu i wybierz pozycję **Utwórz**.

::: moniker-end

::: moniker range="vs-2017"

1. Na **stronie Start**w polu wyszukiwania w obszarze **Nowy projekt**wpisz **JavaScript** , aby odfiltrować listę typów projektu do tych, które zawierają ciąg "JavaScript" w nazwie lub w typie języka.

   ![Wyszukaj szablony projektów na stronie startowej programu Visual Studio](media/start-page-search-templates.png)

   Program Visual Studio oferuje różne rodzaje szablonów projektów, które ułatwiają szybkie rozpoczęcie tworzenia kodu. Wybierz pusty szablon projektu **aplikacji sieci Web Node.js** . (Alternatywnie, jeśli jesteś deweloperem języka TypeScript, możesz utworzyć projekt w tym języku. Interfejs użytkownika, który sprawdzimy, jest podobny dla wszystkich języków programowania.)

1. W wyświetlonym oknie dialogowym **Nowy projekt** zaakceptuj domyślną nazwę projektu i wybierz **przycisk OK**.
::: moniker-end

   Projekt zostanie utworzony, a plik o nazwie *server.js* otwiera się w oknie **edytora** . **Edytor** pokazuje zawartość plików i polega na tym, że większość pracy z kodowaniem będzie w programie Visual Studio.

   ![Edytor w programie Visual Studio](media/editor.png)

## <a name="solution-explorer"></a>Eksplorator rozwiązań

**Eksplorator rozwiązań**, która zwykle znajduje się po prawej stronie programu Visual Studio, pokazuje graficzną reprezentację hierarchii plików i folderów w projekcie, rozwiązaniu lub folderze kodu. Możesz przeglądać hierarchię i przejść do pliku w **Eksplorator rozwiązań**.

![Eksplorator rozwiązań w programie Visual Studio](media/quickstart-IDE-solution-explorer.png)

## <a name="menus"></a>Menu

Pasek menu wzdłuż górnej części poleceń programu Visual Studio grupuje do kategorii. Na przykład menu **projekt** zawiera polecenia związane z projektem, w którym pracujesz. W menu **Narzędzia** można dostosować sposób działania programu Visual Studio, wybierając **Opcje**lub dodając funkcje do instalacji, wybierając pozycję **Pobierz narzędzia i funkcje**.

![Pasek menu w programie Visual Studio](media/quickstart-IDE-menu-bar.png)

Otwórzmy okno **Lista błędów** , wybierając menu **Widok** , a następnie **Lista błędów**.

## <a name="error-list"></a>Lista błędów

W **Lista błędów** przedstawiono błędy, ostrzeżenia i komunikaty dotyczące bieżącego stanu kodu. Jeśli w pliku występują błędy (takie jak brakujące nawiasy klamrowe lub średnik) lub gdziekolwiek w projekcie, są one wyświetlane w tym miejscu.

![Lista błędów w programie Visual Studio](media/quickstart-IDE-error-list.png)

## <a name="output-window"></a>Okno wyniku

W oknie **dane wyjściowe** są wyświetlane komunikaty wyjściowe z kompilowania projektu i od dostawcy kontroli źródła.

Skompilujmy projekt, aby zobaczyć dane wyjściowe kompilacji. Z menu **kompilacja** wybierz polecenie **Kompiluj rozwiązanie**. Okno **dane wyjściowe** automatycznie uzyskuje fokus i wyświetla udany komunikat kompilacji.

![Okno danych wyjściowych w programie Visual Studio](media/build-output-minimal.png)

## <a name="search-box"></a>Pole wyszukiwania

Pole wyszukiwania jest szybkim i łatwym sposobem wykonywania całkiem wielu elementów w programie Visual Studio. Możesz wprowadzić tekst związany z tym, co chcesz zrobić, i wyświetlić listę opcji, które odnoszą się do tekstu. Załóżmy na przykład, że chcesz zwiększyć szczegółowość danych wyjściowych kompilacji, aby wyświetlić dodatkowe szczegóły dotyczące tego, co dokładnie kompiluje. Oto jak to zrobić:

1. Wpisz **szczegółowość** w polu wyszukiwania. Z wyświetlanych wyników wybierz **projekty i rozwiązania — > kompilacja i uruchomienie** w kategorii **Opcje** .

   ![Pole wyszukiwania w programie Visual Studio](media/quickstart-IDE-quick-launch.png)

   Okno dialogowe **Opcje** zostanie otwarte na stronie opcje **kompilacji i uruchomienia** .

1. W obszarze **dane wyjściowe kompilacji projektu MSBuild**, wybierz pozycję **normalny**, a następnie kliknij przycisk **OK**.

1. Ponownie skompiluj projekt, klikając prawym przyciskiem myszy projekt **NodejsWebApp1** w **Eksplorator rozwiązań** i wybierając polecenie **Kompiluj ponownie** z menu kontekstowego.

   Tym razem okno **dane wyjściowe** Wyświetla więcej informacji o pełnym rejestrowaniu z procesu kompilacji, w tym pliki, które zostały skopiowane.

   ![Pełne dane wyjściowe kompilacji w programie Visual Studio](media/build-output-verbose.png)

## <a name="send-feedback-menu"></a>Menu Wyślij opinię

Jeśli podczas korzystania z programu Visual Studio wystąpią jakiekolwiek problemy lub jeśli masz sugestie dotyczące ulepszania produktu, możesz użyć menu **Wyślij opinię** w górnej części okna programu Visual Studio.

![Menu Wyślij opinię w programie Visual Studio](../ide/media/quickstart-ide-send-feedback.png)

## <a name="next-steps"></a>Następne kroki

Oglądamy zaledwie kilka funkcji programu Visual Studio, aby zapoznać się z interfejsem użytkownika. Aby dowiedzieć się więcej:

> [!div class="nextstepaction"]
> [Dowiedz się więcej o edytorze kodu](write-and-edit-code.md)

> [!div class="nextstepaction"]
> [Informacje o projektach i rozwiązaniach](../get-started/tutorial-projects-solutions.md)

## <a name="see-also"></a>Zobacz też

- [Przegląd środowiska IDE programu Visual Studio](../get-started/visual-studio-ide.md)
- [Więcej funkcji programu Visual Studio 2017](../ide/advanced-feature-overview.md)
- [Zmień kolory motywu i czcionki](../ide/quickstart-personalize-the-ide.md)
