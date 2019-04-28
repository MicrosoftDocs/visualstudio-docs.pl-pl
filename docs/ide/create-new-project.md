---
title: Tworzenie nowego projektu
ms.date: 03/19/2019
ms.topic: conceptual
f1_keywords:
- vs.newproject
helpviewer_keywords:
- projects [Visual Studio], creating
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9f5d48ee97e1e0d92237fe5836c8bd9c1888c3a4
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62818922"
---
# <a name="create-a-new-project-in-visual-studio"></a>Utwórz nowy projekt w programie Visual Studio

::: moniker range="vs-2017"

## <a name="open-the-new-project-dialog"></a>Otwórz okno dialogowe Nowy projekt

Istnieje wiele sposobów, aby utworzyć nowy projekt w programie Visual Studio 2017. Na stronie początkowej można wpisać nazwę szablonu projektu w **Wyszukaj szablony projektów** pole, lub wybierz **Tworzenie nowego projektu** link umożliwiający otworzenie **nowy projekt** okna dialogowego pole. Oprócz strony początkowej można również **pliku** > **New** > **projektu** na pasku menu lub kliknij **nowy projekt**  przycisk na pasku narzędzi.

![Strona startowa i plik > Nowy > Projekt](./media/vside-newproject1.png)

## <a name="select-a-template-type"></a>Wybierz typ szablonu

W **nowy projekt** okno dialogowe dostępnych szablonów projektu są wyświetlane na liście w obszarze **szablony** kategorii. Szablony są uporządkowane według programowania języka i projektu typu, na przykład Visual C#, JavaScript i Azure Data Lake.

![Okno dialogowe Nowy projekt](./media/vside-newproject-templates-list.png)

> [!NOTE]
> Wyświetlonej listy dostępnych języków i szablonów projektu zależy od wersji programu Visual Studio, które są uruchomione i obciążeń, które są zainstalowane. Aby dowiedzieć się więcej o sposobie instalowania dodatkowych obciążeń, zobacz [modyfikowanie programu Visual Studio, dodając lub usuwając obciążenia i składniki](../install/modify-visual-studio.md).

Pokaż listę szablonów dla języka programowania, którego chcesz użyć, klikając przycisk trójkąta obok nazwy języka, a następnie wybierając kategorię projektu (np. Windows dla komputerów stacjonarnych).

Na poniższej ilustracji przedstawiono dostępne szablony projektów dla wizualizacji C# projektów .NET Core:

![Szablony projektów](./media/new-project-dialog-net-core.png)

## <a name="configure-your-project"></a>Konfigurowanie projektu

Wprowadź nazwę dla nowego projektu w **nazwa** pole. Projekt można zapisać w lokalizacji domyślnej na komputerze lub kliknij **Przeglądaj** przycisk, aby znaleźć w innej lokalizacji. Można również wybrać Nazwa rozwiązania lub dodać nowy projekt do repozytorium Git (wybierając **Dodaj do kontroli źródła**).

Kliknij przycisk **OK** do tworzenia rozwiązań i projektów.

::: moniker-end

::: moniker range=">=vs-2019"

## <a name="open-the-create-a-new-project-page"></a>Tworzenie nowej stronie projektu otwórz

Istnieje wiele sposobów, aby utworzyć nowy projekt w programie Visual Studio 2019 r. Po pierwszym otwarciu programu Visual Studio, zostanie wyświetlone okno uruchamiania i z tego miejsca możesz wybrać **Utwórz nowy projekt**.

![Utwórz nowy projekt z okna start 2019 programu VS](media/vs-2019/start-window-create-new-project.png)

Jeśli w środowisku programowania Visual Studio jest już otwarty, można utworzyć nowy projekt, wybierając **pliku** > **New** > **projektu** na menu, pasek lub przez kliknięcie przycisku **nowy projekt** przycisk na pasku narzędzi.

![Przycisk Nowy projekt w programie Visual Studio 2019 r.](media/vs-2019/new-project-button.png)

## <a name="select-a-template-type"></a>Wybierz typ szablonu

Na **Utwórz nowy projekt** stronie zostanie wyświetlona lista ostatnio wybranych szablonów po lewej stronie. Szablony są sortowane według *ostatnio używanych*.

Jeśli nie jest to zaznaczenie z ostatnio używanych szablonów, można filtrować wszystkich dostępnych szablonów projektów przez **języka** (na przykład C# lub C++), **platformy** (na przykład Windows lub platformy Azure), i **Typ projektu** (na przykład pulpitu lub w sieci Web). Możesz też wprowadzić wyszukiwany tekst w polu wyszukiwania, aby dokładniej przefiltrować szablonów, na przykład **asp.net**.

![Filtry szablonu projektu w programie Visual Studio 2019 r.](media/vs-2019/create-new-project-filters.png)

Tagi, które są wyświetlane w każdym szablonie odpowiadają trzy filtry listy rozwijanej (typ języka, platformy i projektu).

> [!TIP]
> Jeśli nie widzisz szablonu, którego szukasz, może brakować obciążenia dla programu Visual Studio. Do zainstalowania dodatkowych obciążeń, na przykład **programowanie na platformie Azure** lub **programowanie aplikacji mobilnych przy użyciu platformy .NET**, kliknij przycisk **zainstalować więcej narzędzi i funkcji** link umożliwiający otworzenie Visual Instalator programu Studio. Z tego miejsca wybierz obciążeń, o których chcesz zainstalować, a następnie wybierz **Modyfikuj**. Po tym szablony projektu dodatkowe będą dostępne do wyboru.
>
> ![Zainstaluj link więcej narzędzi i funkcji w 2019 programu VS](media/vs-2019/install-more-tools-features.png)

Wybierz szablon, a następnie kliknij przycisk **dalej**.

## <a name="configure-your-project"></a>Konfigurowanie projektu

**Konfigurowania nowego projektu** strona zawiera opcje, aby nazwa projektu (i rozwiązania), wybierz lokalizację dysku, a następnie wybierz wersję Framework (jeśli ma zastosowanie do szablonu wybrano).

![Konfigurowanie nowej stronie projektu w VS 2019 r](media/vs-2019/configure-new-project.png)

> [!NOTE]
> Jeśli tworzysz nowy projekt, gdy już masz projekt lub rozwiązanie, które są otwarte w programie Visual Studio, powoduje udostępnienie opcji dodatkowej konfiguracji. Można utworzyć nowe rozwiązanie lub dodać nowy projekt do rozwiązania, które jest już otwarty.
>
> ![Utwórz nowe rozwiązanie lub dodać do istniejącego rozwiązania w 2019 programu VS](media/vs-2019/configure-new-project-solution.png)

Kliknij przycisk **Utwórz** Aby utworzyć nowy projekt.

::: moniker-end

## <a name="add-additional-projects-to-a-solution"></a>Dodaj dodatkowe projekty do rozwiązania

Jeśli chcesz dodać dodatkowe projekt do rozwiązania, kliknij prawym przyciskiem myszy węzeł rozwiązania w **Eksploratora rozwiązań** i wybierz polecenie **Dodaj** > **nowy projekt**.

## <a name="see-also"></a>Zobacz także

- [Tworzenie rozwiązań i projektów](creating-solutions-and-projects.md)
