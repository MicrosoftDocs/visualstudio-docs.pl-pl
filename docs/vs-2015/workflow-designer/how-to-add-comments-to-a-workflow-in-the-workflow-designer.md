---
title: 'Instrukcje: Dodawanie komentarzy do przepływu pracy w Projektant przepływu pracy | Microsoft Docs'
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
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d775c79cc7abdf6a66b1174ae625ca468f0764fc
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663450"
---
# <a name="how-to-add-comments-to-a-workflow-in-the-workflow-designer"></a>Instrukcje: Dodawanie komentarzy do przepływu pracy w Projektant przepływu pracy
Aby ułatwić tworzenie większych, bardziej skomplikowanych przepływów pracy, [!INCLUDE[net_v45](../includes/net-v45-md.md)] umożliwia deweloperom Dodawanie adnotacji do następujących typów elementów w projektancie:

- <xref:System.Activities.Activity>

- <xref:System.Activities.Statements.State>

- <xref:System.Activities.Statements.Transition>

- Klasy pochodne <xref:System.Activities.Statements.FlowNode>

- <xref:System.Activities.Variable>

- <xref:System.Activities.Argument>

> [!IMPORTANT]
> Zawartość adnotacji jest zapisywana w postaci zwykłego tekstu do pliku XAML skojarzonego z przepływem pracy i może być potencjalnie odczytana przez inne osoby. Należy zachować ostrożność, wprowadzając informacje poufne do adnotacji.

### <a name="adding-an-annotation-to-an-activity-in-the-designer"></a>Dodawanie adnotacji do działania w projektancie

1. W Projektancie przepływu pracy kliknij prawym przyciskiem myszy element w Projektancie przepływów pracy i wybierz pozycję **Adnotacje**, **Dodaj adnotację**.

2. Dodaj tekst adnotacji do podanego miejsca.

3. W elemencie zostanie wyświetlona ikona adnotacji. Umieszczenie kursora nad ikoną adnotacji spowoduje wyświetlenie tekstu adnotacji.

     ![Działanie sekwencji z pokazywaniem adnotacji](../workflow-designer/media/annotation.png "Adnotacja")

### <a name="displaying-an-annotation-in-an-activitys-designer"></a>Wyświetlanie adnotacji w projektancie działania

1. Za pomocą projektanta działań z adnotacją wyświetlaną poza aktywnością kliknij ikonę **pinezki** w obszarze definiowania układu.

2. Adnotacja będzie wyświetlana w projektancie działania. Na poniższym zrzucie ekranu adnotacja "Uruchamianie działania w przepływie pracy" jest wyświetlana w projektancie działania.

     ![Adnotacja wyświetlana w projektancie działań](../workflow-designer/media/annotationindesigner.png "AnnotationInDesigner")

3. Aby wyświetlić adnotację poza projektantem działania, umieść kursor nad obszarem adnotacji w projektancie działania i kliknij ikonę **Odepnij**

     ![Adnotacja wyświetlana poza projektem działania](../workflow-designer/media/annotationoutsidedesigner.png "AnnotationOutsideDesigner")

### <a name="showing-or-hiding-all-annotations"></a>Wyświetlanie lub ukrywanie wszystkich adnotacji

1. Kliknij prawym przyciskiem myszy działanie, które ma adnotację. Wybierz **Adnotacje**, **Pokaż wszystkie adnotacje**.

2. Wszystkie adnotacje będą wyświetlane w projektantach działania.

3. Aby wyświetlić wszystkie adnotacje poza projektantami działania, kliknij prawym przyciskiem myszy działanie i wybierz pozycję **Adnotacje**, **Ukryj wszystkie adnotacje**.

### <a name="editing-or-deleting-an-annotation-for-an-activity"></a>Edytowanie lub usuwanie adnotacji dla działania

1. Kliknij prawym przyciskiem myszy działanie, które ma adnotację.

2. Wybierz **Adnotacje**, **Edytuj adnotację** lub **Usuń adnotację**.

3. Adnotacja zostanie otwarta do edycji lub usunięcia.

4. Aby usunąć jednocześnie wszystkie adnotacje, kliknij prawym przyciskiem myszy projektanta przepływu pracy i wybierz pozycję **adnotacja**, **Usuń wszystkie adnotacje**.

### <a name="adding-editing-and-deleting-an-annotation-for-a-variable-or-argument"></a>Dodawanie, edytowanie i usuwanie adnotacji dla zmiennej lub argumentu

1. Kliknij prawym przyciskiem myszy zmienną lub argument i wybierz polecenie Dodaj adnotację.

2. Wprowadź tekst adnotacji. Zmienna lub argument będzie wyświetlał ikonę adnotacji.

3. Kliknij prawym przyciskiem myszy zmienną lub argument, który ma adnotację. Wybierz pozycję Edytuj adnotację.

4. Adnotacja zostanie otwarta do edycji.

5. Kliknij prawym przyciskiem myszy zmienną lub argument, który ma adnotację. Wybierz pozycję Usuń adnotację.

6. Adnotacja zostanie usunięta.