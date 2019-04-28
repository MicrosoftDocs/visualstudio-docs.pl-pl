---
title: Sesja debugowania Menedżera | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- session debug manager, unifying session views
- session debug manager, broadcasting
- debugging [Debugging SDK], session debug manager
- session debug manager
- session debug manager, debug engine multiplexing
- session debug manager, delegating
ms.assetid: fbb1928d-dddc-43d1-98a4-e23b0ecbae09
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: edbb1510265307e1c9fe6c8a01cffc0115d879ac
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62864268"
---
# <a name="session-debug-manager"></a>Menedżer debugowania sesji
Menedżer debugowania sesji (SDM) zarządza dowolną liczbę silniki debugowania (DE), które jest debugowany dowolną liczbę programów w wielu procesach w dowolnej liczbie maszyn. Oprócz multiplekser aparat debugowania, SDM zapewnia spójny widok sesji debugowania środowiska IDE.

## <a name="session-debug-manager-operation"></a>Operacja Menedżer debugowania sesji
 Menedżer debugowania sesji (SDM) zarządza DE. Może istnieć więcej niż jeden aparat debugowania uruchomione na komputerze, w tym samym czasie. Aby multipleksować DEs, SDM opakowuje liczbę interfejsów z DEs i udostępnia je do środowiska IDE jako pojedynczy interfejs.

 Aby zwiększyć wydajność, nie są multiplexed niektóre interfejsy. Zamiast tego są one używane bezpośrednio z DE i wywołań do tych interfejsów nie przechodzą SDM. Na przykład multiplexed nie są interfejsy używane z pamięci, kodu i konteksty dokumentu, ponieważ odnoszą się do określonej instrukcji, pamięć lub dokumentu w debugowane określonych DE określonego programu. Nie inne DE należy zaangażować w tym samym poziomie komunikacji.

 Nie dotyczy wszystkich kontekstów. Wywołania interfejsu kontekstu oceny wyrażenia przechodzą przez SDM. Podczas obliczania wyrażenia opakowuje SDM [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) interfejs, który zapewnia środowiska IDE, ponieważ gdy to wyrażenie jest obliczane, może pociągać za sobą wiele DEs, który debugowania programów w ten sam proces, który może być uruchomione na tym samym wątku.

 SDM typowo funkcjonuje jako mechanizm delegowania, ale może ona działać jako mechanizmu emisji. Na przykład podczas obliczania wyrażenia SDM działa jako mechanizmu emisji, aby powiadomić wszystkich DEs czy kodu mogą być uruchamiane na określony wątek. Podobnie gdy model SDM odbiera zdarzenia zatrzymywania, emituje do programów, że ich należy zatrzymać. Po wywołaniu krok SDM emituje do programów może nadal działa. Punkty przerwania są również emisji do każdego DE.

 SDM nie śledzi bieżącego programu, wątku lub ramki stosu. Proces, program i informacji o wątku są wysyłane do SDM w połączeniu z określonych zdarzeń debugowania.

## <a name="see-also"></a>Zobacz także
- [Aparat debugowania](../../extensibility/debugger/debug-engine.md)
- [Składniki debugera](../../extensibility/debugger/debugger-components.md)
- [Konteksty debugera](../../extensibility/debugger/debugger-contexts.md)