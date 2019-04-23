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
ms.openlocfilehash: 1d2c20f25b005e738769d1c8663387f0a427e5dd
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60096897"
---
# <a name="first-look-at-the-visual-studio-ide"></a>Pierwsze spojrzenie na środowisko IDE programu Visual Studio

W ramach tego wprowadzenia do programu Visual Studio zintegrowane środowisko programistyczne (IDE) 5 – 10 minut przeniesiemy się części okna, menu i inne funkcje interfejsu użytkownika.

::: moniker range="vs-2017"

Jeśli jeszcze nie zainstalowano programu Visual Studio, przejdź do strony [program Visual Studio pobiera](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) strony, aby zainstalować go za darmo.

::: moniker-end

::: moniker range="vs-2019"

Jeśli jeszcze nie zainstalowano programu Visual Studio, przejdź do strony [program Visual Studio pobiera](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) strony, aby zainstalować go za darmo.

::: moniker-end

::: moniker range=">=vs-2019"

## <a name="start-window"></a>Okno uruchamiania

Pierwszą rzeczą, jaką zobaczysz po uruchomieniu programu Visual Studio jest oknem rozpoczęcia. W oknie uruchamiania zaprojektowano w celu ułatwienia Ci "kod" szybciej. Posiada opcji, aby zamknąć lub zapoznaj się z kodu, otwórz istniejący projekt lub rozwiązanie, Utwórz nowy projekt lub po prostu otwórz folder, który zawiera kilka plików kodu.

[![](media/vs-2019/start-window.png "Okno uruchamiania w programie Visual Studio 2019 r.")](media/vs-2019/start-window.png)

Jeśli używasz programu Visual Studio po raz pierwszy, listy ostatnich projektów jest pusta.

Jeśli pracujesz z niekorzystających z programu MSBuild na podstawie ścieżek bazowych kodów, użyjesz **Otwórz folder lokalny** opcję, aby otworzyć kod w programie Visual Studio. Aby uzyskać więcej informacji, zobacz [tworzenie kodu w programie Visual Studio bez projektów ani rozwiązań](develop-javascript-code-without-solutions-projects.md). W przeciwnym razie możesz utworzyć nowy projekt lub klonowanie projektu od dostawcy źródła, takich jak GitHub lub DevOps platformy Azure.

**Kontynuuj bez konieczności pisania kodu** opcja po prostu otwiera środowiska programistycznego Visual Studio bez określonego projektu lub kodu załadowanego. Możesz wybrać tę opcję, aby dołączyć [udostępniania na żywo](/visualstudio/liveshare/) sesji lub dołączyć do procesu debugowania. Można również nacisnąć klawisz **Esc** aby zamknąć okno uruchamiania i otworzyć IDE.

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

1. W oknie rozpoczęcia wybierz **Utwórz nowy projekt**, a następnie w polu wyszukiwania wpisz **javascript** do filtrowania listy typów projektów, które zawierają "javascript" w typie ich nazwy lub języka.

   Program Visual Studio zawiera różne rodzaje szablony projektów, które ułatwiają rozpoczęcie pracy, szybko kodowania. (Alternatywnie Jeśli jesteś deweloperem TypeScript, możesz utworzyć projekt, w tym języku. Interfejs użytkownika, które firma Microsoft będzie spojrzenie na jest podobny dla wszystkich języków programowania.)

   ![Wyszukaj szablony projektów w oknie uruchamiania programu Visual Studio](media/vs-2019/create-new-project.png)

1. Wybierz **pusta aplikacja sieci Web Node.js** szablonu projektu i kliknij przycisk **dalej**.

1. W **konfigurowania nowego projektu** okno dialogowe, które zostanie wyświetlone, zaakceptuj domyślną nazwę projektu i wybierz polecenie **Utwórz**.

::: moniker-end

::: moniker range="vs-2017"

1. Na **strona startowa**, w polu wyszukiwania w obszarze **nowy projekt**, wpisz w **javascript** do filtrowania listy typów projektów, które zawierają "javascript" w nazwie lub Typ języka.

   ![Wyszukaj szablony projektów w programie Visual Studio strony początkowej](media/start-page-search-templates.png)

   Program Visual Studio zawiera różne rodzaje szablony projektów, które ułatwiają rozpoczęcie pracy, szybko kodowania. Wybierz **pusta aplikacja sieci Web Node.js** szablonu projektu. (Alternatywnie Jeśli jesteś deweloperem TypeScript, możesz utworzyć projekt, w tym języku. Interfejs użytkownika, które firma Microsoft będzie spojrzenie na jest podobny dla wszystkich języków programowania.)

1. W **nowy projekt** okno dialogowe, które zostanie wyświetlone, zaakceptuj domyślną nazwę projektu i wybierz polecenie **OK**.
::: moniker-end

   Projekt zostanie utworzony i plik o nazwie *server.cs* zostanie otwarty w **edytora** okna. **Edytora** pokazuje zawartość plików, a to, gdzie wykonasz większość swojej pracy kodowania w programie Visual Studio.

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

Pole wyszukiwania jest szybka i łatwa metoda wygląda praktycznie wszystkich wymaganych w programie Visual Studio. Można wprowadzić tekst powiązany co chcesz zrobić, a jego pokazano listę opcji, które odnoszą się do tekstu. Na przykład Wyobraź sobie, że chcesz zwiększyć szczegółowość dane wyjściowe kompilacji, aby wyświetlić dodatkowe informacje o tym, co dokładnie kompilacji robi. Poniżej przedstawiono, jak może to zrobić:

1. Typ **szczegółowości** w polu wyszukiwania. Z wyświetlane wyniki, wybierz **projekty i rozwiązania--> Kompilowanie i uruchamianie** w obszarze **opcje** kategorii.

   ![Pole wyszukiwania w programie Visual Studio](media/quickstart-IDE-quick-launch.png)

   **Opcje** zostanie wyświetlone okno dialogowe **kompilowanie i uruchamianie** Strona opcji.

1. W obszarze **poziom szczegółowości danych wyjściowych kompilacji projektu programu MSBuild**, wybierz **normalny**, a następnie kliknij przycisk **OK**.

1. Ponownie skompiluj projekt, klikając prawym przyciskiem myszy **NodejsWebApp1** projektu w **Eksploratora rozwiązań** i wybierając pozycję **odbudować** z menu kontekstowego.

   Tym razem **dane wyjściowe** okno pokazuje pełniejsze rejestrowanie z procesu kompilacji, w tym pliki, które zostały skopiowane where.

   ![Dane wyjściowe kompilacji pełne w programie Visual Studio](media/build-output-verbose.png)

## <a name="send-feedback-menu"></a>Wyślij opinię menu

Należy napotykasz problemy podczas korzystania z programu Visual Studio, lub jeśli masz sugestie dotyczące poprawy produktu, możesz użyć **Wyślij opinię** menu w górnej części okna programu Visual Studio.

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
