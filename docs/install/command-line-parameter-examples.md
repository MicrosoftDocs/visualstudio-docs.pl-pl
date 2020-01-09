---
title: Przykładowe parametry wiersza polecenia do zainstalowania
description: Dostosuj te przykłady do tworzenia własnych instalacji z wiersza polecenia programu Visual Studio.
ms.date: 03/30/2019
ms.custom: seodec18
ms.topic: conceptual
ms.assetid: 837F31AA-F121-46e9-9996-F8BCE768E579
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: ce4a118d57c20cad9556ecb3b44127ed10ae96b0
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75597285"
---
# <a name="command-line-parameter-examples-for-visual-studio-installation"></a>Przykłady parametrów wiersza polecenia dla instalacji programu Visual Studio

Aby zilustrować, jak [użyć parametrów wiersza polecenia, aby zainstalować program Visual Studio](use-command-line-parameters-to-install-visual-studio.md), poniżej przedstawiono kilka przykładów, które można dostosować do potrzeb.

W każdym przykładzie `vs_enterprise.exe`, `vs_professional.exe` i `vs_community.exe` reprezentują odpowiedniej wersji program inicjujący programu Visual Studio, czyli pliku małe (około 1 MB), który inicjuje proces pobierania. Jeśli używasz innej wersji, należy zastąpić nazwę odpowiedniego programu inicjującego.

