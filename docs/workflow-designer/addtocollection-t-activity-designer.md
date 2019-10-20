---
title: Projektant przepływu pracy — Projektant działań <T> AddToCollection
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.AddToCollection`1.UI
ms.assetid: f7fc0702-164e-4370-8946-bb2f9f9384b7
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e8aa11f93b702f48d93710b9993769289ebc8ffa
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72650744"
---
# <a name="addtocollectiont-activity-designer"></a>AddToCollection \<T > — Projektant działań

**AddToCollection \<T >** Projektant działań służy do tworzenia i konfigurowania działania <xref:System.Activities.Statements.AddToCollection%601>.

## <a name="the-addtocollectiont-activity"></a>Działanie AddToCollection \<T >

Działanie <xref:System.Activities.Statements.AddToCollection%601> dodaje element do kolekcji.

### <a name="using-the-addtocollectiont-activity-designer"></a>Korzystanie z AddToCollection \<T > Projektant działań

Projektanta działań programu **AddToCollection \<T >** można znaleźć w kategorii **kolekcji** **przybornika**, do którego uzyskuje się dostęp przez kliknięcie karty **przybornika** w Projektant przepływu pracy. Alternatywnie wybierz pozycję **Przybornik** z menu **Widok** lub naciśnij **klawisze CTRL** +**Alt** +**X**.

**AddToCollection \<T >** projektanta aktywności można przeciągnąć z **przybornika** i porzucić na Projektant przepływu pracyą powierzchnię wszędzie tam, gdzie działania są umieszczane, na przykład w <xref:System.Activities.Statements.Sequence>. Porzucenie **AddToCollection \<T >** projektanta działań tworzy działanie <xref:System.Activities.Statements.AddToCollection%601> z domyślną <xref:System.Activities.Activity.DisplayName%2A> AddToCollection < Int32 \>. (Domyślnie *elementu TypeArgument* jest **Int32**. Elementu TypeArgument można zmienić w siatce właściwości.) Wartość <xref:System.Activities.Activity.DisplayName%2A> można edytować w nagłówku projektanta działań **AddToCollection < t \>** lub w polu **DisplayName** siatki właściwości. Inne właściwości muszą być edytowane w siatce właściwości.

### <a name="the-addtocollectiont-properties"></a>Właściwości AddToCollection \<T >

W poniższej tabeli przedstawiono właściwości <xref:System.Activities.Statements.AddToCollection%601> i opisano sposób ich używania w projektancie.

|Nazwa właściwości|Wymagane|Użycie|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Przyjazna nazwa działania <xref:System.Activities.Statements.AddToCollection%601>. Wartość domyślna to AddToCollection < Int32 \>. Mimo że wartość <xref:System.Activities.Activity.DisplayName%2A> nie jest ściśle wymagana, najlepszym rozwiązaniem jest użycie jednego z nich.|
|<xref:System.Activities.Statements.AddToCollection%601.Item%2A>|Oznacza|Element, który ma zostać dodany do kolekcji \<T >. Ten element jest typu *T*, który jest typu *elementu TypeArgument*. Aby określić element, wpisz wyrażenie Visual Basic w siatce właściwości.|
|<xref:System.Activities.Statements.AddToCollection%601.Collection%2A>|Oznacza|Kolekcja, do której należy dodać element. Ta kolekcja jest typu **ICollection < elementu typeargument \>** . Aby określić kolekcję, wpisz wyrażenie Visual Basic w siatce właściwości.|
|*Elementu TypeArgument*|Oznacza|Typ T elementów zawartych w <xref:System.Collections.Generic.ICollection%601>. Domyślnie ten typ *elementu TypeArgument* jest ustawiony na **Int32**. Aby zmienić typ, Zmień wartość *elementu TypeArgument* w polu kombi w siatce właściwości.|

## <a name="see-also"></a>Zobacz także

- [Kolekcja](../workflow-designer/collection-activity-designers.md)
- [AddToCollection \<T > — Projektant działań](../workflow-designer/addtocollection-t-activity-designer.md)
- [ClearCollection\<T>](../workflow-designer/clearcollection-t-activity-designer.md)
- [ExistsInCollection\<T>](../workflow-designer/existsincollection-t-activity-designer.md)
- [RemoveFromCollection\<T>](../workflow-designer/removefromcollection-t-activity-designer.md)