---
title: Debugowanie zainstalowanego pakietu aplikacji platformy UWP | Microsoft Docs
ms.custom: ''
ms.date: 11/07/2018
ms.topic: how-to
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
ms.openlocfilehash: eabc694665bede7d193a360a01c42366568e33c5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85350735"
---
# <a name="debug-an-installed-uwp-app-package-in-visual-studio"></a>Debugowanie zainstalowanego pakietu aplikacji platformy UWP w programie Visual Studio

Program Visual Studio umożliwia debugowanie zainstalowanych pakietów aplikacji platforma uniwersalna systemu Windows (platformy UWP) na komputerach z systemem Windows 10 oraz na urządzeniach Xbox, HoloLens i IoT.

>[!NOTE]
>Debugowanie programu Visual Studio dla zainstalowanych aplikacji platformy UWP nie jest obsługiwane na telefonach.

Aby uzyskać więcej informacji na temat debugowania aplikacji platformy UWP, zapoznaj się z wpisami w blogu dotyczącymi [debugowania zainstalowanych pakietów aplikacji](https://devblogs.microsoft.com/devops/updates-for-debugging-installed-app-packages-in-visual-studio-2015-update-2/) i [tworzenia aplikacji uniwersalnych systemu Windows (platformy UWP)](https://devblogs.microsoft.com/visualstudio/universal-windows-apps-targeting-windows-10-anniversary-sdk/).

## <a name="debug-an-installed-uwp-app-on-a-local-machine"></a>Debugowanie zainstalowanej aplikacji platformy UWP na komputerze lokalnym

1. W programie Visual Studio wybierz kolejno opcje **Debuguj**  >  **inne elementy docelowe debugowania**  >  **Debuguj zainstalowany pakiet aplikacji**.

1. W oknie dialogowym **Debuguj zainstalowany pakiet aplikacji** w obszarze **Typ połączenia**wybierz pozycję **komputer lokalny**.

1. W obszarze **zainstalowane pakiety aplikacji**wybierz aplikację, którą chcesz debugować, lub wpisz jej nazwę w polu wyszukiwania. Nieuruchomione zainstalowane pakiety aplikacji są wyświetlane w obszarze **nie działa** **i uruchomione aplikacje działają.**

   ![DebugInstalledAppPackage](../debugger/media/debug-installed-app-pkg.png "DebugInstalledAppPackage")

1. W razie potrzeby zmień typ kodu w obszarze **Debuguj ten typ kodu**i wybierz inne opcje.
   - Wybierz pozycję nie **uruchamiaj, ale Debuguj mój kod po** rozpoczęciu uruchamiania debugowania podczas uruchamiania aplikacji. Rozpoczęcie debugowania, gdy aplikacja jest uruchomiona, jest skutecznym sposobem debugowania ścieżek kontroli z [różnych metod uruchamiania](/windows/uwp/xbox-apps/automate-launching-uwp-apps), takich jak aktywacja protokołu z parametrami niestandardowymi.

1. Wybierz pozycję **Start**lub, jeśli aplikacja jest uruchomiona, a następnie wybierz pozycję **Dołącz**.

> [!NOTE]
> Możesz również dołączyć do dowolnego działającego platformy UWP lub innego procesu aplikacji, wybierając pozycję **Debuguj**  >  **Dołącz do procesu** w programie Visual Studio. Oryginalny projekt programu Visual Studio nie jest potrzebny do dołączenia do uruchomionego procesu, ale załadowanie symboli aplikacji pomoże znacząco podczas debugowania procesu, w którym nie jest używany oryginalny kod. Zobacz [Określanie symboli i plików źródłowych w debugerze](specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

## <a name="debug-an-installed-uwp-app-on-a-remote-computer-or-device"></a><a name="remote"></a> Debugowanie zainstalowanej aplikacji platformy UWP na komputerze zdalnym lub urządzeniu

Gdy program Visual Studio po raz pierwszy debuguje zainstalowaną aplikację platformy UWP na urządzeniu z systemem Windows 10 lub zdalnym komputerze z systemem Windows 10 z aktualizacją dla twórców po stronie użytkownika, instaluje narzędzia zdalnego debugowania na urządzeniu docelowym.

1. [Włącz tryb dewelopera](/windows/uwp/get-started/enable-your-device-for-development) na komputerze programu Visual Studio i urządzeniu zdalnym lub komputerze.

1. W przypadku nawiązywania połączenia z komputerem zdalnym z aktualizacją systemu Windows 10 programu precreator [ręcznie zainstaluj i uruchom zdalny debuger](../debugger/remote-debugging.md) na komputerze zdalnym.

1. Na komputerze z Visual Studio wybierz pozycję **Debuguj**  >  **inne elementy docelowe debugowania**  >  **Debuguj zainstalowany pakiet aplikacji**.

1. W oknie dialogowym **Debuguj zainstalowany pakiet aplikacji** w obszarze **Typ połączenia**wybierz pozycję **maszyna zdalna** lub **urządzenie**.

   W przypadku wybrania opcji **urządzenie**komputer musi być fizycznie podłączony do urządzenia z systemem Windows 10.

   W przypadku komputera zdalnego, jeśli adres komputera nie pojawia się obok pozycji **adres**, wybierz pozycję **Zmień**.

   1. W oknie dialogowym **połączenie zdalne** obok pozycji **adres**wpisz nazwę lub adres IP komputera, z którym chcesz nawiązać połączenie.

      ![ChooseRemoteComputer](../debugger/media/debug-remote-app-pkg.png "ChooseRemoteComputer")

      Jeśli debuger nie może połączyć się z komputerem zdalnym przy użyciu nazwy komputera, zamiast tego użyj adresu IP. Użyj adresu IP dla urządzeń Xbox, HoloLens lub IoT.
   1. Wybierz opcję uwierzytelniania obok opcji **tryb uwierzytelniania**.

      W przypadku większości aplikacji należy zachować wartość domyślną, **uniwersalną (niezaszyfrowany protokół)**.
   1. Wybierz pozycję **Wybierz**.

1. W obszarze **zainstalowane pakiety aplikacji**wybierz aplikację, którą chcesz debugować, lub wpisz jej nazwę w polu wyszukiwania. Nieuruchomione zainstalowane pakiety aplikacji są wyświetlane w obszarze **nie działa** **i uruchomione aplikacje działają.**

1. W razie potrzeby zmień typ kodu w obszarze **Debuguj ten typ kodu**i wybierz inne opcje.
   - Wybierz pozycję nie **uruchamiaj, ale Debuguj mój kod po** rozpoczęciu uruchamiania debugowania podczas uruchamiania aplikacji. Rozpoczęcie debugowania, gdy aplikacja jest uruchomiona, jest skutecznym sposobem debugowania ścieżek kontroli z [różnych metod uruchamiania](/windows/uwp/xbox-apps/automate-launching-uwp-apps), takich jak aktywacja protokołu z parametrami niestandardowymi.

1. Wybierz pozycję **Start**lub, jeśli aplikacja jest uruchomiona, a następnie wybierz pozycję **Dołącz**.

Po rozpoczęciu debugowania zainstalowanego pakietu aplikacji na podłączonym urządzeniu Xbox, HoloLens lub IoT po raz pierwszy program Visual Studio zainstaluje poprawną wersję debugera zdalnego dla urządzenia docelowego. Zainstalowanie zdalnego debugera może zająć trochę czasu, a komunikat, który **uruchamia zdalny debuger** , pojawia się w czasie, gdy występuje.

>[!NOTE]
>Obecnie urządzenie Xbox lub HoloLens uruchamia ponownie aplikację z debugerem dołączonym, jeśli był już uruchomiony.

Aby uzyskać więcej informacji na temat zdalnego wdrażania aplikacji platformy UWP, zobacz [wdrażanie i debugowanie aplikacji platformy UWP](/windows/uwp/debug-test-perf/deploying-and-debugging-uwp-apps#advanced-remote-deployment-options) oraz [debugowanie aplikacji platformy UWP na komputerach zdalnych](run-windows-store-apps-on-a-remote-machine.md).

## <a name="see-also"></a>Zobacz też

- [Debugowanie w Visual Studio](../debugger/index.yml)
- [Pierwsze spojrzenie na debugera](../debugger/debugger-feature-tour.md)
- [Debugowanie zdalne](../debugger/remote-debugging.md)
- [Konfigurowanie zapory systemu Windows na potrzeby debugowania zdalnego](../debugger/configure-the-windows-firewall-for-remote-debugging.md)
- [Przypisania portów zdalnego debugera](../debugger/remote-debugger-port-assignments.md)
- [Błędy debugowania zdalnego i rozwiązywanie problemów](../debugger/remote-debugging-errors-and-troubleshooting.md)