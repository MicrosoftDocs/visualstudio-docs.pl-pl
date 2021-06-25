---
title: Wysyłanie zdarzeń | Microsoft Docs
description: Dowiedz się, jak debuger i aparat debugowania używają modelu zdarzeń opartego na modelu DCOM. Zdarzenia są wysyłane jako obiekty COM.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debugging [Debugging SDK], sending events
ms.assetid: 064231e7-59b5-4437-8240-a23c0a7ec2a9
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 6e9af2618150df522a459e47f312c1dc1e6a220c
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112902257"
---
# <a name="send-events"></a>Wysyłanie zdarzeń
Mechanizm komunikacji między debugerem i aparatem debugowania (DE) jest modelem zdarzeń opartym na modelu DCOM. Zdarzenia są wysyłane jako obiekty COM, a każde zdarzenie ma parametry, które określają:

- De, który wywołał zdarzenie.

- Opis tego, co się stało.

- Informacje o procesie, programie i wątku, które identyfikują kontekst wystąpienia zdarzenia. Proces nie jest wysyłany dla zdarzeń wysyłanych z DE.

- Typ zdarzenia, który wskazuje, czy zdarzenie jest synchroniczne, czy asynchroniczne.

  Wszystkie zdarzenia debugowania są wysyłane przy użyciu [metody IDebugEventCallback2::Event](../../extensibility/debugger/reference/idebugeventcallback2-event.md).

## <a name="in-this-section"></a>W tej sekcji
 [Źródła zdarzeń](../../extensibility/debugger/event-sources-visual-studio-sdk.md) Wyjaśnienie dwóch źródeł zdarzeń: aparatu debugowania (DE) i menedżera debugowania sesji (SDM).

 [Obsługiwane typy zdarzeń](../../extensibility/debugger/supported-event-types.md) W tym artykule omówiono obecnie obsługiwane typy zdarzeń: asynchroniczne i synchroniczne.

 [Opisy zdarzeń](../../extensibility/debugger/event-descriptions.md) Definiuje zdarzenia i przyczyny ich użycia.

## <a name="related-sections"></a>Powiązane sekcje
 [Tworzenie niestandardowego aparatu debugowania](../../extensibility/debugger/creating-a-custom-debug-engine.md) Opisuje sposób współpracy de z interpreterem lub systemem operacyjnym w celu zapewnienia usług debugowania.
