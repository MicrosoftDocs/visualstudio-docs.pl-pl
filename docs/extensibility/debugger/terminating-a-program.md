---
title: Kończenie pracy programu | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80712519"
---
# <a name="terminating-a-program"></a>Kończenie programu
W poniższej sekcji opisano zakończenie jednego programu z jednym wątkiem.

## <a name="termination-process"></a>Proces kończenia

1. Element DE wysyła [IDebugThreadDestroyEvent2](../../extensibility/debugger/reference/idebugthreaddestroyevent2.md) z prawidłowym [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md).

2. Element DE wysyła [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) z prawidłowym [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md).

   IDE przechodzi do trybu projektowania. Aparat debugowania lub środowisko uruchomieniowe wywołuje [IDebugPortNotify2:: RemoveProgramNode](../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md) w celu usunięcia programu z portu.

## <a name="see-also"></a>Zobacz też
- [Wywoływanie zdarzeń debugera](../../extensibility/debugger/calling-debugger-events.md)
