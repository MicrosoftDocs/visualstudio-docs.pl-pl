---
title: Projektant przepływu pracy — &lt; &gt; Projektant działań w RemoveFromCollection T
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.RemoveFromCollection`1.UI
ms.assetid: 6617ba26-c8bc-4aed-b746-112bf490d288
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c8af0a0bf8bdf60c8ae9911ef0926cb9e395989a
ms.sourcegitcommit: 186c0c250d85ac74274fa1e438b4c7c7108d8a36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/22/2020
ms.locfileid: "86875582"
---
# <a name="removefromcollectiont-activity-designer"></a>RemoveFromCollection\<T>, projektant działań

Projektant **działań \<T> RemoveFromCollection** służy do tworzenia i konfigurowania <xref:System.Activities.Statements.RemoveFromCollection%601> działania.

## <a name="the-removefromcollectiontactivity"></a>Działanie RemoveFromCollection \<T>

<xref:System.Activities.Statements.RemoveFromCollection%601>Działanie usuwa określony element z określonej kolekcji.

### <a name="using-the-removefromcollectiont-activity-designer"></a>Korzystanie z \<T> projektanta działań RemoveFromCollection

Dostęp do projektanta działań **RemoveFromCollection \<T> ** w kategorii **Kolekcja** **przybornika**.
Projektanta **działań \<T> RemoveFromCollection** można przeciągnąć z **przybornika** i porzucić na Projektant przepływu pracy powierzchnię, wszędzie tam, gdzie działania są zwykle umieszczane, na przykład wewnątrz <xref:System.Activities.Statements.Sequence> . Spowoduje to utworzenie <xref:System.Activities.Statements.RemoveFromCollection%601> działania z wartością domyślną <xref:System.Activities.Activity.DisplayName%2A> RemoveFromCollection<Int32 \> . <xref:System.Activities.Activity.DisplayName%2A>Wartość można edytować w nagłówku **RemoveFromCollection<T \> ** Activity Designer lub w polu **DisplayName** siatki właściwości. Inne właściwości muszą być edytowane w siatce właściwości.

### <a name="the-removefromcollectiont-properties"></a>Właściwości RemoveFromCollection<T \>

W poniższej tabeli przedstawiono <xref:System.Activities.Statements.RemoveFromCollection%601> właściwości i opisano sposób ich używania w projektancie:

|Nazwa właściwości|Wymagany|Użycie|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Fałsz|Opcjonalna przyjazna nazwa <xref:System.Activities.Statements.RemoveFromCollection%601> działania. Wartość domyślna to RemoveFromCollection<Int32 \> .<br /><br /> Chociaż <xref:System.Activities.Activity.DisplayName%2A> nie jest to ściśle wymagane, najlepszym rozwiązaniem jest użycie jednego z nich.|
|<xref:System.Activities.Statements.RemoveFromCollection%601.Item%2A>|Prawda|Element do usunięcia z **kolekcji \<T> **. Ten element jest typu *T*, który jest typu *elementu TypeArgument*. Aby określić element, wpisz wyrażenie Visual Basic w siatce właściwości.|
|<xref:System.Activities.Statements.RemoveFromCollection%601.Collection%2A>|Prawda|Kolekcja, z której ma zostać usunięty element. Ta kolekcja jest typu **ICollection<elementu TypeArgument \> .** Aby określić kolekcję, wpisz wyrażenie Visual Basic w siatce właściwości.|
|*Elementu TypeArgument*|Prawda|Typ T elementów zawartych w <xref:System.Collections.Generic.ICollection%601> . Domyślnie ten typ *elementu TypeArgument* jest ustawiony na **Int32**. Aby zmienić typ, Zmień wartość *elementu TypeArgument* w polu kombi w siatce właściwości.|
|<xref:System.Activities.Activity%601.Result%2A>|Fałsz|Wartość wskazująca, czy określony element został usunięty z kolekcji. Aby określić zmienną, która ma zostać powiązana z wynikiem, wpisz zmienną w siatce właściwości|

## <a name="see-also"></a>Zobacz także

- [Kolekcja](../workflow-designer/collection-activity-designers.md)
- [AddToCollection\<T>](../workflow-designer/addtocollection-t-activity-designer.md)
- [ClearCollection\<T>](../workflow-designer/clearcollection-t-activity-designer.md)
- [ExistsInCollection\<T>](../workflow-designer/existsincollection-t-activity-designer.md)