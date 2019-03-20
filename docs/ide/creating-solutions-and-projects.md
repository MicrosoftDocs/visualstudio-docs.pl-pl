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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f6f6bd03a47500c127360afd2d2a6ae6b62ee2e5
ms.sourcegitcommit: 5af29226aef0a3b4a506b69a08a97cfd21049521
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2019
ms.locfileid: "58268574"
---
# <a name="create-solutions-and-projects"></a>Tworzenie rozwiązań i projektów

*Projekty* elementy potrzebne do tworzenia aplikacji w programie Visual Studio, takich jak pliki kodu źródłowego, map bitowych, ikon i odwołania do składnika i usługi. Podczas tworzenia nowego projektu programu Visual Studio tworzy *rozwiązania* zawiera projekt. Następnie można dodać inne nowe lub istniejące projekty do rozwiązania, jeśli chcesz. Rozwiązania mogą również zawierać pliki, które nie są podłączone do żadnego konkretnego projektu.

![Hierarchia rozwiązania/projektu](./media/vside-proj-soln.png)

> [!NOTE]
> Ten temat dotyczy programu Visual Studio w Windows. Dla programu Visual Studio dla komputerów Mac, zobacz [tworzyć projekty w programie Visual Studio dla komputerów Mac](/visualstudio/mac/create-new-projects).

Można wyświetlić swoje rozwiązania i projekty, które znajdują się w oknie narzędzia o nazwie **Eksploratora rozwiązań**. Poniższy zrzut ekranu przedstawia przykładowe rozwiązanie w **Eksploratora rozwiązań** (**platformy UWP BikeSharing.Xamarin**) zawierający dwa projekty: **BikeSharing.Clients.Core** i **BikeSharing.Clients.Windows**. Każdy projekt zawiera wiele plików, folderów i odwołania. Nazwa projektu wytłuszczonym drukiem jest *projekt startowy*; oznacza to, że projekt, który rozpoczyna się po uruchomieniu aplikacji. Można określić, który projekt jest projektem startowym.

![Eksplorator rozwiązań z projektami](./media/vside-solution-explorer-projects.png)

Chociaż można utworzyć projektu samodzielnie przez dodanie niezbędnych plików do niego, Visual Studio oferuje szereg szablony projektów umożliwiające rozpoczęcie head. Tworzenie nowego projektu z szablonu zapewnia projektu przy użyciu podstawowych dla tego typu projektu, i można zmienić nazwy plików lub dodać nowego lub istniejącego kodu i innych zasobów do niego zgodnie z potrzebami.

Po uwzględnieniu rozwiązania i projekty nie muszą tworzyć aplikacje w programie Visual Studio. Możesz też po prostu otworzyć kod, który zostały sklonowane z repozytorium Git lub pobrany w innym miejscu. Aby uzyskać więcej informacji, zobacz [tworzenie kodu w programie Visual Studio bez projektów ani rozwiązań](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md).

## <a name="create-a-project-from-a-project-template"></a>Tworzenie projektu z szablonu projektu

Aby uzyskać informacje dotyczące tworzenia nowego projektu z szablonu, zobacz [Utwórz nowy projekt w programie Visual Studio](create-new-project.md).

## <a name="create-a-project-from-existing-code-files"></a>Tworzenie projektu z istniejących plików kodu

Jeśli masz kolekcję plików źródłowych kodu, możesz je łatwo dodać do projektu.

1. W menu, wybierz **pliku** > **New** > **projekt z istniejącego kodu**.

1. W **Utwórz projekt z istniejących plików kodu** kreatora, wybierz typ projektu w **jaki rodzaj projektu chcesz utworzyć?** listy rozwijanej, a następnie wybierz **dalej**  przycisku.

1. W kreatorze, przejdź do lokalizacji plików, a następnie wprowadź nazwę dla nowego projektu w **nazwa** pole. Gdy wszystko będzie gotowe, wybierz pozycję **Zakończ** przycisku.

> [!NOTE]
> Ta opcja działa najlepiej w stosunkowo prosta Kolekcja plików. Obecnie tylko Visual C++, Apache Cordova, Visual Basic i C# obsługiwanych typów projektów.

## <a name="add-files-to-a-solution"></a>Dodawanie plików do rozwiązania

Jeśli masz plik, który ma zastosowanie do wielu projektów, takich jak plik readme dla rozwiązania lub innych plików, które logicznie na poziomie rozwiązania, a nie w ramach określonego projektu, następnie można dodać je do samego rozwiązania. Aby dodać element do rozwiązania, w menu kontekstowym (kliknij prawym przyciskiem myszy) węzła rozwiązanie w **Eksploratora rozwiązań**, wybierz **Dodaj** > **nowy element**, lub **Dodaj** > **istniejący element**.

## <a name="create-a-net-project-that-targets-a-specific-version-of-the-net-framework"></a>Tworzenie projektu platformy .NET, który jest przeznaczony dla określonej wersji programu .NET Framework

Podczas tworzenia projektu można określić określonej wersji programu .NET Framework, który chcesz, aby projekt do użycia.

::: moniker range="vs-2017"

Aby określić wersji programu .NET framework, wybierz **Framework** menu rozwijane w **nowy projekt** okno dialogowe.

