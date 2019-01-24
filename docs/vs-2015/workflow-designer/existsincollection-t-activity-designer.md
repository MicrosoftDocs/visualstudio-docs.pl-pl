---
title: ExistsInCollection&lt;T&gt; projektanta działań | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.ExistsInCollection`1.UI
ms.assetid: 0acf9a13-caf5-4bb4-ba22-ec37d2b7267a
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 263bbf16c72bab5a42dc0ba1465d4c7062333071
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54771215"
---
# <a name="existsincollectionlttgt-activity-designer"></a>ExistsInCollection&lt;T&gt; Projektant działań
**ExistsInCollection\<T >** projektanta działań służy do tworzenia i konfigurowania <xref:System.Activities.Statements.ExistsInCollection%601> działania.  
  
## <a name="the-existsincollectiont-activity"></a>ExistsInCollection\<T > działania  
 <xref:System.Activities.Statements.ExistsInCollection%601> Działania określa, czy określony element istnieje w określonej kolekcji.  
  
### <a name="using-the-existsincollectiont-activity-designer"></a>Za pomocą ExistsInCollection\<T > Projektant działań  
 **ExistsInCollection\<T >** projektanta działań można znaleźć w **kolekcji** kategorii **przybornika**, które jest dostępne po kliknięciu  **Przybornik** karcie [!INCLUDE[wfd2](../includes/wfd2-md.md)] (można także wybrać **narzędzi** z **widoku** menu lub klawiszy CTRL + ALT + X.)  
  
 **ExistsInCollection\<T >** projektanta działań mogą być przeciągnięte z **przybornika** i porzuconych do [!INCLUDE[wfd2](../includes/wfd2-md.md)] powierzchni wszędzie tam, gdzie działań są zazwyczaj umieszczane, takich jak wewnątrz <xref:System.Activities.Statements.Sequence>. Spowoduje to utworzenie <xref:System.Activities.Statements.ExistsInCollection%601> działanie przy użyciu domyślnego <xref:System.Activities.Activity.DisplayName%2A> z ExistsInCollection\<Int32 >. (Domyślnie *elementu typeargument w języku* jest **Int32**. Można ją zmienić w siatce właściwości.)  <xref:System.Activities.Activity.DisplayName%2A> Wartość może być edytowana w nagłówku **ExistsInCollection\<T >** projektanta działań lub **DisplayName** pola siatki właściwości. W siatce właściwości, należy edytować inne właściwości.  
  
### <a name="the-existsincollectiont-properties"></a>ExistsInCollection\<T > Właściwości  
 W poniższej tabeli przedstawiono <xref:System.Activities.Statements.ExistsInCollection%601> właściwości i w tym artykule opisano, jak są używane w projektancie.  
  
|Nazwa właściwości|Wymagane|Użycie|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Przyjazna nazwa <xref:System.Activities.Statements.ExistsInCollection%601> działania. Wartość domyślna to ExistsInCollection\<Int32 >. Mimo że <xref:System.Activities.Activity.DisplayName%2A> wartość nie jest bezwzględnie konieczne, jest najlepszym rozwiązaniem, aby użyć jednego.|  
|<xref:System.Activities.Statements.ExistsInCollection%601.Item%2A>|Prawda|Element do dodania do kolekcji\<T >. Ten element jest typu *T* typu *elementu typeargument w języku*. Aby określić element, wpisz wyrażenie języka Visual Basic w siatce właściwości.|  
|<xref:System.Activities.Statements.ExistsInCollection%601.Collection%2A>|Prawda|Kolekcja, do którego ma zostać dodany element. Ta kolekcja jest typu **ICollection\<elementu typeargument w języku >.** Aby określić kolekcję, wpisz wyrażenie języka Visual Basic w siatce właściwości.|  
|*TypeArgument*|Prawda|Typu T z elementów znajdujących się w <xref:System.Collections.Generic.ICollection%601>. Domyślnie to *elementu typeargument w języku* ustawiono typ **Int32**. Aby zmienić typ, zmień wartość *elementu typeargument w języku* w polu kombi w siatce właściwości.|  
|<xref:System.Activities.Activity%601.Result%2A>|False|Wartość, która wskazuje, czy określony element istnieje w kolekcji. Aby określić zmienną, aby powiązać wynik, typ zmiennej języka Visual Basic w siatce właściwości.|  
  
## <a name="see-also"></a>Zobacz też  
 [Kolekcja](../workflow-designer/collection-activity-designers.md)   
 [AddToCollection\<T>](../workflow-designer/addtocollection-t-activity-designer.md)   
 [ClearCollection\<T>](../workflow-designer/clearcollection-t-activity-designer.md)   
 [RemoveFromCollection\<T>](../workflow-designer/removefromcollection-t-activity-designer.md)