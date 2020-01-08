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
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75589750"
---
# <a name="create-solutions-and-projects"></a>Tworzenie rozwiązań i projektów

*Projekty* przechowują elementy, które są konieczne do kompilowania aplikacji w programie Visual Studio, takie jak pliki kodu źródłowego, mapy bitowe, ikony i odwołania do składników i usług. Podczas tworzenia nowego projektu programu Visual Studio tworzy *rozwiązania* zawiera projekt. Następnie można dodać inne nowe lub istniejące projekty do rozwiązania, jeśli chcesz. Rozwiązania mogą również zawierać pliki, które nie są podłączone do żadnego konkretnego projektu.

![Hierarchia rozwiązania/projektu](./media/vside-proj-soln.png)

> [!NOTE]
> Ten temat dotyczy programu Visual Studio w Windows. Dla programu Visual Studio dla komputerów Mac, zobacz [tworzyć projekty w programie Visual Studio dla komputerów Mac](/visualstudio/mac/create-new-projects).

Można wyświetlić swoje rozwiązania i projekty, które znajdują się w oknie narzędzia o nazwie **Eksploratora rozwiązań**. Poniższy zrzut ekranu przedstawia przykładowe rozwiązanie w **Eksploratora rozwiązań** (**platformy UWP BikeSharing.Xamarin**) zawierający dwa projekty: **BikeSharing.Clients.Core** i **BikeSharing.Clients.Windows**. Każdy projekt zawiera wiele plików, folderów i odwołania. Nazwa projektu wytłuszczonym drukiem jest *projekt startowy*; oznacza to, że projekt, który rozpoczyna się po uruchomieniu aplikacji. Można określić, który projekt jest projektem startowym.

![Eksplorator rozwiązań z projektami](./media/vside-solution-explorer-projects.png)

Chociaż można utworzyć projektu samodzielnie przez dodanie niezbędnych plików do niego, Visual Studio oferuje szereg szablony projektów umożliwiające rozpoczęcie head. Tworzenie nowego projektu z szablonu zapewnia projektu przy użyciu podstawowych dla tego typu projektu, i można zmienić nazwy plików lub dodać nowego lub istniejącego kodu i innych zasobów do niego zgodnie z potrzebami.

Po uwzględnieniu rozwiązania i projekty nie muszą tworzyć aplikacje w programie Visual Studio. Możesz też po prostu otworzyć kod, który zostały sklonowane z repozytorium Git lub pobrany w innym miejscu. Aby uzyskać więcej informacji, zobacz [tworzenie kodu w programie Visual Studio bez projektów ani rozwiązań](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md).

## <a name="create-a-project-from-a-project-template"></a>Tworzenie projektu na podstawie szablonu projektu

Aby uzyskać informacje na temat tworzenia nowego projektu na podstawie szablonu, zobacz [Tworzenie nowego projektu w programie Visual Studio](create-new-project.md).

## <a name="create-a-project-from-existing-code-files"></a>Tworzenie projektu z istniejących plików kodu

Jeśli masz kolekcję plików źródłowych kodu, możesz je łatwo dodać do projektu.

1. W menu, wybierz **pliku** > **New** > **projekt z istniejącego kodu**.

1. W **Utwórz projekt z istniejących plików kodu** kreatora, wybierz typ projektu w **jaki rodzaj projektu chcesz utworzyć?** listy rozwijanej, a następnie wybierz **dalej**  przycisku.

1. W kreatorze, przejdź do lokalizacji plików, a następnie wprowadź nazwę dla nowego projektu w **nazwa** pole. Gdy wszystko będzie gotowe, wybierz pozycję **Zakończ** przycisku.

> [!NOTE]
> Ta opcja działa najlepiej w stosunkowo prosta Kolekcja plików. Obecnie obsługiwane są C++tylko typy Apache Cordova, Visual Basic i C# projektu.

## <a name="add-files-to-a-solution"></a>Dodawanie plików do rozwiązania

Jeśli masz plik, który ma zastosowanie do wielu projektów, takich jak plik readme dla rozwiązania lub innych plików, które logicznie na poziomie rozwiązania, a nie w ramach określonego projektu, następnie można dodać je do samego rozwiązania. Aby dodać element do rozwiązania, w menu kontekstowym (kliknij prawym przyciskiem myszy) węzła rozwiązanie w **Eksploratora rozwiązań**, wybierz **Dodaj** > **nowy element**, lub **Dodaj** > **istniejący element**.

## <a name="create-a-net-project-that-targets-a-specific-version-of-the-net-framework"></a>Tworzenie projektu platformy .NET, który jest przeznaczony dla określonej wersji programu .NET Framework

Podczas tworzenia projektu .NET Framework można określić określoną wersję .NET Framework, która ma być używana przez projekt. (Podczas tworzenia projektu .NET Core nie jest określana wersja struktury).

::: moniker range="vs-2017"

Aby określić wersję .NET Framework, wybierz menu rozwijane **Framework** w oknie dialogowym **Nowy projekt** .

![W ramach listy rozwijanej w oknie dialogowym Nowy projekt](./media/vside-newproject-framework.png)

