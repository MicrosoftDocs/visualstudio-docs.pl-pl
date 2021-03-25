---
title: Uruchamianie programu | Microsoft Docs
description: Zapoznaj się z serią zdarzeń, które należy wykonać podczas debugowania programu przy użyciu klawisza F5 w celu uruchomienia debugera z poziomu środowiska IDE.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, launching
- programs, launching
ms.assetid: 6857e9c6-e44a-468a-afa4-f7c4a0b77844
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a21036d3a9661306d1efff5a66ae47f8f7404209
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105094721"
---
# <a name="launch-a-program"></a>Uruchamianie programu
Użytkownicy, którzy chcą debugować program, mogą nacisnąć klawisz **F5** , aby uruchomić debuger z poziomu środowiska IDE. Spowoduje to rozpoczęcie szeregu zdarzeń, które ostatecznie spowodują połączenie IDE z silnikiem debugowania (DE), który jest z kolei podłączony lub dołączony do programu w następujący sposób:

1. IDE najpierw wywołuje pakiet projektu, aby uzyskać aktywne ustawienia debugowania projektu rozwiązania. Ustawienia obejmują katalog początkowy, zmienne środowiskowe, port, w którym zostanie uruchomiony program, a także wartość nieużywaną do utworzenia programu, jeśli zostanie określony. Te ustawienia są przesyłane do pakietu debugowania.

2. Jeśli jest określona, to usuwa system operacyjny, aby uruchomić program. W wyniku uruchomienia programu załaduje środowisko środowiska uruchomieniowego programu. Na przykład jeśli program jest pisany w języku MSIL, środowisko uruchomieniowe języka wspólnego zostanie wywołane w celu uruchomienia programu.

    -lub-

    Jeśli nie jest określony, port wywoła system operacyjny, aby uruchomić program, co spowoduje załadowanie środowiska uruchomieniowego programu.

   > [!NOTE]
   > Jeśli jest używany do uruchomienia programu, prawdopodobnie zostanie on dołączony do programu.

3. W zależności od tego, czy na serwerze jest uruchomiony program, a w środowisku uruchomieniowym, następnie jest tworzony Opis programu lub węzeł, a następnie jest powiadamiany port, który jest uruchomiony program.

   > [!NOTE]
   > Zaleca się, aby środowisko uruchomieniowe utworzyło węzeł programu, ponieważ węzeł programu jest lekkim reprezentacją programu, który może być debugowany. Nie trzeba ładować całości po prostu, aby utworzyć i zarejestrować węzeł programu. Jeśli DE jest przeznaczony do uruchamiania w procesie IDE, ale żadne środowisko IDE nie działa, musi być składnikiem, który może dodać węzeł programu do portu.

   Nowo utworzony program, wraz z innymi programami, związanymi lub niepowiązanymi, uruchomionymi lub dołączonymi do tego samego środowiska IDE, tworzenia sesji debugowania.

   Program programistyczny, gdy użytkownik najpierw naciśnie klawisz **F5**, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] wywołuje pakiet projektu (skojarzony z typem uruchamianego programu) za pomocą <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg.DebugLaunch%2A> metody, która z kolei wypełnia <xref:Microsoft.VisualStudio.Shell.Interop.VsDebugTargetInfo2> strukturę przy użyciu ustawień aktywnego debugowania projektu rozwiązania. Ta struktura jest przenoszona z powrotem do pakietu debugowania za pomocą wywołania <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebugger2.LaunchDebugTargets2%2A> metody. Pakiet debugowania powoduje utworzenie wystąpienia Menedżera debugowania sesji (SDM), który uruchamia debugowany program i wszystkie skojarzone aparaty debugowania.

   Jeden z argumentów przesłanych do modelu SDM jest identyfikatorem GUID, który ma być używany do uruchamiania programu.

   Jeśli DE GUID nie jest `GUID_NULL` , model SDM współtworzy a, a następnie wywołuje metodę [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) , aby uruchomić program. Na przykład, jeśli program jest pisany w kodzie natywnym, `IDebugEngineLaunch2::LaunchSuspended` prawdopodobnie wywoła `CreateProcess` i `ResumeThread` (funkcje Win32), aby uruchomić program.

   W wyniku uruchomienia programu jest ładowany środowisko uruchomieniowe programu. Natomiast środowisko uruchomieniowe tworzy interfejs [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) do opisywania programu i przekazuje ten interfejs do [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md) w celu powiadomienia portu, w którym program jest uruchomiony.

   Jeśli `GUID_NULL` jest zakończony, port uruchamia program. Po uruchomieniu programu środowisko uruchomieniowe tworzy `IDebugProgramNode2` Interfejs opisujący program i przekazuje go do programu `IDebugPortNotify2::AddProgramNode` . Spowoduje to powiadomienie portu, w którym program jest uruchomiony. Następnie model SDM dołącza aparat debugowania do uruchomionego programu.

## <a name="in-this-section"></a>W tej sekcji
 [Powiadamianie portu](../../extensibility/debugger/notifying-the-port.md) Wyjaśnia, co się stanie po uruchomieniu programu i powiadomieniu o porcie.

 [Dołączanie po uruchomieniu](../../extensibility/debugger/attaching-after-a-launch.md) Dokumenty, gdy sesja debugowania jest gotowa do dołączenia do programu.

## <a name="related-sections"></a>Sekcje pokrewne
 [Zadania debugowania](../../extensibility/debugger/debugging-tasks.md) Zawiera linki do różnych zadań debugowania, takich jak uruchamianie programu i ocenianie wyrażeń.
