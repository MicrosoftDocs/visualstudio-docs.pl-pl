---
title: Pojęcia dotyczące debugera | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK]
ms.assetid: 2d371d38-f1a0-4a9a-8ea3-100e8c0149b7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9ad8a450f9e79c1d44b8e098c8a00bb4b816e1af
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80738982"
---
# <a name="debugger-concepts"></a>Pojęcia dotyczące debugera
Aby skompilować pakiet do debugowania programu Visual Studio, musisz zapoznać się z pojęciami dotyczącymi architektury używanymi podczas projektowania pakietu.

## <a name="in-this-section"></a>W tej sekcji
 [Sesja debugowania](../../extensibility/debugger/debug-session.md) Wyjaśnia rolę sesji w architekturze debugowania.

 [Serwery](../../extensibility/debugger/servers-visual-studio-sdk.md) Definiuje, co serwer jest w zakresie architektury debugowania, zarówno w przypadku abstrakcyjnych, jak i fizycznych.

 [Dostawcy portów](../../extensibility/debugger/port-suppliers.md) Definiuje, co dostawca portów jest w zakresie architektury debugowania.

 [Porty](../../extensibility/debugger/ports.md) Definiuje, co port jest w zakresie architektury debugowania.

 [Procesy](../../extensibility/debugger/processes.md) Definiuje, co proces ma w przypadku architektury debugowania.

 [Węzły programu](../../extensibility/debugger/program-nodes.md) Definiuje węzeł programu pod kątem architektury debugowania, w tym sposób, w jaki może on identyfikować siebie i proces, w którym jest uruchomiony.

 [Programy](../../extensibility/debugger/programs.md) Definiuje program w odniesieniu do architektury debugowania.

 [Wątki](../../extensibility/debugger/threads.md) Definiuje charakterystykę wątków pod względem architektury debugowania.

 [Ramki stosu](../../extensibility/debugger/stack-frames.md) Definiuje ramkę stosu pod kątem architektury debugowania. Ramka stosu jest abstrakcją stosu, który zapewnia kontekst wykonywania wątku.

 [Moduły](../../extensibility/debugger/modules.md) Definiuje moduł, w odniesieniu do architektury debugowania, jako fizyczny kontener kodu, taki jak plik wykonywalny lub biblioteka DLL.

 [Punkty przerwania](../../extensibility/debugger/breakpoints-visual-studio-sdk.md) Definiuje trzy typy punktów przerwania — oczekujące, powiązane i błędy — w odniesieniu do architektury debugowania.

## <a name="related-sections"></a>Sekcje pokrewne
 [Konteksty debugera](../../extensibility/debugger/debugger-contexts.md) Wyjaśnia, w jaki sposób aparat debugowania (DE) działa jednocześnie w kontekście kodu, dokumentacji oraz kontekstów oceny wyrażenia. Opisuje dla każdego z trzech kontekstów, lokalizację, pozycję lub ocenę, która jest dla niego odpowiednia.

 [Składniki debugera](../../extensibility/debugger/debugger-components.md) Zawiera omówienie składników debugowania programu Visual Studio, które obejmują aparat debugowania (DE), ewaluatora wyrażeń (EE) i obsługę symboli (SH).

 [Debuguj zadania](../../extensibility/debugger/debugging-tasks.md) Zawiera linki do różnych zadań debugowania, takich jak uruchamianie programu i ocenianie wyrażeń.
