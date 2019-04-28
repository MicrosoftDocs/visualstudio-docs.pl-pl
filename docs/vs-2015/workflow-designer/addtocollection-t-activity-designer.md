---
title: AddToCollection&lt;T&gt; projektanta działań | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.AddToCollection`1.UI
ms.assetid: f7fc0702-164e-4370-8946-bb2f9f9384b7
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 4e63486ca7e057fdd1bfe0de73e44dc4951462e2
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62977218"
---
# <a name="addtocollectionlttgt-activity-designer"></a>AddToCollection&lt;T&gt; Projektant działań
**AddToCollection\<T >** projektanta działań służy do tworzenia i konfigurowania <xref:System.Activities.Statements.AddToCollection%601> działania.  
  
## <a name="the-addtocollectiont-activity"></a>AddToCollection\<T > działania  
 <xref:System.Activities.Statements.AddToCollection%601> Działania dodaje element do kolekcji.  
  
### <a name="using-the-addtocollectiont-activity-designer"></a>Za pomocą AddToCollection\<T > Projektant działań  
 **AddToCollection\<T >** projektanta działań można znaleźć w **kolekcji** kategorii **przybornika**, które jest dostępne po kliknięciu  **Przybornik** karcie [!INCLUDE[wfd2](../includes/wfd2-md.md)] (można także wybrać **narzędzi** z **widoku** menu lub klawiszy CTRL + ALT + X.)  
  
 **AddToCollection\<T >** projektanta działań mogą być przeciągnięte z **przybornika** i porzuconych do [!INCLUDE[wfd2](../includes/wfd2-md.md)] powierzchni wszędzie tam, gdzie działań są zwyczajowo umieszczane, takie jak wewnątrz <xref:System.Activities.Statements.Sequence>. Spowoduje to utworzenie <xref:System.Activities.Statements.AddToCollection%601> działanie przy użyciu domyślnego <xref:System.Activities.Activity.DisplayName%2A> z AddToCollection\<Int32 >. (Domyślnie *elementu typeargument w języku* jest **Int32**. Można to zmienić w siatce właściwości.) <xref:System.Activities.Activity.DisplayName%2A> Wartość może być edytowana w nagłówku **AddToCollection\<T >** projektanta działań lub **DisplayName** pola siatki właściwości. W siatce właściwości, należy edytować inne właściwości.  
  
### <a name="the-addtocollectiont-properties"></a>AddToCollection\<T > Właściwości  
 W poniższej tabeli przedstawiono <xref:System.Activities.Statements.AddToCollection%601> właściwości i w tym artykule opisano, jak są używane w projektancie.  
  
|Nazwa właściwości|Wymagane|Użycie|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Przyjazna nazwa <xref:System.Activities.Statements.AddToCollection%601> działania. Wartość domyślna to AddToCollection\<Int32 >. Mimo że <xref:System.Activities.Activity.DisplayName%2A> wartość nie jest bezwzględnie konieczne, jest najlepszym rozwiązaniem, aby użyć jednego.|  
|<xref:System.Activities.Statements.AddToCollection%601.Item%2A>|Prawda|Element do dodania do kolekcji\<T >. Ten element jest typu *T*, która jest typu *elementu typeargument w języku*. Aby określić element, wpisz wyrażenie języka Visual Basic w siatce właściwości.|  
|<xref:System.Activities.Statements.AddToCollection%601.Collection%2A>|Prawda|Kolekcja, do którego ma zostać dodany element. Ta kolekcja jest typu **ICollection\<elementu typeargument w języku >**. Aby określić kolekcję, wpisz wyrażenie języka Visual Basic w siatce właściwości.|  
|*TypeArgument*|Prawda|Typu T z elementów znajdujących się w <xref:System.Collections.Generic.ICollection%601>. Domyślnie to *elementu typeargument w języku* ustawiono typ **Int32**. Aby zmienić typ, zmień wartość *elementu typeargument w języku* w polu kombi w siatce właściwości.|  
  
## <a name="see-also"></a>Zobacz też  
 [Kolekcja](../workflow-designer/collection-activity-designers.md)   
 [AddToCollection\<T> Activity Designer](../workflow-designer/addtocollection-t-activity-designer.md)   
 [ClearCollection\<T>](../workflow-designer/clearcollection-t-activity-designer.md)   
 [ExistsInCollection\<T>](../workflow-designer/existsincollection-t-activity-designer.md)   
 [RemoveFromCollection\<T>](../workflow-designer/removefromcollection-t-activity-designer.md)