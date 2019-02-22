---
title: Debugowanie zainstalowanego pakietu aplikacji platformy uniwersalnej systemu Windows | Dokumentacja firmy Microsoft
ms.custom: H1Hack27Feb2017
ms.date: 11/07/2018
ms.topic: conceptual
f1_keywords:
- vs.debug.installedapppackagelauncher
- vs.debug.remote.connection
dev_langs:
- C++
- FSharp
- CSharp
- JScript
- VB
helpviewer_keywords:
- app package, debug
ms.assetid: 5a94ad64-100d-43ca-9779-16cb5af86f97
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- uwp
ms.openlocfilehash: b6a41ad863ee25e4294d5d0242b3113cd405fb00
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56637350"
---
# <a name="debug-an-installed-uwp-app-package-in-visual-studio"></a>Debugowanie zainstalowanego pakietu aplikacji platformy uniwersalnej systemu Windows w programie Visual Studio

Visual Studio umożliwia debugowanie zainstalowanych pakietów aplikacji uniwersalnych platformy Windows (UWP) na komputerach z systemem Windows 10 oraz urządzenia Xbox, HoloLens i IoT.

>[!NOTE]
>Visual Studio do debugowania dla zainstalowanych aplikacji platformy uniwersalnej systemu Windows nie jest obsługiwana na telefonach.

