---
title: Wyczyść projektanta działań w programiecollection &lt; T &gt; | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72657022"
---
# <a name="clearcollectionlttgt-activity-designer"></a>Wyczyść &lt; &gt; projektanta działań w programiecollection T
Projektant działań **ClearCollection \<T> ** służy do tworzenia i konfigurowania <xref:System.Activities.Statements.ClearCollection%601> działania.

## <a name="the-clearcollectiont-activity"></a>Działanie ClearCollection \<T>
 <xref:System.Activities.Statements.ClearCollection%601>Działanie czyści określoną kolekcję wszystkich elementów.

### <a name="using-the-clearcollectiont-activity-designer"></a>Korzystanie z \<T> projektanta działania ClearCollection
 Projektant **działań ClearCollection \<T> ** można znaleźć w kategorii **kolekcji** **przybornika**, do którego uzyskuje się dostęp, klikając kartę **przybornika** [!INCLUDE[wfd2](../includes/wfd2-md.md)] (Alternatywnie wybierz **pasek narzędzi** z menu **Widok** lub CTRL + ALT + X).

 Projektant działań **ClearCollection \<T> ** można przeciągać z **przybornika** i znajdować się na [!INCLUDE[wfd2](../includes/wfd2-md.md)] powierzchni, wszędzie tam, gdzie działania są zwykle umieszczane, na przykład wewnątrz <xref:System.Activities.Statements.Sequence> . Spowoduje to utworzenie <xref:System.Activities.Statements.ClearCollection%601> działania z wartością domyślną <xref:System.Activities.Activity.DisplayName%2A> ClearCollection \<Int32> . (Domyślnie *elementu TypeArgument* jest **Int32**. Tę wartość można zmienić w siatce właściwości. <xref:System.Activities.Activity.DisplayName%2A>Wartość można edytować w nagłówku projektanta działań **ClearCollection \<T> ** lub w polu **DisplayName** siatki właściwości. Inne właściwości muszą być edytowane w siatce właściwości.

### <a name="the-clearcollectiont-properties"></a>Właściwości ClearCollection \<T>
 W poniższej tabeli przedstawiono <xref:System.Activities.Statements.ClearCollection%601> właściwości i opisano sposób ich użycia w projektancie.

|Nazwa właściwości|Wymagany|Użycie|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|Fałsz|Określa opcjonalną przyjazną nazwę <xref:System.Activities.Statements.ClearCollection%601> działania. Wartość domyślna to ClearCollection \<Int32> . Chociaż <xref:System.Activities.Activity.DisplayName%2A> wartość nie jest ściśle wymagana, najlepszym rozwiązaniem jest użycie jednego z nich.|
|<xref:System.Activities.Statements.ClearCollection%601.Collection%2A>|Prawda|Określa kolekcję, która ma zostać wyczyszczona elementów. Ta kolekcja jest typu **ICollection \<TypeArgument> .** Aby określić kolekcję, wpisz wyrażenie Visual Basic w siatce właściwości.|
|*Elementu TypeArgument*|Prawda|Określa typ T elementów zawartych w <xref:System.Collections.Generic.ICollection%601> . Domyślnie ten typ *elementu TypeArgument* jest ustawiony na **Int32**. Aby zmienić typ, Zmień wartość *elementu TypeArgument* w polu kombi w siatce właściwości.|

## <a name="see-also"></a>Zobacz też
 [Kolekcja](../workflow-designer/collection-activity-designers.md) [AddToCollection \<T> ](../workflow-designer/addtocollection-t-activity-designer.md) [ExistsInCollection \<T> ](../workflow-designer/existsincollection-t-activity-designer.md) [RemoveFromCollection \<T> ](../workflow-designer/removefromcollection-t-activity-designer.md)