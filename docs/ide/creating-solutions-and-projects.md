---
title: Tworzenie rozwiązań i projektów
ms.date: 02/06/2018
ms.topic: conceptual
f1_keywords:
- vs.openprojectfromweb
- VS.ToolsOptionsPages.Projects.General
- SolutionItemsProject
helpviewer_keywords:
- solutions [Visual Studio], creating
- projects [Visual Studio], creating
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 503b343299f7b30e9f5e834099274215b262a635
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "79301819"
---
# <a name="create-solutions-and-projects"></a>Tworzenie rozwiązań i projektów

*Projekty* przechowują elementy potrzebne do tworzenia aplikacji w programie Visual Studio, takie jak pliki kodu źródłowego, mapy bitowe, ikony oraz odwołania do składników i usług. Podczas tworzenia nowego projektu visual studio tworzy *rozwiązanie,* które zawiera projekt. Następnie można dodać inne nowe lub istniejące projekty do rozwiązania, jeśli chcesz. Rozwiązania mogą również zawierać pliki, które nie są połączone z żadnym konkretnym projektem.

![Hierarchia rozwiązania/projektu](./media/vside-proj-soln.png)

> [!NOTE]
> W tym temacie stosuje się do programu Visual Studio w systemie Windows. W przypadku programu Visual Studio dla komputerów Mac zobacz [Tworzenie projektów w programie Visual Studio dla komputerów Mac](/visualstudio/mac/create-new-projects).

Rozwiązania i projekty można wyświetlać w oknie narzędzi o nazwie **Eksplorator rozwiązań**. Poniższy zrzut ekranu przedstawia przykładowe rozwiązanie w **Eksploratorze rozwiązań** **(BikeSharing.Xamarin-UWP),** które zawiera dwa projekty: **BikeSharing.Clients.Core** i **BikeSharing.Clients.Windows**. Każdy projekt zawiera wiele plików, folderów i odniesień. Nazwa projektu pogrubioną czcionką jest *projektem startowym;* oznacza to, że projekt, który uruchamia się po uruchomieniu aplikacji. Można określić, który projekt jest projektem startowym.

![Eksplorator rozwiązań z projektami](./media/vside-solution-explorer-projects.png)

Chociaż można utworzyć projekt samodzielnie, dodając do niego niezbędne pliki, Visual Studio oferuje wybór szablonów projektu, aby dać początek. Tworzenie nowego projektu z szablonu daje projekt z podstawowymi dla tego typu projektu i można zmienić nazwę plików lub dodać nowy lub istniejący kod i inne zasoby do niego w razie potrzeby.

Mając na uwadze, że rozwiązania i projekty nie są wymagane do tworzenia aplikacji w programie Visual Studio. Możesz również po prostu otworzyć kod, który został sklonowany z Git lub pobrany w innym miejscu. Aby uzyskać więcej informacji, zobacz [Tworzenie kodu w programie Visual Studio bez projektów i rozwiązań.](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md)

## <a name="create-a-project-from-a-project-template"></a>Tworzenie projektu na podstawie szablonu projektu

Aby uzyskać informacje dotyczące tworzenia nowego projektu z szablonu, zobacz [Tworzenie nowego projektu w programie Visual Studio](create-new-project.md).

## <a name="create-a-project-from-existing-code-files"></a>Tworzenie projektu na podstawie istniejących plików kodu

Jeśli masz kolekcję plików źródłowych kodu, można łatwo dodać je do projektu.

1. W menu wybierz polecenie **Plik** > **nowego** > **projektu z istniejącego kodu**.

1. W kreatorze **Tworzenie projektu z istniejących plików kodu** wybierz odpowiedni typ projektu w polu listy **Next** **rozwijanej Jaki typ projektu chcesz utworzyć?**

1. W kreatorze przejdź do lokalizacji plików, a następnie wprowadź nazwę nowego projektu w polu **Nazwa.** Po zakończeniu wybierz przycisk **Zakończ.**

> [!NOTE]
> Ta opcja działa najlepiej w przypadku stosunkowo prostej kolekcji plików. Obecnie obsługiwane są tylko typy projektów C++, Apache Cordova, Visual Basic i C#.

## <a name="add-files-to-a-solution"></a>Dodawanie plików do rozwiązania

Jeśli masz plik, który ma zastosowanie do wielu projektów, takich jak plik readme dla rozwiązania lub innych plików, które logicznie należą do poziomu rozwiązania, a nie w ramach określonego projektu, następnie można dodać je do samego rozwiązania. Aby dodać element do rozwiązania, w menu kontekstu (kliknięcie prawym przyciskiem myszy) węzła rozwiązania w **Eksploratorze rozwiązań**wybierz pozycję **Dodaj** > **nowy element**lub **Dodaj** > **istniejący element**.

## <a name="create-a-net-project-that-targets-a-specific-version-of-the-net-framework"></a>Tworzenie projektu platformy .NET przeznaczonego dla określonej wersji programu .NET Framework

Podczas tworzenia projektu .NET Framework można określić określoną wersję programu .NET Framework, który ma być używany przez projekt. (Podczas tworzenia projektu .NET Core nie określa się wersji struktury).

::: moniker range="vs-2017"

Aby określić wersję programu .NET Framework, wybierz menu rozwijane **Framework** w oknie dialogowym **Nowy projekt.**

