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
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75588840"
---
# <a name="how-to-add-class-diagrams-to-projects"></a>Instrukcje: Dodawanie diagramów klas do projektów

Do projektowania, edytowania i refaktoryzacji klas oraz innych typów Dodaj Diagram klas do elementu C#, Visual Basic lub C++ projektu. Aby wizualizować różne części kodu w projekcie, należy dodać wiele diagramów klas do projektu.

Nie można tworzyć diagramów klas na podstawie projektów, które współużytkują kod w wielu aplikacjach. Aby utworzyć diagramy klas UML, zobacz [Tworzenie projektów i diagramów modelowania UML](../../modeling/what-s-new-for-design-in-visual-studio.md).

## <a name="install-the-class-designer-component"></a>Zainstaluj składnik Projektant klas

Jeśli składnik **Projektant klas** nie został zainstalowany, wykonaj następujące kroki, aby go zainstalować.

1. Otwórz **Instalator programu Visual Studio** z menu Start systemu Windows lub wybierając pozycję **Narzędzia** > **Pobierz narzędzia i funkcje** z paska menu w programie Visual Studio.

   **Instalator programu Visual Studio** zostanie otwarty.

1. Wybierz kartę **poszczególne składniki** , a następnie przewiń w dół do kategorii **Narzędzia kodu** .

1. Wybierz pozycję **Projektant klas** a następnie wybierz pozycję **Modyfikuj**.

   ![Składnik Projektant klas w Instalator programu Visual Studio](media/class-designer-component.png)

   Składnik **Projektant klas** zostanie uruchomiony.

## <a name="add-a-blank-class-diagram-to-a-project"></a>Dodawanie pustego diagramu klas do projektu

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy węzeł projektu, a następnie wybierz polecenie **Dodaj** > **nowy element**. Lub naciśnij **klawisze Ctrl**+**SHIFT**+**A**.

   Zostanie otwarte okno dialogowe **Dodaj nowy element** .

2. Rozwiń węzeł **wspólne elementy** > **Ogólne**, a następnie wybierz pozycję **Diagram klas** z listy szablon. W przypadku C++ projektów wizualnych poszukaj w kategorii **Narzędzia** , aby znaleźć szablon **diagramu klas** .

   > [!NOTE]
   > Jeśli szablon **diagramu klas** nie jest widoczny, [wykonaj kroki,](#install-the-class-designer-component) aby zainstalować składnik **Projektant klas** dla programu Visual Studio.

   Diagram klas otwiera się w Projektant klas i pojawia się jako plik z rozszerzeniem *. CD* w **Eksplorator rozwiązań**. Możesz przeciągać kształty i linie do diagramu z **przybornika**.

Aby dodać wiele diagramów klas, powtórz czynności opisane w tej procedurze.

## <a name="add-a-class-diagram-based-on-existing-types"></a>Dodawanie diagramu klasy na podstawie istniejących typów

W **Eksplorator rozwiązań**Otwórz menu kontekstowe pliku klasy (kliknij prawym przyciskiem myszy), a następnie wybierz polecenie **Wyświetl Diagram klas**.

lub

W **Widok klasy**Otwórz obszar nazw lub menu kontekstowe typu, a następnie wybierz **widok Diagram klas**.

> [!TIP]
> Jeśli **Widok klasy** nie jest otwarty, Otwórz **Widok klasy** z menu **Widok** .

## <a name="to-display-the-contents-of-a-complete-project-in-a-class-diagram"></a>Aby wyświetlić zawartość kompletnego projektu w diagramie klas

W **Eksplorator rozwiązań** lub widok klasy, kliknij prawym przyciskiem myszy projekt, a następnie wybierz polecenie **Widok**, a następnie wybierz polecenie **Wyświetl Diagram klas**.

Tworzony jest automatycznie wypełniony Diagram klas.

> [!NOTE]
> Projektant klas nie jest dostępna w projektach .NET Core.

## <a name="see-also"></a>Zobacz także

- [Instrukcje: Tworzenie typów przy użyciu Projektant klas](how-to-create-types.md)
- [Instrukcje: wyświetlanie istniejących typów](how-to-view-existing-types.md)
- [Projektowanie i wyświetlanie klas i typów](designing-and-viewing-classes-and-types.md)
