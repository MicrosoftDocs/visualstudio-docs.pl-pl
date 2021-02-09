---
title: Tworzenie niestandardowego aparatu debugowania | Microsoft Docs
description: Skorzystaj z poniższych artykułów, aby dowiedzieć się więcej o tworzeniu aparatu debugowania, który umożliwia debugowanie określonych architektur w czasie wykonywania.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- debug engines, implementing
- debug engines, custom
- debugging [Debugging SDK], custom debug engines
ms.assetid: 52794238-6fae-451c-bf1c-99f344c6f173
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 7c0aa8550bc402520052003b59cf4ab1deaad7b2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99888969"
---
# <a name="create-a-custom-debug-engine"></a>Tworzenie niestandardowego aparatu debugowania
Aparat debugowania (DE) to składnik, który umożliwia debugowanie określonych architektur w czasie wykonywania. Zazwyczaj istnieje tylko jedna cofnięta implementacja dla środowiska wykonawczego.

> [!NOTE]
> Chociaż istnieją oddzielne niewdrożenia dla Transact-SQL i JScript, VBScript i JScript dzielą pojedynczo.

 A DE współpracuje z systemem interpretera lub system operacyjny, aby zapewnić takie usługi debugowania jak kontrolka wykonywania, punkty przerwania i Obliczanie wyrażenia. Te usługi są implementowane przez wszystkie interfejsy i mogą spowodować przejście debugera między różnymi trybami operacyjnymi. Aby uzyskać więcej informacji, zobacz [Tryby operacyjne](../../extensibility/debugger/operational-modes.md).

 Utworzenie elementu DE obejmuje następujące kroki:

1. Zarejestruj się w programie Visual Studio

2. Włącz debugowanie programu

3. Implementowanie kontroli wykonywania i oceny stanu

4. Wysyłanie zdarzeń

5. Skonfiguruj zakończenie i odłączanie

## <a name="in-this-section"></a>W tej sekcji
 [Rejestrowanie niestandardowego aparatu debugowania](../../extensibility/debugger/registering-a-custom-debug-engine.md) Wyjaśnia kroki wymagane do zarejestrowania aparatu debugowania w programie Visual Studio, aby można było go użyć.

 [Włącz debugowanie programu](../../extensibility/debugger/enabling-a-program-to-be-debugged.md) W tym artykule wyjaśniono, że zanim element DE może debugować program, należy najpierw uruchomić go DE lub dołączyć do istniejącego programu.

 [Implementowanie kontroli wykonywania i oceny stanu](../../extensibility/debugger/execution-control-and-state-evaluation.md) W tym artykule omówiono, dlaczego debugowanie aplikacji wymaga wykonania funkcji kontroli wykonywania.

 [Wyślij zdarzenia](../../extensibility/debugger/sending-events.md) Opisuje komunikację między debugerem a niemodelem zdarzenia na podstawie modelu DCOM.

 [Skonfiguruj zakończenie i odłączanie](../../extensibility/debugger/termination-and-detaching.md) Wyjaśnia, jak osiągnąć normalne zakończenie, co oznacza, że nie ma żadnych punktów przerwania, wyjątków, błędów czasu wykonywania lub nieskończonych pętli w aplikacji, które mają być debugowane.

 [Zdarzenia debugera wywołań](../../extensibility/debugger/calling-debugger-events.md) Dokumentuje kolejność wywoływania zdarzeń występujących w sesji debugowania.

 [Instrukcje: debugowanie niestandardowego aparatu debugowania](../../extensibility/debugger/how-to-debug-a-custom-debug-engine.md) Wyjaśnia, jak debugować niestandardowe DE.

## <a name="see-also"></a>Zobacz też
- [Rozszerzalność debugera programu Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md)
