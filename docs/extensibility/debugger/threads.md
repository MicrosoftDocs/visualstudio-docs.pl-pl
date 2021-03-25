---
title: Wątki | Microsoft Docs
description: W tym artykule opisano definicje i rolę wątku w architekturze debugera w programie Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], threads
- threading [Debugging SDK]
ms.assetid: 2243d24a-c3d2-41d1-abbb-6db21a2db9ee
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 168d29b8306ec58233f426b48c3ab0adfacb2bd5
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105057848"
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
