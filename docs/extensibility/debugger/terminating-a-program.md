---
title: Kończenie programu | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- programs, termination events
- debugging [Debugging SDK], terminating a program
ms.assetid: eedda0a3-5e05-44fe-841d-a2f4866ac72d
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 864141055487b598a8f91641f40fe4c027c53b6c
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54918436"
---
# <a name="terminating-a-program"></a>Kończenie programu
W poniższej sekcji opisano przed zakończeniem jednego programu z jednego wątku.  
  
## <a name="termination-process"></a>Zakończenie procesu  
  
1. Wysyła DE [IDebugThreadDestroyEvent2](../../extensibility/debugger/reference/idebugthreaddestroyevent2.md) przy użyciu prawidłowego [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md).  
  
2. Wysyła DE [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) przy użyciu prawidłowego [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md).  
  
   IDE przechodzi do trybu projektowania. Aparat debugowania lub wywołania w środowisku uruchomieniowym [IDebugPortNotify2::RemoveProgramNode](../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md) usunięcie programu z portu.  
  
## <a name="see-also"></a>Zobacz także  
 [Wywoływanie zdarzeń debugera](../../extensibility/debugger/calling-debugger-events.md)