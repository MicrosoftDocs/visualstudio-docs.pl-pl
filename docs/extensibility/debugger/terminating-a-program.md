---
title: Kończenie programu | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- programs, termination events
- debugging [Debugging SDK], terminating a program
ms.assetid: eedda0a3-5e05-44fe-841d-a2f4866ac72d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 985b20fe75f8ceee3d434ac681b437c51baf85e8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712519"
---
# <a name="terminating-a-program"></a>Kończenie programu
W poniższej sekcji opisano zakończenie pojedynczego programu za pomocą jednego wątku.

## <a name="termination-process"></a>Proces rozwiązania umowy

1. DE wysyła [IDebugThreadDestroyEvent2](../../extensibility/debugger/reference/idebugthreaddestroyevent2.md) z prawidłowym [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md).

2. DE wysyła [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) z prawidłowym [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md).

   IDE przechodzi w tryb projektowania. Aparat debugowania lub środowisko pracy wywołuje [IDebugPortNotify2::RemoveProgramNode,](../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md) aby usunąć program z portu.

## <a name="see-also"></a>Zobacz też
- [Wywoływanie zdarzeń debugera](../../extensibility/debugger/calling-debugger-events.md)