![W ramach listy rozwijanej w oknie dialogowym Nowy projekt](./media/vside-newproject-framework.png)

> [!NOTE]
> Musisz mieć program .NET Framework 3.5 zainstalowany w systemie do dostępu do wersji programu .NET Framework wcześniejszych niż .NET Framework 4.

::: moniker-end

::: moniker range=">=vs-2019"

Aby określić wersji programu .NET framework, wybierz **Framework** menu rozwijanego **Utwórz nowy projekt** strony.

![Selektor Framework w konfigurowania nowego projektu](media/vs-2019/configure-new-project-framework.png)

::: moniker-end

## <a name="create-empty-solutions"></a>Utwórz puste rozwiązania

Można również utworzyć pusty rozwiązania, które mają żadne projekty. Może to być preferowana w przypadkach, w którym chcesz utworzyć rozwiązanie i projekty od podstaw.

### <a name="to-create-an-empty-solution"></a>Aby utworzyć puste rozwiązanie

1. Na pasku menu wybierz **pliku** > **New** > **projektu**.

::: moniker range="vs-2017"

2. Po lewej stronie (**szablony**) okienku wybierz **inne typy projektów** > **Visual Studio Solutions** na wyświetlonej liście.

3. W środkowym okienku wybierz **puste rozwiązanie**.

4. Wprowadź **nazwa** i **lokalizacji** wartości dla danego rozwiązania, a następnie wybierz **OK**.

::: moniker-end

::: moniker range=">=vs-2019"

2. Na **Utwórz nowy projekt** wpisz **rozwiązania** w polu wyszukiwania.

3. Wybierz **puste rozwiązanie** szablonu, a następnie kliknij **dalej**.

4. Wprowadź **nazwa** i **lokalizacji** wartości dla danego rozwiązania, a następnie wybierz **Utwórz**.

::: moniker-end

Po utworzeniu puste rozwiązanie, nowe lub istniejące projekty lub elementy można dodać do niego, wybierając **Dodaj nowy element** lub **Dodaj istniejący element** na **projektu** menu.

Jak wspomniano wcześniej, można również otworzyć pliki kodu, bez konieczności używania projektu lub rozwiązania. Aby dowiedzieć się więcej o tworzeniu kodu w ten sposób, zobacz [tworzenie kodu w programie Visual Studio bez projektów ani rozwiązań](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md).

::: moniker range="vs-2017"

## <a name="create-a-temporary-project"></a>Utwórz projekt tymczasowy

(C# i Visual Basic)

Jeśli utworzysz. Projekt oparty na sieci bez określania lokalizacji na dysku, to projekt tymczasowy. Tymczasowe projekty umożliwiają eksperymentować z projektami .NET. W dowolnym momencie podczas pracy z projektem tymczasowej, można go zapisać lub odrzucić je.

Aby utworzyć projekt tymczasowy, najpierw należy przejść do **narzędzia** > **opcje** > **projekty i rozwiązania**  >   **Ogólne**i usuń zaznaczenie pola wyboru **Zapisz nowe projekty po utworzeniu** pola wyboru. Następnie otwórz **nowy projekt** standardowe okno dialogowe.

::: moniker-end

## <a name="delete-a-solution-project-or-item"></a>Usuwanie rozwiązania, projektu lub elementu

Można usunąć rozwiązania i ich zawartość trwale, ale nie przy użyciu programu Visual Studio IDE. Usuwanie elementów w programie Visual Studio tylko usunięcie ich z bieżącego rozwiązania lub projektu. Aby trwale usunąć to rozwiązanie lub innego składnika w systemie, użyj Eksploratora plików, aby usunąć folder, który zawiera *.sln* i *.suo* pliki rozwiązania. Jednak trwale rozwiązanie, zaleca się tworzenie kopii zapasowej wszelkich projektów i plików w przypadku, gdy ich potrzebujesz ponownie.

> [!NOTE]
> *.Suo* plik jest plikiem ukrytym, które nie są wyświetlane w obszarze domyślne ustawienia Eksploratora plików. Aby wyświetlić ukryte pliki na **widoku** menu w Eksploratorze plików wybierz **ukryte elementy** pola wyboru.

### <a name="permanently-delete-a-solution"></a>Trwałe usuwanie rozwiązania

1. W **Eksploratora rozwiązań**, w menu kliknij prawym przyciskiem myszy (menu kontekstowe) rozwiązanie, aby usunąć, wybierz **Otwórz folder w Eksploratorze plików**.

1. W Eksploratorze plików Przejdź jeden poziom w górę.

1. Wybierz folder, zawierająca dane rozwiązanie, a następnie naciśnij klawisz **Usuń** klucza.

## <a name="see-also"></a>Zobacz także

- [Rozwiązania i projekty](../ide/solutions-and-projects-in-visual-studio.md)
- [Repozytoriów typu open source firmy Microsoft w witrynie GitHub](https://github.com/Microsoft)
- [Przykłady kodu dla deweloperów](https://code.msdn.microsoft.com/)
- [Tworzenie projektów (Visual Studio dla komputerów Mac)](/visualstudio/mac/create-new-projects)