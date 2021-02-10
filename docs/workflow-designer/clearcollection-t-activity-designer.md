---
title: Projektant przepływu pracy — Wyczyść &lt; &gt; projektanta działań w programiecollection T
description: Dowiedz się, jak za pomocą <T> projektanta działań ClearCollection utworzyć i skonfigurować działanie ClearCollection <T> .
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.ClearCollection`1.UI
ms.assetid: db0e5da2-7b5a-4f1a-864c-f3aeeeeb51a7
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 31d576712804a75fdca57374ce82a53ff0d1ce84
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99942090"
---
# <a name="clearcollectiont-activity-designer"></a>ClearCollection\<T>, projektant działań

Projektant działań **ClearCollection \<T>** służy do tworzenia i konfigurowania <xref:System.Activities.Statements.ClearCollection%601> działania.

## <a name="the-clearcollectiont-activity"></a>Działanie ClearCollection \<T>

<xref:System.Activities.Statements.ClearCollection%601>Działanie czyści określoną kolekcję wszystkich elementów.

### <a name="using-the-clearcollectiont-activity-designer"></a>Korzystanie z \<T> projektanta działania ClearCollection

Projektant **działań \<T> ClearCollection** można znaleźć w kategorii **kolekcji** **przybornika**, do którego jest uzyskiwany dostęp, klikając kartę **przybornika** Projektant przepływu pracy. Alternatywnie możesz wybrać **Przybornik** z menu **Widok** lub nacisnąć **klawisze CTRL** + **Alt** + **X**.

Projektant działań **ClearCollection \<T>** można przeciągnąć z **przybornika** i porzucić na Projektant przepływu pracy powierzchnię, wszędzie tam, gdzie działania są umieszczane, na przykład wewnątrz <xref:System.Activities.Statements.Sequence> . Porzucenie projektanta działań powoduje utworzenie <xref:System.Activities.Statements.ClearCollection%601> działania z wartością domyślną <xref:System.Activities.Activity.DisplayName%2A> clearcollection<Int32 \> . (Domyślnie *elementu TypeArgument* jest **Int32**. Elementu TypeArgument można zmienić w siatce właściwości.) <xref:System.Activities.Activity.DisplayName%2A>Wartość może być edytowana w nagłówku projektanta działania **clearcollection<T \>** lub w polu **DisplayName** siatki właściwości. Inne właściwości muszą być edytowane w siatce właściwości.

### <a name="the-clearcollectiont-properties"></a>Właściwości ClearCollection \<T>

W poniższej tabeli przedstawiono <xref:System.Activities.Statements.ClearCollection%601> właściwości i opisano sposób ich użycia w projektancie.

|Nazwa właściwości|Wymagany|Użycie|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Fałsz|Określa opcjonalną przyjazną nazwę <xref:System.Activities.Statements.ClearCollection%601> działania. Wartość domyślna to ClearCollection<Int32 \> . Chociaż <xref:System.Activities.Activity.DisplayName%2A> wartość nie jest ściśle wymagana, najlepszym rozwiązaniem jest użycie jednego z nich.|
|<xref:System.Activities.Statements.ClearCollection%601.Collection%2A>|Prawda|Określa kolekcję, która ma zostać wyczyszczona elementów. Ta kolekcja jest typu **ICollection \<TypeArgument> .** Aby określić kolekcję, wpisz wyrażenie Visual Basic w siatce właściwości.|
|*Elementu TypeArgument*|Prawda|Określa typ T elementów zawartych w <xref:System.Collections.Generic.ICollection%601> . Domyślnie ten typ *elementu TypeArgument* jest ustawiony na **Int32**. Aby zmienić typ, Zmień wartość *elementu TypeArgument* w polu kombi w siatce właściwości.|

## <a name="see-also"></a>Zobacz też

- [Kolekcja](../workflow-designer/collection-activity-designers.md)
- [AddToCollection\<T>](../workflow-designer/addtocollection-t-activity-designer.md)
- [ExistsInCollection\<T>](../workflow-designer/existsincollection-t-activity-designer.md)
- [RemoveFromCollection\<T>](../workflow-designer/removefromcollection-t-activity-designer.md)