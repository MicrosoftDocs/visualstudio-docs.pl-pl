---
title: Pojęcia dotyczące debugera | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK]
ms.assetid: 2d371d38-f1a0-4a9a-8ea3-100e8c0149b7
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0f8dd5567fb21fafbac3c63b84dae1e0e33b0b91
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "68200618"
---
# <a name="debugger-concepts"></a>Pojęcia dotyczące debugera
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Aby utworzyć pakiet debugowania programu Visual Studio, musisz należy zapoznać się z architektury koncepcji używanych podczas projektowania pakietu.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Sesja debugowania](../../extensibility/debugger/debug-session.md)  
 W tym artykule wyjaśniono roli w architekturze debugowania sesji.  
  
 [Serwery](../../extensibility/debugger/servers-visual-studio-sdk.md)  
 Określa, jakie serwer znajduje się pod względem Profilowanie architektury, w warunkach abstrakcyjny i fizycznej.  
  
 [Dostawcy portów](../../extensibility/debugger/port-suppliers.md)  
 Definiuje, jakie dostawcy portu jest pod względem architektury debugowania.  
  
 [Porty](../../extensibility/debugger/ports.md)  
 Określa port usługi jest pod względem architektury debugowania.  
  
 [Procesy](../../extensibility/debugger/processes.md)  
 Określa, jakie procesy są pod względem architektury debugowania.  
  
 [Węzły programu](../../extensibility/debugger/program-nodes.md)  
 Definiuje węzeł program pod względem architektury, w tym, jak można zidentyfikować wraz z procesu, który jest uruchomiony w debugowaniu.  
  
 [Programy](../../extensibility/debugger/programs.md)  
 Określa program pod względem architektury debugowania.  
  
 [Wątki](../../extensibility/debugger/threads.md)  
 Definiuje właściwości wątków pod względem architektury debugowania.  
  
 [Ramki stosu](../../extensibility/debugger/stack-frames.md)  
 Definiuje ramki stosu w zakresie debugowania architektury. Ramka stosu jest klasą abstrakcyjną stosu, które dostarcza kontekst wykonanie wątku.  
  
 [Moduły](../../extensibility/debugger/modules.md)  
 Definiuje moduł pod względem Profilowanie architektury, jako fizyczny kontenera kodu, takie jak plik wykonywalny lub bibliotekę DLL.  
  
 [Punkty przerwania](../../extensibility/debugger/breakpoints-visual-studio-sdk.md)  
 Definiuje trzy rodzaje punkty przerwania — oczekiwanie, powiązaną i błąd — pod względem architektury debugowania.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Konteksty debugera](../../extensibility/debugger/debugger-contexts.md)  
 W tym artykule wyjaśniono, jak aparat debugowania (DE) działa jednocześnie w ramach kodu, dokumentację i konteksty oceny wyrażenia. W tym artykule opisano, dla każdego z trzech kontekstów, lokalizacji, pozycja lub oceny odpowiednie do niego.  
  
 [Składniki debugera](../../extensibility/debugger/debugger-components.md)  
 Zawiera omówienie składników debugowania programu Visual Studio, które obejmują aparat debugowania (DE), Ewaluator wyrażeń (EE) i obsługi symboli (SH).  
  
 [Zadania debugowania](../../extensibility/debugger/debugging-tasks.md)  
 Zawiera łącza do różnych zadań debugowania, takie jak uruchamianie programu i wyrażeń.
