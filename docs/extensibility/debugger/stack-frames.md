---
title: Ramek stosu | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- stack frames, debugging
- debugging [Debugging SDK], stack frames
- stack frames
ms.assetid: b5e439d4-1e9d-4e13-9cad-bb8b136d4ca8
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: de3a0267d366f926fa5705c7455b237cafe4820a
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66348505"
---
# <a name="stack-frames"></a>Ramki stosu
W architekturze debugera *ramki stosu*:

- Jest klasą abstrakcyjną stosu, które dostarcza kontekst wykonanie wątku. Wątek jest zawsze wykonywane w ramach funkcji. Ramka stosu zawiera zmienne lokalne, funkcji i argumenty do niego. Aby debugować za pomocą programu Visual Studio, języka lub środowiska debugowania musi obsługiwać ramki stosu.

- Można zarówno zidentyfikować opisania siebie i może zwrócić skojarzonego wątku. Ramka stosu może również zwracać kontekst kodu, który reprezentuje bieżący wskaźnik instrukcji i skojarzone dokumentacji i konteksty oceny wyrażenia.

- Ma właściwości, które opisują nazwy, typu i wartości zmiennych lokalnych i argumenty, i które znajdują się w różnych oknach debugowania środowiska IDE.

- Jest reprezentowany przez [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md) interfejsu, zazwyczaj tworzone przez aparat debugowania (DE) lub maszyny wirtualnej w wyniku wykonywania wątku.

## <a name="see-also"></a>Zobacz także
- [Konteksty debugera](../../extensibility/debugger/debugger-contexts.md)
- [Pojęcia dotyczące debugera](../../extensibility/debugger/debugger-concepts.md)
- [Aparat debugowania](../../extensibility/debugger/debug-engine.md)
- [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md)