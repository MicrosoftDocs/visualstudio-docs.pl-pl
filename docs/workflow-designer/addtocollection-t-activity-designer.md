---
title: Projektant przepływu pracy — Projektant działań<T> AddToCollection
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.AddToCollection`1.UI
ms.assetid: f7fc0702-164e-4370-8946-bb2f9f9384b7
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: eb00679001cc09b8fdfa68f898923ac208b32c4e
ms.sourcegitcommit: f3f668ecaf11b4c2738ebc91923c6b5e38e74670
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/16/2020
ms.locfileid: "76115331"
---
# <a name="addtocollectiont-activity-designer"></a>AddToCollection\<T >, Projektant działań

**AddToCollection\<t >** Projektant działań służy do tworzenia i konfigurowania działania <xref:System.Activities.Statements.AddToCollection%601>.

## <a name="the-addtocollectiont-activity"></a>Działanie AddToCollection\<T >

Działanie <xref:System.Activities.Statements.AddToCollection%601> dodaje element do kolekcji.

### <a name="using-the-addtocollectiont-activity-designer"></a>Korzystanie z programu AddToCollection\<T > Designer

Projektanta działań **AddToCollection\<t >** można znaleźć w kategorii **kolekcji** **przybornika**, do którego jest uzyskiwany dostęp przez kliknięcie karty **przybornika** w Projektant przepływu pracy. Alternatywnie wybierz pozycję **Przybornik** z menu **Widok** lub naciśnij **klawisze CTRL**+**Alt**+**X**.

**AddToCollection\<t >** projektanta aktywności można przeciągnąć z **przybornika** i porzucić na Projektant przepływu pracy powierzchni wszędzie tam, gdzie działania są umieszczane, na przykład w <xref:System.Activities.Statements.Sequence>. Porzucenie **AddToCollection\<t >** , Projektant działań tworzy <xref:System.Activities.Statements.AddToCollection%601> działanie z domyślną <xref:System.Activities.Activity.DisplayName%2A> AddToCollection < Int32\>. (Domyślnie *elementu TypeArgument* jest **Int32**. Elementu TypeArgument można zmienić w siatce właściwości.) Wartość <xref:System.Activities.Activity.DisplayName%2A> można edytować w nagłówku projektanta działań **AddToCollection < t\>** lub w polu **DisplayName** siatki właściwości. Inne właściwości muszą być edytowane w siatce właściwości.

### <a name="the-addtocollectiont-properties"></a>Właściwości AddToCollection\<T >

W poniższej tabeli przedstawiono właściwości <xref:System.Activities.Statements.AddToCollection%601> i opisano sposób ich używania w projektancie.

|Nazwa właściwości|Wymagane|Pomiar|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Fałsz|Przyjazna nazwa działania <xref:System.Activities.Statements.AddToCollection%601>. Wartość domyślna to AddToCollection < Int32\>. Mimo że wartość <xref:System.Activities.Activity.DisplayName%2A> nie jest ściśle wymagana, najlepszym rozwiązaniem jest użycie jednego z nich.|
|<xref:System.Activities.Statements.AddToCollection%601.Item%2A>|Prawda|Element, który ma zostać dodany do kolekcji\<T >. Ten element jest typu *T*, który jest typu *elementu TypeArgument*. Aby określić element, wpisz wyrażenie Visual Basic w siatce właściwości.|
|<xref:System.Activities.Statements.AddToCollection%601.Collection%2A>|Prawda|Kolekcja, do której należy dodać element. Ta kolekcja jest typu **ICollection < elementu typeargument\>** . Aby określić kolekcję, wpisz wyrażenie Visual Basic w siatce właściwości.|
|*TypeArgument*|Prawda|Typ T elementów zawartych w <xref:System.Collections.Generic.ICollection%601>. Domyślnie ten typ *elementu TypeArgument* jest ustawiony na **Int32**. Aby zmienić typ, Zmień wartość *elementu TypeArgument* w polu kombi w siatce właściwości.|

## <a name="see-also"></a>Zobacz także

- [Kolekcja](../workflow-designer/collection-activity-designers.md)
- [AddToCollection\<T >, Projektant działań](../workflow-designer/addtocollection-t-activity-designer.md)
- [ClearCollection\<T>](../workflow-designer/clearcollection-t-activity-designer.md)
- [ExistsInCollection\<T>](../workflow-designer/existsincollection-t-activity-designer.md)
- [RemoveFromCollection\<T>](../workflow-designer/removefromcollection-t-activity-designer.md)
