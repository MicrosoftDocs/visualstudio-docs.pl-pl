---
title: Punkty przerwania (Visual Studio SDK) | Microsoft Docs
description: 'Poznaj trzy typy punktów przerwania: oczekujące, powiązane i błędy. W tym artykule wymieniono interfejsy używane do implementowania typów.'
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 8d266bb97b6d3086a8f5b74100f5821a5cfca3af
ms.sourcegitcommit: 8e9c38da7bcfbe9a461c378083846714933a0e1e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/09/2020
ms.locfileid: "96914455"
---
# <a name="breakpoints-visual-studio-sdk"></a>Punkty przerwania (zestaw SDK programu Visual Studio)
Istnieją trzy typy punktów przerwania: oczekujące, powiązane i błędy.

 **Oczekujący punkt przerwania:**

- Jest abstrakcyjna, która zawiera wszystkie informacje, które są konieczne do powiązania punktu przerwania z co najmniej jednym kontekstem kodu w jednym lub kilku programach. Za każdym razem, gdy debugowany program powoduje załadowanie kodu, aparat debugowania sprawdza wszystkie oczekujące punkty przerwania, aby sprawdzić, czy można je powiązać.

   Oczekujący punkt przerwania nigdy nie wiąże się z kodem, ale raczej zbiera i ma zawierać wszystkie powiązane punkty przerwania, które generuje.

- Jest reprezentowany przez interfejs [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) .

  **Powiązany punkt przerwania:**

- Jest abstrakcją dla punktu przerwania skojarzonego z lub powiązana z pojedynczym kontekstem kodu. Każdy powiązany punkt przerwania jest generowany w odpowiedzi na oczekujący punkt przerwania. Oczekujący punkt przerwania może jednak generować więcej niż jeden powiązany punkt przerwania.

   Gdy kod jest zwolniony, powiązany punkt przerwania może być niepowiązany i odrzucony.

- Jest reprezentowany przez interfejs [IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md) .

  **Punkt przerwania błędu:**

- Jest abstrakcją dla opisywania błędu podczas próby powiązania oczekującego punktu przerwania z kontekstem kodu. Punkt przerwania błędu opisuje błąd w lokalizacji lub w samym wyrażeniu punktu przerwania. Aby uzyskać więcej informacji, zobacz [Powiązywanie punktów przerwania](../../extensibility/debugger/binding-breakpoints.md).

   Błąd punktu przerwania może być błąd lub ostrzeżenie.

- Jest reprezentowany przez interfejs [IDebugErrorBreakpoint2](../../extensibility/debugger/reference/idebugerrorbreakpoint2.md) .

## <a name="see-also"></a>Zobacz też
- [Programy](../../extensibility/debugger/programs.md)
- [Pojęcia dotyczące debugera](../../extensibility/debugger/debugger-concepts.md)
- [Kontekst kodu](../../extensibility/debugger/code-context.md)
- [IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md)
- [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
- [IDebugErrorBreakpoint2](../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)
