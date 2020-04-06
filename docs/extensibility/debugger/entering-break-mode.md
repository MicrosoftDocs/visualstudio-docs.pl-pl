---
title: Wejście w tryb przerwania | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- break mode
- debugging [Debugging SDK], entering break mode
ms.assetid: e9a8a241-cd21-4d4e-999a-283554c288b1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4bbcec8adf6468f70d95df5f291ce1e5540406cf
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738876"
---
# <a name="enter-break-mode"></a>Wprowadź tryb przerwania
Następujące informacje opisują proces, który występuje, gdy punkt przerwania występuje po przejściu do funkcji, uruchomiony do wiersza kodu źródłowego, który ma kursor w nim lub działa do punktu przerwania.

## <a name="break-mode-process"></a>Proces trybu przerwania

1. Aparat debugowania (DE) wysyła [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md), [IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md)lub inne zdarzenie zatrzymania spowodować IDE do trybu przerwania.

2. SDM pobiera informacje stos wywołań z wątku, w następujący sposób:

    - [IDebugThread2::EnumFrameInfo](../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)

    - [IEnumDebugFrameInfo2::GetCount](../../extensibility/debugger/reference/ienumdebugframeinfo2-getcount.md)

    - [IEnumDebugFrameInfo2::Next](../../extensibility/debugger/reference/ienumdebugframeinfo2-next.md)

    - [IDebugStackFrame2::GetDocumentContext,](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md) aby uzyskać informacje o kodzie źródłowym

    - [IDebugDocumentContext2:GetName,](../../extensibility/debugger/reference/idebugdocumentcontext2-getname.md) aby uzyskać nazwę pliku

    - [IDebugDocumentContext2:GetStatementRange,](../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md) aby uzyskać zakres instrukcji

    - [IDebugStackFrame2::GetCodeContext,](../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md) aby uzyskać informacje o pamięci

## <a name="see-also"></a>Zobacz też
- [Wywoływanie zdarzeń debugera](../../extensibility/debugger/calling-debugger-events.md)
