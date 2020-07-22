---
title: Projektant przepływu pracy — &lt; &gt; Projektant działań w ExistsInCollection T
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.ExistsInCollection`1.UI
ms.assetid: 0acf9a13-caf5-4bb4-ba22-ec37d2b7267a
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b48bb11e2aac9d542a07551df62d710c41596d28
ms.sourcegitcommit: 186c0c250d85ac74274fa1e438b4c7c7108d8a36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/22/2020
ms.locfileid: "86875660"
---
# <a name="existsincollectiont-activity-designer"></a>ExistsInCollection\<T>, projektant działań

Projektant **działań \<T> ExistsInCollection** służy do tworzenia i konfigurowania <xref:System.Activities.Statements.ExistsInCollection%601> działania.

## <a name="the-existsincollectiont-activity"></a>Działanie ExistsInCollection \<T>

<xref:System.Activities.Statements.ExistsInCollection%601>Działanie określa, czy określony element istnieje w określonej kolekcji.

### <a name="using-the-existsincollectiont-activity-designer"></a>Korzystanie z \<T> projektanta działań ExistsInCollection

Projektanta **działań \<T> ExistsInCollection** można znaleźć w kategorii **Kolekcja** **przybornika**, do którego uzyskuje się dostęp przez kliknięcie karty **przybornika** w Projektant przepływu pracy. Alternatywnie możesz wybrać **Przybornik** z menu **Widok** lub nacisnąć **klawisze CTRL** + **Alt** + **X**.

Projektanta **działań \<T> ExistsInCollection** można przeciągnąć z **przybornika** i porzucić na Projektant przepływu pracy powierzchnię, wszędzie tam, gdzie działania są zwykle umieszczane, na przykład wewnątrz <xref:System.Activities.Statements.Sequence> . Spowoduje to utworzenie <xref:System.Activities.Statements.ExistsInCollection%601> działania z wartością domyślną <xref:System.Activities.Activity.DisplayName%2A> ExistsInCollection<Int32 \> . (Domyślnie *elementu TypeArgument* jest **Int32**. Można ją zmienić w siatce właściwości.  <xref:System.Activities.Activity.DisplayName%2A>Wartość można edytować w nagłówku **ExistsInCollection<T \> ** Activity Designer lub w polu **DisplayName** siatki właściwości. Inne właściwości muszą być edytowane w siatce właściwości.

### <a name="the-existsincollectiont-properties"></a>Właściwości ExistsInCollection \<T>

W poniższej tabeli przedstawiono <xref:System.Activities.Statements.ExistsInCollection%601> właściwości i opisano sposób ich używania w projektancie:

|Nazwa właściwości|Wymagany|Użycie|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Fałsz|Przyjazna nazwa <xref:System.Activities.Statements.ExistsInCollection%601> działania. Wartość domyślna to ExistsInCollection<Int32 \> . Chociaż <xref:System.Activities.Activity.DisplayName%2A> wartość nie jest ściśle wymagana, najlepszym rozwiązaniem jest użycie jednego z nich.|
|<xref:System.Activities.Statements.ExistsInCollection%601.Item%2A>|Prawda|Element do wyszukania w kolekcji \<T> . Ten element jest typu *T*, który jest typu *elementu TypeArgument*. Aby określić element, wpisz wyrażenie Visual Basic w siatce właściwości.|
|<xref:System.Activities.Statements.ExistsInCollection%601.Collection%2A>|Prawda|Kolekcja, w której należy sprawdzić, czy element istnieje. Ta kolekcja jest typu **ICollection<elementu TypeArgument \> .** Aby określić kolekcję, wpisz wyrażenie Visual Basic w siatce właściwości.|
|*Elementu TypeArgument*|Prawda|Typ T elementów zawartych w <xref:System.Collections.Generic.ICollection%601> . Domyślnie ten typ *elementu TypeArgument* jest ustawiony na **Int32**. Aby zmienić typ, Zmień wartość *elementu TypeArgument* w polu kombi w siatce właściwości.|
|<xref:System.Activities.Activity%601.Result%2A>|Fałsz|Wartość wskazująca, czy określony element istnieje w kolekcji. Aby określić zmienną, która ma zostać powiązana z wynikiem, wpisz zmienną Visual Basicną w siatce właściwości.|

## <a name="see-also"></a>Zobacz także

- [Kolekcja](../workflow-designer/collection-activity-designers.md)
- [AddToCollection\<T>](../workflow-designer/addtocollection-t-activity-designer.md)
- [ClearCollection\<T>](../workflow-designer/clearcollection-t-activity-designer.md)
- [RemoveFromCollection\<T>](../workflow-designer/removefromcollection-t-activity-designer.md)