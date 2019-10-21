---
title: ExistsInCollection &lt;T &gt; — Projektant działań | Microsoft Docs
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
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656731"
---
# <a name="existsincollectionlttgt-activity-designer"></a>ExistsInCollection &lt;T &gt; — Projektant działań
**ExistsInCollection \<T >** Projektant działań służy do tworzenia i konfigurowania działania <xref:System.Activities.Statements.ExistsInCollection%601>.

## <a name="the-existsincollectiont-activity"></a>Działanie ExistsInCollection \<T >
 Działanie <xref:System.Activities.Statements.ExistsInCollection%601> określa, czy określony element istnieje w określonej kolekcji.

### <a name="using-the-existsincollectiont-activity-designer"></a>Korzystanie z ExistsInCollection \<T > Projektant działań
 Projektanta działań programu **ExistsInCollection \<T >** można znaleźć w kategorii **kolekcji** **przybornika**, do którego uzyskuje się dostęp przez kliknięcie karty **przybornika** w [!INCLUDE[wfd2](../includes/wfd2-md.md)] (Alternatywnie wybierz pozycję **pasek narzędzi** z Menu **Widok** lub CTRL + ALT + X.)

 **ExistsInCollection \<T >** projektanta aktywności można przeciągnąć z **przybornika** i porzucić na [!INCLUDE[wfd2](../includes/wfd2-md.md)] powierzchni wszędzie tam, gdzie działania są zwykle umieszczane, na przykład w <xref:System.Activities.Statements.Sequence>. Spowoduje to utworzenie działania <xref:System.Activities.Statements.ExistsInCollection%601> przy użyciu domyślnego <xref:System.Activities.Activity.DisplayName%2A> ExistsInCollection \<Int32 >. (Domyślnie *elementu TypeArgument* jest **Int32**. Można ją zmienić w siatce właściwości.  Wartość <xref:System.Activities.Activity.DisplayName%2A> można edytować w nagłówku projektanta działań programu **ExistsInCollection \<T >** lub w polu **DisplayName** siatki właściwości. Inne właściwości muszą być edytowane w siatce właściwości.

### <a name="the-existsincollectiont-properties"></a>Właściwości ExistsInCollection \<T >
 W poniższej tabeli przedstawiono właściwości <xref:System.Activities.Statements.ExistsInCollection%601> i opisano sposób ich używania w projektancie.

|Nazwa właściwości|Wymagane|Użycie|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Przyjazna nazwa działania <xref:System.Activities.Statements.ExistsInCollection%601>. Wartość domyślna to ExistsInCollection \<Int32 >. Mimo że wartość <xref:System.Activities.Activity.DisplayName%2A> nie jest ściśle wymagana, najlepszym rozwiązaniem jest użycie jednego z nich.|
|<xref:System.Activities.Statements.ExistsInCollection%601.Item%2A>|Oznacza|Element, który ma zostać dodany do kolekcji \<T >. Ten element jest typu *T* jest typu *elementu TypeArgument*. Aby określić element, wpisz wyrażenie Visual Basic w siatce właściwości.|
|<xref:System.Activities.Statements.ExistsInCollection%601.Collection%2A>|Oznacza|Kolekcja, do której należy dodać element. Ta kolekcja jest typu **\<TypeArgument ICollection >.** Aby określić kolekcję, wpisz wyrażenie Visual Basic w siatce właściwości.|
|*Elementu TypeArgument*|Oznacza|Typ T elementów zawartych w <xref:System.Collections.Generic.ICollection%601>. Domyślnie ten typ *elementu TypeArgument* jest ustawiony na **Int32**. Aby zmienić typ, Zmień wartość *elementu TypeArgument* w polu kombi w siatce właściwości.|
|<xref:System.Activities.Activity%601.Result%2A>|False|Wartość wskazująca, czy określony element istnieje w kolekcji. Aby określić zmienną, która ma zostać powiązana z wynikiem, wpisz zmienną Visual Basicną w siatce właściwości.|

## <a name="see-also"></a>Zobacz też
 [Kolekcja](../workflow-designer/collection-activity-designers.md) [AddToCollection \<T >](../workflow-designer/addtocollection-t-activity-designer.md) [clearcollection \<T >](../workflow-designer/clearcollection-t-activity-designer.md) [RemoveFromCollection \<T >](../workflow-designer/removefromcollection-t-activity-designer.md)