---
title: Programy | Microsoft Docs
description: W tym artykule opisano definicję i rolę programu w architekturze debugera w Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debugging [Debugging SDK], programs
- programs, debugging
ms.assetid: e1f955d8-95da-493b-837e-e97741a26d7e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 07b23fbafd9342b555e2578c4bc0401371e30785
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112901282"
---
# <a name="programs"></a>Programy
W architekturze debugera *program*:

- Jest kontenerem dla zestawu wątków i zestawu modułów. Program nie ma jednej analogii w systemie operacyjnym Windows.

     Program jest rodzajem podprocesu. Na przykład podczas debugowania witryny internetowej skrypt może być widoczny jako program. Skrypt jest uruchamiany w procesie aparatu obsługi skryptów, niezależnie od innych skryptów, ale ma również własny zestaw wątków. Aparat debugowania (DE) jest dołączany do programu, a nie do procesu lub wątku.

- Może identyfikować siebie i proces, w jaki jest uruchomiony. Program można dołączyć, odłączyć od i opisać DE, który go utworzył, jeśli jest. Program może również wykonywać, zatrzymywać, kontynuować i kończyć.

- Może wyliczyć wszystkie swoje wątki. Program może również dostarczać własny strumień dezmisembmu i może wyliczać wszystkie konteksty kodu dla danego położenia dokumentu.

- Jest reprezentowany przez [interfejs IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) utworzony przed dołączeniu programu lub w ramach procesu dołączania, w zależności od implementacji. Gdy port wylicza programy procesu, każdy program jest tworzony zgodnie z odpowiednim interfejsem [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) przekazywanym jako argument do [addProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md). Aparaty debugowania również tworzą interfejsy do reprezentowania programów, ale nie są tworzone `IDebugProgram2` zgodnie z węzłem programu. Interfejsy utworzone przez de są używane do rzeczywistego debugowania, podczas gdy te utworzone przez port są używane tylko do odnajdywania programów uruchomionych `IDebugProgramNode2` w procesie.

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
