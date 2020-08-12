---
title: Przykłady parametrów wiersza polecenia do zainstalowania
description: Dostosuj te przykłady, aby utworzyć własną instalację z wiersza polecenia programu Visual Studio.
ms.date: 03/30/2019
ms.custom: seodec18
ms.topic: conceptual
ms.assetid: 837F31AA-F121-46e9-9996-F8BCE768E579
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 1f182351cbb0351256ebe32b4ab70543022ed92c
ms.sourcegitcommit: d9254e54079ae01cdf2d07b11f988faf688f80fc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/11/2020
ms.locfileid: "88114248"
---
# <a name="command-line-parameter-examples-for-visual-studio-installation"></a>Przykłady parametrów wiersza polecenia dla instalacji programu Visual Studio

Aby zilustrować, jak [używać parametrów wiersza polecenia do instalowania programu Visual Studio](use-command-line-parameters-to-install-visual-studio.md), poniżej przedstawiono kilka przykładów, które można dostosować do własnych potrzeb.

W każdym przykładzie, `vs_enterprise.exe` `vs_professional.exe` i `vs_community.exe` reprezentuje odpowiednią wersję programu inicjującego programu Visual Studio, czyli mały (około 1 MB) plik inicjujący proces pobierania. W przypadku korzystania z innej wersji należy zastąpić odpowiednią nazwę programu inicjującego.

