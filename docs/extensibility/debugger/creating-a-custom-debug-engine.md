---
title: Tworzenie niestandardowego aparatu debugowania | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, implementing
- debug engines, custom
- debugging [Debugging SDK], custom debug engines
ms.assetid: 52794238-6fae-451c-bf1c-99f344c6f173
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a350d640fffcc6e09cf8f981c797b97071a0cacf
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739037"
---
# <a name="create-a-custom-debug-engine"></a>Tworzenie niestandardowego aparatu debugowania
Aparat debugowania (DE) jest składnikiem, który umożliwia debugowanie poszczególnych architektur czasu wykonywania. Zazwyczaj istnieje tylko jedna implementacja DE na środowisko wykonawcze.

> [!NOTE]
> Chociaż istnieją oddzielne implementacje DE dla Transact-SQL i JScript, VBScript i JScript współużytkują jeden DE.

 DE współpracuje z interpreter lub system operacji w celu zapewnienia takich usług debugowania, jak kontrola wykonania, punkty przerwania i oceny wyrażenia. Usługi te są implementowane za pośrednictwem interfejsów DE i może spowodować debugerprzejąc się między różnymi trybami operacyjnymi. Aby uzyskać więcej informacji, zobacz [Tryby operacyjne](../../extensibility/debugger/operational-modes.md).

 Tworzenie DE składa się z następujących kroków:

1. Zarejestruj de w programie Visual Studio

2. Włączanie debugowania programu

3. Wdrażanie kontroli wykonania i oceny stanu

4. Wysyłanie zdarzeń

5. Konfigurowanie zakończenia i odłączania

## <a name="in-this-section"></a>W tej sekcji
 [Rejestrowanie niestandardowego aparatu debugowania](../../extensibility/debugger/registering-a-custom-debug-engine.md) Wyjaśniono kroki potrzebne do zarejestrowania aparatu debugowania w programie Visual Studio, aby można było go używać.

 [Włączanie debugowania programu](../../extensibility/debugger/enabling-a-program-to-be-debugged.md) Wyjaśnia, że zanim de można debugować program, należy najpierw uruchomić DE lub dołączyć go do istniejącego programu.

 [Wdrażanie kontroli wykonania i oceny stanu](../../extensibility/debugger/execution-control-and-state-evaluation.md) W tym artykule omówiono dlaczego debugowanie aplikacji wymaga implementacji funkcji kontroli wykonywania.

 [Wysyłanie zdarzeń](../../extensibility/debugger/sending-events.md) Opisuje komunikację między debugerem a DE jako model zdarzenia oparty na modelu DCOM.

 [Konfigurowanie zakończenia i odłączania](../../extensibility/debugger/termination-and-detaching.md) Wyjaśniono, jak osiągnąć normalne zakończenie, co oznacza, że nie ma żadnych punktów przerwania, wyjątków, błędów w czasie wykonywania lub nieskończonych pętli w aplikacji do debugowania.

 [Wywoływanie zdarzeń debugera](../../extensibility/debugger/calling-debugger-events.md) Dokumenty kolejność wywoływania zdarzeń występujących w sesji debugowania.

 [Jak: Debugowanie niestandardowego aparatu debugowania](../../extensibility/debugger/how-to-debug-a-custom-debug-engine.md) W tym artykule wyjaśniono, jak debugować niestandardowe DE.

## <a name="see-also"></a>Zobacz też
- [Rozszerzalność debugera programu Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md)
