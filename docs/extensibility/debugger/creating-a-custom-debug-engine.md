---
title: Tworzenie niestandardowego aparat debugowania | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, implementing
- debug engines, custom
- debugging [Debugging SDK], custom debug engines
ms.assetid: 52794238-6fae-451c-bf1c-99f344c6f173
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: aff0f3ba1bef25c7754f80dcbb6fb04e2e7da60e
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "55029911"
---
# <a name="create-a-custom-debug-engine"></a>Tworzenie niestandardowego aparatu debugowania
Aparat debugowania (DE) to składnik, który umożliwia debugowanie określonej architektury środowiska wykonawczego. Zazwyczaj jest tylko jedna implementacja DE na środowisku uruchomieniowym.  
  
> [!NOTE]
>  Istnieją osobne implementacje DE języka Transact-SQL i JScript, VBScript i JScript udostępniać pojedynczy DE.  
  
 DE działa w systemie operacji lub interpretera zapewnienie debugowania usług wykonywania oceny kontroli, punkty przerwania i wyrażenie. Te usługi są implementowane za pośrednictwem interfejsów DE i może spowodować, że debuger w celu przejścia między różne tryby operacyjne. Aby uzyskać więcej informacji, zobacz [tryby operacyjne](../../extensibility/debugger/operational-modes.md).  
  
 Tworzenie DE składa się z następujących czynności:  
  
1.  Zarejestruj DE z programem Visual Studio  
  
2.  Włącz program do debugowania  
  
3.  Implementowanie wykonanie kontroli i stan oceny  
  
4.  Wysyłanie zdarzeń  
  
5.  Konfigurowanie Kończenie i odłączanie  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Rejestrowanie niestandardowego aparatu debugowania](../../extensibility/debugger/registering-a-custom-debug-engine.md)  
 Wyjaśnia kroki, wymaganych do zarejestrowania aparat debugowania za pomocą programu Visual Studio, dzięki czemu mogą być używane.  
  
 [Włącz program do debugowania](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)  
 Wyjaśniono, że przed swoje DE debugować program, musisz je najpierw uruchom DE lub dołączyć do istniejącego programu.  
  
 [Implementowanie wykonanie kontroli i stan oceny](../../extensibility/debugger/execution-control-and-state-evaluation.md)  
 W tym artykule omówiono, dlaczego debugowania aplikacji wymaga implementacji funkcji kontroli wykonywania.  
  
 [Wysyłanie zdarzeń](../../extensibility/debugger/sending-events.md)  
 W tym artykule opisano komunikację między debugera i "de" jako model zdarzeń oparty na modelu DCOM.  
  
 [Konfigurowanie Kończenie i odłączanie](../../extensibility/debugger/termination-and-detaching.md)  
 Wyjaśnia, jak osiągnąć normalne zakończenie, co oznacza, że nie istnieją żadne punkty przerwania, wyjątki, błędy czasu wykonywania lub nieskończonej pętli w aplikacji przeznaczonej do debugowania.  
  
 [Wywoływanie zdarzeń debugera](../../extensibility/debugger/calling-debugger-events.md)  
 Dokumenty kolejności wywołań zdarzeń występujących w sesji debugowania.  
  
 [Instrukcje: Debugowanie niestandardowego aparatu debugowania](../../extensibility/debugger/how-to-debug-a-custom-debug-engine.md)  
 Wyjaśnia, jak można debugować DE niestandardowych.  
  
## <a name="see-also"></a>Zobacz także  
 [Rozszerzeń debugera programu Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md)