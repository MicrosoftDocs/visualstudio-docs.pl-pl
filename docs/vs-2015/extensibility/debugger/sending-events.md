---
title: Wysyłanie zdarzeń | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], sending events
ms.assetid: 064231e7-59b5-4437-8240-a23c0a7ec2a9
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 98247b894d2db628d508713875ba0ea7d0642729
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204745"
---
# <a name="sending-events"></a>Wysyłanie zdarzeń
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Mechanizm komunikacji między debugerem a aparatem debugowania (DE) jest modelem zdarzeń opartym na modelu DCOM. Zdarzenia są wysyłane jako obiekty COM, a każde zdarzenie ma parametry, które określają następujące elementy:  
  
- DE, która wywołała zdarzenie.  
  
- Opis tego, co się stało.  
  
- Informacje o procesie, programie i wątku, które identyfikują kontekst, w którym wystąpiło zdarzenie. Proces nie jest wysyłany dla zdarzeń wysyłanych z elementu DE.  
  
- Typ zdarzenia, który wskazuje, czy zdarzenie jest synchroniczne, czy asynchroniczne.  
  
  Wszystkie zdarzenia debugowania są wysyłane przy użyciu metody [IDebugEventCallback2:: Event](../../extensibility/debugger/reference/idebugeventcallback2-event.md).  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Źródła zdarzeń](../../extensibility/debugger/event-sources-visual-studio-sdk.md)  
 Wyjaśnia dwa źródła zdarzeń: aparat debugowania (DE) i Menedżer debugowania sesji (SDM).  
  
 [Obsługiwane typy zdarzeń](../../extensibility/debugger/supported-event-types.md)  
 Omawia aktualnie obsługiwane typy zdarzeń: asynchroniczne i synchroniczne.  
  
 [Opisy zdarzeń](../../extensibility/debugger/event-descriptions.md)  
 Definiuje zdarzenia i przyczyny ich użycia.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Tworzenie niestandardowego aparatu debugowania](../../extensibility/debugger/creating-a-custom-debug-engine.md)  
 Opisuje, jak DE współpracuje z interpreterem lub systemem operacyjnym w celu zapewnienia usług debugowania.
