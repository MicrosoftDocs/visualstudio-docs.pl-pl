---
title: Programy | Dokumenty firmy Microsoft
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738207"
---
# <a name="programs"></a>Programy
W architekturze debugera *program:*

- Jest kontenerem dla zestawu wątków i zestawu modułów. Program nie ma jednej analogii w systemie operacyjnym Windows.

     Program jest rodzajem podprocesu. Na przykład podczas debugowania witryny sieci Web skrypt może być postrzegany jako program. Podczas gdy skrypt jest uruchamiany w procesie aparatu skryptów, niezależnie od innych skryptów, ma również swój własny zestaw wątków. Aparat debugowania (DE) dołącza do programu, a nie do procesu lub wątku.

- Może identyfikować siebie i proces, w który działa. Program może być dołączony do, być odłączony od i opisać DE, który go utworzył, jeśli istnieje. Program może również wykonywać, zatrzymywać, kontynuować i być zakończony.

- Można wyliczyć wszystkie jego wątki. Program może również dostarczyć własny strumień demontażu i może wyliczyć wszystkie konteksty kodu danej pozycji dokumentu.

- Jest reprezentowany przez interfejs [IDebugProgram2,](../../extensibility/debugger/reference/idebugprogram2.md) utworzony przed dołączeniem programu lub jako część procesu dołączania, w zależności od implementacji. Gdy port wylicza programy procesu, każdy program jest tworzony zgodnie z odpowiednim [interfejsem IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) przekazanym jako argument do [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md). Podczas gdy aparaty `IDebugProgram2` debugowania również tworzyć interfejsy do reprezentowania programów, programy te nie są tworzone zgodnie z węzłem programu. Interfejsy `IDebugProgramNode2` utworzone przez DE są używane do rzeczywistego debugowania, podczas gdy te utworzone przez port są używane tylko do odnajdowania, które programy są uruchomione w procesie.

## <a name="see-also"></a>Zobacz też
- [Procesów](../../extensibility/debugger/processes.md)
- [Węzły programu](../../extensibility/debugger/program-nodes.md)
- [Moduły](../../extensibility/debugger/modules.md)
- [Pojęcia debugera](../../extensibility/debugger/debugger-concepts.md)
- [Aparat debugowania](../../extensibility/debugger/debug-engine.md)
- [Pozycja dokumentu](../../extensibility/debugger/document-position.md)
- [Kontekst kodu](../../extensibility/debugger/code-context.md)
- [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)
- [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)
