---
title: Projektant przepływu pracy-RemoveFromCollection &lt;T &gt; — Projektant działań
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.RemoveFromCollection`1.UI
ms.assetid: 6617ba26-c8bc-4aed-b746-112bf490d288
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1a8885505607d654327ad9dc36ab88708ab708c3
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72650003"
---
# <a name="removefromcollectiont-activity-designer"></a>RemoveFromCollection \<T > — Projektant działań

**RemoveFromCollection \<T >** Projektant działań służy do tworzenia i konfigurowania działania <xref:System.Activities.Statements.RemoveFromCollection%601>.

## <a name="the-removefromcollectiontactivity"></a>Działanie RemoveFromCollection \<T >

Działanie <xref:System.Activities.Statements.RemoveFromCollection%601> usuwa określony element z określonej kolekcji.

### <a name="using-the-removefromcollectiont-activity-designer"></a>Korzystanie z RemoveFromCollection \<T > Projektant działań

Dostęp do programu **RemoveFromCollection \<T >** projektanta działań w kategorii **Kolekcja** w **przyborniku**.
**RemoveFromCollection \<T >** projektanta aktywności można przeciągnąć z **przybornika** i porzucić na Projektant przepływu pracy powierzchni wszędzie tam, gdzie działania są zwykle umieszczane, na przykład w <xref:System.Activities.Statements.Sequence>. Spowoduje to utworzenie działania <xref:System.Activities.Statements.RemoveFromCollection%601> przy użyciu domyślnej <xref:System.Activities.Activity.DisplayName%2A> RemoveFromCollection < Int32 \>. Wartość <xref:System.Activities.Activity.DisplayName%2A> można edytować w nagłówku projektanta działań **RemoveFromCollection < t \>** lub w polu **DisplayName** siatki właściwości. Inne właściwości muszą być edytowane w siatce właściwości.

### <a name="the-removefromcollectiont-properties"></a>Właściwości RemoveFromCollection < T \>

W poniższej tabeli przedstawiono właściwości <xref:System.Activities.Statements.RemoveFromCollection%601> i opisano sposób ich używania w projektancie:

|Nazwa właściwości|Wymagane|Użycie|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Opcjonalna przyjazna nazwa działania <xref:System.Activities.Statements.RemoveFromCollection%601>. Wartość domyślna to RemoveFromCollection < Int32 \>.<br /><br /> Mimo że <xref:System.Activities.Activity.DisplayName%2A> nie jest ściśle wymagane, najlepszym rozwiązaniem jest użycie jednego z nich.|
|<xref:System.Activities.Statements.RemoveFromCollection%601.Item%2A>|Oznacza|Element, który ma zostać usunięty z **kolekcji \<T >** . Ten element jest typu *T*, który jest typu *elementu TypeArgument*. Aby określić element, wpisz wyrażenie Visual Basic w siatce właściwości.|
|<xref:System.Activities.Statements.RemoveFromCollection%601.Collection%2A>|Oznacza|Kolekcja, z której ma zostać usunięty element. Ta kolekcja jest typu **ICollection < elementu typeargument \>.** Aby określić kolekcję, wpisz wyrażenie Visual Basic w siatce właściwości.|
|*Elementu TypeArgument*|Oznacza|Typ T elementów zawartych w <xref:System.Collections.Generic.ICollection%601>. Domyślnie ten typ *elementu TypeArgument* jest ustawiony na **Int32**. Aby zmienić typ, Zmień wartość *elementu TypeArgument* w polu kombi w siatce właściwości.|
|<xref:System.Activities.Activity%601.Result%2A>|False|Wartość wskazująca, czy określony element został usunięty z kolekcji. Aby określić zmienną, która ma zostać powiązana z wynikiem, wpisz zmienną w siatce właściwości|

## <a name="see-also"></a>Zobacz także

- [Kolekcja](../workflow-designer/collection-activity-designers.md)
- [AddToCollection\<T>](../workflow-designer/addtocollection-t-activity-designer.md)
- [ClearCollection\<T>](../workflow-designer/clearcollection-t-activity-designer.md)
- [ExistsInCollection\<T>](../workflow-designer/existsincollection-t-activity-designer.md)