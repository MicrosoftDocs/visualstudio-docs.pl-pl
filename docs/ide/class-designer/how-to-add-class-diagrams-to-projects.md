---
title: 'Instrukcje: Dodawanie diagramów klasy do projektów (Projektant klas)'
ms.date: 05/08/2018
ms.topic: conceptual
helpviewer_keywords:
- class diagrams, creating
- Class Designer [Visual Studio], opening
ms.assetid: 0eac1b54-2711-4e4b-9654-a0c429c08c8f
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 06432ac0e882df506e4379a2f2cbffcf52c79f42
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66332762"
---
# <a name="how-to-add-class-diagrams-to-projects"></a>Instrukcje: Dodawanie diagramów klas do projektów

Do projektowania, edytować i refaktoryzować klasy a innymi typami danych, należy dodać diagram klas do projektu C#, Visual Basic lub C++. Aby wyświetlić różne części kodu w projekcie, należy dodać wiele diagramów klas do projektu.

Nie można utworzyć diagramy klas z projektów, które współdzielą kod w wielu aplikacjach. Aby utworzyć diagramy klas UML, zobacz [UML tworzenie projektów i diagramów modelowania](../../modeling/create-uml-modeling-projects-and-diagrams.md).

## <a name="install-the-class-designer-component"></a>Zainstaluj składnik projektanta klas

Jeśli nie zainstalowano **projektanta klas** składnika, wykonaj następujące kroki, aby go zainstalować.

1. Otwórz **Instalatora programu Visual Studio** z menu Windows Start lub wybierając **narzędzia** > **Pobierz narzędzia i funkcje** na pasku menu w programie Visual Studio.

   **Instalator programu Visual Studio** zostanie otwarty.

1. Wybierz **poszczególne składniki** kartę, a następnie przewiń w dół do **kodu narzędzia** kategorii.

1. Wybierz **projektanta klas** , a następnie wybierz **Modyfikuj**.

   ![Składnik projektanta klas w Instalatorze programu Visual Studio](media/class-designer-component.png)

   **Projektanta klas** składnika, który rozpoczyna się instalowania.

## <a name="add-a-blank-class-diagram-to-a-project"></a>Dodaj pusty diagram klas do projektu

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy węzeł projektu, a następnie wybierz **Dodaj** > **nowy element**. Lub naciśnij **Ctrl**+**Shift**+**A**.

   **Dodaj nowy element** zostanie otwarte okno dialogowe.

2. Rozwiń **wspólne elementy** > **ogólne**, a następnie wybierz pozycję **Diagram klas** z listy szablonów. Dla projektów Visual C++, poszukaj w **narzędzie** kategorię, aby znaleźć **Diagram klas** szablonu.

   > [!NOTE]
   > Jeśli nie widzisz **Diagram klas** szablonu, [postępuj zgodnie z instrukcjami](#install-the-class-designer-component) zainstalował **projektanta klas** składnika programu Visual Studio.

   Diagram klas zostanie otwarty w Projektancie klas i będzie widoczny jako plik, który ma *.cd* rozszerzenie w **Eksploratora rozwiązań**. Można przeciągnąć kształty i linie do diagramu z **przybornika**.

Aby dodać wiele diagramów klas, powtórz czynności opisane w tej procedurze.

## <a name="add-a-class-diagram-based-on-existing-types"></a>Dodaj diagram klas oparty na istniejących typach

W **Eksploratora rozwiązań**, otwórz menu kontekstowe pliku klasy (kliknij prawym przyciskiem myszy), a następnie wybierz **Pokaż Diagram klas**.

—lub—

W **Widok klas**, otwórz menu kontekstowe przestrzeni nazw lub typ, a następnie wybierz **Pokaż Diagram klas**.

> [!TIP]
> Jeśli **Widok klas** nie jest otwarty, otwórz **Widok klas** z **widoku** menu.

## <a name="to-display-the-contents-of-a-complete-project-in-a-class-diagram"></a>Aby wyświetlić zawartość kompletnego projektu na diagramie klasy

W **Eksploratora rozwiązań** lub w widoku klas, kliknij prawym przyciskiem myszy projekt i wybierz polecenie **widoku**, następnie wybierz **Pokaż Diagram klas**.

Diagram klas wypełniane automatycznie jest tworzony.

> [!NOTE]
> Projektant klas nie jest dostępne w projektach .NET Core.

## <a name="see-also"></a>Zobacz także

- [Instrukcje: Tworzenie typów za pomocą projektanta klas](how-to-create-types.md)
- [Instrukcje: Wyświetlanie istniejących typów](how-to-view-existing-types.md)
- [Projektowanie i wyświetlanie klas i typów](designing-and-viewing-classes-and-types.md)
