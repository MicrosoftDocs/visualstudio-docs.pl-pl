---
title: Oparte na uruchomieniu załączniki | Microsoft Docs
description: Dowiedz się więcej na temat automatycznego załącznika do programu opartego na uruchomieniu, który jest zgodny ze ścieżką, jak w załączniku ręcznym.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debug engines, launching
- debug engines, attaching to programs
ms.assetid: 362f00ac-1909-4a3a-bacb-c0ceb5549816
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 97bbc098e766a1025c372ff35c5849bfe652649f
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112904337"
---
# <a name="launch-based-attachment"></a>Załącznik oparty na uruchomieniu
Załącznik do programu oparty na uruchomieniu jest automatyczny. Gdy proces hostowania programu jest uruchamiany przez program SDM, załącznik oparty na uruchomieniu jest zgodny ze ścieżką podobną do metody ręcznego załącznika. Aby uzyskać więcej informacji, [zobacz Dołączanie do programu](../../extensibility/debugger/attaching-to-the-program.md).

## <a name="the-attaching-process"></a>Proces dołączania
 Główna różnica polega na sekwencji zdarzeń następujących po **wywołaniu attach** w następujący sposób:

1. Wyślij **obiekt zdarzenia IDebugEngineCreateEvent2** do modelu SDM. Aby uzyskać szczegółowe informacje, zobacz [Wysyłanie zdarzeń](../../extensibility/debugger/sending-events.md).

2. Wywołaj `IDebugProgram2::GetProgramId` metodę w **interfejsie IDebugProgram2** przekazanym do **metody Attach.**

3. Wyślij **obiekt zdarzenia IDebugProgramCreateEvent2,** aby powiadomić program SDM o utworzeniu lokalnego obiektu **IDebugProgram2** reprezentującego program de.

4. Wyślij [obiekt zdarzenia IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) w celu powiadomienia modelu SDM o utworzeniu nowego wątku dla uruchomionego procesu.

## <a name="see-also"></a>Zobacz też
- [Wysyłanie wymaganych zdarzeń](../../extensibility/debugger/sending-the-required-events.md)
- [Włączanie debugowania programu](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)
