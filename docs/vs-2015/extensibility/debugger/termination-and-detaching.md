---
title: Kończenie i odłączanie | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- programs, termination events
- debug engines, detaching from programs
ms.assetid: 268c1e51-6363-45d1-964c-1ab99bdfa4f9
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b1641a9a44a3f37b07e8192169e7301153881484
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51773876"
---
# <a name="termination-and-detaching"></a>Kończenie i odłączanie
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Poniżej opisano normalne zakończenie.  
  
## <a name="discussion"></a>Dyskusja  
 Po [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) lub [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) interfejsu będzie nadal występować, jeśli nie ma żadnych punktów przerwania, wyjątki, błędy czasu wykonywania ani pętli nieskończonej w aplikacji przeznaczonej do debugowania, do ukończenia uruchomią się debugowanego programu. Jest to normalne zakończenie.  
  
 Konieczne jest wysłanie [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) do zaimplementowania normalne zakończenie. Wymaga to wykonania [IDebugProgramDestroyEvent2::GetExitCode](../../extensibility/debugger/reference/idebugprogramdestroyevent2-getexitcode.md) metody.  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie niestandardowego aparatu debugowania](../../extensibility/debugger/creating-a-custom-debug-engine.md)