> [!NOTE]
> Musisz mieć program .NET Framework 3.5 zainstalowany w systemie do dostępu do wersji programu .NET Framework wcześniejszych niż .NET Framework 4.

::: moniker-end

::: moniker range=">=vs-2019"

Aby określić wersję .NET Framework, wybierz menu rozwijane **Struktura** na stronie **Utwórz nowy projekt** .

![Selektor struktury w temacie Konfigurowanie nowego projektu](media/vs-2019/configure-new-project-framework.png)

::: moniker-end

## <a name="create-empty-solutions"></a>Utwórz puste rozwiązania

Można również utworzyć pusty rozwiązania, które mają żadne projekty. Może to być preferowana w przypadkach, w którym chcesz utworzyć rozwiązanie i projekty od podstaw.

### <a name="to-create-an-empty-solution"></a>Aby utworzyć puste rozwiązanie

1. Na pasku menu wybierz **pliku** > **New** > **projektu**.

::: moniker range="vs-2017"

2. W okienku po lewej stronie (**Szablony**) wybierz pozycję **inne typy projektów** > **rozwiązania programu Visual Studio** na rozwiniętej liście.

3. W środkowym okienku wybierz **puste rozwiązanie**.

4. Wprowadź wartości w **nazwach** i **lokalizacji** dla rozwiązania, a następnie wybierz przycisk **OK**.

::: moniker-end

::: moniker range=">=vs-2019"

2. Na stronie **Tworzenie nowego projektu** wpisz **rozwiązanie** w polu wyszukiwania.

3. Wybierz szablon **pustego rozwiązania** , a następnie kliknij przycisk **dalej**.

4. Wprowadź wartości **nazwy** i **lokalizacji** dla rozwiązania, a następnie wybierz pozycję **Utwórz**.

::: moniker-end

Po utworzeniu puste rozwiązanie, nowe lub istniejące projekty lub elementy można dodać do niego, wybierając **Dodaj nowy element** lub **Dodaj istniejący element** na **projektu** menu.

Jak wspomniano wcześniej, można również otworzyć pliki kodu, bez konieczności używania projektu lub rozwiązania. Aby dowiedzieć się więcej o tworzeniu kodu w ten sposób, zobacz [tworzenie kodu w programie Visual Studio bez projektów ani rozwiązań](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md).

::: moniker range="vs-2017"

## <a name="create-a-temporary-project"></a>Tworzenie projektu tymczasowego

(C# tylko Visual Basic)

Jeśli utworzysz. Projekt oparty na sieci bez określania lokalizacji na dysku, to projekt tymczasowy. Tymczasowe projekty umożliwiają eksperymentować z projektami .NET. W dowolnym momencie podczas pracy z projektem tymczasowej, można go zapisać lub odrzucić je.

Aby utworzyć projekt tymczasowy, najpierw należy przejść do **narzędzia** > **opcje** > **projekty i rozwiązania**  >   **Ogólne**i usuń zaznaczenie pola wyboru **Zapisz nowe projekty po utworzeniu** pola wyboru. Następnie otwórz **nowy projekt** standardowe okno dialogowe.

::: moniker-end

## <a name="delete-a-solution-project-or-item"></a>Usuwanie rozwiązania, projektu lub elementu

Można usunąć rozwiązania i ich zawartość trwale, ale nie przy użyciu programu Visual Studio IDE. Usuwanie elementów w programie Visual Studio tylko usunięcie ich z bieżącego rozwiązania lub projektu. Aby trwale usunąć to rozwiązanie lub innego składnika w systemie, użyj Eksploratora plików, aby usunąć folder, który zawiera *.sln* i *.suo* pliki rozwiązania. Jednak trwale rozwiązanie, zaleca się tworzenie kopii zapasowej wszelkich projektów i plików w przypadku, gdy ich potrzebujesz ponownie.

> [!NOTE]
> *.Suo* plik jest plikiem ukrytym, które nie są wyświetlane w obszarze domyślne ustawienia Eksploratora plików. Aby wyświetlić ukryte pliki na **widoku** menu w Eksploratorze plików wybierz **ukryte elementy** pola wyboru.

### <a name="permanently-delete-a-solution"></a>Trwałe usuwanie rozwiązania

1. W **Eksplorator rozwiązań**, w menu rozwijanym prawym przyciskiem myszy (menu kontekstowe) rozwiązania, które chcesz usunąć, wybierz polecenie **Otwórz folder w Eksploratorze plików**.

1. W Eksploratorze plików Przejdź jeden poziom w górę.

1. Wybierz folder zawierający rozwiązanie, a następnie naciśnij klawisz **delete** .

## <a name="see-also"></a>Zobacz także

- [Rozwiązania i projekty](../ide/solutions-and-projects-in-visual-studio.md)
- [Repozytoriów typu open source firmy Microsoft w witrynie GitHub](https://github.com/Microsoft)
- [Przykłady kodu dla deweloperów](https://code.msdn.microsoft.com/)
- [Tworzenie projektów (Visual Studio dla komputerów Mac)](/visualstudio/mac/create-new-projects)
