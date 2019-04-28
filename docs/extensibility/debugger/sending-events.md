---
title: Wysyłanie zdarzeń | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], sending events
ms.assetid: 064231e7-59b5-4437-8240-a23c0a7ec2a9
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cd282dd38d322a5b7d9821406d30a303fabb02bb
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62864353"
---
# <a name="send-events"></a>Wysyłanie zdarzeń
Mechanizm komunikacji między debugera i aparat debugowania (DE) to model zdarzeń oparty na modelu DCOM. Zdarzenia są wysyłane jako obiekty COM, a każde zdarzenie ma parametry, które określają:

- DE, która wywołała zdarzenie.

- Opis co się stało.

- Proces, program i informacji o wątku, który identyfikuje kontekst, w którym wystąpiło zdarzenie. Ten proces nie są wysyłane do zdarzeń wysyłanych z URZ.

- Typ zdarzenia, która wskazuje, czy zdarzenie jest synchroniczna lub asynchroniczna.

  Wszystkie zdarzenia debugowania są wysyłane przy użyciu metody [IDebugEventCallback2::Event](../../extensibility/debugger/reference/idebugeventcallback2-event.md).

## <a name="in-this-section"></a>W tej sekcji
 [Źródła zdarzeń](../../extensibility/debugger/event-sources-visual-studio-sdk.md) opisano dwa źródła zdarzeń: aparat debugowania (DE) i sesja debugowania manager (SDM).

 [Obsługiwane typy zdarzeń](../../extensibility/debugger/supported-event-types.md) w tym artykule omówiono aktualnie obsługiwane typy zdarzeń: synchronicznego i asynchronicznego.

 [Opisy zdarzeń](../../extensibility/debugger/event-descriptions.md) definiuje zdarzenia i przyczyny ich użycie.

## <a name="related-sections"></a>Sekcje pokrewne
 [Tworzenie niestandardowego aparatu debugowania](../../extensibility/debugger/creating-a-custom-debug-engine.md) w tym artykule opisano, jak DE współpracuje z interpreter lub systemu operacyjnego w celu dostarczania usług debugowania.