![Rozwijana struktura w oknie dialogowym Nowy projekt](./media/vside-newproject-framework.png)

> [!NOTE]
> Aby uzyskać dostęp do wersji programu .NET Framework 4, w systemie musi być zainstalowany program .NET Framework 3.5.

::: moniker-end

::: moniker range=">=vs-2019"

Aby określić wersję programu .NET Framework, wybierz menu rozwijane **Framework** na stronie **Tworzenie nowego projektu.**

![Selektor struktury w konfigurowaniu nowego projektu](media/vs-2019/configure-new-project-framework.png)

::: moniker-end

## <a name="create-empty-solutions"></a>Tworzenie pustych rozwiązań

Można również utworzyć puste rozwiązania, które nie mają żadnych projektów. Może to być korzystne w przypadkach, gdy chcesz skonstruować rozwiązanie i projekty od podstaw.

### <a name="to-create-an-empty-solution"></a>Aby utworzyć puste rozwiązanie

1. Na pasku menu wybierz pozycję **Plik** > **nowego** > **projektu**.

::: moniker range="vs-2017"

2. Po lewej stronie**okienka (Szablony)** wybierz pozycję **Inne typy** > projektów **Visual Studio Solutions** na rozwiniętej liście.

3. W środkowym okienku wybierz pozycję **Puste rozwiązanie**.

4. Wprowadź **wartości nazwy** i **lokalizacji** rozwiązania, a następnie wybierz przycisk **OK**.

::: moniker-end

::: moniker range=">=vs-2019"

2. Na stronie **Tworzenie nowego projektu** wpisz **rozwiązanie** w polu wyszukiwania.

3. Zaznacz szablon **Puste rozwiązanie,** a następnie kliknij przycisk **Dalej**.

4. Wprowadź **wartości nazwy** i **lokalizacji** dla rozwiązania, a następnie wybierz pozycję **Utwórz**.

::: moniker-end

Po utworzeniu pustego rozwiązania można dodać do niego nowe lub istniejące projekty lub elementy, wybierając polecenie **Dodaj nowy element** lub Dodaj **istniejący element** w menu **Projekt.**

Jak wspomniano wcześniej, można również otworzyć pliki kodu bez konieczności projektu lub rozwiązania. Aby dowiedzieć się więcej o opracowywaniu kodu w ten sposób, zobacz [Tworzenie kodu w programie Visual Studio bez projektów i rozwiązań.](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md)

::: moniker range="vs-2017"

## <a name="create-a-temporary-project"></a>Tworzenie projektu tymczasowego

(tylko c# i visual basic)

Jeśli utworzysz plik . Projekt oparty na sieci, bez określania lokalizacji dysku, jest to projekt tymczasowy. Projekty tymczasowe umożliwiają eksperymentowanie z projektami platformy .NET. W dowolnym momencie podczas pracy z tymczasowym projektem możesz go zapisać lub odrzucić.

Aby utworzyć projekt tymczasowy, najpierw przejdź do **pozycji Narzędzia** > **Opcje** > projekty i rozwiązania**ogólne**i wyewidencjonuj**Projects and Solutions** > pole wyboru **Zapisz nowe projekty podczas tworzenia.** Następnie otwórz okno dialogowe **Nowy projekt** w zwykły sposób.

::: moniker-end

## <a name="delete-a-solution-project-or-item"></a>Usuwanie rozwiązania, projektu lub elementu

Rozwiązania i ich zawartość można usunąć trwale, ale nie przy użyciu środowiska IDE programu Visual Studio. Usuwanie elementów w programie Visual Studio usuwa je tylko z bieżącego rozwiązania lub projektu. Aby trwale usunąć rozwiązanie lub inny składnik z systemu, użyj Eksploratora plików, aby usunąć folder zawierający pliki rozwiązania *.sln* i *.suo.* Jednak przed trwałym usunięciem rozwiązania zaleca się wykonanie kopii zapasowej wszystkich projektów lub plików na wypadek, gdyby były potrzebne ponownie.

> [!NOTE]
> Plik *.suo* jest ukrytym plikiem, który nie jest wyświetlany w domyślnych ustawieniach Eksploratora plików. Aby wyświetlić ukryte pliki, w menu **Widok** w Eksploratorze plików zaznacz pole wyboru **Ukryte elementy.**

### <a name="permanently-delete-a-solution"></a>Trwałe usunięcie rozwiązania

1. W **Eksploratorze rozwiązań**w menu i prawym przyciskiem myszy (menu kontekstowym) rozwiązania, które chcesz usunąć, wybierz polecenie **Otwórz folder w Eksploratorze plików**.

1. W Eksploratorze plików przejdź w górę o jeden poziom.

1. Wybierz folder zawierający rozwiązanie, a następnie naciśnij klawisz **Delete.**

## <a name="see-also"></a>Zobacz też

- [Rozwiązania i projekty](../ide/solutions-and-projects-in-visual-studio.md)
- [Repozytoria open source firmy Microsoft w usłudze GitHub](https://github.com/Microsoft)
- [Przykłady kodu dewelopera](https://code.msdn.microsoft.com/)
- [Tworzenie projektów (Visual Studio dla komputerów Mac)](/visualstudio/mac/create-new-projects)
