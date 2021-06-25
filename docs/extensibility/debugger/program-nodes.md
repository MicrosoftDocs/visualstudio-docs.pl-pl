---
title: Węzły programu | Microsoft Docs
description: W tym artykule opisano definicję i rolę węzła programu w architekturze debugera w Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- program nodes, debugging context
- debugging [Debugging SDK], program nodes
- program nodes, adding
- program nodes, superceding
ms.assetid: 1c5a5c13-c14d-42c3-af11-4c63f1032c8d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 4c26fa95a5fedf325591ce517e7c12ecebcd705c
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899085"
---
# <a name="program-nodes"></a>Węzły programu
W architekturze debugera węzeł *programu*:

- To lekki opis programu.

- Może identyfikować siebie i proces, w który jest uruchomiony. Węzeł programu można dołączyć, odłączyć i opisać aparat debugowania, który go utworzył, jeśli taki został utworzony.

- Jest reprezentowany przez [interfejs IDebugProgramNode2,](../../extensibility/debugger/reference/idebugprogramnode2.md) zazwyczaj tworzony przez DE lub port. Węzły programu są dodawane do portu przez wywołanie [funkcji AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md). Gdy węzeł programu jest dodawany do portu, jest dodawany do procesu zawierającego program, który reprezentuje ten węzeł programu.

  Gdy sesja debugowania zostanie uruchomiona, w zależności od implementacji pakietu debugowania węzły programu są używane do tworzenia odpowiednich programów. Gdy proces jest pytany o jego programy, są wyliczane programy, po jednym dla każdego węzła programu.

  Zanim program zostanie dołączony do środowiska IDE, potrzebuje tylko lekkiego opisu programu. Te informacje można uzyskać z węzła programu. Po dołączeniu programu do środowiska IDE są wyświetlane bardziej szczegółowe informacje, takie jak lista wszystkich wątków uruchomionych w programie. Te informacje są uzyskiwane z samego programu.

## <a name="see-also"></a>Zobacz też
- [Programy](../../extensibility/debugger/programs.md)
- [Procesy](../../extensibility/debugger/processes.md)
- [Aparat debugowania](../../extensibility/debugger/debug-engine.md)
- [Pojęcia dotyczące debugera](../../extensibility/debugger/debugger-concepts.md)
- [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)
- [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)
