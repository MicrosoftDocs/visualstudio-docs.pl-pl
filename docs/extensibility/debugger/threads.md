---
title: Wątki | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80712475"
---
# <a name="threads"></a>Wątki
W architekturze debugera, *wątek*:

- Jest podstawową jednostką obliczeń. Wątek sekwencyjnie wykonuje instrukcje w kontekście pojedynczego stosu wywołań, przechodząc z jednego kontekstu kodu do następnego.

- Może identyfikować siebie i program, w którym działa. Wątki mogą być nazwane, zawieszone i wznowione. Wątek może również wyliczyć skojarzone ramki stosu, a w pewnych warunkach można przenieść do innej ramki stosu. Z uwzględnieniem kontekstu ramki stosu wątek może zwrócić skojarzony z nim wątek logiczny, jeśli istnieje. Wątek ma właściwości, takie jak liczba wstrzymań, które mogą być wyświetlane w oknie **wątki** IDE.

- Jest reprezentowany przez interfejs [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md) , zwykle tworzony przez aparat debugowania (de) lub maszynę wirtualną w ramach wykonywania programu.

## <a name="see-also"></a>Zobacz też
- [Programy](../../extensibility/debugger/programs.md)
- [Ramki stosu](../../extensibility/debugger/stack-frames.md)
- [Aparat debugowania](../../extensibility/debugger/debug-engine.md)
- [Pojęcia dotyczące debugera](../../extensibility/debugger/debugger-concepts.md)
- [Menedżer debugowania sesji](../../extensibility/debugger/session-debug-manager.md)
