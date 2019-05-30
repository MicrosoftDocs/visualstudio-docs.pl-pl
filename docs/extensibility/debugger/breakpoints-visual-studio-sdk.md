---
title: Punkty przerwania (zestaw SDK programu Visual Studio) | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- breakpoints
ms.assetid: acfcabed-9f2f-436c-ad18-7ca2f45d631b
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: be901dcb4692fa556008199aeea250c9427b3167
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66332530"
---
# <a name="breakpoints-visual-studio-sdk"></a>Punkty przerwania (zestaw SDK programu Visual Studio)
Istnieją trzy typy punktów przerwania: Oczekujące, powiązaną i błędów.

 **A oczekujących punktów przerwania:**

- Jest klasą abstrakcyjną, która zawiera wszystkie informacje potrzebne, aby powiązać punkt przerwania z co najmniej jeden kontekst kodu w jednym lub wielu programów. Za każdym razem program debugowany kod przyczyny, aby załadować, aparat debugowania sprawdza wszystkich oczekujących punktów przerwania, aby zobaczyć, jeśli może być powiązana.

   Oczekujący punkt przerwania, sama nigdy nie wiąże się kod, ale raczej zbiera i jest nazywany ma zawierać wszystkie powiązane punkty przerwania, które generuje.

- Jest reprezentowany przez [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) interfejsu.

  **Powiązany punkt przerwania:**

- Jest skojarzony z klasą abstrakcyjną dla punktu przerwania lub powiązany z kontekstu pojedynczego kodu. Każdy powiązany punkt przerwania jest generowany w odpowiedzi na oczekujący punkt przerwania. Oczekujący punkt przerwania, można wygenerować więcej niż jeden powiązany punkt przerwania.

   Gdy kod jest zwolniony, powiązany punkt przerwania można niepowiązanych i odrzucone.

- Jest reprezentowany przez [IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md) interfejsu.

  **Punkt przerwania błąd:**

- Jest klasą abstrakcyjną dla opisujący błąd podczas próby powiązać oczekujący punkt przerwania kontekst kodu. Błąd punktu przerwania w tym artykule opisano albo błąd w lokalizacji lub wyrażenia punktu przerwania. Aby uzyskać więcej informacji, zobacz [Tworzenie powiązań punktów przerwania](../../extensibility/debugger/binding-breakpoints.md).

   Błąd punktu przerwania, może być błąd lub ostrzeżenie.

- Jest reprezentowany przez [IDebugErrorBreakpoint2](../../extensibility/debugger/reference/idebugerrorbreakpoint2.md) interfejsu.

## <a name="see-also"></a>Zobacz także
- [Programy](../../extensibility/debugger/programs.md)
- [Pojęcia dotyczące debugera](../../extensibility/debugger/debugger-concepts.md)
- [Kontekst kodu](../../extensibility/debugger/code-context.md)
- [IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md)
- [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
- [IDebugErrorBreakpoint2](../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)