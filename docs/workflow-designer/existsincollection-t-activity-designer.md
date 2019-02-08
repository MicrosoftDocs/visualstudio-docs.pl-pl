---
title: Projektant przepływu pracy — ExistsInCollection&lt;T&gt; Projektant działań
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.ExistsInCollection`1.UI
ms.assetid: 0acf9a13-caf5-4bb4-ba22-ec37d2b7267a
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 06892bcfdca33e5e77e8c01f06f594849e5293e5
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55909495"
---
# <a name="existsincollectiont-activity-designer"></a>ExistsInCollection\<T > Projektant działań

**ExistsInCollection\<T >** projektanta działań służy do tworzenia i konfigurowania <xref:System.Activities.Statements.ExistsInCollection%601> działania.

## <a name="the-existsincollectiont-activity"></a>ExistsInCollection\<T > działania

<xref:System.Activities.Statements.ExistsInCollection%601> Działania określa, czy określony element istnieje w określonej kolekcji.

### <a name="using-the-existsincollectiont-activity-designer"></a>Za pomocą ExistsInCollection\<T > Projektant działań

**ExistsInCollection\<T >** projektanta działań można znaleźć w **kolekcji** kategorii **przybornika**, które jest dostępne po kliknięciu  **Przybornik** kartę projektanta przepływów pracy. Można także wybrać **przybornika** z **widoku** menu lub naciśnij klawisz **Ctrl**+**Alt** + **X**.

**ExistsInCollection\<T >** projektanta działań mogą być przeciągnięte z **przybornika** i porzucić do powierzchni projektanta przepływów pracy wszędzie tam, gdzie działań są zazwyczaj umieszczane, takie jak wewnątrz <xref:System.Activities.Statements.Sequence>. Spowoduje to utworzenie <xref:System.Activities.Statements.ExistsInCollection%601> działanie przy użyciu domyślnego <xref:System.Activities.Activity.DisplayName%2A> z ExistsInCollection < Int32\>. (Domyślnie *elementu typeargument w języku* jest **Int32**. Można ją zmienić w siatce właściwości.)  <xref:System.Activities.Activity.DisplayName%2A> Wartość może być edytowana w nagłówku **ExistsInCollection < T\>**  projektanta działań lub **DisplayName** pola siatki właściwości. W siatce właściwości, należy edytować inne właściwości.

### <a name="the-existsincollectiont-properties"></a>ExistsInCollection\<T > Właściwości

W poniższej tabeli przedstawiono <xref:System.Activities.Statements.ExistsInCollection%601> właściwości i w tym artykule opisano, jak są używane w Projektancie:

|Nazwa właściwości|Wymagane|Użycie|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Przyjazna nazwa <xref:System.Activities.Statements.ExistsInCollection%601> działania. Wartość domyślna to ExistsInCollection < Int32\>. Mimo że <xref:System.Activities.Activity.DisplayName%2A> wartość nie jest bezwzględnie konieczne, jest najlepszym rozwiązaniem, aby użyć jednego.|
|<xref:System.Activities.Statements.ExistsInCollection%601.Item%2A>|Prawda|Element do wyszukania w kolekcji\<T >. Ten element jest typu *T*, która jest typu *elementu typeargument w języku*. Aby określić element, wpisz wyrażenie języka Visual Basic w siatce właściwości.|
|<xref:System.Activities.Statements.ExistsInCollection%601.Collection%2A>|Prawda|Kolekcja, w którym ma zostać sprawdzona, jeśli element nie istnieje. Ta kolekcja jest typu **ICollection < elementu typeargument w języku\>.** Aby określić kolekcję, wpisz wyrażenie języka Visual Basic w siatce właściwości.|
|*TypeArgument*|Prawda|Typu T z elementów znajdujących się w <xref:System.Collections.Generic.ICollection%601>. Domyślnie to *elementu typeargument w języku* ustawiono typ **Int32**. Aby zmienić typ, zmień wartość *elementu typeargument w języku* w polu kombi w siatce właściwości.|
|<xref:System.Activities.Activity%601.Result%2A>|False|Wartość, która wskazuje, czy określony element istnieje w kolekcji. Aby określić zmienną, aby powiązać wynik, typ zmiennej języka Visual Basic w siatce właściwości.|

## <a name="see-also"></a>Zobacz także

- [Kolekcja](../workflow-designer/collection-activity-designers.md)
- [AddToCollection\<T>](../workflow-designer/addtocollection-t-activity-designer.md)
- [ClearCollection\<T >](../workflow-designer/clearcollection-t-activity-designer.md)
- [RemoveFromCollection\<T>](../workflow-designer/removefromcollection-t-activity-designer.md)