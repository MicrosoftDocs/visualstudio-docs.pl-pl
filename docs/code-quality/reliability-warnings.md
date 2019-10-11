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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cb39bb5f59373f52d77c7cc5d13d12544d4c0314
ms.sourcegitcommit: 3e94d9fb6dc56fa8b23fbacd5d11cf8d6e7e18f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/10/2019
ms.locfileid: "72252584"
---
# <a name="reliability-warnings"></a>Ostrzeżenia dotyczące niezawodności

Ostrzeżenia o niezawodności obsługują niezawodność biblioteki i aplikacji, takie jak poprawne użycie pamięci i wątku. Reguły niezawodności obejmują:

|Reguła|Opis|
|----------|-----------------|
|[CA2000: Usuń obiekty przed utratą zakresu @ no__t-0|Ze względu na to, że może wystąpić wyjątkowe zdarzenie, które uniemożliwi uruchomienie finalizatora obiektu, obiekty powinny być jawnie usuwane, zanim wszystkie odwołania do niego znajdą się poza zakresem.|
|[CA2001: Unikaj wywoływania problematycznych metod @ no__t-0|Element członkowski wywołuje potencjalnie niebezpieczną lub problematyczną metodę.|
|[CA2002: Nie blokuj obiektów o słabej tożsamości @ no__t-0|Obiekt ma słabą tożsamość, gdy można uzyskać do niego bezpośredni dostęp poza granicami domeny aplikacji. Wątek, który próbuje uzyskać blokadę na obiekcie o słabej tożsamości, może zostać zablokowany przez drugi wątek w domenie innej aplikacji, która ma blokady dla tego samego obiektu.|
|[CA2003: Nie Traktuj włókien jako wątków @ no__t-0|Zarządzany wątek jest traktowany jako wątek Win32.|
|[CA2004: Usuń wywołania do GC. Utrzymywanie aktywności przez no__t-0|W przypadku konwertowania na użycie elementu SafeHandle Usuń wszystkie wywołania do GC. Utrzymywanie aktywności (obiekt). W takim przypadku klasy nie powinny mieć wywołania GC. Utrzymywanie aktywności, przy założeniu, że nie mają finalizatora, ale polega na elemencie SafeHandle, aby sfinalizować dla nich dojście systemu operacyjnego.|
|[CA2006: Używanie elementu SafeHandle do hermetyzacji zasobów natywnych @ no__t-0|Wykorzystanie elementu IntPtr w kodzie zarządzanym może wskazywać na potencjalny problem dotyczący bezpieczeństwa i niezawodności. Wszystkie użycia elementu IntPtr muszą być przejrzane w celu ustalenia, czy użycie elementu SafeHandle lub podobnej technologii jest w tym miejscu wymagane.|
|[CA2007: Nie należy bezpośrednio czekać na zadanie @ no__t-0|Metoda asynchroniczna [czeka](/dotnet/csharp/language-reference/keywords/await) bezpośrednio na <xref:System.Threading.Tasks.Task>.|
