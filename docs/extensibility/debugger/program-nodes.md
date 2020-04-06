---
title: Węzły programu | Dokumenty firmy Microsoft
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
ms.openlocfilehash: 2943f74c7316495be93c2f5c20998ffa685f5d01
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738216"
---
# <a name="program-nodes"></a>Węzły programu
W architekturze debugera *węzeł programu:*

- Jest lekki opis programu.

- Może identyfikować siebie i proces, w który działa. Węzeł programu można dołączyć, być odłączone i opisać aparat debugowania (DE), który go utworzył, jeśli istnieje.

- Jest reprezentowany przez interfejs [IDebugProgramNode2,](../../extensibility/debugger/reference/idebugprogramnode2.md) zazwyczaj tworzony przez DE lub portu. Węzły programu są dodawane do portu przez wywołanie [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md). Po dodaniu węzła programu do portu jest on dodawany do procesu zawierającego program, który reprezentuje ten węzeł programu.

  Jakiś czas po uruchomieniu sesji debugowania, w zależności od implementacji pakietu debugowania, węzły programu są używane do tworzenia odpowiednich programów. Gdy proces jest wyszukiwany dla swoich programów, programy są wyliczone, po jednym dla każdego węzła programu.

  Przed dołączonym do programu IDE wymaga tylko lekki opis programu. Te informacje można uzyskać z węzła programu. Po dołączeniu programu IDE wyświetla bardziej szczegółowe informacje, takie jak lista wszystkich wątków uruchomionych w programie. Informacje te są uzyskiwane z samego programu.

## <a name="see-also"></a>Zobacz też
- [Programy](../../extensibility/debugger/programs.md)
- [Procesów](../../extensibility/debugger/processes.md)
- [Aparat debugowania](../../extensibility/debugger/debug-engine.md)
- [Pojęcia debugera](../../extensibility/debugger/debugger-concepts.md)
- [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)
- [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)
