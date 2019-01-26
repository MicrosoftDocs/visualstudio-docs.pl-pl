---
title: Przewodnik po środowisku IDE programu Visual Studio
titleSuffix: ''
ms.date: 07/12/2018
ms.prod: visual-studio-dev15
ms.topic: quickstart
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 31178e30224fed37a142d398a73c1e05c7b35a27
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54928298"
---
# <a name="quickstart-first-look-at-the-visual-studio-ide"></a>Szybki start: Pierwsze spojrzenie na środowisku IDE programu Visual Studio

W ramach tego wprowadzenia do programu Visual Studio zintegrowane środowisko programistyczne (IDE) 5 – 10 minut przeniesiemy się części okna, menu i inne funkcje interfejsu użytkownika.

Jeśli jeszcze nie zainstalowano programu Visual Studio, przejdź do strony [program Visual Studio pobiera](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) strony, aby zainstalować go za darmo.

## <a name="start-page"></a>Strona początkowa

Pierwszą rzeczą, zostaną wyświetlone po uruchomieniu programu Visual Studio jest najprawdopodobniej **strona startowa**. **Strona startowa** został zaprojektowany jako "Centrum", aby pomóc Ci znaleźć polecenia i projektu pliki potrzebne Ci szybciej. **Ostatnie** sekcja wyświetla projektów i foldery pracuje ostatnio. W obszarze **nowy projekt**, możesz kliknąć link, aby wyświetlić **nowy projekt** okno dialogowe, lub w obszarze **Otwórz**, możesz otworzyć istniejący projekt kodu lub folderu. Po prawej stronie jest źródło danych z najnowszymi informacjami dla programistów.

![Strona początkowa w programie Visual Studio](media/start-page.png)

Jeśli zamkniesz **strona startowa** i chcesz zobaczyć ją ponownie, możesz uruchomić go z **pliku** menu.

![Menu Plik w programie Visual Studio](media/quickstart-IDE-file-menu-large.png)

## <a name="create-a-project"></a>Tworzenie projektu

Aby kontynuować poznawanie funkcji programu Visual Studio, Utwórzmy nowy projekt.

1. Na **strona startowa**, w polu wyszukiwania w obszarze **nowy projekt**, wpisz w **konsoli** do filtrowania listy typów projektów, które zawierają "konsoli" w nazwie.

   ![Wyszukaj szablony projektów w programie Visual Studio strony początkowej](media/start-page-search-templates.png)

   Program Visual Studio zawiera różne rodzaje szablony projektów, które ułatwiają rozpoczęcie pracy, szybko kodowania. Wybieranie języka C# **Aplikacja konsoli (.NET Framework)** szablonu projektu. (Również w przypadku języka Visual Basic, C++, Javascript lub innych deweloperów języka, możesz tworzenia projektu w jednym z tych języków. Interfejs użytkownika, które firma Microsoft będzie spojrzenie na jest podobny dla wszystkich języków programowania.)

1. W **nowy projekt** okno dialogowe, które zostanie wyświetlone, zaakceptuj domyślną nazwę projektu i wybierz polecenie **OK**.

   Projekt zostanie utworzony i plik o nazwie *Program.cs* zostanie otwarty w **edytora** okna. **Edytora** pokazuje zawartość plików, a to, gdzie wykonasz większość swojej pracy kodowania w programie Visual Studio.

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

## <a name="quick-launch"></a>Szybkie uruchamianie

**Szybkie uruchamianie** pole jest szybka i łatwa metoda wygląda praktycznie wszystkich wymaganych w programie Visual Studio. Można wprowadzić tekst powiązany co chcesz zrobić, a jego pokazano listę opcji, które odnoszą się do tekstu. Na przykład Wyobraź sobie, że chcesz zwiększyć szczegółowość dane wyjściowe kompilacji, aby wyświetlić dodatkowe informacje o tym, co dokładnie kompilacji robi. Poniżej przedstawiono, jak może to zrobić:

1. Typ **szczegółowości** do **Szybkie uruchamianie** pole. Z wyświetlane wyniki, wybierz **projekty i rozwiązania--> Kompilowanie i uruchamianie** w obszarze **opcje** kategorii.

   ![Szybkie uruchamianie pola w programie Visual Studio](media/quickstart-IDE-quick-launch.png)

   **Opcje** zostanie wyświetlone okno dialogowe **kompilowanie i uruchamianie** Strona opcji.

1. W obszarze **poziom szczegółowości danych wyjściowych kompilacji projektu programu MSBuild**, wybierz **normalny**, a następnie kliknij przycisk **OK**.

1. Ponownie skompiluj projekt, klikając prawym przyciskiem myszy **ConsoleApp1** projektu w **Eksploratora rozwiązań** i wybierając pozycję **odbudować** z menu kontekstowego.

   Tym razem **dane wyjściowe** okno pokazuje pełniejsze rejestrowanie z procesu kompilacji, w tym pliki, które zostały skopiowane where.

   ![Dane wyjściowe kompilacji pełne w programie Visual Studio](media/build-output-verbose.png)

## <a name="send-feedback-menu"></a>Wyślij opinię menu

Należy napotykasz problemy podczas korzystania z programu Visual Studio, lub jeśli masz sugestie dotyczące poprawy produktu, możesz użyć **Wyślij opinię** menu w górnej części okna programu Visual Studio obok **szybki Uruchom** pole.

![Wyślij opinię menu w programie Visual Studio](media/quickstart-IDE-send-feedback.png)

## <a name="next-steps"></a>Następne kroki

Opisaliśmy kilka funkcji programu Visual Studio, aby korzystały z interfejsem użytkownika. Aby dokładniej:

> [!div class="nextstepaction"]
> [Dowiedz się więcej o Edytorze kodu](../get-started/tutorial-editor.md)

> [!div class="nextstepaction"]
> [Dowiedz się więcej o projekty i rozwiązania](../get-started/tutorial-projects-solutions.md)

## <a name="see-also"></a>Zobacz także

- [Omówienie środowiska IDE programu Visual Studio](../get-started/visual-studio-ide.md)
- [Więcej funkcji programu Visual Studio 2017](../ide/advanced-feature-overview.md)
- [Zmienianie motywu i kolory czcionek](../ide/quickstart-personalize-the-ide.md)
