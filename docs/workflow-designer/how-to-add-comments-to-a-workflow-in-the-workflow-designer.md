---
title: 'Projektant przepływu pracy — How to: Dodawanie komentarzy do przepływu pracy'
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- System.Activities.Presentation.Annotations.Annotation.UI
- Annotation
ms.assetid: 9aa0e8d6-8129-4438-8389-d460611581a7
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
author: TerryGLee
ms.openlocfilehash: 77fb43671a45d5d53d2fe23fa3e4e7a9a98c4373
ms.sourcegitcommit: ca777040ca372014b9af5e188d9b60bf56e3e36f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85815503"
---
# <a name="how-to-add-comments-to-a-workflow-in-the-workflow-designer"></a>Instrukcje: Dodawanie komentarzy do przepływu pracy w Projektancie przepływu pracy

Aby ułatwić tworzenie większych, bardziej skomplikowanych przepływów pracy, .NET Framework 4,5 umożliwia deweloperowi Dodawanie adnotacji do następujących typów elementów w projektancie:

- <xref:System.Activities.Activity>

- <xref:System.Activities.Statements.State>

- <xref:System.Activities.Statements.Transition>

- Klasy pochodne<xref:System.Activities.Statements.FlowNode>

- <xref:System.Activities.Variable>

- <xref:System.Activities.Argument>

> [!IMPORTANT]
> Zawartość adnotacji jest zapisywana w postaci zwykłego tekstu do pliku XAML skojarzonego z przepływem pracy i może być potencjalnie odczytana przez inne osoby. Należy zachować ostrożność, wprowadzając informacje poufne do adnotacji.

## <a name="adding-an-annotation-to-an-activity-in-the-designer"></a>Dodawanie adnotacji do działania w projektancie

1. W Projektancie przepływu pracy kliknij prawym przyciskiem myszy element w Projektancie przepływów pracy i wybierz pozycję **Adnotacje**, **Dodaj adnotację**.

1. Dodaj tekst adnotacji do podanego miejsca.

   Element pokazuje ikonę adnotacji. Umieszczenie kursora myszy na ikonie adnotacji powoduje wyświetlenie tekstu adnotacji.

## <a name="displaying-an-annotation-in-an-activitys-designer"></a>Wyświetlanie adnotacji w projektancie działania

1. Za pomocą projektanta działań z adnotacją wyświetlaną poza aktywnością kliknij ikonę **pinezki** w obszarze definiowania układu.

   Adnotacja jest wyświetlana w projektancie działania. Na poniższym zrzucie ekranu adnotacja "Uruchamianie działania w przepływie pracy" jest wyświetlana w projektancie działania.

   ![Adnotacja wyświetlana w projektancie działań](../workflow-designer/media/annotationindesigner.png)

2. Aby wyświetlić adnotację poza projektantem działania, umieść kursor nad obszarem adnotacji w projektancie działania i kliknij ikonę **Odepnij**

   ![Adnotacja wyświetlana poza projektantem działania](../workflow-designer/media/annotationoutsidedesigner.png)

## <a name="showing-or-hiding-all-annotations"></a>Wyświetlanie lub ukrywanie wszystkich adnotacji

1. Kliknij prawym przyciskiem myszy działanie, które ma adnotację. Wybierz **Adnotacje**, **Pokaż wszystkie adnotacje**.

   Wszystkie adnotacje są wyświetlane w projektantach działania.

1. Aby wyświetlić wszystkie adnotacje poza projektantami działania, kliknij prawym przyciskiem myszy działanie i wybierz pozycję **Adnotacje**, **Ukryj wszystkie adnotacje**.

## <a name="editing-or-deleting-an-annotation-for-an-activity"></a>Edytowanie lub usuwanie adnotacji dla działania

1. Kliknij prawym przyciskiem myszy działanie, które ma adnotację.

1. Wybierz **Adnotacje**, **Edytuj adnotację** lub **Usuń adnotację**.

   Adnotacja jest otwierana do edycji lub usuwania.

1. Aby usunąć jednocześnie wszystkie adnotacje, kliknij prawym przyciskiem myszy projektanta przepływu pracy i wybierz pozycję **adnotacja**, **Usuń wszystkie adnotacje**.

## <a name="adding-editing-and-deleting-an-annotation-for-a-variable-or-argument"></a>Dodawanie, edytowanie i usuwanie adnotacji dla zmiennej lub argumentu

1. Kliknij prawym przyciskiem myszy zmienną lub argument i wybierz polecenie Dodaj adnotację.

1. Wprowadź tekst adnotacji. Zmienna lub argument wyświetla ikonę adnotacji.

1. Kliknij prawym przyciskiem myszy zmienną lub argument, który ma adnotację. Wybierz pozycję Edytuj adnotację.

   Adnotacja jest otwierana do edycji.

1. Kliknij prawym przyciskiem myszy zmienną lub argument, który ma adnotację. Wybierz pozycję Usuń adnotację.

   Adnotacja zostanie usunięta.
