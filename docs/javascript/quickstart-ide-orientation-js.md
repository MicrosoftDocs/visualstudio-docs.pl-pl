---
title: Przewodnik po środowiskoch IDE programu Visual Studio
titleSuffix: ''
ms.date: 02/05/2019
ms.topic: quickstart
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f7a05f62685509a69fd5dfe8f758b4e5599b9324
ms.sourcegitcommit: 334024a43477290ecc610e70c80a0f772787a7d6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/01/2020
ms.locfileid: "80527938"
---
# <a name="first-look-at-the-visual-studio-ide"></a>Pierwsze spojrzenie na środowisko IDE programu Visual Studio

W tym 5-10 minut wprowadzenie do środowiska programistycznego zintegrowanego programu Visual Studio (IDE) zajmiemy się zapoznać niektóre z okien, menu i innych funkcji interfejsu użytkownika.

::: moniker range="vs-2017"

Jeśli program Visual Studio nie został jeszcze zainstalowany, przejdź do strony [pobierania programu Visual Studio,](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) aby zainstalować ją bezpłatnie.

::: moniker-end

::: moniker range=">=vs-2019"

Jeśli program Visual Studio nie został jeszcze zainstalowany, przejdź do strony [pobierania programu Visual Studio,](https://visualstudio.microsoft.com/downloads) aby zainstalować ją bezpłatnie.

::: moniker-end

::: moniker range=">=vs-2019"

## <a name="start-window"></a>Okno startowe

Pierwszą rzeczą, którą zobaczysz po uruchomieniu programu Visual Studio, jest okno startowe. Okno startowe ma na celu pomóc "dostać się do kodu" szybciej. Ma opcje zamknięcia lub wyewidencjonowania kodu, otwarcia istniejącego projektu lub rozwiązania, utworzenia nowego projektu lub po prostu otwarcia folderu zawierającego niektóre pliki kodu.

[![Okno startowe w programie Visual Studio 2019](media/vs-2019/start-window.png)](media/vs-2019/start-window.png)

Jeśli jest to pierwszy raz przy użyciu programu Visual Studio, lista ostatnich projektów będzie pusta.

Jeśli pracujesz z bazami kodu opartymi na systemie innych niż MSBuild, użyjesz opcji **Otwórz folder lokalny,** aby otworzyć kod w programie Visual Studio. Aby uzyskać więcej informacji, zobacz [Tworzenie kodu w programie Visual Studio bez projektów i rozwiązań.](develop-javascript-code-without-solutions-projects.md) W przeciwnym razie można utworzyć nowy projekt lub sklonować projekt z dostawcy źródłowego, takiego jak GitHub lub Azure DevOps.

Opcja **Kontynuuj bez kodu** po prostu otwiera środowisko programistyczne Visual Studio bez ładowania określonego projektu lub kodu. Można wybrać tę opcję, aby dołączyć do sesji [udostępniania na żywo](/visualstudio/liveshare/) lub dołączyć do procesu debugowania. Można również nacisnąć **klawisz Esc,** aby zamknąć okno startowe i otworzyć IDE.

::: moniker-end

::: moniker range="vs-2017"

## <a name="start-page"></a>Strona początkowa

Pierwszą rzeczą, którą zobaczysz po uruchomieniu programu Visual Studio, jest najprawdopodobniej **strona początkowa**. Strona **początkowa** została zaprojektowana jako "centrum", aby ułatwić szybsze znajdowanie potrzebnych poleceń i plików projektu. W sekcji **Ostatnie** są wyświetlane projekty i foldery, nad którymi ostatnio pracowałeś. W obszarze **Nowy projekt**można kliknąć łącze, aby przywołać okno dialogowe **Nowy projekt,** lub w obszarze **Otwórz**, można otworzyć istniejący projekt lub folder kodu. Po prawej stronie znajduje się kanał najnowszych wiadomości deweloperów.

![Strona startowa w programie Visual Studio](media/start-page.png)

Jeśli zamkniesz **stronę początkową** i chcesz ją ponownie wyświetlić, możesz ją ponownie otworzyć z menu **Plik.**

![Menu Plik w programie Visual Studio](media/quickstart-IDE-file-menu-large.png)

::: moniker-end

## <a name="create-a-project"></a>Tworzenie projektu

Aby kontynuować eksplorowanie funkcji programu Visual Studio, utwórzmy nowy projekt.

::: moniker range=">=vs-2019"

1. W oknie startowym wybierz pozycję **Utwórz nowy projekt**, a następnie w polu wyszukiwania wpisz w **języku JavaScript,** aby filtrować listę typów projektów do tych, które zawierają "javascript" w nazwie lub typie języka.

   Program Visual Studio udostępnia różne rodzaje szablonów projektów, które ułatwią szybkie rozpoczęcie kodowania. (Alternatywnie, jeśli jesteś programistą TypeScript, możesz utworzyć projekt w tym języku. Interfejs użytkownika, który będziemy patrzeć na jest podobny dla wszystkich języków programowania.)

   ![Wyszukiwanie szablonów projektów w oknie startowym programu Visual Studio](media/vs-2019/create-new-project.png)

1. Wybierz szablon projektu **pustego pliku Node.js Web Application** i kliknij przycisk **Dalej**.

1. W wyświetlonym oknie dialogowym **Konfigurowanie nowego projektu** zaakceptuj domyślną nazwę projektu i wybierz pozycję **Utwórz**.

::: moniker-end

::: moniker range="vs-2017"

1. Na **stronie początkowej**, w polu wyszukiwania w obszarze **Nowy projekt**wpisz **javascript,** aby filtrować listę typów projektów do tych, które zawierają "javascript" w nazwie lub typie języka.

   ![Szukaj szablonów projektów na stronie startowej programu Visual Studio](media/start-page-search-templates.png)

   Program Visual Studio udostępnia różne rodzaje szablonów projektów, które ułatwią szybkie rozpoczęcie kodowania. Wybierz szablon projektu **pustej aplikacji sieci Web Node.js.** (Alternatywnie, jeśli jesteś programistą TypeScript, możesz utworzyć projekt w tym języku. Interfejs użytkownika, który będziemy patrzeć na jest podobny dla wszystkich języków programowania.)

1. W wyświetlonym oknie dialogowym **Nowy projekt** zaakceptuj domyślną nazwę projektu i wybierz przycisk **OK**.
::: moniker-end

   Projekt zostanie utworzony, a plik o nazwie *server.js* zostanie otwarty w oknie **Edytor.** **Edytor** pokazuje zawartość plików i jest, gdzie można wykonać większość pracy kodowania w programie Visual Studio.

   ![Edytor w programie Visual Studio](media/editor.png)

## <a name="solution-explorer"></a>Eksplorator rozwiązań

**Eksplorator rozwiązań**, który jest zazwyczaj po prawej stronie programu Visual Studio, pokazuje graficzną reprezentację hierarchii plików i folderów w projekcie, rozwiązaniu lub folderze kodu. Możesz przeglądać hierarchię i przechodzić do pliku w **Eksploratorze rozwiązań**.

![Eksplorator rozwiązań w programie Visual Studio](media/quickstart-IDE-solution-explorer.png)

## <a name="menus"></a>Menu

Pasek menu u góry polecenia programu Visual Studio grupuje w kategorie. Na przykład **menu Projekt** zawiera polecenia związane z projektem, w którym pracujesz. W menu **Narzędzia** można dostosować zachowanie programu Visual Studio, wybierając pozycję **Opcje**lub dodać funkcje do instalacji, wybierając pozycję **Pobierz narzędzia i funkcje**.

![Pasek menu w programie Visual Studio](media/quickstart-IDE-menu-bar.png)

Otwórzmy okno **Lista błędów,** wybierając menu **Widok,** a następnie **listę błędów**.

## <a name="error-list"></a>Lista błędów

**Lista błędów** pokazuje błędy, ostrzeżenia i komunikaty dotyczące bieżącego stanu kodu. Jeśli w pliku lub w dowolnym miejscu projektu wystąpią błędy (takie jak brakujące nawiasy klamrowe lub średnik), są one wymienione w tym miejscu.

![Lista błędów w programie Visual Studio](media/quickstart-IDE-error-list.png)

## <a name="output-window"></a>Okno wyniku

Okno **Dane wyjściowe** zawiera komunikaty wyjściowe z tworzenia projektu i od dostawcy kontroli źródła.

Skompilujmy projekt, aby zobaczyć niektóre dane wyjściowe kompilacji. Z menu **Kompilacja** wybierz polecenie **Build Solution**. Okno **Dane wyjściowe** automatycznie uzyskuje fokus i wyświetla komunikat kompilacji pomyślnej.

![Okno dane wyjściowe w programie Visual Studio](media/build-output-minimal.png)

## <a name="search-box"></a>Pole wyszukiwania

Pole wyszukiwania jest szybki i łatwy sposób zrobić prawie wszystko w programie Visual Studio. Możesz wprowadzić tekst związany z tym, co chcesz zrobić, a wyświetli listę opcji, które odnoszą się do tekstu. Załóżmy na przykład, że chcesz zwiększyć szczegółowość danych wyjściowych kompilacji, aby wyświetlić dodatkowe szczegóły dotyczące tego, co dokładnie wykonuje kompilacja. Oto jak możesz to zrobić:

1. Wpisz **szczegółowość** w polu wyszukiwania. Z wyświetlanych wyników wybierz pozycję **Projekty i rozwiązania — > budować i uruchamiać** w kategorii **Opcje.**

   ![Pole wyszukiwania w programie Visual Studio](media/quickstart-IDE-quick-launch.png)

   Zostanie otwarte okno dialogowe **Opcje** na stronie Opcje **kompilacji i uruchamiania.**

1. W obszarze **MSBuild project build output verbosity**, choose **Normal**, and then click **OK**.

1. Skompiluj projekt ponownie, klikając prawym przyciskiem myszy projekt **NodejsWebApp1** w **Eksploratorze rozwiązań** i wybierając **polecenie Odbuduj** z menu kontekstowego.

   Tym razem **okno Dane wyjściowe** pokazuje więcej szczegółowego rejestrowania z procesu kompilacji, w tym, które pliki zostały skopiowane gdzie.

   ![Pełne dane wyjściowe kompilacji w programie Visual Studio](media/build-output-verbose.png)

## <a name="send-feedback-menu"></a>Menu Wyślij opinię

Jeśli wystąpią jakiekolwiek problemy podczas korzystania z programu Visual Studio lub jeśli masz sugestie dotyczące sposobu poprawy produktu, można użyć menu **Wyślij opinię** w górnej części okna programu Visual Studio.

![Menu Wyślij opinię w programie Visual Studio](../ide/media/quickstart-ide-send-feedback.png)

## <a name="next-steps"></a>Następne kroki

Przyjrzeliśmy się tylko kilka funkcji programu Visual Studio, aby zapoznać się z interfejsem użytkownika. Aby zbadać dalej:

> [!div class="nextstepaction"]
> [Dowiedz się więcej o edytorze kodu](write-and-edit-code.md)

> [!div class="nextstepaction"]
> [Dowiedz się więcej o projektach i rozwiązaniach](../get-started/tutorial-projects-solutions.md)

## <a name="see-also"></a>Zobacz też

- [Omówienie środowiska IDE programu Visual Studio](../get-started/visual-studio-ide.md)
- [Więcej funkcji programu Visual Studio 2017](../ide/advanced-feature-overview.md)
- [Zmienianie kolorów motywów i czcionek](../ide/quickstart-personalize-the-ide.md)
