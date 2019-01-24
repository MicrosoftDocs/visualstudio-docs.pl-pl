---
title: 'Instrukcje: Dodawanie komentarzy do przepływu pracy w Projektancie przepływu pracy | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Presentation.Annotations.Annotation.UI
- Annotation
ms.assetid: 9aa0e8d6-8129-4438-8389-d460611581a7
caps.latest.revision: 7
author: steved0x
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: d60eaa4d86e3a0bc421b4d8c02eb61976337d553
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54783545"
---
# <a name="how-to-add-comments-to-a-workflow-in-the-workflow-designer"></a>Instrukcje: Dodawanie komentarzy do przepływu pracy w Projektancie przepływu pracy
Aby ułatwić tworzenie większych i bardziej skomplikowanych przepływów pracy [!INCLUDE[net_v45](../includes/net-v45-md.md)] umożliwia deweloperom Dodawanie adnotacji do następujących typów elementów w Projektancie:  
  
-   <xref:System.Activities.Activity>  
  
-   <xref:System.Activities.Statements.State>  
  
-   <xref:System.Activities.Statements.Transition>  
  
-   Klasy pochodne <xref:System.Activities.Statements.FlowNode>  
  
-   <xref:System.Activities.Variable>  
  
-   <xref:System.Activities.Argument>  
  
> [!IMPORTANT]
>  Zawartość adnotacji są zapisywane w postaci zwykłego tekstu do pliku XAML, skojarzone z przepływem pracy i potencjalnie może zostać odczytany przez innych użytkowników. Należy zachować ostrożność podczas wprowadzania informacji poufnych w adnotacji.  
  
### <a name="adding-an-annotation-to-an-activity-in-the-designer"></a>Dodawanie adnotacji do działania w Projektancie  
  
1.  W Projektancie przepływu pracy, kliknij prawym przyciskiem myszy element w przepływie pracy projektanta i wybierz pozycję **adnotacje**, **Dodawanie adnotacji**.  
  
2.  Dodaj tekst adnotacji w podanym miejscu.  
  
3.  Element będzie wyświetlana ikona adnotacja. Kursor myszy na ikonie adnotacji wyświetli tekst adnotacji.  
  
     ![Sekwencja działań, pokazujący adnotacji](../workflow-designer/media/annotation.png "adnotacji")  
  
### <a name="displaying-an-annotation-in-an-activitys-designer"></a>Wyświetlanie adnotacji w Projektant działań  
  
1.  Za pomocą projektanta działań, który ma wyświetlanie adnotacji poza działania, kliknij przycisk **numeru Pin** ikonę adnotacja moduł definiowania układu.  
  
2.  Adnotacja zostanie wyświetlony w Projektancie tego działania. Na poniższym zrzucie ekranu adnotacji "Uruchamianie działanie w przepływie pracy" jest wyświetlany w Projektancie tego działania.  
  
     ![Adnotacja wyświetlany w Projektancie działań](../workflow-designer/media/annotationindesigner.png "AnnotationInDesigner")  
  
3.  Aby wyświetlić adnotacji poza projektanta działań, umieść kursor nad obszarem adnotacji w Projektancie działań, a następnie kliknij przycisk **Wypisz** ikony  
  
     ![Adnotacja wyświetlane poza designe działania](../workflow-designer/media/annotationoutsidedesigner.png "AnnotationOutsideDesigner")  
  
### <a name="showing-or-hiding-all-annotations"></a>Pokazywanie lub ukrywanie wszystkich adnotacji  
  
1.  Kliknij prawym przyciskiem myszy działanie, które ma adnotację. Wybierz **adnotacje**, **Pokaż wszystkie adnotacje**.  
  
2.  Wszystkie adnotacje będą wyświetlane w Projektanci działań.  
  
3.  Aby wyświetlić wszystkie adnotacje poza Projektanci działań, kliknij prawym przyciskiem myszy działanie, a następnie wybierz pozycję **adnotacje**, **ukryć wszystkie adnotacje**.  
  
### <a name="editing-or-deleting-an-annotation-for-an-activity"></a>Edytowanie lub usuwanie adnotacji dla działania  
  
1.  Kliknij prawym przyciskiem myszy na działaniu, który ma adnotację.  
  
2.  Wybierz **adnotacje**, **Edytuj adnotację** lub **usuwanie adnotacji**.  
  
3.  Adnotacja zostanie otwarty do edycji lub usunięta.  
  
4.  Aby usunąć wszystkie adnotacje jednocześnie, kliknij prawym przyciskiem myszy przepływu pracy projektanta i wybierz pozycję **adnotacji**, **Usuń wszystkie adnotacje**.  
  
### <a name="adding-editing-and-deleting-an-annotation-for-a-variable-or-argument"></a>Dodawanie, edytowanie i usuwanie adnotacje do zmiennej lub argumentu  
  
1.  Kliknij prawym przyciskiem myszy na zmiennej lub argumentu, a następnie wybierz Dodawanie adnotacji.  
  
2.  Wprowadź tekst adnotacji. Zmiennej lub argumentu, zostanie wyświetlona ikona adnotacja.  
  
3.  Kliknij prawym przyciskiem myszy na zmiennej lub argumentu, który ma adnotację. Wybierz pozycję Edytuj adnotacji.  
  
4.  Adnotacja zostanie otwarty do edycji.  
  
5.  Kliknij prawym przyciskiem myszy na zmiennej lub argumentu, który ma adnotację. Wybierz pozycję Usuń adnotację.  
  
6.  Adnotacja zostanie usunięta.