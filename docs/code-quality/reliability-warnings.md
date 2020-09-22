---
title: Reguły niezawodności
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.reliabilityrules
helpviewer_keywords:
- rules, reliability
- reliability rules
- managed code analysis rules, reliability rules
ms.assetid: 77886846-10a2-4585-968a-7eb60ebe07e8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e0a35b9c49f2eb5655eeb67721b0fafdbbe1e087
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2020
ms.locfileid: "90808275"
---
# <a name="reliability-rules"></a>Reguły niezawodności

Reguły niezawodności obsługują niezawodność biblioteki i aplikacji, takie jak poprawne użycie pamięci i wątku.

|Reguła|Opis|
|----------|-----------------|
|[CA2000: Likwiduj obiekty przed utratą zakresu](../code-quality/ca2000.md)|Ze względu na to, że może wystąpić wyjątkowe zdarzenie, które uniemożliwi uruchomienie finalizatora obiektu, obiekty powinny być jawnie usuwane, zanim wszystkie odwołania do niego znajdą się poza zakresem.|
|[CA2002: Nie blokuj obiektów o słabej tożsamości](../code-quality/ca2002.md)|Obiekt ma słabą tożsamość, gdy można uzyskać do niego bezpośredni dostęp poza granicami domeny aplikacji. Wątek, który próbuje uzyskać blokadę na obiekcie o słabej tożsamości, może zostać zablokowany przez drugi wątek w domenie innej aplikacji, która ma blokady dla tego samego obiektu.|
|[CA2007: Nie oczekuj bezpośrednio zadania](../code-quality/ca2007.md)|Metoda asynchroniczna [czeka](/dotnet/csharp/language-reference/keywords/await) <xref:System.Threading.Tasks.Task> bezpośrednio.|
|[CA2008: Nie twórz zadań bez przekazania klasy TaskScheduler](../code-quality/ca2008.md)|Operacja tworzenia lub kontynuacji zadania używa przeciążenia metody, które nie określa <xref:System.Threading.Tasks.TaskScheduler> parametru.|
|[CA2009: Nie wywołuj elementu ToImmutableCollection dla wartości ImmutableCollection](../code-quality/ca2009.md)|`ToImmutable` Metoda była niekoniecznie wywoływana w niezmiennej kolekcji z <xref:System.Collections.Immutable> przestrzeni nazw.|
|[CA2011: Nie przypisuj właściwości w ramach jej metody ustawiającej](../code-quality/ca2011.md) | Właściwość przypadkowo przypisała wartość w ramach własnej [metody dostępu set](/dotnet/csharp/programming-guide/classes-and-structs/using-properties#the-set-accessor). |
|[CA2012: Poprawnie używaj elementów ValueTask](../code-quality/ca2012.md) | ValueTasks zwracane z wywołań elementów członkowskich są przeznaczone do bezpośredniego oczekiwania.  Próbuje użyć ValueTask wiele razy lub uzyskać bezpośredni dostęp do wyniku, zanim będzie wiadomo, że może to spowodować wyjątek lub uszkodzenie.  Takie ValueTask jest prawdopodobnie oznaką funkcjonalnej usterki i może obniżyć wydajność. |
|[CA2013: Nie używaj metody ReferenceEquals z typami wartości](../code-quality/ca2013.md) | Porównując wartości przy użyciu <xref:System.Object.ReferenceEquals%2A?displayProperty=fullName> , jeśli obja i objB są typami wartości, są one opakowane przed przekazaniem ich do <xref:System.Object.ReferenceEquals%2A> metody. Oznacza to, że nawet jeśli zarówno objA, jak i objB reprezentują to samo wystąpienie typu wartości, <xref:System.Object.ReferenceEquals%2A> Metoda jednak zwróci wartość false. |
|[CA2014: nie używaj stackalloc w pętlach.](../code-quality/ca2014.md) | Przestrzeń stosu przydzielona przez stackalloc jest wydawana tylko na końcu wywołania bieżącej metody.  Użycie jej w pętli może spowodować powstanie nieograniczonego wzrostu stosu i ostateczne warunki przepełnienia stosu. |
|[CA2015: nie Definiuj finalizatorów dla typów pochodzących z Pamięciobject &lt; T&gt;](../code-quality/ca2015.md) | Dodanie finalizatora do typu pochodzącego od <xref:System.Buffers.MemoryManager%601> może pozwolić na zwolnienie pamięci, gdy jest nadal używany przez <xref:System.Span%601> . |
|[CA2016: Prześlij dalej parametr CancellationToken do metod, które go przyjmują](ca2016.md) | Przekaż `CancellationToken` parametr do metod, które przyjmują w celu zapewnienia, że powiadomienia o anulowaniu operacji są prawidłowo propagowane, lub Przekaż `CancellationToken.None` jawnie, aby wskazać celowo niepropagowanie tokenu. |
