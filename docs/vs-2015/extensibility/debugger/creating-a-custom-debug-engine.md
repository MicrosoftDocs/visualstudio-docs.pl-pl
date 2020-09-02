---
title: Tworzenie niestandardowego aparatu debugowania | Microsoft Docs
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
ms.openlocfilehash: b2a73dfae7772d8edec076238704aa1b52c9b028
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64829299"
---
# <a name="creating-a-custom-debug-engine"></a>Tworzenie niestandardowego aparatu debugowania
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Aparat debugowania (DE) to składnik, który umożliwia debugowanie określonych architektur w czasie wykonywania. Zazwyczaj istnieje tylko jedna cofnięta implementacja dla środowiska wykonawczego.  
  
> [!NOTE]
> Chociaż istnieją oddzielne niewdrożenia dla Transact-SQL i JScript, VBScript i JScript dzielą pojedynczo.  
  
 A DE współpracuje z systemem interpretera lub system operacyjny, aby zapewnić takie usługi debugowania jak kontrolka wykonywania, punkty przerwania i Obliczanie wyrażenia. Te usługi są implementowane przez wszystkie interfejsy i mogą spowodować przejście debugera między różnymi trybami operacyjnymi. Aby uzyskać więcej informacji, zobacz [Tryby operacyjne](../../extensibility/debugger/operational-modes.md).  
  
 Utworzenie elementu DE obejmuje następujące kroki:  
  
1. Rejestrowanie z programu Visual Studio  
  
2. Włączanie debugowania programu  
  
3. Kontrola wykonywania i Ocena stanu  
  
4. Wysyłanie zdarzeń  
  
5. Kończenie i odłączanie  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Rejestrowanie niestandardowego aparatu debugowania](../../extensibility/debugger/registering-a-custom-debug-engine.md)  
 Wyjaśnia kroki wymagane do zarejestrowania aparatu debugowania w programie Visual Studio, aby można było go użyć.  
  
 [Włączanie debugowania programu](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)  
 W tym artykule wyjaśniono, że zanim element DE może debugować program, należy najpierw uruchomić go DE lub dołączyć do istniejącego programu.  
  
 [Kontrola wykonywania i ocena stanu](../../extensibility/debugger/execution-control-and-state-evaluation.md)  
 W tym artykule omówiono, dlaczego debugowanie aplikacji wymaga wykonania funkcji kontroli wykonywania.  
  
 [Wysyłanie zdarzeń](../../extensibility/debugger/sending-events.md)  
 Opisuje komunikację między debugerem a niemodelem zdarzenia na podstawie modelu DCOM.  
  
 [Kończenie i odłączanie](../../extensibility/debugger/termination-and-detaching.md)  
 Wyjaśnia, jak osiągnąć normalne zakończenie, co oznacza, że nie ma żadnych punktów przerwania, wyjątków, błędów czasu wykonywania lub nieskończonych pętli w aplikacji, które mają być debugowane.  
  
 [Wywoływanie zdarzeń debugera](../../extensibility/debugger/calling-debugger-events.md)  
 Dokumentuje kolejność wywoływania zdarzeń występujących w sesji debugowania.  
  
 [Instrukcje: debugowanie niestandardowego aparatu debugowania](../../extensibility/debugger/how-to-debug-a-custom-debug-engine.md)  
 Wyjaśnia, jak debugować niestandardowe DE.  
  
## <a name="see-also"></a>Zobacz też  
 [Rozszerzalność debugera programu Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md)
