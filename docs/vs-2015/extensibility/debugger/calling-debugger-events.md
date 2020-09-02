---
title: Wywoływanie zdarzeń debugera | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], events
ms.assetid: b3440ac3-80af-40c6-bef4-cbf00fa67885
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2f162affe2324afaa8fb1d506c3177311386bfc1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68146402"
---
# <a name="calling-debugger-events"></a>Wywoływanie zdarzeń debugera
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Zdarzenia w debugowaniu sesji odbywają się w określonej kolejności.  
  
## <a name="discussion"></a>Dyskusja  
 Aby zrozumieć wzorzec wywołań między aparatem debugowania (DE) i menedżerem debugowania sesji (SDM), poniżej przedstawiono kolejność wywoływania zdarzeń występujących w typowej sesji debugowania:  
  
1. [Dołączanie i odłączanie do programu](../../extensibility/debugger/attaching-and-detaching-to-a-program.md)  
  
2. [Uruchamianie debugera](../../extensibility/debugger/launching-the-debugger.md)  
  
3. [Kończenie programu](../../extensibility/debugger/terminating-a-program.md)  
  
4. [Tworzenie punktu przerwania](../../extensibility/debugger/creating-a-breakpoint.md)  
  
5. [Gdy punkt przerwania tworzy powiązanie lub staje się niepowiązane](../../extensibility/debugger/when-a-breakpoint-binds-or-becomes-unbound.md)  
  
6. [Błędy punktów przerwania](../../extensibility/debugger/breakpoint-errors.md)  
  
7. [Naciśnięcie punktu przerwania](../../extensibility/debugger/hitting-a-breakpoint.md)  
  
8. [Usuwanie punktu przerwania](../../extensibility/debugger/deleting-a-breakpoint.md)  
  
9. [Wchodzenie w tryb przerwania](../../extensibility/debugger/entering-break-mode.md)  
  
10. [Krokowe przechodzenie w tryb przerwania](../../extensibility/debugger/stepping-in-break-mode.md)  
  
11. [Obliczanie wyrażeń w trybie przerwania](../../extensibility/debugger/expression-evaluation-in-break-mode.md)  
  
12. [Obsługa wyjątków](../../extensibility/debugger/exception-handling-visual-studio-sdk.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie niestandardowego aparatu debugowania](../../extensibility/debugger/creating-a-custom-debug-engine.md)
