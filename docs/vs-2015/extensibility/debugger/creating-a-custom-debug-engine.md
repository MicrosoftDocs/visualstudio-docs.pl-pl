---
title: Tworzenie niestandardowego aparat debugowania | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, implementing
- debug engines, custom
- debugging [Debugging SDK], custom debug engines
ms.assetid: 52794238-6fae-451c-bf1c-99f344c6f173
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a0617d23b49af182504406417023b0d907cadf27
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54759710"
---
# <a name="creating-a-custom-debug-engine"></a>Tworzenie niestandardowego aparatu debugowania
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Aparat debugowania (DE) to składnik, który umożliwia debugowanie określonej architektury środowiska wykonawczego. Zazwyczaj jest tylko jedna implementacja DE na środowisku uruchomieniowym.  
  
> [!NOTE]
>  Istnieją osobne implementacje DE języka Transact-SQL i JScript, VBScript i JScript udostępniać pojedynczy DE.  
  
 DE działa w systemie operacji lub interpretera zapewnienie debugowania usług wykonywania oceny kontroli, punkty przerwania i wyrażenie. Te usługi są implementowane za pośrednictwem interfejsów DE i może spowodować, że debuger w celu przejścia między różne tryby operacyjne. Aby uzyskać więcej informacji, zobacz [tryby operacyjne](../../extensibility/debugger/operational-modes.md).  
  
 Tworzenie DE składa się z następujących czynności:  
  
1.  Rejestrowanie DE przy użyciu programu Visual Studio  
  
2.  Włączanie programu do debugowania  
  
3.  Wykonanie kontroli i stan oceny  
  
4.  Wysyłanie zdarzeń  
  
5.  Kończenie i odłączanie  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Rejestrowanie niestandardowego aparatu debugowania](../../extensibility/debugger/registering-a-custom-debug-engine.md)  
 Wyjaśnia kroki, wymaganych do zarejestrowania aparat debugowania za pomocą programu Visual Studio, dzięki czemu mogą być używane.  
  
 [Włączanie debugowania programu](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)  
 Wyjaśniono, że przed swoje DE debugować program, musisz je najpierw uruchom DE lub dołączyć do istniejącego programu.  
  
 [Kontrola wykonywania i ocena stanu](../../extensibility/debugger/execution-control-and-state-evaluation.md)  
 W tym artykule omówiono, dlaczego debugowania aplikacji wymaga implementacji funkcji kontroli wykonywania.  
  
 [Wysyłanie zdarzeń](../../extensibility/debugger/sending-events.md)  
 W tym artykule opisano komunikację między debugera i "de" jako model zdarzeń oparty na modelu DCOM.  
  
 [Kończenie i odłączanie](../../extensibility/debugger/termination-and-detaching.md)  
 Wyjaśnia, jak osiągnąć normalne zakończenie, co oznacza, że nie istnieją żadne punkty przerwania, wyjątki, błędy czasu wykonywania lub nieskończonej pętli w aplikacji przeznaczonej do debugowania.  
  
 [Wywoływanie zdarzeń debugera](../../extensibility/debugger/calling-debugger-events.md)  
 Dokumenty kolejności wywołań zdarzeń występujących w sesji debugowania.  
  
 [Instrukcje: Debugowanie niestandardowego aparatu debugowania](../../extensibility/debugger/how-to-debug-a-custom-debug-engine.md)  
 Wyjaśnia, jak można debugować DE niestandardowych.  
  
## <a name="see-also"></a>Zobacz też  
 [Rozszerzalność debugera programu Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md)