> [!NOTE]
> Wszystkie polecenia wymaga podniesienia uprawnień administracyjnych oraz Kontrola konta użytkownika, jeśli proces nie jest uruchomiona w wierszu polecenia z podwyższonym poziomem uprawnień zostanie wyświetlony monit.
>
> [!NOTE]
> Możesz użyć `^` znak na końcu wiersza polecenia do łączenia wielu wierszy w pojedynczym poleceniu. Alternatywnie można po prostu umieścić te wiersze razem na jeden wiersz. W programie PowerShell odpowiednik to początkowych (`` ` ``) znaków.

Listę obciążeń i składników, które można zainstalować przy użyciu wiersza polecenia, znajdują się na stronie [obciążenia i identyfikatory składników programu Visual Studio](workload-and-component-ids.md) .

## <a name="using---installpath"></a>Przy użyciu opcji--installPath

* Zainstaluj minimalny wystąpienia programu Visual Studio przy użyciu nie interaktywne monity, ale wyświetlany postęp:

  ```cmd
   vs_enterprise.exe --installPath C:\minVS ^
   --add Microsoft.VisualStudio.Workload.CoreEditor ^
   --passive --norestart
  ```

* Aktualizacja wystąpienia programu Visual Studio przy użyciu wiersza polecenia nie interaktywne monity, ale wyświetlany postęp:

   ```cmd
   vs_enterprise.exe --update --quiet --wait
   vs_enterprise.exe update --wait --passive --norestart --installPath "C:\installPathVS"
   ```

  > [!NOTE]
  > Oba polecenia są wymagane. Pierwsze polecenie aktualizuje Instalatora programu Visual Studio. Drugie polecenie aktualizuje wystąpienia programu Visual Studio. Aby uniknąć okno Kontrola konta użytkownika, należy uruchomić wiersz polecenia jako Administrator.

* Zainstalować pulpitu wystąpienia programu Visual Studio w trybie dyskretnym, przy użyciu pakietu języka francuskiego, zwracając tylko wtedy, gdy produkt jest zainstalowany.

  ```cmd
   vs_enterprise.exe --installPath C:\desktopVS ^
   --addProductLang fr-FR ^
   --add Microsoft.VisualStudio.Workload.ManagedDesktop ^
   --includeRecommended --quiet --wait
  ```

## <a name="using---wait"></a>Użycie--czekaj

* Użyj w plikach wsadowych lub w skryptach, aby poczekać na ukończenie Instalatora programu Visual Studio przed wykonaniem następnego polecenia. W przypadku plików wsadowych zmienna środowiskowa `%ERRORLEVEL%` będzie zawierać wartość zwracaną polecenia, zgodnie z opisem w [parametrach wiersza polecenia Użyj, aby zainstalować stronę programu Visual Studio](use-command-line-parameters-to-install-visual-studio.md) . Niektóre narzędzia poleceń wymagają dodatkowych parametrów oczekiwania na ukończenie i pobrania wartości zwracanej przez Instalatora. Poniżej znajduje się przykład dodatkowych parametrów używanych z poleceniem skryptu programu PowerShell "Start-Process":

   ```cmd
   start /wait vs_professional.exe --installPath "C:\VS" --passive --wait > nul
   echo %errorlevel%
   ```

   ```powershell
   $exitCode = Start-Process -FilePath vs_enterprise.exe -ArgumentList "--installPath", "C:\VS", "--passive", "--wait" -Wait -PassThru
   ```

   lub

   ```powershell
    $startInfo = New-Object System.Diagnostics.ProcessStartInfo
    $startInfo.FileName = "vs_enterprise.exe"
    $startInfo.Arguments = "--all --quiet --wait"
    $process = New-Object System.Diagnostics.Process
    $process.StartInfo = $startInfo
    $process.Start()
    $process.WaitForExit()
   ```

* Pierwszy "--Wait" jest używany przez Instalator programu Visual Studio, a drugi "-Wait" jest używany przez element "Start-Process", aby poczekać na zakończenie. Parametr "-PassThru" jest używany przez "Start-Process", aby użyć kodu zakończenia Instalatora dla jego wartości zwracanej.

## <a name="using---layout"></a>Przy użyciu opcji--układu

* Pobierz podstawowy edytor programu Visual Studio (najbardziej minimalny konfiguracji programu Visual Studio). Tylko obejmują pakiet języka angielskiego:

  ```cmd
   vs_community.exe --layout C:\VS
   --lang en-US ^
   --add Microsoft.VisualStudio.Workload.CoreEditor
  ```

* Pobierz .NET dla komputerów stacjonarnych i obciążenia sieci web platformy .NET oraz wszystkie zalecane składniki i rozszerzenia usługi GitHub. Tylko obejmują pakiet języka angielskiego:

  ```cmd
   vs_community.exe --layout C:\VS ^
   --lang en-US ^
   --add Microsoft.VisualStudio.Workload.NetWeb ^
   --add Microsoft.VisualStudio.Workload.ManagedDesktop ^
   --add Component.GitHub.VisualStudio ^
   --includeRecommended
  ```

## <a name="using---all"></a>Użycie — wszystkie

* Rozpocznij instalację interaktywną wszystkich obciążeń i składników, które są dostępne w wersji Visual Studio Enterprise:

   ```cmd
   vs_enterprise.exe --all
   ```

## <a name="using---includerecommended"></a>Za pomocą--includeRecommended

* Zainstaluj drugie nazwane wystąpienie Visual Studio Professional na komputerze z zainstalowanym już programem Visual Studio Community Edition z obsługą programowania Node. js:

   ```cmd
   vs_professional.exe --installPath C:\VSforNode ^
   --add Microsoft.VisualStudio.Workload.Node --includeRecommended --nickname VSforNode
  ```

## <a name="using---remove"></a>Przy użyciu opcji--Usuń

::: moniker range="vs-2017"

* Usuń składnik Profiling Tools z domyślnego zainstalowane wystąpienia programu Visual Studio:

  ```cmd
   vs_enterprise.exe modify ^
   --installPath "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise" ^
   --remove Microsoft.VisualStudio.Component.DiagnosticTools ^
   --passive
  ```

::: moniker-end

::: moniker range="vs-2019"

* Usuń składnik Profiling Tools z domyślnego zainstalowane wystąpienia programu Visual Studio:

  ```cmd
   vs_enterprise.exe modify ^
   --installPath "C:\Program Files (x86)\Microsoft Visual Studio\2019\Enterprise" ^
   --remove Microsoft.VisualStudio.Component.DiagnosticTools ^
   --passive
  ```

::: moniker-end

## <a name="using---path"></a>Przy użyciu opcji--ścieżki

::: moniker range="vs-2017"

Te parametry wiersza polecenia jest **Nowość w wersji 15.7**. Aby uzyskać więcej informacji na temat ich zobacz [użyć parametrów wiersza polecenia, aby zainstalować program Visual Studio](use-command-line-parameters-to-install-visual-studio.md) strony.

::: moniker-end

* Korzystanie z instalacji, pamięci podręcznej i udostępnionej ścieżki:

  `vs_enterprise.exe --add Microsoft.VisualStudio.Workload.CoreEditor --path install="C:\VS" --path cache="C:\VS\cache" --path shared="C:\VS\shared"`

* Przy użyciu tylko ścieżki instalacji i pamięci podręcznej:

  `vs_enterprise.exe --add Microsoft.VisualStudio.Workload.CoreEditor --path install="C:\VS" --path cache="C:\VS\cache"`

* Przy użyciu tylko instalacji i udostępnionej ścieżki:

  `vs_enterprise.exe --add Microsoft.VisualStudio.Workload.CoreEditor --path install="C:\VS" --path shared="C:\VS\shared"`

* Przy użyciu tylko ścieżki instalacji:

  `vs_enterprise.exe --add Microsoft.VisualStudio.Workload.CoreEditor --path install="C:\VS"`

## <a name="using-export"></a>Użycie opcji eksportowania

::: moniker range="vs-2017"

To polecenie wiersza polecenia jest **nowego w programie 15.9**. Aby uzyskać więcej informacji na ten temat, zobacz [użyć parametrów wiersza polecenia, aby zainstalować program Visual Studio](use-command-line-parameters-to-install-visual-studio.md) strony.

::: moniker-end

* Użycie opcji eksportowania zapisać je przy użyciu instalacji:

  ```cmd
  "C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe" export --installPath "C:\VS" --config "C:\.vsconfig"
  ```

* Zapisz niestandardowy wybór od podstaw przy użyciu eksportu:

  ```cmd
  "C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe" export --add Microsoft.VisualStudio.Workload.ManagedDesktop --includeRecommended --config "C:\.vsconfig"
  ```

## <a name="using---config"></a>Za pomocą--config

::: moniker range="vs-2017"

Ten parametr wiersza polecenia jest **nowego w programie 15.9**. Aby uzyskać więcej informacji na ten temat, zobacz [użyć parametrów wiersza polecenia, aby zainstalować program Visual Studio](use-command-line-parameters-to-install-visual-studio.md) strony.

::: moniker-end

* Do zainstalowania obciążeń i składników z pliku konfiguracji instalacji wcześniej zapisany, przy użyciu--config:

  ```cmd
  vs_enterprise.exe --config "C:\.vsconfig" --installPath "C:\VS"
  ```

* Dodawanie obciążeń i składników do istniejącej instalacji przy użyciu--config:

  ```cmd
  vs_enterprise.exe modify --installPath "C:\VS" --config "C:\.vsconfig"
  ```

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Zobacz także

* [Podręcznik administratora programu Visual Studio](visual-studio-administrator-guide.md)
* [Korzystanie z parametrów wiersza polecenia do zainstalowania programu Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
* [Tworzenie instalacji w trybie offline programu Visual Studio](create-an-offline-installation-of-visual-studio.md)
* [Identyfikatory obciążeń i składników programu Visual Studio](workload-and-component-ids.md)
