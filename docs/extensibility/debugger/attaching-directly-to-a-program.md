---
title: Dołączanie bezpośrednio do programu | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, attaching to programs
ms.assetid: ad2b7db8-821c-440c-ba07-c55c6a395e0f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8a9a5699ee81b8c8ae36bcf492e93467615a9e89
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739261"
---
# <a name="attach-directly-to-a-program"></a>Dołączanie bezpośrednio do programu
Użytkownicy, którzy chcą debugować programy w procesie, który jest już uruchomiony, zazwyczaj postępują zgodnie z tym procesem:

1. W ide wybierz polecenie **Procesy debugowania** z menu **Narzędzia.**

    Zostanie wyświetlone okno dialogowe **Procesy.**

2. Wybierz proces i kliknij przycisk **Dołącz.**

    Zostanie **wyświetlone** okno dialogowe Dołącz do procesu z listą wszystkich aparatów debugowania (DEs) zainstalowanych na komputerze.

3. Określ dane DE używane do debugowania wybranego procesu, a następnie kliknij przycisk **OK**.

   Pakiet debugowania uruchamia sesję debugowania i przekazuje do niego listę DEs. Sesja debugowania z kolei przekazuje tę listę, wraz z funkcją wywołania zwrotnego, do wybranego procesu, a następnie prosi proces o wyliczenie jego uruchomionych programów.

   Programowo, w odpowiedzi na żądanie użytkownika pakiet debugowania zawiera wystąpienia menedżera debugowania sesji (SDM) i przekazuje do niego listę wybranych danych. Wraz z listą pakiet debugowania przekazuje interfejs [SDM i IDebugEventCallback2.](../../extensibility/debugger/reference/idebugeventcallback2.md) Pakiet debugowania przekazuje listę DEs do wybranego procesu, wywołując [IDebugProcess2::Attach](../../extensibility/debugger/reference/idebugprocess2-attach.md). SDM następnie wywołuje [IDebugProcess2::EnumPrograms](../../extensibility/debugger/reference/idebugprocess2-enumprograms.md) na porcie, aby wyliczyć programy uruchomione w procesie.

   Od tego momentu każdy aparat debugowania jest dołączony do programu dokładnie tak szczegółowo w [Dołączanie po uruchomieniu,](../../extensibility/debugger/attaching-after-a-launch.md)z dwoma wyjątkami.

   Dla wydajności, DEs, które są implementowane do udostępniania przestrzeni adresowej z SDM są pogrupowane tak, że każdy DE ma zestaw programów, które dołączy do. W takim przypadku [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md) wywołuje [IDebugEngine2::Attach](../../extensibility/debugger/reference/idebugengine2-attach.md) i przekazuje tablicę programów do dołączenia.

   Drugi wyjątek jest, że zdarzenia uruchamiania wysyłane przez DE dołączając do programu, który jest już uruchomiony zazwyczaj nie obejmują zdarzenia punktu wejścia.

## <a name="see-also"></a>Zobacz też
- [Wysyłanie zdarzeń startowych po uruchomieniu](../../extensibility/debugger/sending-startup-events-after-a-launch.md)
- [Zadania debugowania](../../extensibility/debugger/debugging-tasks.md)
