---
title: Ramki stosu | Microsoft Docs
description: W tym artykule opisano definicję i rolę ramki stosu w architekturze debugera w Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
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
ms.openlocfilehash: 77b503afcc38ab9427e5268097655433007de5d9
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112898555"
---
# <a name="stack-frames"></a>Ramki stosu
W architekturze debugera ramka *stosu:*

- Jest abstrakcją stosu, która zapewnia kontekst wykonywania wątku. Wątek jest zawsze wykonywany w ramach funkcji. Ramka stosu zawiera zmienne lokalne funkcji i jej argumenty. Aby debugować za pomocą Visual Studio, debugowany język lub środowisko musi obsługiwać ramki stosu.

- Może identyfikować i opisywać samą siebie oraz może zwracać skojarzony wątek. Ramka stosu może również zwrócić kontekst kodu, który reprezentuje bieżący wskaźnik instrukcji oraz skojarzone konteksty dokumentacji i oceny wyrażeń.

- Ma właściwości, które opisują nazwę, typ i wartość zmiennych lokalnych i argumentów, które są wyświetlane w różnych oknach debugowania środowiska IDE.

- Jest reprezentowany przez [interfejs IDebugStackFrame2,](../../extensibility/debugger/reference/idebugstackframe2.md) zazwyczaj tworzony przez aparat debugowania (DE) lub maszynę wirtualną w wyniku wykonania wątku.

## <a name="see-also"></a>Zobacz też
- [Konteksty debugera](../../extensibility/debugger/debugger-contexts.md)
- [Pojęcia dotyczące debugera](../../extensibility/debugger/debugger-concepts.md)
- [Aparat debugowania](../../extensibility/debugger/debug-engine.md)
- [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md)
