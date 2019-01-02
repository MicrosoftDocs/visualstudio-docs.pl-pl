---
title: Włączanie debugowania programu | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], enabling for programs
ms.assetid: 61d24820-0cd9-48b6-8674-6813f7493237
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 94034f54457a66b0dccd4ccf2d533915a8d818dc
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53888481"
---
# <a name="enable-a-program-to-be-debugged"></a>Włącz program do debugowania
Zanim program debugować silnik debugowania (DE), możesz uruchomić DE lub dołączyć do istniejącego programu.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Pobieranie portu](../../extensibility/debugger/getting-a-port.md)  
 W tym artykule omówiono sposób uzyskiwania portu jako pierwszy krok, aby włączyć program do debugowania.  
  
 [Rejestrowanie programu](../../extensibility/debugger/registering-the-program.md)  
 Wyjaśnia, następnym krokiem podczas włączania programu do debugowania: rejestrując ją za pomocą portu. Po zarejestrowaniu programu mogą być debugowane przez proces dołączania lub debugowania just-in-time (JIT).  
  
 [Dołącz do programu](../../extensibility/debugger/attaching-to-the-program.md)  
 Wyjaśnia, następnym krokiem: dołączanie debugera do programu.  
  
 [Dołączanie na podstawie uruchamiania](../../extensibility/debugger/launch-based-attachment.md)  
 W tym artykule opisano na podstawie uruchamiania załącznika program, który odbywa się automatycznie po uruchomieniu przez kierownika ds.  
  
 [Wysyłanie wymaganych zdarzeń](../../extensibility/debugger/sending-the-required-events.md)  
 Kroki wykonywane w wymaganych zdarzeń podczas tworzenia aparatu debugowania (DE) i dołączania ich do programu.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Tworzenie niestandardowego aparatu debugowania](../../extensibility/debugger/creating-a-custom-debug-engine.md)  
 Definiuje aparat debugowania (DE), a w tym artykule opisano usług implementowane za pomocą interfejsów DE i jak może spowodować, że debuger w celu przejścia między różne tryby operacyjne.