---
title: Projektant przepływu pracy-ExistsInCollection &lt;T &gt; — Projektant działań
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.ExistsInCollection`1.UI
ms.assetid: 0acf9a13-caf5-4bb4-ba22-ec37d2b7267a
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a9dc1f6a3694b6164fe4f2187fa4c6e2b42751e7
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72650485"
---
# <a name="existsincollectiont-activity-designer"></a>ExistsInCollection \<T > — Projektant działań

**ExistsInCollection \<T >** Projektant działań służy do tworzenia i konfigurowania działania <xref:System.Activities.Statements.ExistsInCollection%601>.

## <a name="the-existsincollectiont-activity"></a>Działanie ExistsInCollection \<T >

Działanie <xref:System.Activities.Statements.ExistsInCollection%601> określa, czy określony element istnieje w określonej kolekcji.

### <a name="using-the-existsincollectiont-activity-designer"></a>Korzystanie z ExistsInCollection \<T > Projektant działań

Projektanta działań programu **ExistsInCollection \<T >** można znaleźć w kategorii **kolekcji** **przybornika**, do którego jest uzyskiwany dostęp przez kliknięcie karty **przybornika** w Projektant przepływu pracy. Alternatywnie wybierz pozycję **Przybornik** z menu **Widok** lub naciśnij **klawisze CTRL** +**Alt** +**X**.

**ExistsInCollection \<T >** projektanta aktywności można przeciągnąć z **przybornika** i porzucić na Projektant przepływu pracy powierzchni wszędzie tam, gdzie działania są zwykle umieszczane, na przykład w <xref:System.Activities.Statements.Sequence>. Spowoduje to utworzenie działania <xref:System.Activities.Statements.ExistsInCollection%601> przy użyciu domyślnej <xref:System.Activities.Activity.DisplayName%2A> ExistsInCollection < Int32 \>. (Domyślnie *elementu TypeArgument* jest **Int32**. Można ją zmienić w siatce właściwości.  Wartość <xref:System.Activities.Activity.DisplayName%2A> można edytować w nagłówku projektanta działań **ExistsInCollection < t \>** lub w polu **DisplayName** siatki właściwości. Inne właściwości muszą być edytowane w siatce właściwości.

### <a name="the-existsincollectiont-properties"></a>Właściwości ExistsInCollection \<T >

W poniższej tabeli przedstawiono właściwości <xref:System.Activities.Statements.ExistsInCollection%601> i opisano sposób ich używania w projektancie:

|Nazwa właściwości|Wymagane|Użycie|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Przyjazna nazwa działania <xref:System.Activities.Statements.ExistsInCollection%601>. Wartość domyślna to ExistsInCollection < Int32 \>. Mimo że wartość <xref:System.Activities.Activity.DisplayName%2A> nie jest ściśle wymagana, najlepszym rozwiązaniem jest użycie jednego z nich.|
|<xref:System.Activities.Statements.ExistsInCollection%601.Item%2A>|Oznacza|Element do wyszukania w kolekcji \<T >. Ten element jest typu *T*, który jest typu *elementu TypeArgument*. Aby określić element, wpisz wyrażenie Visual Basic w siatce właściwości.|
|<xref:System.Activities.Statements.ExistsInCollection%601.Collection%2A>|Oznacza|Kolekcja, w której należy sprawdzić, czy element istnieje. Ta kolekcja jest typu **ICollection < elementu typeargument \>.** Aby określić kolekcję, wpisz wyrażenie Visual Basic w siatce właściwości.|
|*Elementu TypeArgument*|Oznacza|Typ T elementów zawartych w <xref:System.Collections.Generic.ICollection%601>. Domyślnie ten typ *elementu TypeArgument* jest ustawiony na **Int32**. Aby zmienić typ, Zmień wartość *elementu TypeArgument* w polu kombi w siatce właściwości.|
|<xref:System.Activities.Activity%601.Result%2A>|False|Wartość wskazująca, czy określony element istnieje w kolekcji. Aby określić zmienną, która ma zostać powiązana z wynikiem, wpisz zmienną Visual Basicną w siatce właściwości.|

## <a name="see-also"></a>Zobacz także

- [Kolekcja](../workflow-designer/collection-activity-designers.md)
- [AddToCollection\<T>](../workflow-designer/addtocollection-t-activity-designer.md)
- [ClearCollection\<T>](../workflow-designer/clearcollection-t-activity-designer.md)
- [RemoveFromCollection\<T>](../workflow-designer/removefromcollection-t-activity-designer.md)