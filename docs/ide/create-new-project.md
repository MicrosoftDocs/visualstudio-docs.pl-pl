---
title: Tworzenie nowego projektu
ms.date: 03/19/2019
ms.topic: conceptual
f1_keywords:
- vs.newproject
helpviewer_keywords:
- projects [Visual Studio], creating
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 77a6a33a1dde4d779a56c9ee559ecfd3b20dfbfb
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75585473"
---
# <a name="create-a-new-project-in-visual-studio"></a>Utworzenie nowego projektu w Visual Studio

::: moniker range="vs-2017"

## <a name="open-the-new-project-dialog"></a>Otwieranie okna dialogowego Nowy projekt

Istnieje wiele sposobów tworzenia nowego projektu w programie Visual Studio 2017. Na stronie Start można wpisać nazwę szablonu projektu w polu **Wyszukaj szablony projektów** lub wybrać łącze **Utwórz nowy projekt,** aby otworzyć okno dialogowe **Nowy projekt.** Oprócz strony Start można również wybrać **pozycję Plik** > **nowego** > **projektu** na pasku menu lub kliknąć przycisk Nowy **projekt** na pasku narzędzi.

![Strona początkowa i > pliku Nowy projekt >](./media/vside-newproject1.png)

## <a name="select-a-template-type"></a>Wybieranie typu szablonu

W oknie dialogowym **Nowy projekt** dostępne szablony projektów są wyświetlane na liście w kategorii **Szablony.** Szablony są zorganizowane według języka programowania i typu projektu, takich jak Visual C#, JavaScript i Azure Data Lake.

![Okno dialogowe Nowy projekt](./media/vside-newproject-templates-list.png)

> [!NOTE]
> Lista dostępnych języków i szablonów projektów, który pojawia się zależy od wersji programu Visual Studio, które są uruchomione i obciążeń, które są zainstalowane. Aby dowiedzieć się, jak zainstalować dodatkowe obciążenia, zobacz [Modyfikowanie programu Visual Studio przez dodawanie lub usuwanie obciążeń i składników](../install/modify-visual-studio.md).

Pokaż listę szablonów dla języka programowania, którego chcesz użyć, klikając trójkąt obok nazwy języka, a następnie wybierając kategorię projektu (na przykład Pulpit systemu Windows).

Na poniższej ilustracji przedstawiono szablony projektów dostępne dla projektów programu Visual C# .NET Core:

![Szablony projektów](./media/new-project-dialog-net-core.png)

## <a name="configure-your-project"></a>Konfigurowanie projektu

Wprowadź nazwę nowego projektu w polu **Nazwa.** Projekt można zapisać w lokalizacji domyślnej na komputerze lub kliknąć przycisk **Przeglądaj,** aby znaleźć inną lokalizację. Można również wybrać nazwę rozwiązania lub dodać nowy projekt do repozytorium Git (wybierając **pozycję Dodaj do kontroli źródła).**

Kliknij **przycisk OK,** aby utworzyć rozwiązanie i projekt.

::: moniker-end

::: moniker range=">=vs-2019"

## <a name="open-the-create-a-new-project-page"></a>Otwieranie strony Tworzenie nowego projektu

Istnieje wiele sposobów tworzenia nowego projektu w programie Visual Studio 2019. Po pierwszym otwarciu programu Visual Studio pojawi się okno startowe, a stamtąd można wybrać pozycję **Utwórz nowy projekt**.

![Tworzenie nowego projektu z okna początkowego w programie VS 2019](media/vs-2019/start-window-create-new-project.png)

Jeśli środowisko programistyczne Visual Studio jest już otwarte, można utworzyć nowy projekt, wybierając **pozycję Plik** > **nowego** > **projektu** na pasku menu lub klikając przycisk Nowy **projekt** na pasku narzędzi.

![Przycisk Nowy projekt w programie Visual Studio 2019](media/vs-2019/new-project-button.png)

## <a name="select-a-template-type"></a>Wybieranie typu szablonu

Po lewej stronie znajduje się lista ostatnio wybranych szablonów na stronie **Tworzenie nowego projektu.** Szablony są sortowane według *ostatnio używanego*pliku .

Jeśli nie wybierasz z ostatnio używanych szablonów, możesz filtrować wszystkie dostępne szablony projektów według **języka** (na przykład C# lub C++), **platformy** (na przykład systemu Windows lub Platformy Azure) i **typu projektu** (na przykład pulpitu lub sieci Web). Można również wprowadzić tekst wyszukiwania w polu wyszukiwania, aby dodatkowo filtrować szablony, na przykład **asp.net**.

![Filtry szablonów projektu w programie Visual Studio 2019](media/vs-2019/create-new-project-filters.png)

Znaczniki wyświetlane pod każdym szablonem odpowiadają trzem filtrom rozwijanym (język, platforma i typ projektu).

> [!TIP]
> Jeśli nie widzisz szablonu, którego szukasz, może brakować obciążenia dla programu Visual Studio. Aby zainstalować dodatkowe obciążenia, na przykład **program Azure Development** lub Mobile Development za pomocą platformy **.NET,** kliknij łącze **Zainstaluj więcej narzędzi i funkcji,** aby otworzyć Instalatora programu Visual Studio. W tym miejscu wybierz obciążenia, które chcesz zainstalować, a następnie wybierz pozycję **Modyfikuj**. Następnie dostępne będą dodatkowe szablony projektów.
>
> ![Instalowanie łącza więcej narzędzi i funkcji w programie VS 2019](media/vs-2019/install-more-tools-features.png)

Wybierz szablon, a następnie kliknij przycisk **Dalej**.

## <a name="configure-your-project"></a>Konfigurowanie projektu

Strona **Konfiguruj nowy projekt** ma opcje nadaniem nazwy projektu (i rozwiązania), wybrania lokalizacji dysku i wybrania wersji programu Framework (jeśli dotyczy wybranego szablonu).

![Konfigurowanie nowej strony projektu w programie VS 2019](media/vs-2019/configure-new-project.png)

> [!NOTE]
> Jeśli tworzysz nowy projekt, gdy masz już otwarty projekt lub rozwiązanie w programie Visual Studio, dostępna jest dodatkowa opcja konfiguracji. Można utworzyć nowe rozwiązanie lub dodać nowy projekt do rozwiązania, które jest już otwarte.
>
> ![Tworzenie nowego rozwiązania lub dodawanie do istniejącego rozwiązania w programie VS 2019](media/vs-2019/configure-new-project-solution.png)

Kliknij **przycisk Utwórz,** aby utworzyć nowy projekt.

::: moniker-end

## <a name="add-additional-projects-to-a-solution"></a>Dodawanie dodatkowych projektów do rozwiązania

Jeśli chcesz dodać dodatkowy projekt do rozwiązania, kliknij prawym przyciskiem myszy węzeł rozwiązania w **Eksploratorze rozwiązań** i wybierz pozycję **Dodaj** > **nowy projekt**.

## <a name="see-also"></a>Zobacz też

- [Tworzenie rozwiązań i projektów](creating-solutions-and-projects.md)
