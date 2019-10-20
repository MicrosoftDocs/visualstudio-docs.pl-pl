---
title: Wyczyść &lt;T projektanta działań &gt; | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.ClearCollection`1.UI
ms.assetid: db0e5da2-7b5a-4f1a-864c-f3aeeeeb51a7
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 8c2f1e0264d39c65601a70e8c24b51c7eceadf4a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72657022"
---
# <a name="clearcollectionlttgt-activity-designer"></a>Wyczyść &lt;T projektanta działań &gt;
**@No__t_1T clearcollection >** Designer służy do tworzenia i konfigurowania działania <xref:System.Activities.Statements.ClearCollection%601>.

## <a name="the-clearcollectiont-activity"></a>Działanie > Wyczyśćcollection \<T
 Działanie <xref:System.Activities.Statements.ClearCollection%601> czyści określoną kolekcję wszystkich elementów.

### <a name="using-the-clearcollectiont-activity-designer"></a>Korzystanie z programu ClearCollection \<T > Projektant działań
 **@No__t_1T Wyczyść** projektanta działań > można znaleźć w kategorii **kolekcji** **przybornika**, do którego uzyskuje się dostęp przez kliknięcie karty **przybornika** w [!INCLUDE[wfd2](../includes/wfd2-md.md)] (Alternatywnie wybierz pozycję **pasek narzędzi** z Menu **Widok** lub CTRL + ALT + X.)

 **@No__t_1T Wyczyść** projektanta działań > można przeciągnąć z **przybornika** i porzucić na [!INCLUDE[wfd2](../includes/wfd2-md.md)]ą powierzchnię wszędzie tam, gdzie działania są zwykle umieszczane, na przykład w <xref:System.Activities.Statements.Sequence>. Spowoduje to utworzenie działania <xref:System.Activities.Statements.ClearCollection%601> przy użyciu domyślnego <xref:System.Activities.Activity.DisplayName%2A> \<Int32 ClearCollection >. (Domyślnie *elementu TypeArgument* jest **Int32**. Tę wartość można zmienić w siatce właściwości. Wartość <xref:System.Activities.Activity.DisplayName%2A> można edytować w nagłówku projektanta działania programu **clearcollection \<T >** lub w polu **DisplayName** siatki właściwości. Inne właściwości muszą być edytowane w siatce właściwości.

### <a name="the-clearcollectiont-properties"></a>Właściwości > \<T czyszczenia
 W poniższej tabeli przedstawiono właściwości <xref:System.Activities.Statements.ClearCollection%601> i opisano sposób ich używania w projektancie.

|Nazwa właściwości|Wymagane|Użycie|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Określa opcjonalną przyjazną nazwę działania <xref:System.Activities.Statements.ClearCollection%601>. Wartość domyślna to ClearCollection \<Int32 >. Mimo że wartość <xref:System.Activities.Activity.DisplayName%2A> nie jest ściśle wymagana, najlepszym rozwiązaniem jest użycie jednego z nich.|
|<xref:System.Activities.Statements.ClearCollection%601.Collection%2A>|Oznacza|Określa kolekcję, która ma zostać wyczyszczona elementów. Ta kolekcja jest typu **\<TypeArgument ICollection >.** Aby określić kolekcję, wpisz wyrażenie Visual Basic w siatce właściwości.|
|*Elementu TypeArgument*|Oznacza|Określa typ T elementów zawartych w <xref:System.Collections.Generic.ICollection%601>. Domyślnie ten typ *elementu TypeArgument* jest ustawiony na **Int32**. Aby zmienić typ, Zmień wartość *elementu TypeArgument* w polu kombi w siatce właściwości.|

## <a name="see-also"></a>Zobacz też
 [Kolekcja](../workflow-designer/collection-activity-designers.md) [AddToCollection \<T >](../workflow-designer/addtocollection-t-activity-designer.md) [ExistsInCollection \<T >](../workflow-designer/existsincollection-t-activity-designer.md) [RemoveFromCollection \<T >](../workflow-designer/removefromcollection-t-activity-designer.md)