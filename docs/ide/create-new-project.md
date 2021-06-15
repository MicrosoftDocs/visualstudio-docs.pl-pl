---
title: Tworzenie nowego projektu
description: Dowiedz się, jak utworzyć nowy projekt w Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 12/23/2020
ms.topic: how-to
f1_keywords:
- vs.newproject
helpviewer_keywords:
- projects [Visual Studio], creating
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 05cfb7cf053a3275b49b76b46bec8054fb105078
ms.sourcegitcommit: 529e1716924c3e1ac8a750550b996ad3c79f353b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/14/2021
ms.locfileid: "112066959"
---
# <a name="create-a-new-project-in-visual-studio"></a>Utworzenie nowego projektu w Visual Studio

W tym artykule pokażemy, jak szybko utworzyć nowy projekt na podstawie Visual Studio szablonu.

::: moniker range="vs-2017"

## <a name="open-the-new-project-dialog"></a>Otwieranie okna dialogowego Nowy projekt

Istnieje wiele sposobów tworzenia nowego projektu w programie Visual Studio 2017. Na stronie Start możesz wpisać nazwę szablonu projektu w  polu Wyszukaj szablony projektów lub wybrać **link** Utwórz nowy projekt, aby otworzyć okno **dialogowe Nowy** projekt. Oprócz strony Start możesz również wybrać pozycję File New Project (Plik nowy projekt) na pasku menu lub kliknąć przycisk  >    >   **New Project** (Nowy projekt) na pasku narzędzi.

![Zrzut ekranu przedstawiający pasek menu w Visual Studio z wybranymi > Nowy > Projekt.](./media/vside-newproject1.png)

## <a name="select-a-template-type"></a>Wybieranie typu szablonu

W **oknie dialogowym Nowy** projekt dostępne szablony projektów są wyświetlane na liście w **kategorii** Szablony. Szablony są zorganizowane według języka programowania i typu projektu, takiego jak Visual C#, JavaScript i Azure Data Lake.

![Zrzut ekranu przedstawiający okno dialogowe Nowy projekt z listą zainstalowanych szablonów.](./media/vside-newproject-templates-list.png)

> [!NOTE]
> Wyświetlana lista dostępnych języków i szablonów projektów zależy od wersji Visual Studio i zainstalowanych obciążeń. Aby dowiedzieć się więcej na temat sposobu instalowania dodatkowych obciążeń, zobacz [Modyfikowanie Visual Studio przez dodawanie lub usuwanie obciążeń i składników](../install/modify-visual-studio.md).

Wyświetl listę szablonów dla języka programowania, którego chcesz użyć, klikając trójkąt obok nazwy języka, a następnie wybierając kategorię projektu (na przykład Windows Desktop).

Na poniższej ilustracji przedstawiono szablony projektów dostępne dla projektów .NET Core w języku Visual C#:

![Zrzut ekranu przedstawiający okno dialogowe Nowy projekt z listą szablonów projektów do wyboru.](./media/new-project-dialog-net-core.png)

## <a name="configure-your-project"></a>Konfigurowanie projektu

Wprowadź nazwę nowego projektu w **polu** Nazwa. Możesz zapisać projekt w domyślnej lokalizacji na komputerze lub kliknąć przycisk **Przeglądaj,** aby znaleźć inną lokalizację. Możesz również wybrać nazwę rozwiązania lub dodać nowy projekt do repozytorium Git (wybierając pozycję **Dodaj do kontroli źródła).**

Kliknij **przycisk OK,** aby utworzyć rozwiązanie i projekt.

::: moniker-end

::: moniker range=">=vs-2019"

## <a name="open-the-create-a-new-project-page"></a>Otwórz stronę Create a new project (Tworzenie nowego projektu)

Istnieje wiele sposobów tworzenia nowego projektu w programie Visual Studio 2019. Po pierwszym otwarciu Visual Studio zostanie wyświetlone okno uruchamiania, a następnie wybierz pozycję **Utwórz nowy projekt.**

:::image type="content" source="media/vs-2019/start-window-create-new-project.png" alt-text="Zrzut ekranu przedstawiający okno dialogowe &quot;Tworzenie nowego projektu&quot; w oknie uruchamiania w Visual Studio 2019 r.":::

Jeśli środowisko Visual Studio projektowe jest już otwarte, możesz utworzyć nowy projekt, wybierając pozycję **File** New Project (Nowy projekt  >    >   pliku) na pasku menu. Możesz również kliknąć przycisk **Nowy projekt na** pasku narzędzi lub nacisnąć klawisz **Ctrl** + **Shift** + **N**.

