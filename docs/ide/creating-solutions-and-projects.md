---
title: Tworzenie rozwiązań i projektów
ms.date: 02/06/2018
ms.topic: how-to
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
ms.openlocfilehash: 19a836847aa01038bdbb015612c4fb4a3964d9a9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85770539"
---
# <a name="create-solutions-and-projects"></a>Tworzenie rozwiązań i projektów

*Projekty* przechowują elementy, które są konieczne do kompilowania aplikacji w programie Visual Studio, takie jak pliki kodu źródłowego, mapy bitowe, ikony i odwołania do składników i usług. Podczas tworzenia nowego projektu program Visual Studio tworzy *rozwiązanie* , które zawiera projekt. Jeśli chcesz, możesz dodać inne nowe lub istniejące projekty do rozwiązania. Rozwiązania mogą również zawierać pliki, które nie są połączone z żadnym konkretnym projektem.

![Rozwiązanie/Hierarchia projektu](./media/vside-proj-soln.png)

> [!NOTE]
> Ten temat ma zastosowanie do programu Visual Studio w systemie Windows. Aby uzyskać Visual Studio dla komputerów Mac, zobacz [Tworzenie projektów w Visual Studio dla komputerów Mac](/visualstudio/mac/create-new-projects).

Możesz wyświetlić swoje rozwiązania i projekty w oknie narzędzia o nazwie **Eksplorator rozwiązań**. Poniższy zrzut ekranu przedstawia przykładowe rozwiązanie w **Eksplorator rozwiązań** (**BikeSharing. Xamarin-platformy UWP**), które zawiera dwa projekty: **BikeSharing. clients. Core** i **BikeSharing. clients. Windows**. Każdy projekt zawiera wiele plików, folderów i odwołań. Nazwa projektu pogrubiona to *projekt startowy*. oznacza to, że projekt jest uruchamiany po uruchomieniu aplikacji. Można określić, który projekt jest projektem startowym.

![Eksplorator rozwiązań z projektami](./media/vside-solution-explorer-projects.png)

Chociaż można skonstruować projekt samodzielnie przez dodanie do niego niezbędnych plików, program Visual Studio oferuje wybór szablonów projektu, które umożliwiają rozpoczęcie od początku. Tworzenie nowego projektu na podstawie szablonu zapewnia projekt z Essentials dla tego typu projektu i można zmienić jego nazwę lub dodać do niego nowy lub istniejący kod oraz inne zasoby.

Z tego wynikają, że rozwiązania i projekty nie są wymagane do tworzenia aplikacji w programie Visual Studio. Możesz również otworzyć kod, który został sklonowany z usługi Git lub który został pobrany w innym miejscu. Aby uzyskać więcej informacji, zobacz [Programowanie kodu w programie Visual Studio bez projektów i rozwiązań](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md).

## <a name="create-a-project-from-a-project-template"></a>Tworzenie projektu na podstawie szablonu projektu

Aby uzyskać informacje na temat tworzenia nowego projektu na podstawie szablonu, zobacz [Tworzenie nowego projektu w programie Visual Studio](create-new-project.md).

## <a name="create-a-project-from-existing-code-files"></a>Tworzenie projektu na podstawie istniejących plików kodu

Jeśli masz kolekcję plików źródłowych kodu, możesz łatwo dodać je do projektu.

1. Z menu wybierz pozycję **plik**  >  **Nowy**  >  **projekt z istniejącego kodu**.

1. W kreatorze **tworzenia projektu z istniejących plików z kodem** wybierz typ projektu, który chcesz **utworzyć?** pole listy rozwijanej, a następnie wybierz przycisk **dalej** .

1. W Kreatorze przejdź do lokalizacji plików, a następnie wprowadź nazwę nowego projektu w polu **Nazwa** . Gdy wszystko będzie gotowe, wybierz przycisk **Zakończ** .

> [!NOTE]
> Ta opcja działa najlepiej dla stosunkowo prostej kolekcji plików. Obecnie obsługiwane są tylko typy projektów C++, Apache Cordova, Visual Basic i C#.

## <a name="add-files-to-a-solution"></a>Dodawanie plików do rozwiązania

Jeśli masz plik, który dotyczy wielu projektów, takich jak plik Readme dla rozwiązania lub inne pliki, które logicznie należą do poziomu rozwiązania, a nie w określonym projekcie, możesz dodać je do samego rozwiązania. Aby dodać element do rozwiązania, w menu kontekstowym (kliknij prawym przyciskiem myszy) węzła rozwiązania w **Eksplorator rozwiązań**wybierz pozycję **Dodaj**  >  **nowy element**lub **Dodaj**  >  **istniejący element**.

## <a name="create-a-net-project-that-targets-a-specific-version-of-the-net-framework"></a>Utwórz projekt platformy .NET, który jest przeznaczony dla określonej wersji .NET Framework

Podczas tworzenia projektu .NET Framework można określić określoną wersję .NET Framework, która ma być używana przez projekt. (Podczas tworzenia projektu .NET Core nie jest określana wersja struktury).

::: moniker range="vs-2017"

Aby określić wersję .NET Framework, wybierz menu rozwijane **Framework** w oknie dialogowym **Nowy projekt** .

