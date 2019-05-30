---
title: Kończenie i odłączanie | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- programs, termination events
- debug engines, detaching from programs
ms.assetid: 268c1e51-6363-45d1-964c-1ab99bdfa4f9
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8aafb94e0a07462d93cc77a34f7199f61f944d0f
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66333725"
---
# <a name="termination-and-detaching"></a>Kończenie i odłączanie
W poniższej sekcji opisano normalne zakończenie.

## <a name="discussion"></a>Dyskusja
 Po [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) lub [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) interfejsu będzie nadal występować, jeśli nie ma żadnych punktów przerwania, wyjątki, błędy czasu wykonywania ani pętli nieskończonej w aplikacji przeznaczonej do debugowania, wykonywanie debugowanego aż do zakończenia. Ten proces jest normalne zakończenie.

 Konieczne jest wysłanie [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) do zaimplementowania normalne zakończenie. Normalne zakończenie wymaga uruchamiania [IDebugProgramDestroyEvent2::GetExitCode](../../extensibility/debugger/reference/idebugprogramdestroyevent2-getexitcode.md) metody.

## <a name="see-also"></a>Zobacz także
- [Tworzenie niestandardowego aparatu debugowania](../../extensibility/debugger/creating-a-custom-debug-engine.md)