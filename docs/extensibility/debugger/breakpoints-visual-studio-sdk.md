---
title: Punkty przerwania (zestaw SDK programu Visual Studio) | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- breakpoints
ms.assetid: acfcabed-9f2f-436c-ad18-7ca2f45d631b
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4c353ca11df1a897ec5dc8acecd822c1c1f44e92
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62890701"
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