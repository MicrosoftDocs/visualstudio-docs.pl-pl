---
title: Załącznik z systemem | Microsoft Docs
description: Zapoznaj się z załącznikiem uruchamiania do programu, który jest automatyczny, i postępuj zgodnie z ścieżką, taką jak w przypadku załączników ręcznych.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, launching
- debug engines, attaching to programs
ms.assetid: 362f00ac-1909-4a3a-bacb-c0ceb5549816
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: fe698d8d1b29f02ae3971fc95a66c4823f7252c7
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105059720"
---
# <a name="launch-based-attachment"></a>Załącznik z systemem
Przymocowanie na podstawie uruchamiania do programu jest automatyczne. Gdy proces hostujący program jest uruchamiany przez model SDM, przystawka na podstawie uruchamiania następuje po ścieżce podobnej do metody ręcznego załączników. Aby uzyskać więcej informacji, zobacz [dołączanie do programu](../../extensibility/debugger/attaching-to-the-program.md).

## <a name="the-attaching-process"></a>Proces dołączania
 Główną różnicą jest sekwencja zdarzeń po wywołaniu **Attach** w następujący sposób:

1. Wyślij obiekt zdarzenia **IDebugEngineCreateEvent2** do modelu SDM. Aby uzyskać szczegółowe informacje, zobacz [wysyłanie zdarzeń](../../extensibility/debugger/sending-events.md).

2. Wywołaj `IDebugProgram2::GetProgramId` metodę w interfejsie **IDebugProgram2** przekazaną do metody **Attach** .

3. Wyślij obiekt zdarzenia **IDebugProgramCreateEvent2** , aby powiadomić model SDM, że lokalny obiekt **IDebugProgram2** został utworzony, aby reprezentować program do de.

4. Wyślij obiekt zdarzenia [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) , aby powiadomić model SDM o utworzeniu nowego wątku dla uruchomionego procesu.

## <a name="see-also"></a>Zobacz też
- [Wyślij wymagane zdarzenia](../../extensibility/debugger/sending-the-required-events.md)
- [Włącz debugowanie programu](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)
