---
title: Kończenie i odłączanie | Dokumentacja firmy Microsoft
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
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54793906"
---
# <a name="termination-and-detaching"></a>Kończenie i odłączanie
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Poniżej opisano normalne zakończenie.  
  
## <a name="discussion"></a>Dyskusja  
 Po [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) lub [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) interfejsu będzie nadal występować, jeśli nie ma żadnych punktów przerwania, wyjątki, błędy czasu wykonywania ani pętli nieskończonej w aplikacji przeznaczonej do debugowania, do ukończenia uruchomią się debugowanego programu. Jest to normalne zakończenie.  
  
 Konieczne jest wysłanie [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) do zaimplementowania normalne zakończenie. Wymaga to wykonania [IDebugProgramDestroyEvent2::GetExitCode](../../extensibility/debugger/reference/idebugprogramdestroyevent2-getexitcode.md) metody.  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie niestandardowego aparatu debugowania](../../extensibility/debugger/creating-a-custom-debug-engine.md)
