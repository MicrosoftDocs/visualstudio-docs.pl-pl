---
title: Punkty przerwania (visual studio SDK) | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- breakpoints
ms.assetid: acfcabed-9f2f-436c-ad18-7ca2f45d631b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7c9d61c82886f237e8c9f544a59d8fe167548277
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739190"
---
# <a name="breakpoints-visual-studio-sdk"></a>Punkty przerwania (zestaw SDK programu Visual Studio)
Istnieją trzy typy punktów przerwania: oczekujące, powiązane i błąd.

 **Oczekujący punkt przerwania:**

- Jest abstrakcją, która zawiera wszystkie informacje potrzebne do powiązania punktu przerwania z co najmniej jednym kontekstem kodu w jednym lub kilku programach. Za każdym razem, gdy program jest debugowany spowodować załadowanie kodu, aparat debugowania sprawdza wszystkie oczekujące punkty przerwania, aby sprawdzić, czy mogą być powiązane.

   Oczekujący punkt przerwania sam nigdy nie wiąże się z kodem, ale raczej zbiera i mówi się, że zawiera wszystkie powiązane punkty przerwania, które generuje.

- Jest reprezentowana przez interfejs [IDebugPendingBreakpoint2.](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)

  **Powiązany punkt przerwania:**

- Jest abstrakcją dla punktu przerwania skojarzonego z kontekstem pojedynczego kodu lub powiązanego z nim. Każdy powiązany punkt przerwania jest generowany w odpowiedzi na oczekujący punkt przerwania. Oczekujący punkt przerwania może jednak wygenerować więcej niż jeden powiązany punkt przerwania.

   Gdy kod jest zwalniany, powiązany punkt przerwania może być niezwiązany i odrzucony.

- Jest reprezentowany przez interfejs [IDebugBoundBreakpoint2.](../../extensibility/debugger/reference/idebugboundbreakpoint2.md)

  **Punkt przerwania błędu:**

- Jest abstrakcja opisujące błąd podczas próby powiązania oczekującego punktu przerwania do kontekstu kodu. Punkt przerwania błędu opisuje błąd w lokalizacji lub w samym wyrażeniu punktu przerwania. Aby uzyskać więcej informacji, zobacz [Powiązanie punktów przerwania](../../extensibility/debugger/binding-breakpoints.md).

   Błąd punktu przerwania może być błędem lub ostrzeżeniem.

- Jest reprezentowany przez interfejs [IDebugErrorBreakpoint2.](../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)

## <a name="see-also"></a>Zobacz też
- [Programy](../../extensibility/debugger/programs.md)
- [Pojęcia debugera](../../extensibility/debugger/debugger-concepts.md)
- [Kontekst kodu](../../extensibility/debugger/code-context.md)
- [IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md)
- [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
- [IDebugErrorBreakpoint2](../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)
