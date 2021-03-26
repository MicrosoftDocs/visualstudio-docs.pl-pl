---
title: Ramki stosu | Microsoft Docs
description: W tym artykule opisano definicje i rolę ramki stosu w architekturze debugera w programie Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- stack frames, debugging
- debugging [Debugging SDK], stack frames
- stack frames
ms.assetid: b5e439d4-1e9d-4e13-9cad-bb8b136d4ca8
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b0c54292d79b119fc36c9eff3f0f3519c92a4205
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105079398"
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
