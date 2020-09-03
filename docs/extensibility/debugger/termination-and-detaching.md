---
title: Kończenie i odłączanie | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- programs, termination events
- debug engines, detaching from programs
ms.assetid: 268c1e51-6363-45d1-964c-1ab99bdfa4f9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0b88255d618ce42fa55d878f192d31523ba3f83b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80712496"
---
# <a name="termination-and-detaching"></a>Kończenie i odłączanie
W poniższej sekcji opisano normalne zakończenie.

## <a name="discussion"></a>Dyskusja
 Po zakończeniu działania interfejsu [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) lub [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) , jeśli nie ma żadnych punktów przerwania, wyjątków, błędów czasu wykonywania lub nieskończonych pętli w aplikacji, które mają być debugowane, debugowany program zostanie uruchomiony do ukończenia. Ten proces to normalne zakończenie.

 Aby zaimplementować normalne zakończenie, należy wysłać [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) . Normalne zakończenie wymaga uruchomienia metody [IDebugProgramDestroyEvent2:: GetExitCode](../../extensibility/debugger/reference/idebugprogramdestroyevent2-getexitcode.md) .

## <a name="see-also"></a>Zobacz też
- [Tworzenie niestandardowego aparatu debugowania](../../extensibility/debugger/creating-a-custom-debug-engine.md)
