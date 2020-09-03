---
title: AddToCollection &lt; T — &gt; Projektant działań | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.AddToCollection`1.UI
ms.assetid: f7fc0702-164e-4370-8946-bb2f9f9384b7
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 50deab447b3dcb93d352e73fc4765d913b4d24bf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72659206"
---
# <a name="addtocollectionlttgt-activity-designer"></a>AddToCollection &lt; T, &gt; Projektant działań
Projektant **działań \<T> AddToCollection** służy do tworzenia i konfigurowania <xref:System.Activities.Statements.AddToCollection%601> działania.

## <a name="the-addtocollectiont-activity"></a>Działanie AddToCollection \<T>
 <xref:System.Activities.Statements.AddToCollection%601>Działanie dodaje element do kolekcji.

### <a name="using-the-addtocollectiont-activity-designer"></a>Korzystanie z \<T> projektanta działań AddToCollection
 Projektanta **działań \<T> AddToCollection** można znaleźć w kategorii **Kolekcja** **przybornika**, do którego uzyskuje się dostęp, klikając kartę **przybornika** [!INCLUDE[wfd2](../includes/wfd2-md.md)] (Alternatywnie wybierz **pasek narzędzi** z menu **Widok** lub CTRL + ALT + X).

 Projektanta **działań \<T> AddToCollection** można przeciągnąć z **przybornika** i porzucić na [!INCLUDE[wfd2](../includes/wfd2-md.md)] powierzchni, wszędzie tam, gdzie działania są zwykle umieszczane, na przykład wewnątrz <xref:System.Activities.Statements.Sequence> . Spowoduje to utworzenie <xref:System.Activities.Statements.AddToCollection%601> działania z wartością domyślną <xref:System.Activities.Activity.DisplayName%2A> AddToCollection \<Int32> . (Domyślnie *elementu TypeArgument* jest **Int32**. Tę wartość można zmienić w siatce właściwości. <xref:System.Activities.Activity.DisplayName%2A>Wartość można edytować w nagłówku projektanta działań ** \<T> AddToCollection** lub w polu **DisplayName** siatki właściwości. Inne właściwości muszą być edytowane w siatce właściwości.

### <a name="the-addtocollectiont-properties"></a>Właściwości AddToCollection \<T>
 W poniższej tabeli przedstawiono <xref:System.Activities.Statements.AddToCollection%601> właściwości i opisano sposób ich użycia w projektancie.

|Nazwa właściwości|Wymagany|Użycie|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|Fałsz|Przyjazna nazwa <xref:System.Activities.Statements.AddToCollection%601> działania. Wartość domyślna to AddToCollection \<Int32> . Chociaż <xref:System.Activities.Activity.DisplayName%2A> wartość nie jest ściśle wymagana, najlepszym rozwiązaniem jest użycie jednego z nich.|
|<xref:System.Activities.Statements.AddToCollection%601.Item%2A>|Prawda|Element, który ma zostać dodany do kolekcji \<T> . Ten element jest typu *T*, który jest typu *elementu TypeArgument*. Aby określić element, wpisz wyrażenie Visual Basic w siatce właściwości.|
|<xref:System.Activities.Statements.AddToCollection%601.Collection%2A>|Prawda|Kolekcja, do której należy dodać element. Ta kolekcja jest typu **ICollection \<TypeArgument> **. Aby określić kolekcję, wpisz wyrażenie Visual Basic w siatce właściwości.|
|*Elementu TypeArgument*|Prawda|Typ T elementów zawartych w <xref:System.Collections.Generic.ICollection%601> . Domyślnie ten typ *elementu TypeArgument* jest ustawiony na **Int32**. Aby zmienić typ, Zmień wartość *elementu TypeArgument* w polu kombi w siatce właściwości.|

## <a name="see-also"></a>Zobacz też
 [Kolekcja](../workflow-designer/collection-activity-designers.md) [ \<T> działań AddToCollection](../workflow-designer/addtocollection-t-activity-designer.md) kolekcji [ClearCollection \<T> ](../workflow-designer/clearcollection-t-activity-designer.md) [ExistsInCollection \<T> ](../workflow-designer/existsincollection-t-activity-designer.md) [RemoveFromCollection \<T> ](../workflow-designer/removefromcollection-t-activity-designer.md)