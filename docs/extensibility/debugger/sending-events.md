---
title: Wysyłanie zdarzeń | Microsoft Docs
description: Dowiedz się, w jaki sposób debuger i aparat debugowania wykorzystują model zdarzeń oparty na modelu DCOM. Zdarzenia są wysyłane jako obiekty COM.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], sending events
ms.assetid: 064231e7-59b5-4437-8240-a23c0a7ec2a9
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 135dd0278ee765ef88ae6cef39675a2fa92236d7
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105070395"
---
# <a name="send-events"></a>Wysyłanie zdarzeń
Mechanizm komunikacji między debugerem a aparatem debugowania (DE) jest modelem zdarzeń opartym na modelu DCOM. Zdarzenia są wysyłane jako obiekty COM, a każde zdarzenie ma parametry, które określają:

- DE, która wywołała zdarzenie.

- Opis tego, co się stało.

- Informacje o procesie, programie i wątku, które identyfikują kontekst, w którym wystąpiło zdarzenie. Proces nie jest wysyłany dla zdarzeń wysyłanych z elementu DE.

- Typ zdarzenia, który wskazuje, czy zdarzenie jest synchroniczne, czy asynchroniczne.

  Wszystkie zdarzenia debugowania są wysyłane przy użyciu metody [IDebugEventCallback2:: Event](../../extensibility/debugger/reference/idebugeventcallback2-event.md).

## <a name="in-this-section"></a>W tej sekcji
 [Źródła zdarzeń](../../extensibility/debugger/event-sources-visual-studio-sdk.md) Wyjaśnia dwa źródła zdarzeń: aparat debugowania (DE) i Menedżer debugowania sesji (SDM).

 [Obsługiwane typy zdarzeń](../../extensibility/debugger/supported-event-types.md) Omawia aktualnie obsługiwane typy zdarzeń: asynchroniczne i synchroniczne.

 [Opisy zdarzeń](../../extensibility/debugger/event-descriptions.md) Definiuje zdarzenia i przyczyny ich użycia.

## <a name="related-sections"></a>Sekcje pokrewne
 [Tworzenie niestandardowego aparatu debugowania](../../extensibility/debugger/creating-a-custom-debug-engine.md) Opisuje, jak DE współpracuje z interpreterem lub systemem operacyjnym w celu zapewnienia usług debugowania.
