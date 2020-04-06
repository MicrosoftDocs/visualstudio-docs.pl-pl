---
title: Włączanie debugowania programu | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], enabling for programs
ms.assetid: 61d24820-0cd9-48b6-8674-6813f7493237
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 17c6218cd0b25c0cf0134351fd5efd7490b6a1f3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738895"
---
# <a name="enable-a-program-to-be-debugged"></a>Włączanie debugowania programu
Zanim aparat debugowania (DE) może debugować program, należy najpierw uruchomić DE lub dołączyć go do istniejącego programu.

## <a name="in-this-section"></a>W tej sekcji
 [Uzyskaj port](../../extensibility/debugger/getting-a-port.md) W tym artykule omówiono sposób uzyskania portu jako pierwszy krok do włączania programu do debugowania.

 [Zarejestruj program](../../extensibility/debugger/registering-the-program.md) W tym artykule wyjaśniono, że jest to kolejny krok umożliwiający debugowanie programu: rejestrowanie go w porcie. Po zarejestrowaniu program może być debugowany przez proces dołączania lub debugowania just-in-time (JIT).

 [Dołącz do programu](../../extensibility/debugger/attaching-to-the-program.md) W tym celu opisano następny krok: dołączanie debugera do programu.

 [Dołączanie oparte na uruchamianiu](../../extensibility/debugger/launch-based-attachment.md) W tym artykule opisano załącznik oparty na uruchomieniu do programu, który jest automatyczny po uruchomieniu przez SDM.

 [Wysyłanie wymaganych zdarzeń](../../extensibility/debugger/sending-the-required-events.md) Kroki przez wymagane zdarzenia podczas tworzenia aparatu debugowania (DE) i dołączanie go do programu.

## <a name="related-sections"></a>Powiązane sekcje
 [Tworzenie niestandardowego aparatu debugowania](../../extensibility/debugger/creating-a-custom-debug-engine.md) Definiuje aparat debugowania (DE) i opisuje usługi zaimplementowane za pośrednictwem interfejsów DE i jak mogą one spowodować debugerprzejące między różnymi trybami pracy.
