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
ms.openlocfilehash: 0cf41afa91ce1e77904b99f17ea0321e9bdb12d1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62889553"
---
# <a name="launch-based-attachment"></a>Dołączanie na podstawie uruchamiania
Na podstawie uruchamiania załącznika do programu odbywa się automatycznie. Podczas procesu hostingu program jest uruchamiany przez SDM, na podstawie uruchamiania załącznika poniżej ścieżką podobną do tej metody ręcznego załącznika. Aby uzyskać informacje, zobacz [dołączyć do programu](../../extensibility/debugger/attaching-to-the-program.md).

## <a name="the-attaching-process"></a>Dołączanie procesu
 Główna różnica polega na sekwencję zdarzeń po **Dołącz** wywołań w następujący sposób:

1. Wyślij **IDebugEngineCreateEvent2** obiekt zdarzenia do SDM. Aby uzyskać więcej informacji, zobacz [wysyłanie zdarzeń](../../extensibility/debugger/sending-events.md).

2. Wywołania `IDebugProgram2::GetProgramId` metody **IDebugProgram2** interfejsu przekazany do **Dołącz** metody.

3. Wyślij **IDebugProgramCreateEvent2** zdarzeń obiektowi powiadomić SDM, lokalnej **IDebugProgram2** do reprezentowania program DE został utworzony obiekt.

4. Wyślij [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) obiektu zdarzenia, aby powiadomić SDM, utworzenia nowego wątku dla procesu, który uruchomił.

## <a name="see-also"></a>Zobacz także
- [Wysyłanie wymaganych zdarzeń](../../extensibility/debugger/sending-the-required-events.md)
- [Włącz program do debugowania](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)