Aby uzyskać więcej informacji na temat debugowania aplikacji platformy uniwersalnej systemu Windows, zobacz wpisy w blogu na [debugowania zainstalowanych pakietów aplikacji](https://devblogs.microsoft.com/devops/updates-for-debugging-installed-app-packages-in-visual-studio-2015-update-2/) i [tworzenia Windows aplikacji Uniwersalnej](https://devblogs.microsoft.com/visualstudio/universal-windows-apps-targeting-windows-10-anniversary-sdk/).

## <a name="debug-an-installed-uwp-app-on-a-local-machine"></a>Debugowanie aplikacji platformy uniwersalnej systemu Windows zainstalowanych na komputerze lokalnym

1. W programie Visual Studio, wybierz **debugowania** > **inne cele debugowania** > **pakietu debugowania zainstalowanej aplikacji**.

1. W **pakietu debugowania zainstalowanej aplikacji** okna dialogowego, w obszarze **typu połączenia**, wybierz opcję **komputera lokalnego**.

1. W obszarze **zainstalowane pakiety aplikacji**, a następnie wybierz aplikację, którą chcesz debugować lub wpisz jego nazwę w polu wyszukiwania. Uruchomiona bez zainstalowanych pakietów aplikacji są wyświetlane w obszarze **nieuruchomiona**, oraz uruchamiania aplikacji na podstawie **systemem**.

   ![DebugInstalledAppPackage](../debugger/media/debug-installed-app-pkg.png "DebugInstalledAppPackage")

1. W razie potrzeby zmień typ kodu, w obszarze **debugować tego typu kodu**i wybierz inne opcje.
   - Wybierz **nie uruchamiaj, ale Debuguj kod przy rozpoczęciu** można rozpocząć debugowania po uruchomieniu aplikacji. Uruchamianie, debugowanie po uruchomieniu aplikacji jest efektywnym sposobem debugowania ścieżek kontroli [uruchomienia różnych metod](/windows/uwp/xbox-apps/automate-launching-uwp-apps), takich jak protokół aktywacji z użyciem niestandardowych parametrów.

1. Wybierz **Start**, lub jeśli aplikacja jest uruchomiona, wybierz opcję **Dołącz**.

> [!NOTE]
> Można również dołączyć do dowolnej działającej platformy uniwersalnej systemu Windows lub inny proces aplikacji, wybierając **debugowania** > **dołączyć do procesu** w programie Visual Studio. Nie ma potrzeby oryginalnego projektu programu Visual Studio można dołączyć do uruchomionego procesu, ale symbole obciążenia aplikacji pomoże znacznie podczas debugowania procesu, które nie mają oryginalny kod. Zobacz [określanie plików symboli i źródeł w debugerze programu](specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

## <a name="remote"></a> Debugowanie aplikacji platformy uniwersalnej systemu Windows zainstalowanych na komputerze zdalnym lub urządzeniu

Visual Studio debuguje aplikację platformy uniwersalnej systemu Windows zainstalowanego na urządzeniu z systemem Windows 10 lub komputerze aktualizacji systemu Windows 10 zdalnego post twórcy, po raz pierwszy instalacji narzędzia do debugowania zdalnego na urządzeniu docelowym.

1. [Włącz tryb dewelopera](/windows/uwp/get-started/enable-your-device-for-development) na komputer z programem Visual Studio i zdalnym urządzeniu lub komputerze.

1. Jeśli łączysz się z komputerem zdalnym systemem pre twórcy aktualizacji Windows 10, [ręcznie zainstalować i uruchomić zdalny debuger](../debugger/remote-debugging.md) na komputerze zdalnym.

1. Na komputerze programu Visual Studio, wybierz **debugowania** > **inne cele debugowania** > **pakietu debugowania zainstalowanej aplikacji**.

1. W **pakietu debugowania zainstalowanej aplikacji** okna dialogowego, w obszarze **typu połączenia**, wybierz opcję **maszyny zdalnej** lub **urządzenia**.

   Jeśli wybierzesz **urządzenia**, komputer musi być fizycznie połączone urządzenia z systemem Windows 10.

   Na komputerze zdalnym, jeśli adres komputera nie pojawia się obok **adres**, wybierz opcję **zmiany**.

   1. W **połączenia zdalnego** okno dialogowe, obok **adres**, wpisz nazwę lub adres IP komputera, o których chcesz się połączyć.

      ![ChooseRemoteComputer](../debugger/media/debug-remote-app-pkg.png "ChooseRemoteComputer")

      Jeśli debuger nie może połączyć się z komputerem zdalnym przy użyciu nazwy komputera, należy użyć adresu IP. Użyj adresu IP dla urządzeń z konsoli Xbox, HoloLens i IoT.
   1. Zaznacz opcję uwierzytelniania **tryb uwierzytelniania**.

      W przypadku większości aplikacji zachować wartość domyślną, **uniwersalny (protokół niezaszyfrowanym)**.
   1. Wybierz **wybierz**.

1. W obszarze **zainstalowane pakiety aplikacji**, a następnie wybierz aplikację, którą chcesz debugować lub wpisz jego nazwę w polu wyszukiwania. Uruchomiona bez zainstalowanych pakietów aplikacji są wyświetlane w obszarze **nieuruchomiona**, oraz uruchamiania aplikacji na podstawie **systemem**.

1. W razie potrzeby zmień typ kodu, w obszarze **debugować tego typu kodu**i wybierz inne opcje.
   - Wybierz **nie uruchamiaj, ale Debuguj kod przy rozpoczęciu** można rozpocząć debugowania po uruchomieniu aplikacji. Uruchamianie, debugowanie po uruchomieniu aplikacji jest efektywnym sposobem debugowania ścieżek kontroli [uruchomienia różnych metod](/windows/uwp/xbox-apps/automate-launching-uwp-apps), takich jak protokół aktywacji z użyciem niestandardowych parametrów.

1. Wybierz **Start**, lub jeśli aplikacja jest uruchomiona, wybierz opcję **Dołącz**.

Kiedy uruchamiasz debugowanie zainstalowanego pakietu aplikacji na konsoli Xbox, HoloLens i IoT na podłączonym urządzeniu po raz pierwszy, program Visual Studio instaluje poprawną wersję zdalnego debugera na urządzeniu docelowym. Instalowanie debugera zdalnego może zająć trochę czasu i komunikat o **Uruchamianie zdalnego debugera** Wyświetla trwającego.

>[!NOTE]
>Obecnie urządzenia Xbox lub na urządzeniu HoloLens powoduje ponowne uruchomienie aplikacji w debugerze, jeśli została już uruchomiona.

Aby uzyskać więcej informacji dotyczących zdalnego wdrażania aplikacji platformy uniwersalnej systemu Windows, zobacz [wdrażanie i debugowanie aplikacji platformy UWP](/windows/uwp/debug-test-perf/deploying-and-debugging-uwp-apps#advanced-remote-deployment-options) i [debugowanie aplikacji platformy UWP na komputerach zdalnych](run-windows-store-apps-on-a-remote-machine.md).

## <a name="see-also"></a>Zobacz także

- [Debugowanie w programie Visual Studio](../debugger/index.md)
- [Przewodnik po funkcjach debugera](../debugger/debugger-feature-tour.md)
- [Debugowanie zdalne](../debugger/remote-debugging.md)
- [Konfigurowanie zapory systemu Windows na potrzeby debugowania zdalnego](../debugger/configure-the-windows-firewall-for-remote-debugging.md)
- [Przypisania portów debugera zdalnego](../debugger/remote-debugger-port-assignments.md)
- [Błędy związane z debugowaniem zdalnym i rozwiązywanie problemów](../debugger/remote-debugging-errors-and-troubleshooting.md)