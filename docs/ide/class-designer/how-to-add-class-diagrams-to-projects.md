---
title: Dodawanie diagramów klas do projektów (Projektant klas)
description: Dowiedz się, jak projektować, edytować i refaktoryzować klasy i inne typy oraz dodać diagram klas do projektu języka C#, Visual Basic lub C++.
ms.custom: SEO-VS-2020
ms.date: 05/08/2018
ms.topic: how-to
helpviewer_keywords:
- class diagrams, creating
- Class Designer [Visual Studio], opening
ms.assetid: 0eac1b54-2711-4e4b-9654-a0c429c08c8f
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0af2717efec7cab8594f193c06e8813bd556b01f
ms.sourcegitcommit: c3713f284c4fe10b10996d5eb67077ddd8641424
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112375789"
---
# <a name="how-to-add-class-diagrams-to-projects"></a>How to: Add class diagrams to projects (Jak dodać diagramy klas do projektów)

Aby projektować, edytować i refaktoryzować klasy i inne typy, dodaj diagram klas do projektu języka C#, Visual Basic lub C++. Aby zwizualizować różne części kodu w projekcie, dodaj do projektu wiele diagramów klas.

Nie można tworzyć diagramów klas z projektów, które współdzielą kod w wielu aplikacjach. Aby utworzyć diagramy klas UML, zobacz [Create UML modeling projects and diagrams](https://devblogs.microsoft.com/devops/uml-designers-have-been-removed-layer-designer-now-supports-live-architectural-analysis/)(Tworzenie projektów i diagramów modelowania UML).

## <a name="install-the-class-designer-component"></a>Instalowanie Projektant klas programu

Jeśli nie zainstalowano  składnika Projektant klas, wykonaj następujące kroki, aby go zainstalować.

1. Otwórz **Instalator programu Visual Studio** z witryny Windows menu Start lub wybierając pozycję Narzędzia Pobierz narzędzia i funkcje na pasku menu w  >   Visual Studio.

   **Instalator programu Visual Studio** zostanie otwarta.

1. Wybierz **kartę Poszczególne składniki,** a następnie przewiń w dół do **kategorii Narzędzia** kodu.

1. Wybierz **Projektant klas** a następnie wybierz pozycję **Modyfikuj.**

   ![Projektant klas w programie Instalator programu Visual Studio](media/class-designer-component.png)

   Składnik **Projektant klas** rozpoczyna instalowanie.

## <a name="add-a-blank-class-diagram-to-a-project"></a>Dodawanie pustego diagramu klas do projektu

1. W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy węzeł projektu, a następnie wybierz **polecenie Dodaj** nowy  >  **element**. Możesz też nacisnąć **klawisze Ctrl+** +  + **Shift A.**

   Zostanie **otwarte okno dialogowe Dodawanie** nowego elementu.

2. Rozwiń **pozycję Ogólne elementy**  >  **wspólne,** a następnie wybierz pozycję Diagram **klas** z listy szablonów. Aby Visual C++ projektów, znajdź szablon **Diagram klas** **w** kategorii Narzędzie.

   > [!NOTE]
   > Jeśli nie widzisz szablonu **Diagram klas,** [wykonaj kroki](#install-the-class-designer-component) instalacji składnika **Projektant klas** dla Visual Studio.

   Diagram klas zostanie otwarty w Projektant klas i pojawi się jako plik z rozszerzeniem *.cd* w Eksplorator rozwiązań **.** Kształty i linie można przeciągać do diagramu z **przybornika**.

Aby dodać wiele diagramów klas, powtórz czynności opisane w tej procedurze.

## <a name="add-a-class-diagram-based-on-existing-types"></a>Dodawanie diagramu klas opartego na istniejących typach

W **Eksplorator rozwiązań**, otwórz menu kontekstowe pliku klasy (kliknij prawym przyciskiem myszy), a następnie wybierz **pozycję Wyświetl diagram klas.**

-lub-

W **Widok klasy** otwórz menu kontekstowe przestrzeni nazw lub typu, a następnie wybierz pozycję **Wyświetl diagram klas.**

> [!TIP]
> Jeśli **Widok klasy** nie jest otwarty, otwórz **Widok klasy** z menu **Widok.**

## <a name="to-display-the-contents-of-a-complete-project-in-a-class-diagram"></a>Aby wyświetlić zawartość kompletnego projektu w diagramie klas

W **Eksplorator rozwiązań** lub Widok klasy kliknij prawym przyciskiem myszy projekt i wybierz pozycję **Wyświetl,** a następnie wybierz **pozycję Wyświetl diagram klas.**

Zostanie utworzony automatycznie wypełniony diagram klas.

> [!NOTE]
> Projektant klas nie jest dostępna w projektach .NET Core.

## <a name="see-also"></a>Zobacz też

- [How to: Create types using the Projektant klas (Tworzyć typy przy użyciu Projektant klas](how-to-create-types.md)
- [Jak wyświetlić istniejące typy](how-to-view-existing-types.md)
- [Projektowanie i wyświetlanie klas i typów](designing-and-viewing-classes-and-types.md)
