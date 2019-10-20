---
title: RemoveFromCollection &lt;T &gt; — Projektant działań | Microsoft Docs
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
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672573"
---
# <a name="removefromcollectionlttgt-activity-designer"></a>RemoveFromCollection &lt;T &gt; — Projektant działań
**RemoveFromCollection \<T >** Projektant działań służy do tworzenia i konfigurowania działania <xref:System.Activities.Statements.RemoveFromCollection%601>.

## <a name="the-removefromcollectiont-activity"></a>Działanie RemoveFromCollection \<T >
 Działanie <xref:System.Activities.Statements.RemoveFromCollection%601> usuwa określony element z określonej kolekcji.

### <a name="using-the-removefromcollectiont-activity-designer"></a>Korzystanie z RemoveFromCollection \<T > Projektant działań
 **RemoveFromCollection \<T >** projektanta aktywności można znaleźć w kategorii **kolekcji** **przybornika**, do którego uzyskuje się dostęp przez kliknięcie karty **przybornika** na [!INCLUDE[wfd2](../includes/wfd2-md.md)] (można także wybrać pozycję **pasek narzędzi** z menu **Widok** lub CTRL + ALT + X.)

 **RemoveFromCollection \<T >** projektanta aktywności można przeciągnąć z **przybornika** i porzucić na [!INCLUDE[wfd2](../includes/wfd2-md.md)] powierzchni wszędzie tam, gdzie działania są zwykle umieszczane, na przykład w <xref:System.Activities.Statements.Sequence>. Spowoduje to utworzenie działania <xref:System.Activities.Statements.RemoveFromCollection%601> przy użyciu domyślnego <xref:System.Activities.Activity.DisplayName%2A> RemoveFromCollection \<Int32 >. Wartość <xref:System.Activities.Activity.DisplayName%2A> można edytować w nagłówku projektanta działań programu **RemoveFromCollection \<T >** lub w polu **DisplayName** siatki właściwości. Inne właściwości muszą być edytowane w siatce właściwości.

### <a name="the-removefromcollectiont-properties"></a>Właściwości RemoveFromCollection \<T >
 W poniższej tabeli przedstawiono właściwości <xref:System.Activities.Statements.RemoveFromCollection%601> i opisano sposób ich używania w projektancie.

|Nazwa właściwości|Wymagane|Użycie|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Opcjonalna przyjazna nazwa działania <xref:System.Activities.Statements.RemoveFromCollection%601>. Wartość domyślna to RemoveFromCollection \<Int32 >.<br /><br /> Mimo że <xref:System.Activities.Activity.DisplayName%2A> nie jest ściśle wymagane, najlepszym rozwiązaniem jest użycie jednego z nich.|
|<xref:System.Activities.Statements.RemoveFromCollection%601.Item%2A>|Oznacza|Element, który ma zostać dodany do **kolekcji \<T >** . Ten element jest typu *T*, który jest typu *elementu TypeArgument*. Aby określić element, wpisz wyrażenie Visual Basic w siatce właściwości.|
|<xref:System.Activities.Statements.RemoveFromCollection%601.Collection%2A>|Oznacza|Kolekcja, do której należy dodać element. Ta kolekcja jest typu **\<TypeArgument ICollection >.** Aby określić kolekcję, wpisz wyrażenie Visual Basic w siatce właściwości.|
|*Elementu TypeArgument*|Oznacza|Typ T elementów zawartych w <xref:System.Collections.Generic.ICollection%601>. Domyślnie ten typ *elementu TypeArgument* jest ustawiony na **Int32**. Aby zmienić typ, Zmień wartość *elementu TypeArgument* w polu kombi w siatce właściwości.|
|<xref:System.Activities.Activity%601.Result%2A>|False|Wartość wskazująca, czy określony element został usunięty z kolekcji. Aby określić zmienną, która ma zostać powiązana z wynikiem, wpisz zmienną w siatce właściwości|

## <a name="see-also"></a>Zobacz też
 [Kolekcja](../workflow-designer/collection-activity-designers.md) [AddToCollection \<T >](../workflow-designer/addtocollection-t-activity-designer.md) [clearcollection \<T >](../workflow-designer/clearcollection-t-activity-designer.md) [ExistsInCollection \<T >](../workflow-designer/existsincollection-t-activity-designer.md)