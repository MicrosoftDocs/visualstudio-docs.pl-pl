---
title: Wątki | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], threads
- threading [Debugging SDK]
ms.assetid: 2243d24a-c3d2-41d1-abbb-6db21a2db9ee
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5d931568258099fa4a8fe8f3b82d3fe50d5a3e35
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60099776"
---
# <a name="threads"></a>Wątki
W architekturze debugera *wątku*:

- Jest podstawową jednostką obliczeń. Wątek sekwencyjnie wykonuje instrukcji w ramach pojedynczego wywołania stosu, przechodzenia z jednego kodu kontekstu do następnego.

- Można zidentyfikować sam, jak i program, który jest uruchomiony w. Wątki mogą o nazwie, zawieszone i wznowić. Wątek również wyliczyć jego ramek stosu skojarzone oraz w niektórych warunkach mogą zostać przeniesione do innej ramki stosu. Podany kontekst ramkę stosu, wątek może zwrócić skojarzony wątek logiczne ewentualne. Wątek ma właściwości, takie jak wstrzymania liczenia, które mogą być wyświetlane w **wątków** okna środowiska IDE.

- Jest reprezentowany przez [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md) interfejsu, zazwyczaj tworzone przez aparat debugowania (DE) lub maszyny wirtualnej w wyniku wykonywania programu.

## <a name="see-also"></a>Zobacz także
- [Programy](../../extensibility/debugger/programs.md)
- [Ramki stosu](../../extensibility/debugger/stack-frames.md)
- [Aparat debugowania](../../extensibility/debugger/debug-engine.md)
- [Pojęcia dotyczące debugera](../../extensibility/debugger/debugger-concepts.md)
- [Menedżer debugowania sesji](../../extensibility/debugger/session-debug-manager.md)