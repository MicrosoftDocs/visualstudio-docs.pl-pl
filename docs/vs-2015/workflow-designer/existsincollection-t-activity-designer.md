---
title: ExistsInCollection &lt; T — &gt; Projektant działań | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.ExistsInCollection`1.UI
ms.assetid: 0acf9a13-caf5-4bb4-ba22-ec37d2b7267a
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 08aabbcb7dbef2df9a3affa8589a9c6d4205ac58
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656731"
---
# <a name="existsincollectionlttgt-activity-designer"></a>ExistsInCollection &lt; T, &gt; Projektant działań
Projektant **działań \<T> ExistsInCollection** służy do tworzenia i konfigurowania <xref:System.Activities.Statements.ExistsInCollection%601> działania.

## <a name="the-existsincollectiont-activity"></a>Działanie ExistsInCollection \<T>
 <xref:System.Activities.Statements.ExistsInCollection%601>Działanie określa, czy określony element istnieje w określonej kolekcji.

### <a name="using-the-existsincollectiont-activity-designer"></a>Korzystanie z \<T> projektanta działań ExistsInCollection
 Projektanta **działań \<T> ExistsInCollection** można znaleźć w kategorii **Kolekcja** **przybornika**, do którego uzyskuje się dostęp, klikając kartę **przybornika** [!INCLUDE[wfd2](../includes/wfd2-md.md)] (Alternatywnie wybierając pozycję **pasek narzędzi** w menu **Widok** lub CTRL + ALT + X).

 Projektanta **działań \<T> ExistsInCollection** można przeciągnąć z **przybornika** i porzucić na [!INCLUDE[wfd2](../includes/wfd2-md.md)] powierzchni, wszędzie tam, gdzie działania są zwykle umieszczane, na przykład wewnątrz <xref:System.Activities.Statements.Sequence> . Spowoduje to utworzenie <xref:System.Activities.Statements.ExistsInCollection%601> działania z wartością domyślną <xref:System.Activities.Activity.DisplayName%2A> ExistsInCollection \<Int32> . (Domyślnie *elementu TypeArgument* jest **Int32**. Można ją zmienić w siatce właściwości.  <xref:System.Activities.Activity.DisplayName%2A>Wartość można edytować w nagłówku projektanta działań ** \<T> ExistsInCollection** lub w polu **DisplayName** siatki właściwości. Inne właściwości muszą być edytowane w siatce właściwości.

### <a name="the-existsincollectiont-properties"></a>Właściwości ExistsInCollection \<T>
 W poniższej tabeli przedstawiono <xref:System.Activities.Statements.ExistsInCollection%601> właściwości i opisano sposób ich użycia w projektancie.

|Nazwa właściwości|Wymagany|Użycie|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|Fałsz|Przyjazna nazwa <xref:System.Activities.Statements.ExistsInCollection%601> działania. Wartość domyślna to ExistsInCollection \<Int32> . Chociaż <xref:System.Activities.Activity.DisplayName%2A> wartość nie jest ściśle wymagana, najlepszym rozwiązaniem jest użycie jednego z nich.|
|<xref:System.Activities.Statements.ExistsInCollection%601.Item%2A>|Prawda|Element, który ma zostać dodany do kolekcji \<T> . Ten element jest typu *T* jest typu *elementu TypeArgument*. Aby określić element, wpisz wyrażenie Visual Basic w siatce właściwości.|
|<xref:System.Activities.Statements.ExistsInCollection%601.Collection%2A>|Prawda|Kolekcja, do której należy dodać element. Ta kolekcja jest typu **ICollection \<TypeArgument> .** Aby określić kolekcję, wpisz wyrażenie Visual Basic w siatce właściwości.|
|*Elementu TypeArgument*|Prawda|Typ T elementów zawartych w <xref:System.Collections.Generic.ICollection%601> . Domyślnie ten typ *elementu TypeArgument* jest ustawiony na **Int32**. Aby zmienić typ, Zmień wartość *elementu TypeArgument* w polu kombi w siatce właściwości.|
|<xref:System.Activities.Activity%601.Result%2A>|Fałsz|Wartość wskazująca, czy określony element istnieje w kolekcji. Aby określić zmienną, która ma zostać powiązana z wynikiem, wpisz zmienną Visual Basicną w siatce właściwości.|

## <a name="see-also"></a>Zobacz też
 [Kolekcja](../workflow-designer/collection-activity-designers.md) [AddToCollection \<T> ](../workflow-designer/addtocollection-t-activity-designer.md) [ClearCollection \<T> ](../workflow-designer/clearcollection-t-activity-designer.md) [RemoveFromCollection \<T> ](../workflow-designer/removefromcollection-t-activity-designer.md)