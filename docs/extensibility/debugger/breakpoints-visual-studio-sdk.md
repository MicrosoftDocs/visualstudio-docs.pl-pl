---
title: Punkty przerwania (Visual Studio SDK) | Microsoft Docs
description: 'Dowiedz się więcej o trzech typach punktów przerwania: oczekujących, powiązanych i błędnych. W tym artykule wymieniono interfejsy używane do implementowanie typów.'
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- breakpoints
ms.assetid: acfcabed-9f2f-436c-ad18-7ca2f45d631b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 1fce472faf95aa77f87ab02d78a3da640b6bd3bf
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112901490"
---
# <a name="breakpoints-visual-studio-sdk"></a>Punkty przerwania (zestaw SDK programu Visual Studio)
Istnieją trzy typy punktów przerwania: oczekujące, powiązane i błędy.

 **Oczekujący punkt przerwania:**

- Jest abstrakcją zawierającą wszystkie informacje potrzebne do powiązania punktu przerwania z co najmniej jednym kontekstem kodu w co najmniej jednym programie. Za każdym razem, gdy debugowany program powoduje załadowanie kodu, aparat debugowania sprawdza wszystkie oczekujące punkty przerwania, aby sprawdzić, czy można je powiązywać.

   Oczekujący punkt przerwania nigdy nie jest powiązany z kodem, ale zamiast tego zbiera i jest mówiny, że zawiera wszystkie powiązane punkty przerwania, które generuje.

- Jest reprezentowany przez [interfejs IDebugPendingBreakpoint2.](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)

  **Powiązany punkt przerwania:**

- Jest abstrakcją dla punktu przerwania skojarzonego z pojedynczym kontekstem kodu lub powiązanego z nim. Każdy powiązany punkt przerwania jest generowany w odpowiedzi na oczekujący punkt przerwania. Oczekujący punkt przerwania może jednak wygenerować więcej niż jeden powiązany punkt przerwania.

   Gdy kod jest zwalniany, powiązany punkt przerwania może być niepowiązany i odrzucony.

- Jest reprezentowany przez [interfejs IDebugBoundBreakpoint2.](../../extensibility/debugger/reference/idebugboundbreakpoint2.md)

  **Punkt przerwania błędu:**

- Jest abstrakcją do opisywania błędu podczas próby powiązania oczekującego punktu przerwania z kontekstem kodu. Punkt przerwania błędu opisuje błąd w lokalizacji lub w wyrażeniu punktu przerwania. Aby uzyskać więcej informacji, zobacz [Wiązanie punktów przerwania](../../extensibility/debugger/binding-breakpoints.md).

   Błąd punktu przerwania może być błędem lub ostrzeżeniem.

- Jest reprezentowany przez [interfejs IDebugErrorBreakpoint2.](../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)

## <a name="see-also"></a>Zobacz też
- [Programy](../../extensibility/debugger/programs.md)
- [Pojęcia dotyczące debugera](../../extensibility/debugger/debugger-concepts.md)
- [Kontekst kodu](../../extensibility/debugger/code-context.md)
- [IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md)
- [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
- [IDebugErrorBreakpoint2](../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)
