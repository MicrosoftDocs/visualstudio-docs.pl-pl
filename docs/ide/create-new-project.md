---
title: Tworzenie nowego projektu
description: Dowiedz się, jak utworzyć nowy projekt w programie Visual Studio.
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
ms.openlocfilehash: 97d585f8c484f1ef8b4cbd0514585d6f328af67c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99956883"
---
# <a name="create-a-new-project-in-visual-studio"></a>Utworzenie nowego projektu w Visual Studio

W tym artykule przedstawiono sposób szybkiego tworzenia nowego projektu w programie Visual Studio.

::: moniker range="vs-2017"

## <a name="open-the-new-project-dialog"></a>Otwórz okno dialogowe Nowy projekt

Istnieje wiele sposobów tworzenia nowego projektu w programie Visual Studio 2017. Na stronie startowej można wpisać nazwę szablonu projektu w polu **Wyszukaj szablony projektu** lub wybrać łącze **Utwórz nowy projekt** , aby otworzyć okno dialogowe **Nowy projekt** . Poza stroną początkową można również wybrać pozycję **plik**  >  **Nowy**  >  **projekt** na pasku menu lub kliknąć przycisk **Nowy projekt** na pasku narzędzi.

![Zrzut ekranu przedstawiający pasek menu w programie Visual Studio z wybranymi opcjami > nowy > projektu.](./media/vside-newproject1.png)

## <a name="select-a-template-type"></a>Wybierz typ szablonu

W oknie dialogowym **Nowy projekt** dostępne szablony projektu są wyświetlane na liście w kategorii **Szablony** . Szablony są zorganizowane według języka programowania i typu projektu, takich jak Visual C#, JavaScript i Azure Data Lake.

![Zrzut ekranu przedstawiający okno dialogowe Nowy projekt, w którym jest wyświetlana lista zainstalowanych szablonów.](./media/vside-newproject-templates-list.png)

> [!NOTE]
> Wyświetlana lista dostępnych języków i szablonów projektu zależy od używanej wersji programu Visual Studio i zainstalowanych obciążeń. Aby dowiedzieć się więcej o instalowaniu dodatkowych obciążeń, zobacz [modyfikowanie programu Visual Studio przez dodawanie lub usuwanie obciążeń i składników](../install/modify-visual-studio.md).

Aby wyświetlić listę szablonów dla języka programowania, którego chcesz użyć, kliknij trójkąt obok nazwy języka, a następnie wybierz kategorię projektu (na przykład Windows Desktop).

Na poniższej ilustracji przedstawiono szablony projektu dostępne dla projektów programu Visual C# .NET Core:

![Zrzut ekranu okna dialogowego Nowy projekt zawierający listę szablonów projektu, spośród których można dokonać wyboru.](./media/new-project-dialog-net-core.png)

## <a name="configure-your-project"></a>Konfigurowanie projektu

Wprowadź nazwę nowego projektu w polu **Nazwa** . Projekt można zapisać w domyślnej lokalizacji na komputerze lub kliknąć przycisk **Przeglądaj** , aby znaleźć inną lokalizację. Możesz również wybrać nazwę rozwiązania lub dodać nowy projekt do repozytorium git (wybierając pozycję **Dodaj do kontroli źródła**).

Kliknij przycisk **OK** , aby utworzyć rozwiązanie i projekt.

::: moniker-end

::: moniker range=">=vs-2019"

## <a name="open-the-create-a-new-project-page"></a>Otwórz stronę Tworzenie nowego projektu

Istnieje wiele sposobów tworzenia nowego projektu w programie Visual Studio 2019. Po pierwszym otwarciu programu Visual Studio pojawi się okno uruchamiania, a w tym miejscu możesz wybrać opcję **Utwórz nowy projekt**.

:::image type="content" source="media/vs-2019/start-window-create-new-project.png" alt-text="Zrzut ekranu przedstawiający okno dialogowe &quot;Tworzenie nowego projektu&quot; z okna uruchamiania w programie Visual Studio 2019":::

Jeśli środowisko programistyczne programu Visual Studio jest już otwarte, możesz utworzyć nowy projekt, wybierając pozycję **plik**  >  **Nowy**  >  **projekt** na pasku menu. Możesz również kliknąć przycisk **Nowy projekt** na pasku narzędzi lub nacisnąć **klawisze CTRL** + **SHIFT** + **N**.

