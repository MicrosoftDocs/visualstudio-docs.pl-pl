---
title: Ostrzeżenia niezawodności
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.reliabilityrules
helpviewer_keywords:
- warnings, reliability
- reliability warnings
- managed code analysis warnings, reliability warnings
ms.assetid: 77886846-10a2-4585-968a-7eb60ebe07e8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3449723394f603b4b726fa8ebf2258e2c8f4c46c
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/23/2020
ms.locfileid: "85283388"
---
# <a name="reliability-warnings"></a>Ostrzeżenia dotyczące niezawodności

Ostrzeżenia o niezawodności obsługują niezawodność biblioteki i aplikacji, takie jak poprawne użycie pamięci i wątku. Reguły niezawodności obejmują:

|Reguła|Opis|
|----------|-----------------|
|[CA2000: Likwiduj obiekty przed utratą zakresu](../code-quality/ca2000.md)|Ze względu na to, że może wystąpić wyjątkowe zdarzenie, które uniemożliwi uruchomienie finalizatora obiektu, obiekty powinny być jawnie usuwane, zanim wszystkie odwołania do niego znajdą się poza zakresem.|
|[CA2001: Unikaj wywoływania problematycznych metod](../code-quality/ca2001.md)|Element członkowski wywołuje potencjalnie niebezpieczną lub problematyczną metodę.|
|[CA2002: Nie blokuj obiektów o słabej tożsamości](../code-quality/ca2002.md)|Obiekt ma słabą tożsamość, gdy można uzyskać do niego bezpośredni dostęp poza granicami domeny aplikacji. Wątek, który próbuje uzyskać blokadę na obiekcie o słabej tożsamości, może zostać zablokowany przez drugi wątek w domenie innej aplikacji, która ma blokady dla tego samego obiektu.|
|[CA2003: Nie traktuj włókien jak wątków](../code-quality/ca2003.md)|Zarządzany wątek jest traktowany jako wątek Win32.|
|[CA2004: Usuń wywołania funkcji GC.KeepAlive](../code-quality/ca2004.md)|W przypadku konwertowania na użycie elementu SafeHandle Usuń wszystkie wywołania do GC. Utrzymywanie aktywności (obiekt). W takim przypadku klasy nie powinny mieć wywołania GC. Utrzymywanie aktywności, przy założeniu, że nie mają finalizatora, ale polega na elemencie SafeHandle, aby sfinalizować dla nich dojście systemu operacyjnego.|
|[CA2006: Używaj klasy SafeHandle w celu hermetyzacji zasobów natywnych](../code-quality/ca2006.md)|Wykorzystanie elementu IntPtr w kodzie zarządzanym może wskazywać na potencjalny problem dotyczący bezpieczeństwa i niezawodności. Wszystkie użycia elementu IntPtr muszą być przejrzane w celu ustalenia, czy użycie elementu SafeHandle lub podobnej technologii jest w tym miejscu wymagane.|
|[CA2007: Nie oczekuj bezpośrednio zadania](../code-quality/ca2007.md)|Metoda asynchroniczna [czeka](/dotnet/csharp/language-reference/keywords/await) <xref:System.Threading.Tasks.Task> bezpośrednio.|
|[CA2009: Nie wywołuj elementu ToImmutableCollection dla wartości ImmutableCollection](../code-quality/ca2009.md)|`ToImmutable`Metoda była niekoniecznie wywoływana w niezmiennej kolekcji z <xref:System.Collections.Immutable> przestrzeni nazw.|
|[CA2011: Nie przypisuj właściwości w ramach jej metody ustawiającej](../code-quality/ca2011.md) | Właściwość przypadkowo przypisała wartość w ramach własnej [metody dostępu set](/dotnet/csharp/programming-guide/classes-and-structs/using-properties#the-set-accessor). |
|[CA2012: Użyj ValueTasks prawidłowo](../code-quality/ca2012.md) | ValueTasks zwracane z wywołań elementów członkowskich są przeznaczone do bezpośredniego oczekiwania.  Próbuje użyć ValueTask wiele razy lub uzyskać bezpośredni dostęp do wyniku, zanim będzie wiadomo, że może to spowodować wyjątek lub uszkodzenie.  Takie ValueTask jest prawdopodobnie oznaką funkcjonalnej usterki i może obniżyć wydajność. |
|[CA2013: nie używaj ReferenceEquals z typami wartości](../code-quality/ca2013.md) | Porównując wartości przy użyciu <xref:System.Object.ReferenceEquals%2A?displayProperty=fullName> , jeśli obja i objB są typami wartości, są one opakowane przed przekazaniem ich do <xref:System.Object.ReferenceEquals%2A> metody. Oznacza to, że nawet jeśli zarówno objA, jak i objB reprezentują to samo wystąpienie typu wartości, <xref:System.Object.ReferenceEquals%2A> Metoda jednak zwróci wartość false. |
|[CA2014: nie używaj stackalloc w pętlach.](../code-quality/ca2014.md) | Przestrzeń stosu przydzielona przez stackalloc jest wydawana tylko na końcu wywołania bieżącej metody.  Użycie jej w pętli może spowodować powstanie nieograniczonego wzrostu stosu i ostateczne warunki przepełnienia stosu. |
|[CA2015: nie Definiuj finalizatorów dla typów pochodzących z Pamięciobject &lt; T&gt;](../code-quality/ca2015.md) | Dodanie finalizatora do typu pochodzącego od <xref:System.Buffers.MemoryManager%601> może pozwolić na zwolnienie pamięci, gdy jest nadal używany przez <xref:System.Span%601> . |
