---
title: Projektant przepływu pracy — &lt; &gt; Projektant działań w AddToCollection T
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
ms.openlocfilehash: 1ffa24dce2691f061c5947e15d7fc7923d632b38
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "88706545"
---
# <a name="addtocollectiont-activity-designer"></a>AddToCollection\<T>, projektant działań

Projektant **działań \<T> AddToCollection** służy do tworzenia i konfigurowania <xref:System.Activities.Statements.AddToCollection%601> działania.

## <a name="the-addtocollectiont-activity"></a>Działanie AddToCollection \<T>

<xref:System.Activities.Statements.AddToCollection%601>Działanie dodaje element do kolekcji.

### <a name="using-the-addtocollectiont-activity-designer"></a>Korzystanie z \<T> projektanta działań AddToCollection

Projektanta **działań \<T> AddToCollection** można znaleźć w kategorii **Kolekcja** **przybornika**, do którego uzyskuje się dostęp przez kliknięcie karty **przybornika** w Projektant przepływu pracy. Alternatywnie możesz wybrać **Przybornik** z menu **Widok** lub nacisnąć **klawisze CTRL** + **Alt** + **X**.

Projektanta **działań \<T> AddToCollection** można przeciągnąć z **przybornika** i porzucić na Projektant przepływu pracy powierzchnię, wszędzie tam, gdzie działania są umieszczane, na przykład wewnątrz <xref:System.Activities.Statements.Sequence> . Porzucenie projektanta działań **AddToCollection \<T> ** tworzy <xref:System.Activities.Statements.AddToCollection%601> działanie z wartością domyślną <xref:System.Activities.Activity.DisplayName%2A> AddToCollection<Int32 \> . (Domyślnie *elementu TypeArgument* jest **Int32**. Elementu TypeArgument można zmienić w siatce właściwości.) <xref:System.Activities.Activity.DisplayName%2A>Wartość można edytować w nagłówku **AddToCollection<T \> ** Activity Designer lub w polu **DisplayName** siatki właściwości. Inne właściwości muszą być edytowane w siatce właściwości.

### <a name="the-addtocollectiont-properties"></a>Właściwości AddToCollection \<T>

W poniższej tabeli przedstawiono <xref:System.Activities.Statements.AddToCollection%601> właściwości i opisano sposób ich użycia w projektancie.

|Nazwa właściwości|Wymagany|Użycie|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Fałsz|Przyjazna nazwa <xref:System.Activities.Statements.AddToCollection%601> działania. Wartość domyślna to AddToCollection<Int32 \> . Chociaż <xref:System.Activities.Activity.DisplayName%2A> wartość nie jest ściśle wymagana, najlepszym rozwiązaniem jest użycie jednego z nich.|
|<xref:System.Activities.Statements.AddToCollection%601.Item%2A>|Prawda|Element, który ma zostać dodany do kolekcji \<T> . Ten element jest typu *T*, który jest typu *elementu TypeArgument*. Aby określić element, wpisz wyrażenie Visual Basic w siatce właściwości.|
|<xref:System.Activities.Statements.AddToCollection%601.Collection%2A>|Prawda|Kolekcja, do której należy dodać element. Ta kolekcja jest typu **ICollection<elementu TypeArgument \> **. Aby określić kolekcję, wpisz wyrażenie Visual Basic w siatce właściwości.|
|*Elementu TypeArgument*|Prawda|Typ T elementów zawartych w <xref:System.Collections.Generic.ICollection%601> . Domyślnie ten typ *elementu TypeArgument* jest ustawiony na **Int32**. Aby zmienić typ, Zmień wartość *elementu TypeArgument* w polu kombi w siatce właściwości.|

## <a name="see-also"></a>Zobacz też

- [Kolekcja](../workflow-designer/collection-activity-designers.md)
- [AddToCollection, \<T> Projektant działań](../workflow-designer/addtocollection-t-activity-designer.md)
- [ClearCollection\<T>](../workflow-designer/clearcollection-t-activity-designer.md)
- [ExistsInCollection\<T>](../workflow-designer/existsincollection-t-activity-designer.md)
- [RemoveFromCollection\<T>](../workflow-designer/removefromcollection-t-activity-designer.md)
