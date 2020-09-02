---
title: Menedżer debugowania sesji | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
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
manager: jillfra
ms.openlocfilehash: 9fd7c7555c19f850a15161f6fba00b1184621a9e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68157825"
---
# <a name="session-debug-manager"></a>Menedżer debugowania sesji
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Menedżer debugowania sesji (SDM) zarządza dowolną liczbą aparatów debugowania (DE), co umożliwia debugowanie dowolnej liczby programów w wielu procesach na dowolnej liczbie komputerów. Oprócz jako multiplekser aparatu debugowania model SDM zapewnia ujednolicony widok sesji debugowania do IDE.  
  
## <a name="session-debug-manager-operation"></a>Operacja Menedżera debugowania sesji  
 Menedżer debugowania sesji (SDM) zarządza. W tym samym czasie może istnieć więcej niż jeden aparat debugowania uruchomiony na komputerze. W celu multipleksera algorytmu DEs model SDM zawija wiele interfejsów z algorytmu DEs i udostępnia je środowisku IDE jako pojedynczy interfejs.  
  
 W celu zwiększenia wydajności niektóre interfejsy nie są multiplekserne. Zamiast tego są one używane bezpośrednio z programu i wywołania tych interfejsów nie przechodzą przez model SDM. Na przykład interfejsy używane z atrybutami Memory, Code i Document nie są multiplekserne, ponieważ odnoszą się do konkretnej instrukcji, pamięci lub dokumentu w określonym programie debugowanym przez określony element DE. Żadne inne nie muszą być związane z tym poziomem komunikacji.  
  
 Nie dotyczy to wszystkich kontekstów. Wywołania interfejsu kontekstu oceny wyrażenia przechodzą przez model SDM. Podczas obliczania wyrażenia model SDM otacza Interfejs [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) , który zapewnia IDE, ponieważ w przypadku obliczenia tego wyrażenia może zaistnieć wiele des, które są debugowaniem programów w tym samym procesie, które mogą być uruchomione w tym samym wątku.  
  
 Model SDM zazwyczaj działa jako mechanizm delegowania, ale może działać jako mechanizm emisji. Na przykład podczas obliczania wyrażenia SDM działa jako mechanizm emisji, aby powiadomić wszystkie DEs, że mogą uruchamiać kod w określonym wątku. Podobnie, gdy model SDM odbiera zdarzenie zatrzymania, emituje wszystkie programy, które powinny przestać działać. Gdy krok jest wywoływany, model SDM emituje wszystkie programy, które mogą nadal działać. Punkty przerwania są również emitowane do każdej z nich.  
  
 Model SDM nie śledzi bieżącego programu, wątku lub ramki stosu. Informacje o procesie, programie i wątku są wysyłane do modelu SDM w połączeniu z określonymi zdarzeniami debugowania.  
  
## <a name="see-also"></a>Zobacz też  
 [Aparat debugowania](../../extensibility/debugger/debug-engine.md)   
 [Składniki debugera](../../extensibility/debugger/debugger-components.md)   
 [Konteksty debugera](../../extensibility/debugger/debugger-contexts.md)