> [!NOTE]
> Wszystkie polecenia wymagają podniesienia uprawnień administracyjnych, a monit kontroli konta użytkownika będzie wyświetlany, jeśli proces nie zostanie uruchomiony z wiersza polecenia z podwyższonym poziomem uprawnień.
>
> [!NOTE]
> Możesz użyć `^` znaku na końcu wiersza polecenia, aby połączyć wiele wierszy w jedno polecenie. Alternatywnie możesz po prostu umieścić te wiersze w pojedynczym wierszu. W programie PowerShell odpowiednik jest znakiem kreski ( `` ` `` ).

Listę obciążeń i składników, które można zainstalować przy użyciu wiersza polecenia, znajdują się na stronie [obciążenia i identyfikatory składników programu Visual Studio](workload-and-component-ids.md) .

## <a name="using---installpath"></a>Używanie--installPath

* Zainstaluj minimalne wystąpienie programu Visual Studio bez interakcyjnych wyświetleń, ale zostanie wyświetlony postęp:

  ```cmd
   vs_enterprise.exe --installPath C:\minVS ^
   --add Microsoft.VisualStudio.Workload.CoreEditor ^
   --passive --norestart
  ```

* Zaktualizuj wystąpienie programu Visual Studio przy użyciu wiersza polecenia bez interaktywnych wierszy, ale jest wyświetlany postęp:

   ```cmd
   vs_enterprise.exe --update --quiet --wait
   vs_enterprise.exe update --wait --passive --norestart --installPath "C:\installPathVS"
   ```

  > [!NOTE]
  > Oba polecenia są zalecane. Pierwsze polecenie aktualizuje Instalator programu Visual Studio. Drugie polecenie aktualizuje wystąpienie programu Visual Studio. Aby uniknąć okna dialogowego Kontrola konta użytkownika, Uruchom wiersz polecenia jako administrator.

* Zainstaluj wystąpienie klasyczne programu Visual Studio w trybie dyskretnym z pakietem języka francuskiego, zwracając się tylko wtedy, gdy produkt jest zainstalowany.

  ```cmd
   vs_enterprise.exe --installPath C:\desktopVS ^
   --addProductLang fr-FR ^
   --add Microsoft.VisualStudio.Workload.ManagedDesktop ^
   --includeRecommended --quiet --wait
  ```

## <a name="using---wait"></a>Użycie--czekaj

* Użyj w plikach wsadowych lub w skryptach, aby poczekać na ukończenie Instalatora programu Visual Studio przed wykonaniem następnego polecenia. W przypadku plików wsadowych `%ERRORLEVEL%` zmienna środowiskowa będzie zawierać wartość zwracaną polecenia, zgodnie z opisem w [parametrach wiersza polecenia Użyj, aby zainstalować stronę programu Visual Studio](use-command-line-parameters-to-install-visual-studio.md) . Niektóre narzędzia poleceń wymagają dodatkowych parametrów oczekiwania na ukończenie i pobrania wartości zwracanej przez Instalatora. Poniżej znajduje się przykład dodatkowych parametrów używanych z poleceniem skryptu programu PowerShell "Start-Process":

   ```cmd
   start /wait vs_professional.exe --installPath "C:\VS" --passive --wait > nul
   echo %errorlevel%
   ```

   ```powershell
   $process = Start-Process -FilePath vs_enterprise.exe -ArgumentList "--installPath", "C:\VS", "--passive", "--wait" -Wait -PassThru
   Write-Output $process.ExitCode 
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

## <a name="using---layout"></a>Using — układ

* Pobierz Edytor podstawowy programu Visual Studio (najważniejsza konfiguracja programu Visual Studio). Uwzględnij tylko pakiet języka angielskiego:

  ```cmd
   vs_community.exe --layout C:\VS ^
   --lang en-US ^
   --add Microsoft.VisualStudio.Workload.CoreEditor
  ```

* Pobierz obciążenia sieci Web programu .NET Desktop i .NET wraz ze wszystkimi zalecanymi składnikami i rozszerzeniem usługi GitHub. Uwzględnij tylko pakiet języka angielskiego:

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

## <a name="using---includerecommended"></a>Używanie--includeRecommended

* Zainstaluj drugie nazwane wystąpienie Visual Studio Professional na komputerze z zainstalowanym już programem Visual Studio Community Edition z obsługą Node.js tworzenia oprogramowania:

   ```cmd
   vs_professional.exe --installPath C:\VSforNode ^
   --add Microsoft.VisualStudio.Workload.Node --includeRecommended --nickname VSforNode
  ```

## <a name="using---remove"></a>Użycie--Remove

::: moniker range="vs-2017"

* Usuń składnik narzędzia profilowania z domyślnego zainstalowanego wystąpienia programu Visual Studio:

  ```cmd
   vs_enterprise.exe modify ^
   --installPath "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise" ^
   --remove Microsoft.VisualStudio.Component.DiagnosticTools ^
   --passive
  ```

::: moniker-end

::: moniker range="vs-2019"

* Usuń składnik narzędzia profilowania z domyślnego zainstalowanego wystąpienia programu Visual Studio:

  ```cmd
   vs_enterprise.exe modify ^
   --installPath "C:\Program Files (x86)\Microsoft Visual Studio\2019\Enterprise" ^
   --remove Microsoft.VisualStudio.Component.DiagnosticTools ^
   --passive
  ```

::: moniker-end

## <a name="using---path"></a>Użycie--Path

::: moniker range="vs-2017"

Te parametry wiersza polecenia są **nowe w 15,7**. Aby uzyskać więcej informacji na ten temat, zobacz temat [Używanie parametrów wiersza polecenia do instalowania programu Visual Studio](use-command-line-parameters-to-install-visual-studio.md) .

::: moniker-end

* Przy użyciu ścieżki instalacji, pamięci podręcznej i udostępnionych:

  `vs_enterprise.exe --add Microsoft.VisualStudio.Workload.CoreEditor --path install="C:\VS" --path cache="C:\VS\cache" --path shared="C:\VS\shared"`

* Używanie tylko ścieżek instalacji i pamięci podręcznej:

  `vs_enterprise.exe --add Microsoft.VisualStudio.Workload.CoreEditor --path install="C:\VS" --path cache="C:\VS\cache"`

* Używane są tylko ścieżki instalacyjne i udostępnione:

  `vs_enterprise.exe --add Microsoft.VisualStudio.Workload.CoreEditor --path install="C:\VS" --path shared="C:\VS\shared"`

* Używanie tylko ścieżki instalacji:

  `vs_enterprise.exe --add Microsoft.VisualStudio.Workload.CoreEditor --path install="C:\VS"`

## <a name="using-export"></a>Korzystanie z eksportu

::: moniker range="vs-2017"

To polecenie wiersza polecenia jest **nowe w 15,9**. Aby uzyskać więcej informacji na ten temat, zobacz temat [Używanie parametrów wiersza polecenia do instalowania programu Visual Studio](use-command-line-parameters-to-install-visual-studio.md) .

::: moniker-end

* Za pomocą eksportu Zapisz zaznaczenie z instalacji:

  ```cmd
  "C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe" export --installPath "C:\VS" --config "C:\.vsconfig"
  ```

* Za pomocą eksportu Zapisz niestandardowe zaznaczenie od podstaw:

  ```cmd
  "C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe" export --add Microsoft.VisualStudio.Workload.ManagedDesktop --includeRecommended --config "C:\.vsconfig"
  ```

## <a name="using---config"></a>Użycie--config

::: moniker range="vs-2017"

Ten parametr wiersza polecenia jest **Nowy w 15,9**. Aby uzyskać więcej informacji na ten temat, zobacz temat [Używanie parametrów wiersza polecenia do instalowania programu Visual Studio](use-command-line-parameters-to-install-visual-studio.md) .

::: moniker-end

* Użycie polecenia--config w celu zainstalowania obciążeń i składników z wcześniej zapisanego pliku konfiguracji instalacji:

  ```cmd
  vs_enterprise.exe --config "C:\.vsconfig" --installPath "C:\VS"
  ```

* Użycie--config do dodania obciążeń i składników do istniejącej instalacji:

  ```cmd
  vs_enterprise.exe modify --installPath "C:\VS" --config "C:\.vsconfig"
  ```

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Zobacz także

* [Przewodnik administratora programu Visual Studio](visual-studio-administrator-guide.md)
* [Korzystanie z parametrów wiersza polecenia do zainstalowania programu Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
* [Tworzenie instalacji w trybie offline programu Visual Studio](create-an-offline-installation-of-visual-studio.md)
* [Identyfikatory obciążeń i składników programu Visual Studio](workload-and-component-ids.md)
