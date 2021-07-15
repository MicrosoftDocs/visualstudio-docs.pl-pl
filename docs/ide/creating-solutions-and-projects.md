---
title: Tworzenie projektów & rozwiązań
description: Dowiedz się, jak tworzyć rozwiązania i projekty Visual Studio używać ich do przechowywania artefaktów.
ms.custom: SEO-VS-2020, contperf-fy21q2
ms.date: 06/14/2021
ms.topic: how-to
f1_keywords:
- vs.openprojectfromweb
- VS.ToolsOptionsPages.Projects.General
helpviewer_keywords:
- solutions [Visual Studio], creating
- projects [Visual Studio], creating
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: a76051c2be5bf6f260c953ded3d1e10ecb676ea9
ms.sourcegitcommit: d0061f62c8543ff0db500972d9402a7f00e017c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/15/2021
ms.locfileid: "114201809"
---
# <a name="create-work-with-and-delete-visual-studio-projects-and-solutions"></a>Tworzenie, praca z projektami i rozwiązaniami oraz Visual Studio z projektami i rozwiązaniami

W tym artykule dowiesz się, jak tworzyć i używać projektów Visual Studio od podstaw do przechowywania artefaktów potrzebnych do kompilowania aplikacji.  Jeśli nie znasz projektów w programie Visual Studio, zobacz to omówienie projektów [i rozwiązań.](solutions-and-projects-in-visual-studio.md)  Aby dowiedzieć się, jak szybko utworzyć projekt na podstawie szablonu, zobacz [Tworzenie projektu na podstawie szablonu](create-new-project.md).

