---
title: Punkty przerwania (zestaw SDK programu Visual Studio) | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- breakpoints
ms.assetid: acfcabed-9f2f-436c-ad18-7ca2f45d631b
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 39c13271bad984291f609ef45505549855bee99f
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54796147"
---
# <a name="breakpoints-visual-studio-sdk"></a>Punkty przerwania (zestaw SDK programu Visual Studio)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Istnieją trzy typy punktów przerwania: Oczekujące, powiązaną i błędów.  
  
 **A oczekujących punktów przerwania:**  
  
- Jest klasą abstrakcyjną, która zawiera wszystkie informacje potrzebne, aby powiązać punkt przerwania z co najmniej jeden kontekst kodu w jednym lub wielu programów. Za każdym razem program debugowany kod przyczyny, aby załadować, aparat debugowania sprawdza wszystkich oczekujących punktów przerwania, aby zobaczyć, jeśli może być powiązana.  
  
   Oczekujący punkt przerwania, sama nigdy nie wiąże się kod, ale raczej zbiera i jest nazywany ma zawierać wszystkie powiązane punkty przerwania, które generuje.  
  
- Jest reprezentowany przez [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) interfejsu.  
  
  **Powiązany punkt przerwania:**  
  
- Jest skojarzony z klasą abstrakcyjną dla punktu przerwania lub powiązany z kontekstu pojedynczego kodu. Każdy powiązany punkt przerwania jest generowany w odpowiedzi na oczekujący punkt przerwania. Oczekujący punkt przerwania, można wygenerować więcej niż jeden powiązany punkt przerwania.  
  
   Gdy kod jest zwolniony, powiązany punkt przerwania można niepowiązanych i odrzucone.  
  
- Jest reprezentowany przez [IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md) interfejsu.  
  
  **Punkt przerwania błąd:**  
  
- Jest klasą abstrakcyjną dla opisujący błąd podczas próby powiązać oczekujący punkt przerwania kontekst kodu. Błąd punktu przerwania w tym artykule opisano albo błąd w lokalizacji lub wyrażenia punktu przerwania. Aby uzyskać więcej informacji, zobacz [powiązań punktów przerwania](../../extensibility/debugger/binding-breakpoints.md).  
  
   Błąd punktu przerwania, może być błąd lub ostrzeżenie.  
  
- Jest reprezentowany przez [IDebugErrorBreakpoint2](../../extensibility/debugger/reference/idebugerrorbreakpoint2.md) interfejsu.  
  
## <a name="see-also"></a>Zobacz też  
 [Programy](../../extensibility/debugger/programs.md)   
 [Pojęcia dotyczące debugera](../../extensibility/debugger/debugger-concepts.md)   
 [Kontekst kodu](../../extensibility/debugger/code-context.md)   
 [IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md)   
 [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)   
 [IDebugErrorBreakpoint2](../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)