![Lista rozwijana platformy w oknie dialogowym Nowy projekt](./media/vside-newproject-framework.png)

> [!NOTE]
> Aby uzyskać dostęp do wersji .NET Framework starszej niż .NET Framework 4, musisz mieć zainstalowany .NET Framework 3,5 w systemie.

::: moniker-end

::: moniker range=">=vs-2019"

Aby określić wersję .NET Framework, wybierz menu rozwijane **Struktura** na stronie **Utwórz nowy projekt** .

![Selektor struktury w temacie Konfigurowanie nowego projektu](media/vs-2019/configure-new-project-framework.png)

::: moniker-end

## <a name="create-empty-solutions"></a>Utwórz puste rozwiązania

Można również tworzyć puste rozwiązania, które nie mają projektów. Może to być zalecane w przypadkach, w których chcesz skonstruować swoje rozwiązanie i projekty od podstaw.

### <a name="to-create-an-empty-solution"></a>Aby utworzyć puste rozwiązanie

1. Na pasku menu wybierz pozycję **plik**  >  **Nowy**  >  **projekt**.

::: moniker range="vs-2017"

2. W okienku po lewej stronie (**Szablony**) wybierz pozycję **Inne typy projektów** > **Visual Studio** na rozwiniętej liście.

3. W środkowym okienku wybierz pozycję **puste rozwiązanie**.

4. Wprowadź wartości w **nazwach** i **lokalizacji** dla rozwiązania, a następnie wybierz przycisk **OK**.

::: moniker-end

::: moniker range=">=vs-2019"

2. Na stronie **Tworzenie nowego projektu** wpisz **rozwiązanie** w polu wyszukiwania.

3. Wybierz szablon **pustego rozwiązania** , a następnie kliknij przycisk **dalej**.

4. Wprowadź wartości **nazwy** i **lokalizacji** dla rozwiązania, a następnie wybierz pozycję **Utwórz**.

::: moniker-end

Po utworzeniu pustego rozwiązania można dodać do niego nowe lub istniejące projekty lub elementy, wybierając pozycję **Dodaj nowy element** lub **Dodaj istniejący element** w menu **projekt** .

Jak wspomniano wcześniej, można również otwierać pliki kodu bez potrzeby projektu lub rozwiązania. Aby dowiedzieć się więcej na temat opracowywania kodu w ten sposób, zobacz [Programowanie kodu w programie Visual Studio bez projektów i rozwiązań](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md).

::: moniker range="vs-2017"

## <a name="create-a-temporary-project"></a>Tworzenie projektu tymczasowego

(Tylko w językach C# i Visual Basic)

Jeśli utworzysz. Projekt oparty na sieci, bez określania lokalizacji dysku, jest projektem tymczasowym. Projekty tymczasowe umożliwiają eksperymentowanie z projektami .NET. W dowolnym momencie podczas pracy z projektem tymczasowym można wybrać opcję zapisywania lub odrzucania go.

Aby utworzyć projekt tymczasowy, najpierw przejdź do opcji **Narzędzia**  >  **Opcje**  >  **projekty i rozwiązania**  >  **Ogólne**i usuń zaznaczenie pola wyboru **Zapisz nowe projekty po utworzeniu** . Następnie otwórz okno dialogowe **Nowy projekt** w zwykły sposób.

::: moniker-end

## <a name="delete-a-solution-project-or-item"></a>Usuwanie rozwiązania, projektu lub elementu

Rozwiązania i ich zawartość można trwale usunąć, ale nie za pomocą środowiska IDE programu Visual Studio. Usunięcie elementów w programie Visual Studio powoduje jedynie usunięcie ich z bieżącego rozwiązania lub projektu. Aby trwale usunąć rozwiązanie lub inny składnik z systemu, należy użyć Eksploratora plików w celu usunięcia folderu zawierającego pliki rozwiązania *. sln* i *. suo* . Jednak przed trwałe usunięciem rozwiązania zaleca się wykonanie kopii zapasowej wszystkich projektów lub plików w razie potrzeby ich ponownego użycia.

> [!NOTE]
> Plik *. suo* to ukryty plik, który nie jest wyświetlany w domyślnych ustawieniach Eksploratora plików. Aby wyświetlić ukryte pliki, w menu **Widok** w Eksploratorze plików zaznacz pole wyboru **ukryte elementy** .

### <a name="permanently-delete-a-solution"></a>Trwałe usuwanie rozwiązania

1. W **Eksplorator rozwiązań**, w menu rozwijanym prawym przyciskiem myszy (menu kontekstowe) rozwiązania, które chcesz usunąć, wybierz polecenie **Otwórz folder w Eksploratorze plików**.

1. W Eksploratorze plików przejdź do góry o jeden poziom.

1. Wybierz folder zawierający rozwiązanie, a następnie naciśnij klawisz **delete** .

## <a name="see-also"></a>Zobacz też

- [Rozwiązania i projekty](../ide/solutions-and-projects-in-visual-studio.md)
- [Repozytoria Open Source firmy Microsoft w serwisie GitHub](https://github.com/Microsoft)
- [Przykłady kodu dla deweloperów](https://code.msdn.microsoft.com/)
- [Tworzenie projektów (Visual Studio dla komputerów Mac)](/visualstudio/mac/create-new-projects)
