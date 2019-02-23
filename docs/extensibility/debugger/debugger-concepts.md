---
title: Pojęcia dotyczące debugera | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK]
ms.assetid: 2d371d38-f1a0-4a9a-8ea3-100e8c0149b7
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7e3a9043215c5242246e54dc3e1eb2e85cd26c91
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56711192"
---
# <a name="debugger-concepts"></a>Pojęcia dotyczące debugera
Aby utworzyć pakiet debugowania programu Visual Studio, musisz należy zapoznać się z architektury koncepcji używanych podczas projektowania pakietu.

## <a name="in-this-section"></a>W tej sekcji
 [Sesja debugowania](../../extensibility/debugger/debug-session.md) opisano rolę sesję debugowania architektury.

 [Serwery](../../extensibility/debugger/servers-visual-studio-sdk.md) definiuje, o jaki serwer znajduje się pod względem Profilowanie architektury, w warunkach abstrakcyjny i fizycznej.

 [Port dostawców](../../extensibility/debugger/port-suppliers.md) definiuje, jakie dostawcy portu jest pod względem architektury debugowania.

 [Porty](../../extensibility/debugger/ports.md) definiuje, jakie port jest pod względem architektury debugowania.

 [Procesy](../../extensibility/debugger/processes.md) definiuje, jakie procesy są pod względem architektury debugowania.

 [Program węzłów](../../extensibility/debugger/program-nodes.md) definiuje węzeł program pod względem Profilowanie architektury, w tym, jak można zidentyfikować, proces jest uruchomiony w wraz z.

 [Programy](../../extensibility/debugger/programs.md) definiuje program pod względem architektury debugowania.

 [Wątki](../../extensibility/debugger/threads.md) określa właściwości wątków pod względem architektury debugowania.

 [Ramek stosu](../../extensibility/debugger/stack-frames.md) definiuje ramki stosu w zakresie debugowania architektury. Ramka stosu jest klasą abstrakcyjną stosu, które dostarcza kontekst wykonanie wątku.

 [Moduły](../../extensibility/debugger/modules.md) definiuje moduł, pod kątem debugowania architektury, jako kontenera fizycznego kodu, takie jak plik wykonywalny lub bibliotekę DLL.

 [Punkty przerwania](../../extensibility/debugger/breakpoints-visual-studio-sdk.md) definiuje trzy rodzaje punkty przerwania — oczekujące granicy, a błąd — pod względem architektury debugowania.

## <a name="related-sections"></a>Sekcje pokrewne
 [Konteksty debugera](../../extensibility/debugger/debugger-contexts.md) wyjaśnia, jak aparat debugowania (DE) działa jednocześnie w kontekstach oceny kodu, dokumentację i wyrażenia. W tym artykule opisano, dla każdego z trzech kontekstów, lokalizacji, pozycja lub oceny odpowiednie do niego.

 [Składniki debugera](../../extensibility/debugger/debugger-components.md) zawiera omówienie składników debugowania programu Visual Studio, które obejmują aparat debugowania (DE), Ewaluator wyrażeń (EE) i obsługi symboli (SH).

 [Debugowanie zadań](../../extensibility/debugger/debugging-tasks.md) zawiera łącza do różnych zadań debugowania, takich jak uruchamianie programu i wyrażeń.