---
title: Dołączanie na podstawie uruchamiania | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, launching
- debug engines, attaching to programs
ms.assetid: 362f00ac-1909-4a3a-bacb-c0ceb5549816
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fa0f03c37b92366e9872cbd170605a385aabdd1a
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54975858"
---
# <a name="launch-based-attachment"></a>Dołączanie na podstawie uruchamiania
Na podstawie uruchamiania załącznika do programu odbywa się automatycznie. Podczas procesu hostingu program jest uruchamiany przez SDM, na podstawie uruchamiania załącznika poniżej ścieżką podobną do tej metody ręcznego załącznika. Aby uzyskać informacje, zobacz [dołączyć do programu](../../extensibility/debugger/attaching-to-the-program.md).  
  
## <a name="the-attaching-process"></a>Dołączanie procesu  
 Główna różnica polega na sekwencję zdarzeń po **Dołącz** wywołań w następujący sposób:  
  
1.  Wyślij **IDebugEngineCreateEvent2** obiekt zdarzenia do SDM. Aby uzyskać więcej informacji, zobacz [wysyłanie zdarzeń](../../extensibility/debugger/sending-events.md).  
  
2.  Wywołania `IDebugProgram2::GetProgramId` metody **IDebugProgram2** interfejsu przekazany do **Dołącz** metody.  
  
3.  Wyślij **IDebugProgramCreateEvent2** zdarzeń obiektowi powiadomić SDM, lokalnej **IDebugProgram2** do reprezentowania program DE został utworzony obiekt.  
  
4.  Wyślij [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) obiektu zdarzenia, aby powiadomić SDM, utworzenia nowego wątku dla procesu, który uruchomił.  
  
## <a name="see-also"></a>Zobacz także  
 [Wysyłanie wymaganych zdarzeń](../../extensibility/debugger/sending-the-required-events.md)   
 [Włącz program do debugowania](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)