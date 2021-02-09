---
title: Gdy punkt przerwania jest aktywny okno dialogowe | Microsoft Docs
description: Użyj po trafieniu punktu przerwania, aby określić akcję podczas dzielenia. Można określić, że będzie drukowany komunikat, a wykonywanie powinno być kontynuowane.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: bfb5099bd0fab17cd983af4e16a435fd192a1668
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99883873"
---
# <a name="when-breakpoint-is-hit-dialog-box"></a>Okno dialogowe wyświetlane po osiągnięciu punktu przerwania
Za pomocą tego okna dialogowego można dostosować akcję wykonywaną po trafieniu punktu przerwania.

## <a name="uielement-list"></a>Lista elementów UI
 **Drukuj komunikat** Drukuje komunikat przy użyciu składni DebuggerDisplay. Aby uzyskać więcej informacji, zobacz [Korzystanie z atrybutu DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md).

 To pole tekstowe obsługuje również specjalne słowa kluczowe (takie jak $ADDRESS), które mogą być używane przez siebie lub w nawiasach klamrowych wyrażenia DebuggerDisplay. Dostępne słowa kluczowe są wyświetlane w oknie dialogowym.

 **Kontynuuj wykonywanie** Ten formant jest włączony tylko w przypadku wybrania **drukowania wiadomości** . Po wybraniu tej kontrolki punkt przerwania można użyć jako punkt śledzenia, aby śledzić wykonywanie programu, a nie przerywać się podczas trafiania lokalizacji.

## <a name="see-also"></a>Zobacz też
- [Używanie punktów przerwania](../debugger/using-breakpoints.md)
- [Używanie atrybutu DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md)