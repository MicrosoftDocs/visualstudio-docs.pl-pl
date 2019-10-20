---
title: AddToCollection &lt;T &gt; — Projektant działań | Microsoft Docs
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
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72659206"
---
# <a name="addtocollectionlttgt-activity-designer"></a>AddToCollection &lt;T &gt; — Projektant działań
**AddToCollection \<T >** Projektant działań służy do tworzenia i konfigurowania działania <xref:System.Activities.Statements.AddToCollection%601>.

## <a name="the-addtocollectiont-activity"></a>Działanie AddToCollection \<T >
 Działanie <xref:System.Activities.Statements.AddToCollection%601> dodaje element do kolekcji.

### <a name="using-the-addtocollectiont-activity-designer"></a>Korzystanie z AddToCollection \<T > Projektant działań
 **AddToCollection \<T >** projektanta aktywności można znaleźć w kategorii **kolekcji** **przybornika**, do którego uzyskuje się dostęp przez kliknięcie karty **przybornika** w [!INCLUDE[wfd2](../includes/wfd2-md.md)] (Alternatywnie wybierz pozycję **pasek narzędzi** z Menu **Widok** lub CTRL + ALT + X.)

 **AddToCollection \<T >** projektanta aktywności można przeciągnąć z **przybornika** i porzucić na [!INCLUDE[wfd2](../includes/wfd2-md.md)] powierzchni wszędzie tam, gdzie działania są zwykle umieszczane, na przykład w <xref:System.Activities.Statements.Sequence>. Spowoduje to utworzenie działania <xref:System.Activities.Statements.AddToCollection%601> przy użyciu domyślnego <xref:System.Activities.Activity.DisplayName%2A> AddToCollection \<Int32 >. (Domyślnie *elementu TypeArgument* jest **Int32**. Tę wartość można zmienić w siatce właściwości. Wartość <xref:System.Activities.Activity.DisplayName%2A> można edytować w nagłówku projektanta działań programu **AddToCollection \<T >** lub w polu **DisplayName** siatki właściwości. Inne właściwości muszą być edytowane w siatce właściwości.

### <a name="the-addtocollectiont-properties"></a>Właściwości AddToCollection \<T >
 W poniższej tabeli przedstawiono właściwości <xref:System.Activities.Statements.AddToCollection%601> i opisano sposób ich używania w projektancie.

|Nazwa właściwości|Wymagane|Użycie|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Przyjazna nazwa działania <xref:System.Activities.Statements.AddToCollection%601>. Wartość domyślna to AddToCollection \<Int32 >. Mimo że wartość <xref:System.Activities.Activity.DisplayName%2A> nie jest ściśle wymagana, najlepszym rozwiązaniem jest użycie jednego z nich.|
|<xref:System.Activities.Statements.AddToCollection%601.Item%2A>|Oznacza|Element, który ma zostać dodany do kolekcji \<T >. Ten element jest typu *T*, który jest typu *elementu TypeArgument*. Aby określić element, wpisz wyrażenie Visual Basic w siatce właściwości.|
|<xref:System.Activities.Statements.AddToCollection%601.Collection%2A>|Oznacza|Kolekcja, do której należy dodać element. Ta kolekcja jest typu **\<TypeArgument ICollection >** . Aby określić kolekcję, wpisz wyrażenie Visual Basic w siatce właściwości.|
|*Elementu TypeArgument*|Oznacza|Typ T elementów zawartych w <xref:System.Collections.Generic.ICollection%601>. Domyślnie ten typ *elementu TypeArgument* jest ustawiony na **Int32**. Aby zmienić typ, Zmień wartość *elementu TypeArgument* w polu kombi w siatce właściwości.|

## <a name="see-also"></a>Zobacz też
 [Kolekcja](../workflow-designer/collection-activity-designers.md) [AddToCollection \<T > ExistsInCollection projektanta aktywności](../workflow-designer/addtocollection-t-activity-designer.md) [> \<T](../workflow-designer/clearcollection-t-activity-designer.md) [](../workflow-designer/existsincollection-t-activity-designer.md) \<T > [RemoveFromCollection](../workflow-designer/removefromcollection-t-activity-designer.md) \<T >