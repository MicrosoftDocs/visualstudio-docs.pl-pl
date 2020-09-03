---
title: RemoveFromCollection &lt; T — &gt; Projektant działań | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.RemoveFromCollection`1.UI
ms.assetid: 6617ba26-c8bc-4aed-b746-112bf490d288
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3ac088c6e5710fcd1b7c401402ad473488f89524
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72672573"
---
# <a name="removefromcollectionlttgt-activity-designer"></a>RemoveFromCollection &lt; T, &gt; Projektant działań
Projektant **działań \<T> RemoveFromCollection** służy do tworzenia i konfigurowania <xref:System.Activities.Statements.RemoveFromCollection%601> działania.

## <a name="the-removefromcollectiont-activity"></a>Działanie RemoveFromCollection \<T>
 <xref:System.Activities.Statements.RemoveFromCollection%601>Działanie usuwa określony element z określonej kolekcji.

### <a name="using-the-removefromcollectiont-activity-designer"></a>Korzystanie z \<T> projektanta działań RemoveFromCollection
 Projektanta **działań \<T> RemoveFromCollection** można znaleźć w kategorii **Kolekcja** **przybornika**, do którego uzyskuje się dostęp przez kliknięcie karty **przybornika** [!INCLUDE[wfd2](../includes/wfd2-md.md)] (Alternatywnie wybierz pozycję **pasek narzędzi** z menu **Widok** lub CTRL + ALT + X).

 Projektanta **działań \<T> RemoveFromCollection** można przeciągnąć z **przybornika** i porzucić na [!INCLUDE[wfd2](../includes/wfd2-md.md)] powierzchni, wszędzie tam, gdzie działania są zwykle umieszczane, na przykład wewnątrz <xref:System.Activities.Statements.Sequence> . Spowoduje to utworzenie <xref:System.Activities.Statements.RemoveFromCollection%601> działania z wartością domyślną <xref:System.Activities.Activity.DisplayName%2A> RemoveFromCollection \<Int32> . <xref:System.Activities.Activity.DisplayName%2A>Wartość można edytować w nagłówku projektanta działań ** \<T> RemoveFromCollection** lub w polu **DisplayName** siatki właściwości. Inne właściwości muszą być edytowane w siatce właściwości.

### <a name="the-removefromcollectiont-properties"></a>Właściwości RemoveFromCollection \<T>
 W poniższej tabeli przedstawiono <xref:System.Activities.Statements.RemoveFromCollection%601> właściwości i opisano sposób ich użycia w projektancie.

|Nazwa właściwości|Wymagany|Użycie|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|Fałsz|Opcjonalna przyjazna nazwa <xref:System.Activities.Statements.RemoveFromCollection%601> działania. Wartość domyślna to RemoveFromCollection \<Int32> .<br /><br /> Chociaż <xref:System.Activities.Activity.DisplayName%2A> nie jest to ściśle wymagane, najlepszym rozwiązaniem jest użycie jednego z nich.|
|<xref:System.Activities.Statements.RemoveFromCollection%601.Item%2A>|Prawda|Element, który ma zostać dodany **do \<T> kolekcji**. Ten element jest typu *T*, który jest typu *elementu TypeArgument*. Aby określić element, wpisz wyrażenie Visual Basic w siatce właściwości.|
|<xref:System.Activities.Statements.RemoveFromCollection%601.Collection%2A>|Prawda|Kolekcja, do której należy dodać element. Ta kolekcja jest typu **ICollection \<TypeArgument> .** Aby określić kolekcję, wpisz wyrażenie Visual Basic w siatce właściwości.|
|*Elementu TypeArgument*|Prawda|Typ T elementów zawartych w <xref:System.Collections.Generic.ICollection%601> . Domyślnie ten typ *elementu TypeArgument* jest ustawiony na **Int32**. Aby zmienić typ, Zmień wartość *elementu TypeArgument* w polu kombi w siatce właściwości.|
|<xref:System.Activities.Activity%601.Result%2A>|Fałsz|Wartość wskazująca, czy określony element został usunięty z kolekcji. Aby określić zmienną, która ma zostać powiązana z wynikiem, wpisz zmienną w siatce właściwości|

## <a name="see-also"></a>Zobacz też
 [Kolekcja](../workflow-designer/collection-activity-designers.md) [AddToCollection \<T> ](../workflow-designer/addtocollection-t-activity-designer.md) [ClearCollection \<T> ](../workflow-designer/clearcollection-t-activity-designer.md) [ExistsInCollection \<T> ](../workflow-designer/existsincollection-t-activity-designer.md)