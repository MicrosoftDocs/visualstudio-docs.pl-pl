---
title: Załącznik oparty na uruchomieniu | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, launching
- debug engines, attaching to programs
ms.assetid: 362f00ac-1909-4a3a-bacb-c0ceb5549816
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4910a97350366500b56593ec0076fdf0990b6d8f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738463"
---
# <a name="launch-based-attachment"></a>Załącznik oparty na uruchamianiu
Załącznik oparty na uruchomieniu do programu jest automatyczny. Gdy proces hostingu programu jest uruchamiany przez SDM, załącznik oparty na uruchomieniu podąża ścieżką podobną do tej, którą stosuje metoda ręcznego mocowania. Aby uzyskać więcej informacji, zobacz [Dołączanie do programu](../../extensibility/debugger/attaching-to-the-program.md).

## <a name="the-attaching-process"></a>Proces dołączania
 Główną różnicą jest sekwencja zdarzeń następujących po **wywołaniu Attach,** w następujący sposób:

1. Wyślij obiekt zdarzenia **IDebugEngineCreateEvent2** do SDM. Aby uzyskać szczegółowe informacje, zobacz [Wysyłanie zdarzeń](../../extensibility/debugger/sending-events.md).

2. Wywołanie `IDebugProgram2::GetProgramId` metody na **interfejsie IDebugProgram2** przeszedł do **Attach** metody.

3. Wyślij obiekt zdarzenia **IDebugProgramCreateEvent2,** aby powiadomić SDM, że lokalny obiekt **IDebugProgram2** został utworzony w celu reprezentowania programu do DE.

4. Wyślij [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) obiekt zdarzenia, aby powiadomić SDM, że nowy wątek jest tworzony dla procesu, który został uruchomiony.

## <a name="see-also"></a>Zobacz też
- [Wysyłanie wymaganych zdarzeń](../../extensibility/debugger/sending-the-required-events.md)
- [Włączanie debugowania programu](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)
