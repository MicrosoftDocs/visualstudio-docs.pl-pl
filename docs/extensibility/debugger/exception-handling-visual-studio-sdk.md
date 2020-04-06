---
title: Obsługa wyjątków (visual studio SDK) | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], exception handling
ms.assetid: 7279dc16-db14-482c-86b8-7b3da5a581d2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 34b83c7181a7ba405e642d9911e2c53df3f4401d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738761"
---
# <a name="exception-handling-visual-studio-sdk"></a>Obsługa wyjątków (visual studio SDK)
Poniżej opisano proces, który występuje, gdy są zgłaszane wyjątki.

## <a name="exception-handling-process"></a>Proces obsługi wyjątków

1. Gdy wyjątek jest najpierw zgłaszany, ale zanim zostanie obsłużony przez program obsługi wyjątków w debugowane programu, aparat debugowania (DE) wysyła [IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md) do menedżera debugowania sesji (SDM) jako zdarzenie zatrzymania. Jest `IDebugExceptionEvent2` wysyłany, jeśli tylko ustawienia wyjątku (określone w oknie dialogowym Wyjątki w pakiecie debugowania) określają, że użytkownik chce zatrzymać powiadomienia o wyjątkach pierwszej szansy.

2. SDM wywołuje [IDebugExceptionEvent2::GetException,](../../extensibility/debugger/reference/idebugexceptionevent2-getexception.md) aby uzyskać właściwość wyjątku.

3. Pakiet debugowania wywołuje [IDebugExceptionEvent2::CanPassToDebuggee,](../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md) aby określić, jakie opcje przedstawić użytkownikowi.

4. Pakiet debugowania pyta użytkownika, jak obsługiwać wyjątek, otwierając okno dialogowe wyjątku pierwszej szansy.

5. Jeśli użytkownik zdecyduje się kontynuować, SDM wywołuje [IDebugExceptionEvent2::CanPassToDebuggee](../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md).

    - Jeśli metoda zwraca S_OK, wywołuje [IDebugExceptionEvent2::PassToDebuggee](../../extensibility/debugger/reference/idebugexceptionevent2-passtodebuggee.md).

         — lub —

         Jeśli metoda zwraca S_FALSE, program debugowany otrzymuje drugą szansę na obsługę wyjątku.

6. Jeśli program debugowany nie ma obsługi dla wyjątku drugiej szansy, DE wysyła `IDebugExceptionEvent2` do SDM jako **EVENT_SYNC_STOP**.

7. Pakiet debugowania pyta użytkownika, jak obsługiwać wyjątek, otwierając okno dialogowe wyjątku pierwszej szansy.

8. Pakiet debugowania wywołuje [IDebugExceptionEvent2::CanPassToDebuggee,](../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md) aby określić, jakie opcje przedstawić użytkownikowi.

9. Pakiet debugowania pyta użytkownika, jak obsługiwać wyjątek, otwierając okno dialogowe wyjątku drugiej szansy.

10. Jeśli metoda zwraca S_OK, wywołuje `IDebugExceptionEvent2::PassToDebuggee`.

## <a name="see-also"></a>Zobacz też
- [Wywoływanie zdarzeń debugera](../../extensibility/debugger/calling-debugger-events.md)
