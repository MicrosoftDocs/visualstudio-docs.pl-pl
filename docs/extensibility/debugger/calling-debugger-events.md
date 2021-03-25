---
title: Wywoływanie zdarzeń debugera | Microsoft Docs
description: Zdarzenia w debugowaniu sesji odbywają się w określonej kolejności. W tym artykule przedstawiono kolejność wywoływania zdarzeń występujących w typowej sesji debugowania.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- debugging [Debugging SDK], events
ms.assetid: b3440ac3-80af-40c6-bef4-cbf00fa67885
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 5b0c3169039115432758cfdcd3f0612c3578b74c
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105055054"
---
# <a name="call-debugger-events"></a>Zdarzenia debugera wywołań
Zdarzenia w debugowaniu sesji odbywają się w określonej kolejności.

## <a name="discussion"></a>Dyskusja
 Aby zrozumieć wzorzec wywołań między aparatem debugowania (DE) i menedżerem debugowania sesji (SDM), poniżej przedstawiono kolejność wywoływania zdarzeń występujących w typowej sesji debugowania:

1. [Dołączanie i odłączanie do programu](../../extensibility/debugger/attaching-and-detaching-to-a-program.md)

2. [Uruchamianie debugera](../../extensibility/debugger/launching-the-debugger.md)

3. [Kończenie programu](../../extensibility/debugger/terminating-a-program.md)

4. [Tworzenie punktu przerwania](../../extensibility/debugger/creating-a-breakpoint.md)

5. [Gdy punkt przerwania tworzy powiązanie lub staje się niepowiązane](../../extensibility/debugger/when-a-breakpoint-binds-or-becomes-unbound.md)

6. [Błędy punktów przerwania](../../extensibility/debugger/breakpoint-errors.md)

7. [Naciśnięcie punktu przerwania](../../extensibility/debugger/hitting-a-breakpoint.md)

8. [Usuwanie punktu przerwania](../../extensibility/debugger/deleting-a-breakpoint.md)

9. [Wchodzenie w tryb przerwania](../../extensibility/debugger/entering-break-mode.md)

10. [Krokowe przechodzenie w tryb przerwania](../../extensibility/debugger/stepping-in-break-mode.md)

11. [Obliczanie wyrażeń w trybie przerwania](../../extensibility/debugger/expression-evaluation-in-break-mode.md)

12. [Obsługa wyjątków](../../extensibility/debugger/exception-handling-visual-studio-sdk.md)

## <a name="see-also"></a>Zobacz też
- [Tworzenie niestandardowego aparatu debugowania](../../extensibility/debugger/creating-a-custom-debug-engine.md)
