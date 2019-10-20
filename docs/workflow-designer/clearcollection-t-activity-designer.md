---
title: Projektant przepływu pracy — Wyczyść projektanta działań <T>
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.ClearCollection`1.UI
ms.assetid: db0e5da2-7b5a-4f1a-864c-f3aeeeeb51a7
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a4808c046c4da23bc5c95d3978965afd938962f5
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72650690"
---
# <a name="clearcollectiont-activity-designer"></a>Wyczyść \<T projektanta działań >

**@No__t_1T clearcollection >** Designer służy do tworzenia i konfigurowania działania <xref:System.Activities.Statements.ClearCollection%601>.

## <a name="the-clearcollectiont-activity"></a>Działanie > Wyczyśćcollection \<T

Działanie <xref:System.Activities.Statements.ClearCollection%601> czyści określoną kolekcję wszystkich elementów.

### <a name="using-the-clearcollectiont-activity-designer"></a>Korzystanie z programu ClearCollection \<T > Projektant działań

Program **clearcollection \<T >** Projektant działań można znaleźć w kategorii **kolekcji** **przybornika**, do którego jest uzyskiwany dostęp, klikając kartę **przybornika** w Projektant przepływu pracy. Alternatywnie wybierz pozycję **Przybornik** z menu **Widok** lub naciśnij **klawisze CTRL** +**Alt** +**X**.

**@No__t_1T Wyczyść** projektanta działań > można przeciągnąć z **przybornika** i porzucić na Projektant przepływu pracyą powierzchnię wszędzie tam, gdzie działania są umieszczane, na przykład w <xref:System.Activities.Statements.Sequence>. Porzucenie projektanta działań powoduje utworzenie działania <xref:System.Activities.Statements.ClearCollection%601> z domyślnym <xref:System.Activities.Activity.DisplayName%2A>m ClearCollection < Int32 \>. (Domyślnie *elementu TypeArgument* jest **Int32**. Elementu TypeArgument można zmienić w siatce właściwości.) Wartość <xref:System.Activities.Activity.DisplayName%2A> można edytować w nagłówku projektanta działań **clearcollection < t \>** lub w polu **DisplayName** siatki właściwości. Inne właściwości muszą być edytowane w siatce właściwości.

### <a name="the-clearcollectiont-properties"></a>Właściwości > \<T czyszczenia

W poniższej tabeli przedstawiono właściwości <xref:System.Activities.Statements.ClearCollection%601> i opisano sposób ich używania w projektancie.

|Nazwa właściwości|Wymagane|Użycie|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Określa opcjonalną przyjazną nazwę działania <xref:System.Activities.Statements.ClearCollection%601>. Wartość domyślna to ClearCollection < Int32 \>. Mimo że wartość <xref:System.Activities.Activity.DisplayName%2A> nie jest ściśle wymagana, najlepszym rozwiązaniem jest użycie jednego z nich.|
|<xref:System.Activities.Statements.ClearCollection%601.Collection%2A>|Oznacza|Określa kolekcję, która ma zostać wyczyszczona elementów. Ta kolekcja jest typu **\<TypeArgument ICollection >.** Aby określić kolekcję, wpisz wyrażenie Visual Basic w siatce właściwości.|
|*Elementu TypeArgument*|Oznacza|Określa typ T elementów zawartych w <xref:System.Collections.Generic.ICollection%601>. Domyślnie ten typ *elementu TypeArgument* jest ustawiony na **Int32**. Aby zmienić typ, Zmień wartość *elementu TypeArgument* w polu kombi w siatce właściwości.|

## <a name="see-also"></a>Zobacz także

- [Kolekcja](../workflow-designer/collection-activity-designers.md)
- [AddToCollection\<T>](../workflow-designer/addtocollection-t-activity-designer.md)
- [ExistsInCollection\<T>](../workflow-designer/existsincollection-t-activity-designer.md)
- [RemoveFromCollection\<T>](../workflow-designer/removefromcollection-t-activity-designer.md)