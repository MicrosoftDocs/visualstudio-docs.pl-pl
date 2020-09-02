---
title: Kończenie i odłączanie | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- programs, termination events
- debug engines, detaching from programs
ms.assetid: 268c1e51-6363-45d1-964c-1ab99bdfa4f9
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d92fe88826baf19ba66b200990aee7797e91f87b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68176674"
---
# <a name="termination-and-detaching"></a>Kończenie i odłączanie
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Poniżej opisano normalne zakończenie.  
  
## <a name="discussion"></a>Dyskusja  
 Po zakończeniu interfejsu [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) lub [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) , jeśli nie ma żadnych punktów przerwania, wyjątków, błędów czasu wykonywania lub nieskończonych pętli w aplikacji, które mają być debugowane, debugowany program zostanie uruchomiony do ukończenia. Jest to normalne zakończenie.  
  
 Aby zaimplementować normalne zakończenie, należy wysłać [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) . Wymaga to wykonania metody [IDebugProgramDestroyEvent2:: GetExitCode](../../extensibility/debugger/reference/idebugprogramdestroyevent2-getexitcode.md) .  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie niestandardowego aparatu debugowania](../../extensibility/debugger/creating-a-custom-debug-engine.md)
