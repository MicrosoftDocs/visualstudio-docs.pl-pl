---
title: Włączanie debugowania programu | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], enabling for programs
ms.assetid: 61d24820-0cd9-48b6-8674-6813f7493237
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1f301de66421ef1327b86d900305cb4ecbfb5623
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56695131"
---
# <a name="enable-a-program-to-be-debugged"></a>Włącz program do debugowania
Zanim program debugować silnik debugowania (DE), możesz uruchomić DE lub dołączyć do istniejącego programu.

## <a name="in-this-section"></a>W tej sekcji
 [Pobieranie portu](../../extensibility/debugger/getting-a-port.md) w tym artykule omówiono sposób uzyskiwania portu jako pierwszy krok, aby włączyć program do debugowania.

 [Zarejestruj program](../../extensibility/debugger/registering-the-program.md) wyjaśnia, następnym krokiem podczas włączania programu do debugowania: rejestrując ją za pomocą portu. Po zarejestrowaniu programu mogą być debugowane przez proces dołączania lub debugowania just-in-time (JIT).

 [Dołącz do programu](../../extensibility/debugger/attaching-to-the-program.md) wyjaśnia następny krok: dołączanie debugera do programu.

 [Dołączanie na podstawie uruchamiania](../../extensibility/debugger/launch-based-attachment.md) opisano na podstawie uruchamiania załącznika program, który odbywa się automatycznie po uruchomieniu przez kierownika ds.

 [Wysyłanie wymaganych zdarzeń](../../extensibility/debugger/sending-the-required-events.md) przeprowadzi Cię przez wymaganych zdarzeń podczas tworzenia aparatu debugowania (DE) i dołączania ich do programu.

## <a name="related-sections"></a>Sekcje pokrewne
 [Tworzenie niestandardowego aparatu debugowania](../../extensibility/debugger/creating-a-custom-debug-engine.md) definiuje aparat debugowania (DE), a także opis usług implementowane za pomocą interfejsów DE i jak może spowodować, że debuger w celu przejścia między różne tryby operacyjne.