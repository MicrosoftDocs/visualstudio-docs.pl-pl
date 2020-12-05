---
title: Węzły programu | Microsoft Docs
description: W tym artykule opisano definicje i rolę węzła programu w architekturze debugera w programie Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- program nodes, debugging context
- debugging [Debugging SDK], program nodes
- program nodes, adding
- program nodes, superceding
ms.assetid: 1c5a5c13-c14d-42c3-af11-4c63f1032c8d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d2f3694eff6cd48cc01c0e244d3a068f3bb13fda
ms.sourcegitcommit: 42981ace63c0f2b087de5703ca76b8dcdd93a719
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/04/2020
ms.locfileid: "96606492"
---
# <a name="program-nodes"></a>Węzły programu
W architekturze debugera, *węzeł programu*:

- Jest lekkim opisem programu.

- Może identyfikować siebie i proces, w którym jest uruchomiona. Węzeł programu może być dołączony do, odłączony od i opisywany aparat debugowania (DE), który go utworzył (jeśli istnieje).

- Jest reprezentowany przez interfejs [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) , zwykle tworzony przez de lub port. Węzły programu są dodawane do portu przez wywołanie [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md). Gdy węzeł programu zostanie dodany do portu, zostaje dodany do procesu zawierającego program, który reprezentuje ten węzeł programu.

  Czasami po rozpoczęciu sesji debugowania, w zależności od implementacji pakietu debugowania, węzły programu są używane do tworzenia odpowiednich programów. Po wykonaniu zapytania dotyczącego jego programów wyliczane są programy, po jednej dla każdego węzła programu.

  Przed dołączeniem programu do środowiska IDE wymaga tylko lekkiego opisu programu. Te informacje można uzyskać z węzła program. Po dołączeniu programu do środowiska IDE wyświetla bardziej szczegółowe informacje, takie jak lista wszystkich wątków uruchomionych w programie. Te informacje są uzyskiwane z samego programu.

## <a name="see-also"></a>Zobacz także
- [Programy](../../extensibility/debugger/programs.md)
- [Procesy](../../extensibility/debugger/processes.md)
- [Aparat debugowania](../../extensibility/debugger/debug-engine.md)
- [Pojęcia dotyczące debugera](../../extensibility/debugger/debugger-concepts.md)
- [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)
- [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)
