---
title: Wątki | Microsoft Docs
description: W tym artykule opisano definicję i rolę wątku w architekturze debugera w Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debugging [Debugging SDK], threads
- threading [Debugging SDK]
ms.assetid: 2243d24a-c3d2-41d1-abbb-6db21a2db9ee
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: dc745a4361c0935896048bbf72a4084f007ecf7b
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112905738"
---
# <a name="threads"></a>Wątki
W architekturze debugera *wątek*:

- Jest podstawową jednostką obliczeniową. Wątek sekwencyjnie wykonuje instrukcje w kontekście jednego stosu wywołań, przenosząc się z jednego kontekstu kodu do następnego.

- Może identyfikować siebie i program, w ramach który jest uruchomiony. Wątki można nazywać, zawieszać i wznawiać. Wątek może również wyliczyć skojarzone ramki stosu i w pewnych warunkach można go przenieść do innej ramki stosu. Biorąc pod uwagę kontekst ramki stosu, wątek może zwrócić skojarzony wątek logiczny, jeśli jest związany. Wątek ma właściwości, takie jak liczba wstrzymania, które mogą być wyświetlane w oknie **Wątki** środowiska IDE.

- Jest reprezentowany przez [interfejs IDebugThread2,](../../extensibility/debugger/reference/idebugthread2.md) zazwyczaj tworzony przez aparat debugowania (DE) lub maszynę wirtualną w wyniku wykonania programu.

## <a name="see-also"></a>Zobacz też
- [Programy](../../extensibility/debugger/programs.md)
- [Ramki stosu](../../extensibility/debugger/stack-frames.md)
- [Aparat debugowania](../../extensibility/debugger/debug-engine.md)
- [Pojęcia dotyczące debugera](../../extensibility/debugger/debugger-concepts.md)
- [Menedżer debugowania sesji](../../extensibility/debugger/session-debug-manager.md)
