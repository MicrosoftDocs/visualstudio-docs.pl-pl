---
title: Wysyłanie zdarzeń | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], sending events
ms.assetid: 064231e7-59b5-4437-8240-a23c0a7ec2a9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5ec0d3aa29da562147b71b8efde49baf07d8ae0b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713043"
---
# <a name="send-events"></a>Wysyłanie zdarzeń
Mechanizm komunikacji między debugerem a aparatem debugowania (DE) jest modelem zdarzeń opartym na modelu DCOM. Zdarzenia są wysyłane jako obiekty COM, a każde zdarzenie ma parametry, które określają:

- DE, który nazwał zdarzenie.

- Opis tego, co się stało.

- Informacje o procesie, programie i wątku, które identyfikują kontekst miejsca wystąpienia zdarzenia. Proces nie jest wysyłany dla zdarzeń wysłanych z DE.

- Typ zdarzenia, który wskazuje, czy zdarzenie jest synchroniczne lub asynchroniczne.

  Wszystkie zdarzenia debugowania są wysyłane przy użyciu metody [IDebugEventCallback2::Event](../../extensibility/debugger/reference/idebugeventcallback2-event.md).

## <a name="in-this-section"></a>W tej sekcji
 [Źródła zdarzeń](../../extensibility/debugger/event-sources-visual-studio-sdk.md) W tym artykule wyjaśniono dwa źródła zdarzeń: aparat debugowania (DE) i menedżer debugowania sesji (SDM).

 [Obsługiwane typy zdarzeń](../../extensibility/debugger/supported-event-types.md) W tym artykule omówiono aktualnie obsługiwane typy zdarzeń: asynchroniczne i synchroniczne.

 [Opisy zdarzeń](../../extensibility/debugger/event-descriptions.md) Definiuje zdarzenia i przyczyny ich użycia.

## <a name="related-sections"></a>Powiązane sekcje
 [Tworzenie niestandardowego aparatu debugowania](../../extensibility/debugger/creating-a-custom-debug-engine.md) W tym artykule opisano, jak DE współpracuje z interpreterem lub systemem operacyjnym w celu świadczenia usług debugowania.
