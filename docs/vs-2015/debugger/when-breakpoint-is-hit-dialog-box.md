---
title: Gdy punkt przerwania jest aktywny okno dialogowe | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.whenbreakpointishit
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- SQL
- VB
- CSharp
- C++
ms.assetid: 476e3d98-cf35-4338-b124-cd0f3010d854
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9a7cd140a22c435df0875c089a69476d3e1e61cf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68149411"
---
# <a name="when-breakpoint-is-hit-dialog-box"></a>Okno dialogowe wyświetlane po osiągnięciu punktu przerwania
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Za pomocą tego okna dialogowego można dostosować akcję wykonywaną po trafieniu punktu przerwania.  
  
## <a name="uielement-list"></a>Lista elementów UI  
 **Drukuj komunikat**  
 Drukuje komunikat przy użyciu składni DebuggerDisplay. Aby uzyskać więcej informacji, zobacz [Korzystanie z atrybutu DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md).  
  
 To pole tekstowe obsługuje również specjalne słowa kluczowe (takie jak $ADDRESS), które mogą być używane przez siebie lub w nawiasach klamrowych wyrażenia DebuggerDisplay. Dostępne słowa kluczowe są wyświetlane w oknie dialogowym.  
  
 **Kontynuuj wykonywanie**  
 Ten formant jest włączony tylko w przypadku wybrania **drukowania wiadomości** . Po wybraniu tej kontrolki punkt przerwania można użyć jako punkt śledzenia, aby śledzić wykonywanie programu, a nie przerywać się podczas trafiania lokalizacji.  
  
## <a name="see-also"></a>Zobacz też  
 [Używanie punktów przerwania](../debugger/using-breakpoints.md)   
 [Używanie atrybutu DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md)
