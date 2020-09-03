---
title: Ramki stosu | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- stack frames, debugging
- debugging [Debugging SDK], stack frames
- stack frames
ms.assetid: b5e439d4-1e9d-4e13-9cad-bb8b136d4ca8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1ea79ad199e20afeb5d2bf1ca6a3cf881c6d51c3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80712840"
---
# <a name="stack-frames"></a>Ramki stosu
W architekturze debugera, *Ramka stosu*:

- Jest abstrakcją stosu, który zapewnia kontekst wykonywania wątku. Wątek jest zawsze wykonywany w ramach funkcji. Ramka stosu przechowuje zmienne lokalne funkcji i argumenty. Aby debugować za pomocą programu Visual Studio, debugowany język lub środowisko musi obsługiwać ramki stosu.

- Może zarówno identyfikować, jak i opisywanie, a także zwracać skojarzony wątek. Ramka stosu może również zwracać kontekst kodu, który reprezentuje bieżący wskaźnik instrukcji i powiązane z nim dokumenty i kontekst oceny wyrażenia.

- Ma właściwości opisujące nazwę, typ i wartość zmiennych lokalnych i argumentów, które są wyświetlane w różnych oknach debugowania IDE.

- Jest reprezentowany przez interfejs [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md) , zwykle tworzony przez aparat debugowania (de) lub maszynę wirtualną w ramach wykonywania wątku.

## <a name="see-also"></a>Zobacz też
- [Konteksty debugera](../../extensibility/debugger/debugger-contexts.md)
- [Pojęcia dotyczące debugera](../../extensibility/debugger/debugger-concepts.md)
- [Aparat debugowania](../../extensibility/debugger/debug-engine.md)
- [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md)
