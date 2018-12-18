---
title: Gdy punkt przerwania jest okno dialogowe trafień | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
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
manager: ghogen
ms.openlocfilehash: ad979fa302a29f9d444579655e368db6da8b3e1f
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51805414"
---
# <a name="when-breakpoint-is-hit-dialog-box"></a>Okno dialogowe wyświetlane po osiągnięciu punktu przerwania
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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



