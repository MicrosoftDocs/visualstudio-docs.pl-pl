---
title: Wątki | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], threads
- threading [Debugging SDK]
ms.assetid: 2243d24a-c3d2-41d1-abbb-6db21a2db9ee
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e9759536e1b27018a3361bbb723b4cde0f88269e
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66333660"
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