*Projekty* przechowywać elementy potrzebne do kompilowania aplikacji w usłudze Visual Studio, takie jak pliki kodu źródłowego, mapy bitowe, ikony oraz odwołania do składników i usług. Podczas tworzenia nowego projektu Visual Studio *rozwiązanie, które* będzie zawierać projekt. Następnie możesz dodać inne nowe lub istniejące projekty do rozwiązania, jeśli chcesz. Możesz również utworzyć [puste lub puste rozwiązania](#create-empty-solutions). Rozwiązania mogą również zawierać pliki, które nie są połączone z żadnym konkretnym projektem.

![Diagram przedstawiający hierarchię rozwiązania i projektu.](./media/vside-proj-soln.png)

> [!NOTE]
> Ten temat dotyczy Visual Studio na Windows. Aby uzyskać Visual Studio dla komputerów Mac, zobacz [Create projects in Visual Studio dla komputerów Mac (Tworzenie projektów w programie Visual Studio dla komputerów Mac](/visualstudio/mac/create-new-projects)).

Rozwiązania i projekty można wyświetlać w oknie narzędzi o nazwie **Eksplorator rozwiązań**. Poniższy zrzut ekranu przedstawia przykładowe rozwiązanie w programie **Eksplorator rozwiązań** **(BikeSharing.Xamarin-UWP),** które zawiera dwa projekty: **BikeSharing.Clients.Core** i **BikeSharing.Clients.Windows**. Każdy projekt zawiera wiele plików, folderów i odwołań. Nazwa projektu pogrubiona to *projekt startowy*. oznacza to, że projekt, który jest uruchamiany po uruchomieniu aplikacji. Możesz określić, który projekt jest projektem startowym.

![Zrzut ekranu przedstawiający Eksplorator rozwiązań z dwoma projektami.](./media/vside-solution-explorer-projects.png)

Chociaż projekt można skonstruować samodzielnie, dodając do niego niezbędne pliki, Visual Studio oferuje wybór szablonów projektów, które zapewniają początek pracy. Utworzenie nowego projektu na podstawie szablonu daje projekt z podstawowymi elementami dla tego typu projektu i można zmienić nazwy plików lub dodać do niego nowy lub istniejący kod i inne zasoby zgodnie z potrzebami.

Oznacza to, że rozwiązania i projekty nie są wymagane do tworzenia aplikacji w Visual Studio. Możesz również po prostu otworzyć kod sklonowany z usługi Git lub pobrany w innym miejscu. Aby uzyskać więcej informacji, zobacz Develop code in Visual Studio without projects or solutions (Tworzenie kodu [w programie Visual Studio bez projektów lub rozwiązań).](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md)

## <a name="create-a-project-from-a-project-template"></a>Tworzenie projektu na podstawie szablonu projektu

Aby uzyskać informacje na temat wybierania szablonu w celu utworzenia nowego projektu, zobacz [Tworzenie nowego projektu w](create-new-project.md)Visual Studio . Aby uzyskać przykładowy projekt i rozwiązanie utworzone od podstaw, wraz z instrukcjami krok po kroku i przykładowym kodem, zobacz Introduction to projects and solutions (Wprowadzenie do projektów [i rozwiązań).](../get-started/tutorial-projects-solutions.md)

## <a name="create-a-project-from-existing-code-files"></a>Tworzenie projektu z istniejących plików kodu

Jeśli masz kolekcję plików źródłowych kodu, możesz łatwo dodać je do projektu.

1. W menu wybierz pozycję **Nowy** plik  >  **Project** z  >  **istniejącego kodu.**

1. W **kreatorze Tworzenie Project** z istniejących plików kodu wybierz typ projektu z listy rozwijanej Jakiego typu projekt chcesz  **utworzyć?,** a następnie wybierz przycisk Dalej.

1. W kreatorze przejdź do lokalizacji plików, a następnie wprowadź nazwę nowego projektu w **polu** Nazwa. Gdy wszystko będzie gotowe, wybierz **przycisk** Zakończ.

> [!NOTE]
> Ta opcja sprawdza się najlepiej w przypadku stosunkowo prostej kolekcji plików. Obecnie obsługiwane są tylko typy projektów C++, Apache Cordova, Visual Basic i C#.

## <a name="add-files-to-a-solution"></a>Dodawanie plików do rozwiązania

Jeśli masz plik, który ma zastosowanie do wielu projektów, takich jak plik readme dla rozwiązania lub inne pliki, które logicznie należą na poziomie rozwiązania, a nie w ramach określonego projektu, możesz dodać je do samego rozwiązania. Aby dodać element do rozwiązania, w menu kontekstowym (kliknij prawym przyciskiem myszy) węzła rozwiązania w **programie Eksplorator rozwiązań** wybierz pozycję Dodaj nowy element lub Dodaj  >  istniejący   >  **element.**

> [!TIP]
> Plik rozwiązania to struktura do organizowania projektów w Visual Studio. Zawiera ona stan tych informacji w dwóch plikach: plik *sln* (tekstowy, udostępniony) i plik *suo* (binarny, ukryty, opcje rozwiązania specyficzne dla użytkownika). W związku z tym rozwiązanie nie jest czymś, co powinno zostać skopiowane i zmienione. Zamiast tego najlepiej jest utworzyć nowe rozwiązanie, a następnie dodać do niego istniejące elementy.

## <a name="create-a-net-project-that-targets-a-specific-version-of-the-net-framework"></a>Tworzenie projektu .NET, który jest przeznaczony dla określonej wersji .NET Framework

Podczas tworzenia .NET Framework projektu można określić konkretną wersję aplikacji.NET Framework której ma używać projekt. (Podczas tworzenia projektu .NET Core nie określasz wersji struktury).

::: moniker range="vs-2017"

Aby określić .NET Framework wersji, wybierz menu rozwijane **Framework** w oknie **Project** dialogowym.

![Zrzut ekranu przedstawiający menu rozwijane Framework w oknie Project dialogowym.](./media/vside-newproject-framework.png)

> [!NOTE]
> Aby uzyskać dostęp do .NET Framework starszych niż .NET Framework 4, musisz mieć zainstalowaną w systemie .NET Framework 3.5.

::: moniker-end

::: moniker range=">=vs-2019"

Aby określić .NET Framework, wybierz menu rozwijane **Framework** na stronie **Tworzenie nowego** projektu.

![Zrzut ekranu selektora struktury w oknie dialogowym "Konfigurowanie nowego projektu".](media/vs-2019/configure-new-project-framework.png)

::: moniker-end

## <a name="create-empty-solutions"></a>Tworzenie pustych rozwiązań

Można również tworzyć puste rozwiązania, które nie mają projektów. Może to być preferowane w przypadkach, gdy chcesz skonstruować rozwiązanie i projekty od podstaw.

### <a name="to-create-an-empty-solution"></a>Aby utworzyć puste rozwiązanie

1. Na pasku menu wybierz pozycję **Nowy**  >    >  **plik Project.**

::: moniker range="vs-2017"

2. W okienku po **lewej** stronie (Szablony) wybierz pozycję **Inne Project typów** Visual Studio > **Rozwiązania** na rozwiniętej liście.

3. W środkowym okienku wybierz pozycję **Puste rozwiązanie.**

4. Wprowadź **wartości** **Nazwa i Lokalizacja** dla rozwiązania, a następnie wybierz przycisk **OK.**

::: moniker-end

::: moniker range=">=vs-2019"

2. Na stronie **Tworzenie nowego projektu** wpisz **rozwiązanie** w polu wyszukiwania.

3. Wybierz szablon **Puste rozwiązanie,** a następnie kliknij przycisk **Dalej.**

4. Wprowadź **wartości** **Nazwa i Lokalizacja** dla rozwiązania, a następnie wybierz pozycję **Utwórz.**

::: moniker-end

Po utworzeniu pustego rozwiązania możesz dodać do niego nowe  lub istniejące  projekty lub elementy, wybierając pozycję Dodaj nowy element lub Dodaj istniejący element w **Project** menu.

Jak wspomniano wcześniej, można również otwierać pliki kodu bez konieczności użycia projektu lub rozwiązania. Aby dowiedzieć się więcej na temat tworzenia kodu w ten sposób, zobacz [Develop code in Visual Studio without projects or solutions (Tworzenie kodu w](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md)programie Visual Studio bez projektów i rozwiązań).

::: moniker range="vs-2017"

## <a name="create-a-temporary-project"></a>Tworzenie projektu tymczasowego

(Tylko język C# i Visual Basic)

Jeśli tworzysz . Projekt oparty na sieci bez określania lokalizacji dysku jest projektem tymczasowym. Projekty tymczasowe umożliwiają eksperymentowanie z projektami .NET. W dowolnym momencie podczas pracy z projektem tymczasowym możesz go zapisać lub odrzucić.

Aby utworzyć projekt tymczasowy, najpierw przejdź do pozycji **Narzędzia** Opcje Projekty i rozwiązania Ogólne i usuń zaznaczenie pola wyboru Zapisz nowe projekty  >    >    >   **po utworzeniu.** Następnie otwórz **okno dialogowe Project** jak zwykle.

::: moniker-end

## <a name="delete-a-solution-project-or-item"></a>Usuwanie rozwiązania, projektu lub elementu

Menu kontekstowe dostępne po kliknięciu prawym przyciskiem myszy umożliwia usuwanie rozwiązań, projektów lub elementów w programie Visual Studio, ale powoduje tylko usunięcie ich z bieżącego rozwiązania lub projektu.

Aby trwale usunąć rozwiązanie lub inne składniki z systemu, użyj programu **Eksplorator plików** w programie Windows, aby usunąć folder zawierający pliki rozwiązania *sln* i *suo.* (Przed usunięciem rozwiązania możesz chcieć chcieć ponownie wrócić do kopii zapasowej projektów i plików).

> [!NOTE]
> Plik *suo jest* ukrytym plikiem, który nie jest wyświetlany w domyślnych ustawieniach Eksplorator plików. Aby wyświetlić ukryte pliki, w menu **Widok** Eksplorator plików zaznacz pole **wyboru Ukryte** elementy.

### <a name="permanently-delete-a-solution"></a>Trwałe usuwanie rozwiązania

Dostęp do aplikacji Eksplorator plików w Windows przy użyciu Eksplorator rozwiązań w Visual Studio. Oto jak to zrobić.

1. W **Eksplorator rozwiązań** menu prawym przyciskiem myszy (menu kontekstowe) rozwiązania, które chcesz usunąć, wybierz pozycję **Otwórz folder** w Eksplorator plików .

1. W Eksplorator plików przejdź o jeden poziom w górę.

1. Wybierz folder zawierający rozwiązanie, a następnie naciśnij klawisz **Delete.**

## <a name="see-also"></a>Zobacz też

- [Wprowadzenie do projektów i rozwiązań](../get-started/tutorial-projects-solutions.md)
- [Zarządzanie właściwościami projektów i rozwiązań](managing-project-and-solution-properties.md)
- [Odfiltrowane rozwiązania w Visual Studio](filtered-solutions.md)
- [Repozytoria open source firmy Microsoft na GitHub](https://github.com/Microsoft)
- [Przykłady kodu dla deweloperów](https://code.msdn.microsoft.com/)
- [Zasoby dotyczące rozwiązywania problemów Visual Studio IDE](./reference/resources-for-troubleshooting-integrated-development-environment-errors.md)
