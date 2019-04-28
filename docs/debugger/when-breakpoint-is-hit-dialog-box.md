---
title: Gdy punkt przerwania jest okno dialogowe trafień | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.debug.whenbreakpointishit
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
- SQL
ms.assetid: 476e3d98-cf35-4338-b124-cd0f3010d854
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d4cc3c2366ca20328f591b0661e8c2b3e5af1e45
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62929204"
---
# <a name="when-breakpoint-is-hit-dialog-box"></a>Okno dialogowe wyświetlane po osiągnięciu punktu przerwania
Z tego okna dialogowego, można dostosować akcję wykonywaną po trafieniu punktu przerwania.

## <a name="uielement-list"></a>Lista elementów UI
 **Wydrukuj komunikat** drukuje wiadomość, używając składni DebuggerDisplay. Aby uzyskać więcej informacji, zobacz [korzystanie z atrybutu DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md).

 To pole tekstowe obsługuje także słowa kluczowe (takie jak $ADDRESS), które mogą być używane samodzielnie lub w obrębie nawiasów klamrowych DebuggerDisplay wyrażenia. Dostępne słowa kluczowe są wyświetlane w oknie dialogowym.

 **Kontynuuj wykonywanie** ta kontrolka jest włączona tylko wtedy, gdy **wydrukuj komunikat** jest zaznaczone. Ten formant jest zaznaczony punkt przerwania można użyć jako punkt śledzenia, śledzenie wykonywania programu, zamiast przerywanie, gdy zostanie osiągnięty jako lokalizację.

## <a name="see-also"></a>Zobacz też
- [Używanie punktów przerwania](../debugger/using-breakpoints.md)
- [Używanie atrybutu DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md)