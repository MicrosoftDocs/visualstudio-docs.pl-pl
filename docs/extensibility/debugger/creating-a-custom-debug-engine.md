---
title: Tworzenie niestandardowego aparat debugowania | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, implementing
- debug engines, custom
- debugging [Debugging SDK], custom debug engines
ms.assetid: 52794238-6fae-451c-bf1c-99f344c6f173
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3756eb105ec562d902d4631318e7a5fc698601a2
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66345320"
---
# <a name="create-a-custom-debug-engine"></a>Tworzenie niestandardowego aparatu debugowania
Aparat debugowania (DE) to składnik, który umożliwia debugowanie określonej architektury środowiska wykonawczego. Zazwyczaj jest tylko jedna implementacja DE na środowisku uruchomieniowym.

> [!NOTE]
> Istnieją osobne implementacje DE języka Transact-SQL i JScript, VBScript i JScript udostępniać pojedynczy DE.

 DE działa w systemie operacji lub interpretera zapewnienie debugowania usług wykonywania oceny kontroli, punkty przerwania i wyrażenie. Te usługi są implementowane za pośrednictwem interfejsów DE i może spowodować, że debuger w celu przejścia między różne tryby operacyjne. Aby uzyskać więcej informacji, zobacz [tryby operacyjne](../../extensibility/debugger/operational-modes.md).

 Tworzenie DE składa się z następujących czynności:

1. Zarejestruj DE z programem Visual Studio

2. Włącz program do debugowania

3. Implementowanie wykonanie kontroli i stan oceny

4. Wysyłanie zdarzeń

5. Konfigurowanie Kończenie i odłączanie

## <a name="in-this-section"></a>W tej sekcji
 [Rejestrowanie niestandardowego aparatu debugowania](../../extensibility/debugger/registering-a-custom-debug-engine.md) wyjaśniono czynności wymaganych do zarejestrowania aparat debugowania za pomocą programu Visual Studio, dzięki czemu mogą być używane.

 [Włącz program do debugowania](../../extensibility/debugger/enabling-a-program-to-be-debugged.md) wyjaśniono, że przed swoje DE debugować program, musisz je najpierw uruchom DE lub dołączyć do istniejącego programu.

 [Implementowanie wykonanie kontroli i stanu oceny](../../extensibility/debugger/execution-control-and-state-evaluation.md) Discusses Dlaczego debugowania aplikacji wymaga implementacji funkcji kontroli wykonywania.

 [Wysyłanie zdarzeń](../../extensibility/debugger/sending-events.md) komunikacji w tym artykule opisano między debugera i "de" jako model zdarzeń oparte na modelu DCOM.

 [Konfigurowanie Kończenie i odłączanie](../../extensibility/debugger/termination-and-detaching.md) wyjaśnia, jak osiągnąć normalne zakończenie, co oznacza, że nie istnieją żadne punkty przerwania, wyjątki, błędy czasu wykonywania lub nieskończonej pętli w aplikacji przeznaczonej do debugowania.

 [Wywołanie zdarzenia debuger](../../extensibility/debugger/calling-debugger-events.md) dokumenty w kolejności wywołań zdarzeń występujących w sesji debugowania.

 [Instrukcje: Debugowanie niestandardowego aparatu debugowania](../../extensibility/debugger/how-to-debug-a-custom-debug-engine.md) wyjaśnia, jak można debugować DE niestandardowych.

## <a name="see-also"></a>Zobacz także
- [Rozszerzeń debugera programu Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md)