:::image type="content" source="media/vs-2019/new-project-button.png" alt-text="Zrzut ekranu przedstawiający przycisk Nowy projekt w Visual Studio 2019 r.":::

## <a name="select-a-template-type"></a>Wybieranie typu szablonu

Na **stronie Tworzenie nowego projektu** po lewej stronie zostanie wyświetlona lista ostatnio wybranych szablonów. Szablony są sortowane według *ostatnio używanych .*

Jeśli nie wybierasz z ostatnio używanych szablonów, możesz filtrować wszystkie dostępne szablony projektów według języka **(na** przykład C# lub C++), **platformy** (na przykład Windows lub Azure) i typu projektu **(na** przykład Desktop lub Web). Możesz również wprowadzić tekst wyszukiwania w polu wyszukiwania, aby dalej filtrować szablony, na przykład **asp.net**.

:::image type="content" source="media/vs-2019/create-new-project-filters.png" alt-text="Zrzut ekranu przedstawiający filtry szablonów projektu w Visual Studio 2019 r.":::

Tagi wyświetlane pod każdym szablonem odpowiadają trzem filtrom listy rozwijanej (Język, Platforma i Typ projektu).

> [!TIP]
> Jeśli nie widzisz szablonu, którego szukasz, być może brakuje obciążenia dla Visual Studio. Aby zainstalować dodatkowe obciążenia, na przykład Tworzenie aplikacji na platformie **Azure** lub Tworzenie aplikacji mobilnych za pomocą platformy **.NET,** kliknij **link** Zainstaluj więcej narzędzi i funkcji, aby otworzyć Instalator programu Visual Studio. W tym miejscu wybierz obciążenia, które chcesz zainstalować, a następnie wybierz pozycję **Modyfikuj.** Następnie będą dostępne dodatkowe szablony projektów do wyboru.
>
> :::image type="content" source="media/vs-2019/install-more-tools-features.png" alt-text="Zrzut ekranu przedstawiający link &quot;Zainstaluj więcej narzędzi i funkcji&quot; Visual Studio 2019 r.":::

Wybierz szablon, a następnie kliknij przycisk **Dalej.**

## <a name="configure-your-project"></a>Konfigurowanie projektu

Na **stronie Konfigurowanie nowego projektu** dostępne są opcje na nazwania projektu (i rozwiązania), wybierania lokalizacji dysku i wybierania wersji struktury (jeśli ma zastosowanie do wybranego szablonu).

:::image type="content" source="media/vs-2019/configure-new-project.png" alt-text="Zrzut ekranu przedstawiający stronę &quot;Konfigurowanie nowego projektu&quot; w Visual Studio 2019 r.":::

> [!NOTE]
> Jeśli tworzysz nowy projekt, gdy masz już otwarty projekt lub rozwiązanie Visual Studio, dostępna jest dodatkowa opcja konfiguracji. Możesz utworzyć nowe rozwiązanie lub dodać nowy projekt do rozwiązania, które jest już otwarte.
>
> :::image type="content" source="media/vs-2019/configure-new-project-solution.png" alt-text="Zrzut ekranu przedstawiający okno dialogowe &quot;Tworzenie nowego rozwiązania&quot; lub &quot;Dodawanie do rozwiązania&quot; Visual Studio 2019 r.":::

Kliknij **pozycję Utwórz,** aby utworzyć nowy projekt.

::: moniker-end

## <a name="add-additional-projects-to-a-solution"></a>Dodawanie dodatkowych projektów do rozwiązania

Jeśli chcesz dodać dodatkowy projekt do rozwiązania, kliknij prawym  przyciskiem myszy węzeł rozwiązania w Eksplorator rozwiązań a następnie wybierz **pozycję Dodaj**  >  **nowy projekt.**

> [!TIP]
> Aby uzyskać przykładowy projekt i rozwiązanie utworzone od podstaw, wraz z instrukcjami krok po kroku i przykładowym kodem, zobacz [Introduction to projects and solutions (Wprowadzenie do projektów i rozwiązań).](../get-started/tutorial-projects-solutions.md)

## <a name="see-also"></a>Zobacz też

- [Wprowadzenie do projektów i rozwiązań](../get-started/tutorial-projects-solutions.md)
- [Praca z rozwiązaniami i projektami](creating-solutions-and-projects.md)
- [Zarządzanie właściwościami projektów i rozwiązań](managing-project-and-solution-properties.md)
- [Tworzenie projektów (Visual Studio dla komputerów Mac)](/visualstudio/mac/create-new-projects)
