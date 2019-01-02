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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 560a79892ee50f3d151971f46bcc2c2b7f205d3f
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53845619"
---
# <a name="when-breakpoint-is-hit-dialog-box"></a>Okno dialogowe wyświetlane po osiągnięciu punktu przerwania
Z tego okna dialogowego, można dostosować akcję wykonywaną po trafieniu punktu przerwania.  
  
## <a name="uielement-list"></a>Lista elementów UI  
 **Wydrukuj komunikat**  
 Drukuje wiadomość, używając składni DebuggerDisplay. Aby uzyskać więcej informacji, zobacz [korzystanie z atrybutu DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md).  
  
 To pole tekstowe obsługuje także słowa kluczowe (takie jak $ADDRESS), które mogą być używane samodzielnie lub w obrębie nawiasów klamrowych DebuggerDisplay wyrażenia. Dostępne słowa kluczowe są wyświetlane w oknie dialogowym.  
  
 **Kontynuuj wykonywanie**  
 Ta kontrolka jest włączona tylko wtedy, gdy **wydrukuj komunikat** jest zaznaczone. Ten formant jest zaznaczony punkt przerwania można użyć jako punkt śledzenia, śledzenie wykonywania programu, zamiast przerywanie, gdy zostanie osiągnięty jako lokalizację.  
  
## <a name="see-also"></a>Zobacz też  
 [Używanie punktów przerwania](../debugger/using-breakpoints.md)   
 [Używanie atrybutu DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md)