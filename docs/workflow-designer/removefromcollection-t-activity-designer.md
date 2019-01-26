---
title: Projektant przepływu pracy — RemoveFromCollection&lt;T&gt; Projektant działań
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
f1_keywords:
- System.Activities.Statements.RemoveFromCollection`1.UI
ms.assetid: 6617ba26-c8bc-4aed-b746-112bf490d288
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6105668b8511d340200e13c191c532c8743a0b0d
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54940092"
---
# <a name="removefromcollectiont-activity-designer"></a>RemoveFromCollection\<T > Projektant działań

**RemoveFromCollection\<T >** projektanta działań służy do tworzenia i konfigurowania <xref:System.Activities.Statements.RemoveFromCollection%601> działania.

## <a name="the-removefromcollectiontactivity"></a>RemoveFromCollection\<T > działania

<xref:System.Activities.Statements.RemoveFromCollection%601> Działanie usuwa określony element z określonej kolekcji.

### <a name="using-the-removefromcollectiont-activity-designer"></a>Za pomocą RemoveFromCollection\<T > Projektant działań

Dostęp do **RemoveFromCollection\<T >** projektanta działań w **kolekcji** kategorii **przybornika**.
**RemoveFromCollection\<T >** projektanta działań mogą być przeciągnięte z **przybornika** i porzucić do powierzchni projektanta przepływów pracy wszędzie tam, gdzie działań są zwyczajowo umieszczane, takich jak wewnątrz <xref:System.Activities.Statements.Sequence>. Spowoduje to utworzenie <xref:System.Activities.Statements.RemoveFromCollection%601> działanie przy użyciu domyślnego <xref:System.Activities.Activity.DisplayName%2A> z RemoveFromCollection < Int32\>. <xref:System.Activities.Activity.DisplayName%2A> Wartość może być edytowana w nagłówku **RemoveFromCollection < T\>**  projektanta działań lub **DisplayName** pola siatki właściwości. W siatce właściwości, należy edytować inne właściwości.

### <a name="the-removefromcollectiont-properties"></a>RemoveFromCollection < T\> właściwości

W poniższej tabeli przedstawiono <xref:System.Activities.Statements.RemoveFromCollection%601> właściwości i w tym artykule opisano, jak są używane w Projektancie:

|Nazwa właściwości|Wymagane|Użycie|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Opcjonalna nazwa przyjazna <xref:System.Activities.Statements.RemoveFromCollection%601> działania. Wartość domyślna to RemoveFromCollection < Int32\>.<br /><br /> Mimo że <xref:System.Activities.Activity.DisplayName%2A> nie jest bezwzględnie konieczne jest najlepszym rozwiązaniem, aby użyć jednego.|
|<xref:System.Activities.Statements.RemoveFromCollection%601.Item%2A>|Prawda|Element do usunięcia z **kolekcji\<T >**. Ten element jest typu *T*, która jest typu *elementu typeargument w języku*. Aby określić element, wpisz wyrażenie języka Visual Basic w siatce właściwości.|
|<xref:System.Activities.Statements.RemoveFromCollection%601.Collection%2A>|Prawda|Kolekcja, z którego można usunąć elementu. Ta kolekcja jest typu **ICollection < elementu typeargument w języku\>.** Aby określić kolekcję, wpisz wyrażenie języka Visual Basic w siatce właściwości.|
|*TypeArgument*|Prawda|Typu T z elementów znajdujących się w <xref:System.Collections.Generic.ICollection%601>. Domyślnie to *elementu typeargument w języku* ustawiono typ **Int32**. Aby zmienić typ, zmień wartość *elementu typeargument w języku* w polu kombi w siatce właściwości.|
|<xref:System.Activities.Activity%601.Result%2A>|False|Wartość, która wskazuje, czy określony element został usunięty z kolekcji. Aby określić zmienną, aby powiązać wynik, wpisz w zmiennej w siatce właściwości|

## <a name="see-also"></a>Zobacz także

- [Kolekcja](../workflow-designer/collection-activity-designers.md)
- [AddToCollection\<T>](../workflow-designer/addtocollection-t-activity-designer.md)
- [ClearCollection\<T >](../workflow-designer/clearcollection-t-activity-designer.md)
- [ExistsInCollection\<T >](../workflow-designer/existsincollection-t-activity-designer.md)