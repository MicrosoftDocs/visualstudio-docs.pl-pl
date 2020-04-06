---
title: Uruchamianie programu | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, launching
- programs, launching
ms.assetid: 6857e9c6-e44a-468a-afa4-f7c4a0b77844
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bf638e0c96c7df1de2650260427a972a07efce23
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738475"
---
# <a name="launch-a-program"></a>Uruchamianie programu
Użytkownicy, którzy chcą debugować program można nacisnąć **klawisz F5,** aby uruchomić debuger z IDE. Rozpoczyna się seria zdarzeń, które ostatecznie doprowadzić do ide połączenia z aparatem debugowania (DE), który jest z kolei podłączony lub dołączony do programu w następujący sposób:

1. IDE najpierw wywołuje pakiet projektu, aby uzyskać aktywne ustawienia debugowania projektu rozwiązania. Ustawienia obejmują katalog początkowy, zmienne środowiskowe, port, w którym program będzie uruchamiany, oraz DE do utworzenia programu, jeśli określono. Te ustawienia są przekazywane do pakietu debugowania.

2. Jeśli de jest określony, DE wywołuje system operacyjny, aby uruchomić program. W wyniku uruchomienia programu, program jest uruchamiany środowisko. Na przykład jeśli program jest napisany w MSIL, środowisko uruchomieniowe języka wspólnego zostanie wywołane w celu uruchomienia programu.

    — lub —

    Jeśli DE nie jest określony, port wywołuje system operacyjny, aby uruchomić program, co powoduje, że środowisko wykonywania programu do załadowania.

   > [!NOTE]
   > Jeśli DE jest używany do uruchomienia programu, jest prawdopodobne, że ten sam DE zostanie dołączony do programu.

3. W zależności od tego, czy DE lub port uruchomił program, DE lub środowiska w czasie wykonywania następnie tworzy opis programu lub węzeł i powiadamia port, że program jest uruchomiony.

   > [!NOTE]
   > Zaleca się, aby środowisko pracy utworzyło węzeł programu, ponieważ węzeł programu jest lekką reprezentacją programu, który można debugować. Nie ma potrzeby, aby załadować cały DE tylko do tworzenia i rejestrowania węzła programu. Jeśli DE jest przeznaczony do uruchamiania w procesie IDE, ale nie IDE jest faktycznie uruchomiony, musi istnieć składnik, który można dodać węzeł programu do portu.

   Nowo utworzony program, wraz z innymi programami, pokrewnymi lub niepowiązanymi, uruchomionymi lub dołączonymi do tego samego IDE, tworzą sesję debugowania.

   Programowo, gdy użytkownik po raz pierwszy [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]naciska **F5**, 's pakiet debugowania wywołuje pakiet projektu (który jest skojarzony z <xref:Microsoft.VisualStudio.Shell.Interop.VsDebugTargetInfo2> typem programu uruchamianego) za pomocą <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg.DebugLaunch%2A> metody, która z kolei wypełnia strukturę z aktywnych ustawień debugowania projektu rozwiązania. Ta struktura jest przekazywana z powrotem <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebugger2.LaunchDebugTargets2%2A> do pakietu debugowania za pośrednictwem wywołania metody. Pakiet debugowania następnie wystąpienia menedżera debugowania sesji (SDM), który uruchamia program jest debugowany i wszystkie skojarzone aparaty debugowania.

   Jednym z argumentów przekazanych do SDM jest identyfikator GUID DE, który ma być używany do uruchomienia programu.

   Jeśli identyfikator GUID `GUID_NULL`DE nie jest , SDM współtworzy DE, a następnie wywołuje jego [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) metody, aby uruchomić program. Na przykład, jeśli program jest napisany `IDebugEngineLaunch2::LaunchSuspended` w kodzie macierzystym, prawdopodobnie wywoła `CreateProcess` i `ResumeThread` (funkcje Win32) do uruchomienia programu.

   W wyniku uruchomienia programu, środowisko pracy programu jest ładowany. De lub środowiska w czasie wykonywania następnie tworzy interfejs [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) do opisania programu i przekazuje ten interfejs do [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md) powiadomić port, że program jest uruchomiony.

   Jeśli `GUID_NULL` zostanie przekazany, port uruchamia program. Po uruchomieniu programu środowisko w czasie wykonywania `IDebugProgramNode2` tworzy interfejs opisujący program `IDebugPortNotify2::AddProgramNode`i przekazuje go do programu . To powiadamia port, że program jest uruchomiony. Następnie moduł SDM dołącza aparat debugowania do uruchomionego programu.

## <a name="in-this-section"></a>W tej sekcji
 [Powiadamianie portu](../../extensibility/debugger/notifying-the-port.md) Wyjaśnia, co się dzieje po uruchomieniu programu i powiadomiony o porcie.

 [Dołączanie po uruchomieniu](../../extensibility/debugger/attaching-after-a-launch.md) Dokumenty, gdy sesja debugowania jest gotowa do dołączenia DE do programu.

## <a name="related-sections"></a>Powiązane sekcje
 [Zadania debugowania](../../extensibility/debugger/debugging-tasks.md) Zawiera łącza do różnych zadań debugowania, takich jak uruchamianie programu i oceny wyrażeń.
