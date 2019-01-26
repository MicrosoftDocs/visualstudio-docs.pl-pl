---
title: 'Projektant przepływu pracy — jak: Dodawanie komentarzy do przepływu pracy'
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
f1_keywords:
- System.Activities.Presentation.Annotations.Annotation.UI
- Annotation
ms.assetid: 9aa0e8d6-8129-4438-8389-d460611581a7
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: b25f662f5c4e84639926d093db0660c8754456f1
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "55030421"
---
# <a name="how-to-add-comments-to-a-workflow-in-the-workflow-designer"></a>Instrukcje: Dodawanie komentarzy do przepływu pracy w Projektancie przepływu pracy

W celu ułatwienia tworzenia większych i bardziej skomplikowanych przepływów pracy, .NET Framework 4.5 umożliwia deweloperom Dodawanie adnotacji do następujących typów elementów w Projektancie:

-   <xref:System.Activities.Activity>

-   <xref:System.Activities.Statements.State>

-   <xref:System.Activities.Statements.Transition>

-   Klasy pochodne <xref:System.Activities.Statements.FlowNode>

-   <xref:System.Activities.Variable>

-   <xref:System.Activities.Argument>

> [!IMPORTANT]
> Zawartość adnotacji są zapisywane w postaci zwykłego tekstu do pliku XAML, skojarzone z przepływem pracy i potencjalnie może zostać odczytany przez innych użytkowników. Należy zachować ostrożność podczas wprowadzania informacji poufnych w adnotacji.

## <a name="adding-an-annotation-to-an-activity-in-the-designer"></a>Dodawanie adnotacji do działania w Projektancie

1. W Projektancie przepływu pracy, kliknij prawym przyciskiem myszy element w przepływie pracy projektanta i wybierz pozycję **adnotacje**, **Dodawanie adnotacji**.

1. Dodaj tekst adnotacji w podanym miejscu.

   Element znajduje się ikona adnotacja. Kursor myszy na ikonie adnotacji Wyświetla tekst adnotacji.

## <a name="displaying-an-annotation-in-an-activitys-designer"></a>Wyświetlanie adnotacji w Projektant działań

1. Za pomocą projektanta działań, który ma wyświetlanie adnotacji poza działania, kliknij przycisk **numeru Pin** ikonę adnotacja moduł definiowania układu.

   Adnotacja jest wyświetlany w Projektancie tego działania. Na poniższym zrzucie ekranu adnotacji "Uruchamianie działanie w przepływie pracy" jest wyświetlany w Projektancie tego działania.

   ![Adnotacja objętego Projektant działań](../workflow-designer/media/annotationindesigner.png)

2. Aby wyświetlić adnotacji poza projektanta działań, umieść kursor nad obszarem adnotacji w Projektancie działań, a następnie kliknij przycisk **Wypisz** ikony

   ![Adnotacja wyświetlane poza Projektant działań](../workflow-designer/media/annotationoutsidedesigner.png)

## <a name="showing-or-hiding-all-annotations"></a>Pokazywanie lub ukrywanie wszystkich adnotacji

1. Kliknij prawym przyciskiem myszy działanie, które ma adnotację. Wybierz **adnotacje**, **Pokaż wszystkie adnotacje**.

   Wszystkie adnotacje są wyświetlane w Projektanci działań.

1. Aby wyświetlić wszystkie adnotacje poza Projektanci działań, kliknij prawym przyciskiem myszy działanie, a następnie wybierz pozycję **adnotacje**, **ukryć wszystkie adnotacje**.

## <a name="editing-or-deleting-an-annotation-for-an-activity"></a>Edytowanie lub usuwanie adnotacji dla działania

1. Kliknij prawym przyciskiem myszy na działaniu, który ma adnotację.

1. Wybierz **adnotacje**, **Edytuj adnotację** lub **usuwanie adnotacji**.

   Adnotacja jest otwarty do edycji lub usunięta.

1. Aby usunąć wszystkie adnotacje jednocześnie, kliknij prawym przyciskiem myszy przepływu pracy projektanta i wybierz pozycję **adnotacji**, **Usuń wszystkie adnotacje**.

## <a name="adding-editing-and-deleting-an-annotation-for-a-variable-or-argument"></a>Dodawanie, edytowanie i usuwanie adnotacje do zmiennej lub argumentu

1. Kliknij prawym przyciskiem myszy na zmiennej lub argumentu, a następnie wybierz Dodawanie adnotacji.

1. Wprowadź tekst adnotacji. Wyświetla ikonę adnotacja, zmiennej lub argumentu.

1. Kliknij prawym przyciskiem myszy na zmiennej lub argumentu, który ma adnotację. Wybierz pozycję Edytuj adnotacji.

   Adnotacja jest otwarty do edycji.

1. Kliknij prawym przyciskiem myszy na zmiennej lub argumentu, który ma adnotację. Wybierz pozycję Usuń adnotację.

   Adnotacja jest usuwany.