---
title: Wątki | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], threads
- threading [Debugging SDK]
ms.assetid: 2243d24a-c3d2-41d1-abbb-6db21a2db9ee
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8ed5c06e0c42dac1f0539cc2c7c5886d95b23ae1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712475"
---
# <a name="threads"></a>Wątki
W architekturze debugera *wątek:*

- Jest podstawową jednostką obliczeń. Wątek sekwencyjnie wykonuje swoje instrukcje w kontekście stosu pojedynczych wywołań, przechodząc z jednego kontekstu kodu do następnego.

- Można zidentyfikować siebie i program, w który jest uruchomiony. Wątki mogą być nazwane, zawieszone i wznowione. Wątek można również wyliczyć jego skojarzone ramki stosu i, w pewnych warunkach, mogą być przenoszone do innej ramki stosu. Biorąc pod uwagę kontekst ramki stosu, wątek może zwrócić skojarzony jego wątek logiczny, jeśli istnieje. Wątek ma właściwości, takie jak liczba wstrzymania, które mogą być wyświetlane w oknie **Wątki** IDE.

- Jest reprezentowany przez interfejs [IDebugThread2,](../../extensibility/debugger/reference/idebugthread2.md) zazwyczaj tworzony przez aparat debugowania (DE) lub maszyny wirtualnej w wyniku wykonywania programu.

## <a name="see-also"></a>Zobacz też
- [Programy](../../extensibility/debugger/programs.md)
- [Ramki stosu](../../extensibility/debugger/stack-frames.md)
- [Aparat debugowania](../../extensibility/debugger/debug-engine.md)
- [Pojęcia debugera](../../extensibility/debugger/debugger-concepts.md)
- [Menedżer debugowania sesji](../../extensibility/debugger/session-debug-manager.md)