:::image type="content" source="media/vs-2019/new-project-button.png" alt-text="Zrzut ekranu przedstawiający przycisk Nowy projekt w programie Visual Studio 2019.":::

## <a name="select-a-template-type"></a>Wybierz typ szablonu

Na stronie **Tworzenie nowego projektu** zostanie wyświetlona lista ostatnio wybranych szablonów wyświetlana po lewej stronie. Szablony są sortowane według *ostatnio używanych*.

Jeśli nie chcesz wybierać z ostatnio używanych szablonów, możesz filtrować wszystkie dostępne szablony projektu według **języka** (na przykład C# lub C++), **platformy** (na przykład Windows lub Azure) i **typu projektu** (na przykład Desktop lub Web). Możesz również wprowadzić tekst wyszukiwania w polu wyszukiwania, aby dodatkowo filtrować szablony, na przykład **ASP.NET**.

:::image type="content" source="media/vs-2019/create-new-project-filters.png" alt-text="Zrzut ekranu przedstawiający filtry szablonów projektu w programie Visual Studio 2019.":::

Znaczniki, które są wyświetlane pod każdym szablonem, odpowiadają trzem filtrom listy rozwijanej (język, platforma i typ projektu).

> [!TIP]
> Jeśli nie widzisz szablonu, którego szukasz, może brakować obciążenia dla programu Visual Studio. Aby zainstalować dodatkowe obciążenia, na przykład Programowanie na **platformie Azure** lub **opracowywanie aplikacji mobilnych przy użyciu platformy .NET**, kliknij link **Zainstaluj więcej narzędzi i funkcji** , aby otworzyć Instalator programu Visual Studio. W tym miejscu wybierz obciążenia, które chcesz zainstalować, a następnie wybierz polecenie **Modyfikuj**. Po wykonaniu tych dodatkowych szablonów projektu będą dostępne do wyboru.
>
> :::image type="content" source="media/vs-2019/install-more-tools-features.png" alt-text="Zrzut ekranu przedstawiający link &quot;Zainstaluj więcej narzędzi i funkcji&quot; w programie Visual Studio 2019.":::

Wybierz szablon, a następnie kliknij przycisk **dalej**.

## <a name="configure-your-project"></a>Konfigurowanie projektu

Na stronie **Konfiguruj nowy projekt** są dostępne opcje nazwy projektu (i rozwiązania), wybierz lokalizację dysku i wybierz wersję platformy (jeśli dotyczy wybranego szablonu).

:::image type="content" source="media/vs-2019/configure-new-project.png" alt-text="Zrzut ekranu przedstawiający stronę &quot;Konfigurowanie nowego projektu&quot; w programie Visual Studio 2019.":::

> [!NOTE]
> Jeśli tworzysz nowy projekt, gdy masz już otwarty projekt lub rozwiązanie w programie Visual Studio, dostępna jest opcja dodatkowa konfiguracja. Możesz utworzyć nowe rozwiązanie lub dodać nowy projekt do rozwiązania, które jest już otwarte.
>
> :::image type="content" source="media/vs-2019/configure-new-project-solution.png" alt-text="Zrzut ekranu przedstawiający okno dialogowe Utwórz nowe rozwiązanie lub Dodaj do rozwiązania w programie Visual Studio 2019.":::

Kliknij przycisk **Utwórz** , aby utworzyć nowy projekt.

::: moniker-end

## <a name="add-additional-projects-to-a-solution"></a>Dodawanie kolejnych projektów do rozwiązania

Jeśli chcesz dodać dodatkowy projekt do rozwiązania, kliknij prawym przyciskiem myszy węzeł rozwiązanie w **Eksplorator rozwiązań** a następnie wybierz pozycję **Dodaj**  >  **Nowy projekt**.

> [!TIP]
> Aby zapoznać się z przykładem projektu i rozwiązania utworzonego od podstaw, wykonaj instrukcje krok po kroku i przykładowy kod, zobacz [wprowadzenie do projektów i rozwiązań](../get-started/tutorial-projects-solutions.md).

## <a name="see-also"></a>Zobacz też

- [Wprowadzenie do projektów i rozwiązań](../get-started/tutorial-projects-solutions.md)
- [Praca z rozwiązaniami i projektami](creating-solutions-and-projects.md)
- [Zarządzanie właściwościami projektów i rozwiązań](managing-project-and-solution-properties.md)
- [Tworzenie projektów (Visual Studio dla komputerów Mac)](/visualstudio/mac/create-new-projects)