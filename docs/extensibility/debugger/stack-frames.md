---
title: Ramki stosu | Dokumenty firmy Microsoft
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712840"
---
# <a name="stack-frames"></a>Ramki stosu
W architekturze debugera *ramka stosu:*

- Jest abstrakcja stosu, który zapewnia kontekst wykonywania wątku. Wątek zawsze wykonuje w ramach funkcji. Ramka stosu zawiera zmienne lokalne funkcji i argumenty do niej. W celu debugowania za pomocą programu Visual Studio, język lub środowisko debugowane musi obsługiwać ramki stosu.

- Można zarówno zidentyfikować i opisać siebie i może zwrócić skojarzony wątek. Ramka stosu można również zwrócić kontekst kodu, który reprezentuje bieżący wskaźnik instrukcji i skojarzone konteksty oceny dokumentacji i wyrażenia.

- Ma właściwości, które opisują nazwę, typ i wartość zmiennych lokalnych i argumentów i które pojawiają się w różnych oknach debugowania IDE.

- Jest reprezentowany przez interfejs [IDebugStackFrame2,](../../extensibility/debugger/reference/idebugstackframe2.md) zazwyczaj tworzony przez aparat debugowania (DE) lub maszyny wirtualnej w wyniku wykonywania wątku.

## <a name="see-also"></a>Zobacz też
- [Konteksty debugera](../../extensibility/debugger/debugger-contexts.md)
- [Pojęcia debugera](../../extensibility/debugger/debugger-concepts.md)
- [Aparat debugowania](../../extensibility/debugger/debug-engine.md)
- [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md)
