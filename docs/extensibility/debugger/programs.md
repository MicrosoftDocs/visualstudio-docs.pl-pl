---
title: Programy | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], programs
- programs, debugging
ms.assetid: e1f955d8-95da-493b-837e-e97741a26d7e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d3fd1db5add74d2d94467e1f369916feb5f30d4a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80738207"
---
# <a name="programs"></a>Programy
W architekturze debugera, *program*:

- Jest kontenerem dla zestawu wątków i zestawu modułów. Program nie ma pojedynczej analogu w systemie operacyjnym Windows.

     Program jest rodzajem podprocesu. Na przykład podczas debugowania witryny sieci Web skrypt może być traktowany jako program. Skrypt jest uruchamiany w procesie aparatu skryptów, niezależnie od innych skryptów, również ma swój własny zestaw wątków. Aparat debugowania (DE) dołącza do programu, a nie do procesu lub wątku.

- Może identyfikować siebie i proces, w którym jest uruchomiona. Program może zostać dołączony do, zostać odłączony od i opisany dla DE, który go utworzył. Program może również wykonywać, zatrzymywać, kontynuować i być zakończony.

- Może wyliczyć wszystkie jej wątki. Program może również dostarczyć swój własny strumień demontażu i może wyliczyć wszystkie konteksty kodu danego położenia dokumentu.

- Jest reprezentowany przez interfejs [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) , utworzony przed dołączeniem programu lub jako część procesu dołączania, w zależności od implementacji. Gdy port wylicza programy, każdy program jest tworzony zgodnie z odpowiednim interfejsem [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) przekazaną jako argument do [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md). Chociaż aparaty debugowania również tworzą `IDebugProgram2` interfejsy do reprezentowania programów, te programy nie są tworzone zgodnie z węzłem programu. `IDebugProgramNode2`Interfejsy utworzone przez de są używane do rzeczywistego debugowania, podczas gdy te utworzone przez port są używane tylko do odnajdywania programów uruchomionych w procesie.

## <a name="see-also"></a>Zobacz też
- [Procesy](../../extensibility/debugger/processes.md)
- [Węzły programu](../../extensibility/debugger/program-nodes.md)
- [Moduły](../../extensibility/debugger/modules.md)
- [Pojęcia dotyczące debugera](../../extensibility/debugger/debugger-concepts.md)
- [Aparat debugowania](../../extensibility/debugger/debug-engine.md)
- [Położenie dokumentu](../../extensibility/debugger/document-position.md)
- [Kontekst kodu](../../extensibility/debugger/code-context.md)
- [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)
- [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)
