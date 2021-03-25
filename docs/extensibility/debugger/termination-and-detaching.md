---
title: Kończenie i odłączanie | Microsoft Docs
description: Normalne zakończenie oznacza, że debugowany program jest uruchamiany do ukończenia bez punktów przerwania, wyjątków, błędów czasu wykonywania lub nieskończonych pętli.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- programs, termination events
- debug engines, detaching from programs
ms.assetid: 268c1e51-6363-45d1-964c-1ab99bdfa4f9
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 8662809b50dbfec3046af1d0d6b6fa151c3a33e0
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105057835"
---
# <a name="termination-and-detaching"></a>Kończenie i odłączanie
W poniższej sekcji opisano normalne zakończenie.

## <a name="discussion"></a>Dyskusja
 Po zakończeniu działania interfejsu [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) lub [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) , jeśli nie ma żadnych punktów przerwania, wyjątków, błędów czasu wykonywania lub nieskończonych pętli w aplikacji, które mają być debugowane, debugowany program zostanie uruchomiony do ukończenia. Ten proces to normalne zakończenie.

 Aby zaimplementować normalne zakończenie, należy wysłać [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) . Normalne zakończenie wymaga uruchomienia metody [IDebugProgramDestroyEvent2:: GetExitCode](../../extensibility/debugger/reference/idebugprogramdestroyevent2-getexitcode.md) .

## <a name="see-also"></a>Zobacz też
- [Tworzenie niestandardowego aparatu debugowania](../../extensibility/debugger/creating-a-custom-debug-engine.md)
