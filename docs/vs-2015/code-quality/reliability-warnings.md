---
title: Ostrzeżenia dotyczące niezawodności | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.reliabilityrules
helpviewer_keywords:
- warnings, reliability
- reliability warnings
- managed code analysis warnings, reliability warnings
ms.assetid: 77886846-10a2-4585-968a-7eb60ebe07e8
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 250eb10581858534ec6325a1bfb61d84bddac05a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72603972"
---
# <a name="reliability-warnings"></a>Ostrzeżenia niezawodności
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ostrzeżenia o niezawodności obsługują niezawodność biblioteki i aplikacji, takie jak poprawne użycie pamięci i wątku.

## <a name="in-this-section"></a>W tej sekcji

|Reguła|Opis|
|----------|-----------------|
|[CA2000: Likwiduj obiekty przed utratą zakresu](../code-quality/ca2000-dispose-objects-before-losing-scope.md)|Ze względu na to, że może wystąpić wyjątkowe zdarzenie, które uniemożliwi uruchomienie finalizatora obiektu, obiekty powinny być jawnie usuwane, zanim wszystkie odwołania do niego znajdą się poza zakresem.|
|[CA2001: Unikaj wywoływania problematycznych metod](../code-quality/ca2001-avoid-calling-problematic-methods.md)|Element członkowski wywołuje potencjalnie niebezpieczną lub problematyczną metodę.|
|[CA2002: Nie blokuj obiektów o słabej tożsamości](../code-quality/ca2002-do-not-lock-on-objects-with-weak-identity.md)|Obiekt ma słabą tożsamość, gdy można uzyskać do niego bezpośredni dostęp poza granicami domeny aplikacji. Wątek, który próbuje uzyskać blokadę na obiekcie o słabej tożsamości, może zostać zablokowany przez drugi wątek w domenie innej aplikacji, która ma blokady dla tego samego obiektu.|
|[CA2003: Nie traktuj włókien jak wątków](../code-quality/ca2003-do-not-treat-fibers-as-threads.md)|Zarządzany wątek jest traktowany jako wątek Win32.|
|[CA2004: Usuń wywołania funkcji GC.KeepAlive](../code-quality/ca2004-remove-calls-to-gc-keepalive.md)|W przypadku konwertowania na użycie elementu SafeHandle Usuń wszystkie wywołania do GC. Utrzymywanie aktywności (obiekt). W takim przypadku klasy nie powinny mieć wywołania GC. Utrzymywanie aktywności, przy założeniu, że nie mają finalizatora, ale polega na elemencie SafeHandle, aby sfinalizować dla nich dojście systemu operacyjnego.|
|[CA2006: Używaj klasy SafeHandle w celu hermetyzacji zasobów natywnych](../code-quality/ca2006-use-safehandle-to-encapsulate-native-resources.md)|Wykorzystanie elementu IntPtr w kodzie zarządzanym może wskazywać na potencjalny problem dotyczący bezpieczeństwa i niezawodności. Wszystkie użycia elementu IntPtr muszą być przejrzane w celu ustalenia, czy użycie elementu SafeHandle lub podobnej technologii jest w tym miejscu wymagane.|
