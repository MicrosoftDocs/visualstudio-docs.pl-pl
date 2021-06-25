---
title: Menedżer debugowania sesji | Microsoft Docs
description: Dowiedz się więcej o menedżerze debugowania sesji, który zarządza wieloma aparatami debugowania debugowania w wielu procesach na dowolnej liczbie maszyn.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- session debug manager, unifying session views
- session debug manager, broadcasting
- debugging [Debugging SDK], session debug manager
- session debug manager
- session debug manager, debug engine multiplexing
- session debug manager, delegating
ms.assetid: fbb1928d-dddc-43d1-98a4-e23b0ecbae09
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 217a2d401e61c58a58d958bb754265a19a2a367d
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112902088"
---
# <a name="session-debug-manager"></a>Menedżer debugowania sesji
Menedżer debugowania sesji (SDM) zarządza dowolną liczbą aparatów debugowania(DE), które debugują dowolną liczbę programów w wielu procesach na dowolnej liczbie maszyn. Oprócz multipleksera aparatu debugowania, program SDM zapewnia ujednolicony widok sesji debugowania środowiska IDE.

## <a name="session-debug-manager-operation"></a>Operacja menedżera debugowania sesji
 Menedżer debugowania sesji (SDM) zarządza DE. Na maszynie może działać jednocześnie więcej niż jeden aparat debugowania. Aby multipleksować środowiska DE, program SDM opakowywuje wiele interfejsów z tych obiektów i uwidacznia je w ide jako pojedynczy interfejs.

 Aby zwiększyć wydajność, niektóre interfejsy nie są multipleksowane. Zamiast tego są one używane bezpośrednio z DE i wywołania do tych interfejsów nie przechodzi przez SDM. Na przykład interfejsy używane z pamięcią, kodem i kontekstami dokumentu nie są multipleksowane, ponieważ odwołują się do określonej instrukcji, pamięci lub dokumentu w określonym programie debugowany przez określone de. Żaden inny de nie musi być zaangażowany w ten poziom komunikacji.

 Nie dotyczy to wszystkich kontekstów. Wywołania interfejsu kontekstu oceny wyrażeń są przechodzić przez sdm. Podczas oceny wyrażeń program SDM opakowywuje interfejs [IDebugExpression2,](../../extensibility/debugger/reference/idebugexpression2.md) który przekazuje do środowiska IDE, ponieważ podczas oceny tego wyrażenia może obejmować wiele obiektów DE, które debugują programy w tym samym procesie, które mogą być uruchomione w tym samym wątku.

 SdM zazwyczaj działa jako mechanizm delegowania, ale może działać jako mechanizm emisji. Na przykład podczas oceny wyrażeń SDM działa jako mechanizm emisji, aby powiadomić wszystkie interfejsy DE, że mogą uruchamiać kod w określonym wątku. Podobnie, gdy program SDM odbiera zdarzenie zatrzymania, jest emitowany do programów, które powinny przestać działać. Po wywołaniu kroku program SDM emituje do programów, które mogą nadal działać. Punkty przerwania są również rozgłaszane do każdego de.

 Program SDM nie śledzi bieżącego programu, wątku ani ramki stosu. Informacje o procesie, programie i wątku są wysyłane do narzędzia SDM w połączeniu z określonymi zdarzeniami debugowania.

## <a name="see-also"></a>Zobacz też
- [Aparat debugowania](../../extensibility/debugger/debug-engine.md)
- [Składniki debugera](../../extensibility/debugger/debugger-components.md)
- [Konteksty debugera](../../extensibility/debugger/debugger-contexts.md)
