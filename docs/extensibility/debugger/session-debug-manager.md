---
title: Menedżer debugowania sesji | Microsoft Docs
description: Informacje o Menedżerze debugowania sesji, które zarządza wieloma aparatami debugowania debugowanie programów w wielu procesach na dowolnej liczbie komputerów.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d67716f78249bda5d316ffde175b80f4ef1c1e45
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99960783"
---
# <a name="session-debug-manager"></a>Menedżer debugowania sesji
Menedżer debugowania sesji (SDM) zarządza dowolną liczbą aparatów debugowania (DE), które są debugowaniem dowolnej liczby programów w wielu procesach na dowolnej liczbie maszyn. Oprócz jako multiplekser aparatu debugowania model SDM zapewnia ujednolicony widok sesji debugowania do IDE.

## <a name="session-debug-manager-operation"></a>Operacja Menedżera debugowania sesji
 Menedżer debugowania sesji (SDM) zarządza. W tym samym czasie może istnieć więcej niż jeden aparat debugowania uruchomiony na komputerze. W celu multipleksera algorytmu DEs model SDM zawija wiele interfejsów z algorytmu DEs i udostępnia je środowisku IDE jako pojedynczy interfejs.

 W celu zwiększenia wydajności niektóre interfejsy nie są multiplekserne. Zamiast tego są one używane bezpośrednio z programu, a wywołania do tych interfejsów nie przechodzą przez model SDM. Na przykład interfejsy używane z pamięcią, kod i konteksty dokumentu nie są multipleksne, ponieważ odnoszą się do określonej instrukcji, pamięci lub dokumentu w określonym programie debugowanym przez określony element DE. Żadne inne nie muszą być związane z tym poziomem komunikacji.

 Nie dotyczy to wszystkich kontekstów. Wywołania interfejsu kontekstu oceny wyrażenia przechodzą przez model SDM. Podczas obliczania wyrażenia model SDM otacza Interfejs [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) , który zapewnia IDE, ponieważ w przypadku obliczenia tego wyrażenia może zaistnieć wiele des, które są debugowaniem programów w tym samym procesie, które mogą być uruchomione w tym samym wątku.

 Model SDM zazwyczaj działa jako mechanizm delegowania, ale może działać jako mechanizm emisji. Na przykład podczas obliczania wyrażenia SDM działa jako mechanizm emisji, aby powiadomić wszystkie DEs, że mogą uruchamiać kod w określonym wątku. Podobnie, gdy model SDM odbiera zdarzenie zatrzymania, emituje je do programów, które powinny przestać działać. Gdy krok jest wywoływany, model SDM emituje do programów, które mogą być nadal uruchomione. Punkty przerwania są również emitowane do każdej z nich.

 Model SDM nie śledzi bieżącego programu, wątku lub ramki stosu. Informacje o procesie, programie i wątku są wysyłane do modelu SDM w połączeniu z określonymi zdarzeniami debugowania.

## <a name="see-also"></a>Zobacz też
- [Aparat debugowania](../../extensibility/debugger/debug-engine.md)
- [Składniki debugera](../../extensibility/debugger/debugger-components.md)
- [Konteksty debugera](../../extensibility/debugger/debugger-contexts.md)
