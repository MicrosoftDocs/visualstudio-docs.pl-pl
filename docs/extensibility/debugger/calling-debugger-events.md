---
title: Wywoływanie zdarzeń debugera | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], events
ms.assetid: b3440ac3-80af-40c6-bef4-cbf00fa67885
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 869bd87952aebf8ad640c5aeb439c9e99929f4c1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739164"
---
# <a name="call-debugger-events"></a>Wywoływanie zdarzeń debugera
Zdarzenia w sesjach debugowania występują w określonej kolejności.

## <a name="discussion"></a>Dyskusji
 Aby zrozumieć wzorzec wywołań między aparatem debugowania (DE) i menedżerem debugowania sesji (SDM), następujące reprezentuje kolejność wywoływania zdarzeń występujących w typowej sesji debugowania:

1. [Dołączanie i odłączanie do programu](../../extensibility/debugger/attaching-and-detaching-to-a-program.md)

2. [Uruchamianie debugera](../../extensibility/debugger/launching-the-debugger.md)

3. [Kończenie programu](../../extensibility/debugger/terminating-a-program.md)

4. [Tworzenie punktu przerwania](../../extensibility/debugger/creating-a-breakpoint.md)

5. [Gdy punkt przerwania wiąże się lub staje się niezwiązany](../../extensibility/debugger/when-a-breakpoint-binds-or-becomes-unbound.md)

6. [Błędy punktu przerwania](../../extensibility/debugger/breakpoint-errors.md)

7. [Trafienie w punkt przerwania](../../extensibility/debugger/hitting-a-breakpoint.md)

8. [Usuwanie punktu przerwania](../../extensibility/debugger/deleting-a-breakpoint.md)

9. [Wprowadzanie trybu przerwania](../../extensibility/debugger/entering-break-mode.md)

10. [Przechodzenie w trybie przerwania](../../extensibility/debugger/stepping-in-break-mode.md)

11. [Ocena wyrażenia w trybie przerwania](../../extensibility/debugger/expression-evaluation-in-break-mode.md)

12. [Obsługa wyjątków](../../extensibility/debugger/exception-handling-visual-studio-sdk.md)

## <a name="see-also"></a>Zobacz też
- [Tworzenie niestandardowego aparatu debugowania](../../extensibility/debugger/creating-a-custom-debug-engine.md)
