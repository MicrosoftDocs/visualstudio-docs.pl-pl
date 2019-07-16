---
title: Wysyłanie zdarzeń | Dokumentacja firmy Microsoft
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
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "68204745"
---
# <a name="sending-events"></a>Wysyłanie zdarzeń
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Mechanizm komunikacji między debugera i aparat debugowania (DE) to model zdarzeń oparty na modelu DCOM. Zdarzenia są wysyłane jako obiekty COM, a każde zdarzenie ma następujące parametry, które określają następujące czynności:  
  
- DE, która wywołała zdarzenie.  
  
- Opis co się stało.  
  
- Proces, program i informacji o wątku, który identyfikuje kontekst, w którym wystąpiło zdarzenie. Ten proces nie są wysyłane do zdarzeń wysyłanych z URZ.  
  
- Typ zdarzenia, która wskazuje, czy zdarzenie jest synchroniczna lub asynchroniczna.  
  
  Wszystkie zdarzenia debugowania są wysyłane przy użyciu metody [IDebugEventCallback2::Event](../../extensibility/debugger/reference/idebugeventcallback2-event.md).  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Źródła zdarzeń](../../extensibility/debugger/event-sources-visual-studio-sdk.md)  
 Opisano dwa źródła zdarzeń: aparat debugowania (DE) i sesja debugowania manager (SDM).  
  
 [Obsługiwane typy zdarzeń](../../extensibility/debugger/supported-event-types.md)  
 W tym artykule omówiono aktualnie obsługiwane typy zdarzeń: synchronicznego i asynchronicznego.  
  
 [Opisy zdarzeń](../../extensibility/debugger/event-descriptions.md)  
 Definiuje zdarzenia i przyczyny ich użycie.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Tworzenie niestandardowego aparatu debugowania](../../extensibility/debugger/creating-a-custom-debug-engine.md)  
 W tym artykule opisano, jak DE współpracuje z interpreter lub systemu operacyjnego w celu dostarczania usług debugowania.
