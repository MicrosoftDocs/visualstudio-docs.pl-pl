---
title: .NET Kompilator&quot;Platform&quot;( Roslyn ) Rozszerzalność | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 564201b3-1e18-4b88-b615-42c2f57f3fe8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 62ceac6e2be8a0a84d82f6b86b685c7c8b20a182
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712076"
---
# <a name="net-compiler-platform-quotroslynquot-extensibility"></a>Rozszerzalność platformy&quot;kompilatora .NET (Roslyn)&quot;
Podstawową misją platformy kompilatora .NET ("Roslyn") jest otwarcie kompilatorów języka C# i Visual Basic oraz umożliwienie narzędziom i deweloperom udostępniania w programach kompilatorów informacji o bogatych informacjach. Narzędzia do analizy kodu poprawiają jakość kodu, a generatory kodu pomagają w budowie aplikacji. Jak narzędzia stają się inteligentniejsze, potrzebują dostępu do coraz więcej wiedzy głębokiego kodu, które posiadają tylko kompilatory. Zamiast być nieprzezroczyste tłumacze (kod źródłowy i kod obiektu out), kompilatory Roslyn oferują interfejsy API, które można użyć do zadań związanych z kodem w narzędziach i aplikacjach.

 Najlepsze jest to, że kompilatory Roslyn, ich interfejsy API, przykłady i instruktaże oraz prawdziwe narzędzia zbudowane na tych interfejsach API są w pełni otwarte w [github.com/dotnet/roslyn](https://github.com/dotnet/Roslyn). Przejdź do witryny OSS, aby dowiedzieć się więcej i zacząć z Roslyn. Znajdziesz łącza, aby uzyskać najnowsze funkcje Języka C# i Visual Basic, które można użyć jako użytkownik końcowy, a także łącza, aby rozpocząć pracę jako kreator narzędzi wykorzystujących interfejsy API Roslyn.

## <a name="see-also"></a>Zobacz też
- [Wprowadzenie do analizatorów Roslyn](../extensibility/getting-started-with-roslyn-analyzers.md)
