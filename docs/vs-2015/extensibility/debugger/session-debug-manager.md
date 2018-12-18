---
title: Sesja debugowania Menedżera | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- session debug manager, unifying session views
- session debug manager, broadcasting
- debugging [Debugging SDK], session debug manager
- session debug manager
- session debug manager, debug engine multiplexing
- session debug manager, delegating
ms.assetid: fbb1928d-dddc-43d1-98a4-e23b0ecbae09
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d0c3bb1ce939ed54997d8d8b40de75bcd095e4dc
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51759150"
---
# <a name="session-debug-manager"></a>Menedżer debugowania sesji
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Menedżer debugowania sesji (SDM) zarządza dowolną liczbę silniki debugowania (DE) debugowanie dowolną liczbę programów w wielu procesach w dowolnej liczbie maszyn. Oprócz multiplekser aparat debugowania, SDM zapewnia spójny widok sesji debugowania środowiska IDE.  
  
## <a name="session-debug-manager-operation"></a>Operacja Menedżer debugowania sesji  
 Menedżer debugowania sesji (SDM) zarządza DE. Może istnieć więcej niż jeden aparat debugowania uruchomione na komputerze, w tym samym czasie. Aby multipleksować DEs, SDM opakowuje liczbę interfejsów z DEs i udostępnia je do środowiska IDE jako pojedynczy interfejs.  
  
 Aby zwiększyć wydajność, nie są multipleksowane niektóre interfejsy. Zamiast tego są one używane bezpośrednio z DE i wywołań do tych interfejsów nie odbywają się za pośrednictwem SDM. Na przykład interfejsy używane z pamięci, kodu i konteksty dokumentu są nie multipleksowane, ponieważ odnoszą się do określonej instrukcji, pamięć lub dokumentu w debugowane określonych DE określonego programu. Nie inne DE należy zaangażować w tym samym poziomie komunikacji.  
  
 Nie dotyczy wszystkich kontekstów. Wywołania interfejsu kontekstu oceny wyrażenia przechodzą przez SDM. Podczas obliczania wyrażenia opakowuje SDM [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) interfejs, który zapewnia środowiska IDE, ponieważ gdy to wyrażenie jest obliczane, może pociągać za sobą wiele DEs, który debugowania programów w ten sam proces, który może być uruchomione na tym samym wątku.  
  
 SDM typowo funkcjonuje jako mechanizm delegowania, ale może ona działać jako mechanizmu emisji. Na przykład podczas obliczania wyrażenia SDM działa jako mechanizmu emisji, aby powiadomić wszystkich DEs czy kodu mogą być uruchamiane na określony wątek. Podobnie gdy model SDM odbiera zdarzenia zatrzymywania, emituje wszystkie programy, że ich należy zatrzymać. Wywołanego krok SDM jest wysyłana do wszystkich programów, mogą nadal działa. Punkty przerwania są również emisji do każdego DE.  
  
 SDM nie śledzi bieżącego programu, wątku lub ramki stosu. Proces, program i wątku informacje są wysyłane do SDM w połączeniu z określonych zdarzeń debugowania.  
  
## <a name="see-also"></a>Zobacz też  
 [Aparat debugowania](../../extensibility/debugger/debug-engine.md)   
 [Składniki debugera](../../extensibility/debugger/debugger-components.md)   
 [Konteksty debugera](../../extensibility/debugger/debugger-contexts.md)

