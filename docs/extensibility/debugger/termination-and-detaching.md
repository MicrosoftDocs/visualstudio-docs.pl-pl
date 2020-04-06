---
title: Zakończenie i odłączenie | Dokumenty firmy Microsoft
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712496"
---
# <a name="termination-and-detaching"></a>Zakończenie i odłączenie
W poniższej sekcji opisano normalne zakończenie.

## <a name="discussion"></a>Dyskusji
 Po [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) lub [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) interfejs nadal, jeśli nie ma punktów przerwania, wyjątki, błędy w czasie wykonywania lub nieskończone pętle w aplikacji, które mają być debugowane, program jest debugowany uruchamia się do zakończenia. Ten proces jest normalnym zakończeniem.

 Musisz wysłać [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) do zaimplementowania normalnego zakończenia. Normalne zakończenie wymaga uruchomienia [metody IDebugProgramDestroyEvent2::GetExitCode.](../../extensibility/debugger/reference/idebugprogramdestroyevent2-getexitcode.md)

## <a name="see-also"></a>Zobacz też
- [Tworzenie niestandardowego aparatu debugowania](../../extensibility/debugger/creating-a-custom-debug-engine.md)
