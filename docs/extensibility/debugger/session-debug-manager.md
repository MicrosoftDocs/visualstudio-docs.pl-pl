---
title: Menedżer debugowania sesji | Dokumenty firmy Microsoft
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
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 953b4e948ef5e21531a3e73bceed3a363ed3cec5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712885"
---
# <a name="session-debug-manager"></a>Menedżer debugowania sesji
Menedżer debugowania sesji (SDM) zarządza dowolną liczbą aparatów debugowania (DE), które debugują dowolną liczbę programów w wielu procesach na dowolnej liczbie komputerów. Oprócz multipleksera aparatu debugowania, SDM zapewnia ujednolicony widok sesji debugowania do IDE.

## <a name="session-debug-manager-operation"></a>Operacja menedżera debugowania sesji
 Menedżer debugowania sesji (SDM) zarządza DE. Może istnieć więcej niż jeden aparat debugowania uruchomiony na komputerze w tym samym czasie. Do multipleksowania DEs, SDM zawija szereg interfejsów z DEs i udostępnia je do IDE jako pojedynczy interfejs.

 Aby zwiększyć wydajność, niektóre interfejsy nie są multipleksowane. Zamiast tego są one używane bezpośrednio z DE i wywołania tych interfejsów nie przechodzą przez SDM. Na przykład interfejsy używane z pamięci, kodu i kontekstów dokumentu nie są multipleksowane, ponieważ odnoszą się do określonej instrukcji, pamięci lub dokumentu w określonym programie debugowane przez określonego DE. Żaden inny DE nie musi być zaangażowany w ten poziom komunikacji.

 Nie dotyczy to wszystkich kontekstów. Wywołania interfejsu kontekstu oceny wyrażenia przejść przez SDM. Podczas oceny wyrażenia SDM zawija interfejs [IDebugExpression2,](../../extensibility/debugger/reference/idebugexpression2.md) który daje do IDE, ponieważ gdy to wyrażenie jest oceniane, może obejmować wiele DEs, które są debugowanie programów w tym samym procesie, który może być uruchomiony w tym samym wątku.

 SDM zazwyczaj działa jako mechanizm delegowania, ale może działać jako mechanizm emisji. Na przykład podczas oceny wyrażenia SDM działa jako mechanizm emisji, aby powiadomić wszystkie DEs, że mogą uruchamiać kod w określonym wątku. Podobnie, gdy SDM odbiera zdarzenie zatrzymania, emituje do programów, które powinny przestać działać. Po wywołaniu kroku, SDM emituje do programów, które mogą kontynuować uruchamianie. Punkty przerwania są również nadawane do każdego DE.

 SDM nie śledzi bieżącego programu, wątku lub ramki stosu. Informacje o procesie, programie i wątku są wysyłane do SDM w połączeniu z określonymi zdarzeniami debugowania.

## <a name="see-also"></a>Zobacz też
- [Aparat debugowania](../../extensibility/debugger/debug-engine.md)
- [Składniki debugera](../../extensibility/debugger/debugger-components.md)
- [Konteksty debugera](../../extensibility/debugger/debugger-contexts.md)
