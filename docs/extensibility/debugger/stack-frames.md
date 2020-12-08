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
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ab2c891002ad90d767a4c5ca9efffd3f3d1d10ee
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/08/2020
ms.locfileid: "96845209"
---
# <a name="stack-frames"></a>Ramki stosu
W architekturze debugera, *Ramka stosu*:

- Jest abstrakcją stosu, który zapewnia kontekst wykonywania wątku. Wątek jest zawsze wykonywany w ramach funkcji. Ramka stosu przechowuje zmienne lokalne funkcji i argumenty. Aby debugować za pomocą programu Visual Studio, debugowany język lub środowisko musi obsługiwać ramki stosu.

- Może zarówno identyfikować, jak i opisywanie, a także zwracać skojarzony wątek. Ramka stosu może również zwracać kontekst kodu, który reprezentuje bieżący wskaźnik instrukcji i powiązane z nim dokumenty i kontekst oceny wyrażenia.

- Ma właściwości opisujące nazwę, typ i wartość zmiennych lokalnych i argumentów, które są wyświetlane w różnych oknach debugowania IDE.

- Jest reprezentowany przez interfejs [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md) , zwykle tworzony przez aparat debugowania (de) lub maszynę wirtualną w ramach wykonywania wątku.

## <a name="see-also"></a>Zobacz także
- [Konteksty debugera](../../extensibility/debugger/debugger-contexts.md)
- [Pojęcia dotyczące debugera](../../extensibility/debugger/debugger-concepts.md)
- [Aparat debugowania](../../extensibility/debugger/debug-engine.md)
- [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md)
