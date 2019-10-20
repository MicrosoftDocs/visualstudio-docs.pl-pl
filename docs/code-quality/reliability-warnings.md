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
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 602f372e11c4a9a8506186535958fc4f22da7806
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72649113"
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
|[CA2007: nie należy bezpośrednio czekać na zadanie](../code-quality/ca2007.md)|Metoda asynchroniczna [czeka](/dotnet/csharp/language-reference/keywords/await) bezpośrednio na <xref:System.Threading.Tasks.Task>.|
