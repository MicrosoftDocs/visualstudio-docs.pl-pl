---
title: 'Porady: dodawanie diagramów klasy do projektu (Projektant klas)'
ms.date: 05/08/2018
ms.topic: conceptual
helpviewer_keywords:
- class diagrams, creating
- Class Designer [Visual Studio], opening
ms.assetid: 0eac1b54-2711-4e4b-9654-a0c429c08c8f
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 87a6c1e996d820724138b6bf38c6440193a4c26b
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75588840"
---
# <a name="how-to-add-class-diagrams-to-projects"></a>Jak: Dodawanie diagramów klas do projektów

Aby zaprojektować, edytować i refaktoryzuje klas i innych typów, dodaj diagram klas do projektu C#, Visual Basic lub C++. Aby wizualizować różne części kodu w projekcie, dodaj wiele diagramów klas do projektu.

Nie można tworzyć diagramów klas z projektów, które współużytkuje kod w wielu aplikacjach. Aby utworzyć diagramy klas UML, zobacz [Tworzenie projektów i diagramów modelowania UML](../../modeling/what-s-new-for-design-in-visual-studio.md).

## <a name="install-the-class-designer-component"></a>Instalowanie składnika Projektant klasy

Jeśli składnik **Projektant klas** nie został zainstalowany, wykonaj następujące kroki, aby go zainstalować.

1. Otwórz **Instalatora programu Visual Studio** z menu Start systemu Windows lub wybierając polecenie **Narzędzia** > **Pobierz narzędzia i funkcje** z paska menu w programie Visual Studio.

   Zostanie otwarty **Instalator programu Visual Studio.**

1. Wybierz kartę **Poszczególne składniki,** a następnie przewiń w dół do kategorii **Narzędzia kodowania.**

1. Wybierz **projektanta klas,** a następnie wybierz pozycję **Modyfikuj**.

   ![Składnik Projektant klasy w Instalatorze programu Visual Studio](media/class-designer-component.png)

   Rozpocznie się instalacja składnika **Projektant klasy.**

## <a name="add-a-blank-class-diagram-to-a-project"></a>Dodawanie pustego diagramu klasy do projektu

1. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy węzeł projektu, a następnie wybierz polecenie **Dodaj** > **nowy element**. Możesz też **nacisnąć klawisze Ctrl**+**Shift**+**A**.

   Zostanie otwarte okno dialogowe **Dodaj nowy element.**

2. Rozwiń rozwiń **ogólne elementy** > **wspólne**, a następnie wybierz diagram **klas** z listy szablonów. W przypadku projektów programu Visual C++ poszukaj w kategorii **Narzędzia,** aby znaleźć szablon **diagramu klas.**

   > [!NOTE]
   > Jeśli nie widzisz szablonu **diagramu klas,** [wykonaj kroki,](#install-the-class-designer-component) aby zainstalować składnik **Projektanta klas** dla programu Visual Studio.

   Diagram klasy zostanie otwarty w Projektancie klas i pojawi się jako plik z rozszerzeniem *.cd* w **Eksploratorze rozwiązań**. Kształty i linie można przeciągać do diagramu z **pola narzędzi .**

Aby dodać wiele diagramów klas, powtórz czynności opisane w tej procedurze.

## <a name="add-a-class-diagram-based-on-existing-types"></a>Dodawanie diagramu klas na podstawie istniejących typów

W **Eksploratorze rozwiązań**otwórz menu kontekstowe pliku klasy (kliknij prawym przyciskiem myszy), a następnie wybierz polecenie **Wyświetl diagram klas**.

— lub —

W **widoku klasy**otwórz obszar nazw lub polecenie kontekstowe, a następnie wybierz polecenie Wyświetl diagram **klas**.

> [!TIP]
> Jeśli **widok klasy** nie jest otwarty, otwórz widok **klasy** z menu **Widok.**

## <a name="to-display-the-contents-of-a-complete-project-in-a-class-diagram"></a>Aby wyświetlić zawartość kompletnego projektu na diagramie klas

W **Eksploratorze rozwiązań** lub widoku klas kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Widok**, a następnie wybierz polecenie Wyświetl **diagram klas**.

Tworzony jest diagram klasy wypełnianej automatycznie.

> [!NOTE]
> Projektant klas nie jest dostępny w projektach .NET Core.

## <a name="see-also"></a>Zobacz też

- [Jak: Tworzenie typów przy użyciu Projektanta klas](how-to-create-types.md)
- [Jak: Wyświetlanie istniejących typów](how-to-view-existing-types.md)
- [Projektowanie i wyświetlanie klas i typów](designing-and-viewing-classes-and-types.md)
