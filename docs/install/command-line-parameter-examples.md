---
title: Przykłady parametrów wiersza polecenia do instalacji
description: Dostosuj te przykłady, aby utworzyć własną instalację wiersza polecenia programu Visual Studio.
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
ms.openlocfilehash: 8fc43cef8526b2ca79bb0b88a1d56ef4f4a2a65a
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77275252"
---
# <a name="command-line-parameter-examples-for-visual-studio-installation"></a>Przykłady parametrów wiersza polecenia dla instalacji programu Visual Studio

Aby zilustrować sposób [używania parametrów wiersza polecenia do zainstalowania programu Visual Studio,](use-command-line-parameters-to-install-visual-studio.md)oto kilka przykładów, które można dostosować do swoich potrzeb.

W każdym `vs_enterprise.exe`przykładzie `vs_community.exe` i `vs_professional.exe` reprezentują odpowiednią wersję programu inicjującego programu Visual Studio, który jest mały (około 1MB) plik, który inicjuje proces pobierania. Jeśli używasz innej wersji, zastąp odpowiednią nazwę programu inicjującego.

> [!NOTE]
> Wszystkie polecenia wymagają podniesienia uprawnień administracyjnych, a monit kontroli konta użytkownika zostanie wyświetlony, jeśli proces nie zostanie uruchomiony z monitu z podwyższonym poziomem uprawnień.
>
> [!NOTE]
> Za pomocą `^` znaku na końcu wiersza polecenia można łączyć wiele wierszy w jedno polecenie. Alternatywnie można po prostu umieścić te linie razem na jednym wierszu. W programie PowerShell odpowiednikiem jest`` ` ``znak zaplecza ( ).

Aby uzyskać listę obciążeń i składników, które można zainstalować za pomocą wiersza polecenia, zobacz [obciążenie programu Visual Studio i identyfikatory składników](workload-and-component-ids.md) strony.

## <a name="using---installpath"></a>Korzystanie z --installPath

* Zainstaluj minimalne wystąpienie programu Visual Studio, bez interaktywnych monitów, ale wyświetlany postęp:

  ```cmd
   vs_enterprise.exe --installPath C:\minVS ^
   --add Microsoft.VisualStudio.Workload.CoreEditor ^
   --passive --norestart
  ```

* Zaktualizuj wystąpienie programu Visual Studio przy użyciu wiersza polecenia, bez interaktywnych monitów, ale wyświetlany postęp:

   ```cmd
   vs_enterprise.exe --update --quiet --wait
   vs_enterprise.exe update --wait --passive --norestart --installPath "C:\installPathVS"
   ```

  > [!NOTE]
  > Zaleca się stosowanie obu poleceń. Pierwsze polecenie aktualizuje Instalatora programu Visual Studio. Drugie polecenie aktualizuje wystąpienie programu Visual Studio. Aby uniknąć okna dialogowego Kontrola konta użytkownika, uruchom wiersz polecenia jako administrator.

* Zainstaluj wystąpienie pulpitu visual studio dyskretnie, z pakietem języka francuskiego, zwracany tylko wtedy, gdy produkt jest zainstalowany.

  ```cmd
   vs_enterprise.exe --installPath C:\desktopVS ^
   --addProductLang fr-FR ^
   --add Microsoft.VisualStudio.Workload.ManagedDesktop ^
   --includeRecommended --quiet --wait
  ```

## <a name="using---wait"></a>Korzystanie z --wait

* Użyj w plikach wsadowych lub skryptach, aby poczekać na zainstalowanie instalatora programu Visual Studio przed wykonaniem następnego polecenia. W przypadku plików `%ERRORLEVEL%` wsadowych zmienna środowiskowa będzie zawierać zwracaną wartość polecenia, zgodnie z dokumentami na stronie [Użyj wiersza polecenia do zainstalowania](use-command-line-parameters-to-install-visual-studio.md) programu Visual Studio. Niektóre narzędzia poleceń wymagają dodatkowych parametrów, aby poczekać na zakończenie i uzyskać wartość zwracaną instalatora. Poniżej przedstawiono przykład dodatkowych parametrów używanych w poleceniu skryptu programu PowerShell "Start-Process":

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

* Pierwszy '--wait' jest używany przez Instalatora programu Visual Studio, a drugi '-Wait' jest używany przez "Start-Process", aby czekać na zakończenie. Parametr '-PassThru' jest używany przez "Start-Process", aby użyć kodu wyjściowego instalatora dla jego wartości zwracanej.

## <a name="using---layout"></a>Korzystanie z --layout

* Pobierz edytor podstawowy programu Visual Studio (najbardziej minimalna konfiguracja programu Visual Studio). Dołącz tylko pakiet języka angielskiego:

  ```cmd
   vs_community.exe --layout C:\VS ^
   --lang en-US ^
   --add Microsoft.VisualStudio.Workload.CoreEditor
  ```

* Pobierz obciążenia sieci .NET na komputerach stacjonarnych i .NET wraz ze wszystkimi zalecanymi składnikami i rozszerzeniem GitHub. Dołącz tylko pakiet języka angielskiego:

  ```cmd
   vs_community.exe --layout C:\VS ^
   --lang en-US ^
   --add Microsoft.VisualStudio.Workload.NetWeb ^
   --add Microsoft.VisualStudio.Workload.ManagedDesktop ^
   --add Component.GitHub.VisualStudio ^
   --includeRecommended
  ```

## <a name="using---all"></a>Korzystanie z --all

* Rozpocznij interaktywną instalację wszystkich obciążeń i składników, które są dostępne w wersji programu Visual Studio Enterprise:

   ```cmd
   vs_enterprise.exe --all
   ```

## <a name="using---includerecommended"></a>Korzystanie z --includeReommended

* Zainstaluj drugie, nazwane wystąpienie programu Visual Studio Professional na komputerze z już zainstalowaną edycją społeczności programu Visual Studio, z obsługą rozwoju node.js:

   ```cmd
   vs_professional.exe --installPath C:\VSforNode ^
   --add Microsoft.VisualStudio.Workload.Node --includeRecommended --nickname VSforNode
  ```

## <a name="using---remove"></a>Korzystanie z --remove

::: moniker range="vs-2017"

* Usuń składnik Narzędzia profilowania z domyślnego zainstalowanego wystąpienia programu Visual Studio:

  ```cmd
   vs_enterprise.exe modify ^
   --installPath "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise" ^
   --remove Microsoft.VisualStudio.Component.DiagnosticTools ^
   --passive
  ```

::: moniker-end

::: moniker range="vs-2019"

* Usuń składnik Narzędzia profilowania z domyślnego zainstalowanego wystąpienia programu Visual Studio:

  ```cmd
   vs_enterprise.exe modify ^
   --installPath "C:\Program Files (x86)\Microsoft Visual Studio\2019\Enterprise" ^
   --remove Microsoft.VisualStudio.Component.DiagnosticTools ^
   --passive
  ```

::: moniker-end

## <a name="using---path"></a>Korzystanie ze ścieżki --

::: moniker range="vs-2017"

Te parametry wiersza polecenia są **nowe w 15.7**. Aby uzyskać więcej informacji na ich temat, zobacz [użyj parametrów wiersza polecenia, aby zainstalować](use-command-line-parameters-to-install-visual-studio.md) visual studio strony.

::: moniker-end

* Korzystanie ze ścieżek instalacji, pamięci podręcznej i udostępnionych:

  `vs_enterprise.exe --add Microsoft.VisualStudio.Workload.CoreEditor --path install="C:\VS" --path cache="C:\VS\cache" --path shared="C:\VS\shared"`

* Używanie tylko ścieżek instalacji i pamięci podręcznej:

  `vs_enterprise.exe --add Microsoft.VisualStudio.Workload.CoreEditor --path install="C:\VS" --path cache="C:\VS\cache"`

* Używanie tylko ścieżek instalacyjnych i udostępnionych:

  `vs_enterprise.exe --add Microsoft.VisualStudio.Workload.CoreEditor --path install="C:\VS" --path shared="C:\VS\shared"`

* Używanie tylko ścieżki instalacji:

  `vs_enterprise.exe --add Microsoft.VisualStudio.Workload.CoreEditor --path install="C:\VS"`

## <a name="using-export"></a>Korzystanie z eksportu

::: moniker range="vs-2017"

To polecenie wiersza polecenia jest **nowe w 15.9**. Aby uzyskać więcej informacji na ten temat, zobacz [użyj parametrów wiersza polecenia, aby zainstalować](use-command-line-parameters-to-install-visual-studio.md) visual studio strony.

::: moniker-end

* Za pomocą eksportu, aby zapisać zaznaczenie z instalacji:

  ```cmd
  "C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe" export --installPath "C:\VS" --config "C:\.vsconfig"
  ```

* Używanie eksportu do zapisywania zaznaczenia niestandardowego od podstaw:

  ```cmd
  "C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe" export --add Microsoft.VisualStudio.Workload.ManagedDesktop --includeRecommended --config "C:\.vsconfig"
  ```

## <a name="using---config"></a>Korzystanie z --config

::: moniker range="vs-2017"

Ten parametr wiersza polecenia jest **nowy w 15.9**. Aby uzyskać więcej informacji na ten temat, zobacz [użyj parametrów wiersza polecenia, aby zainstalować](use-command-line-parameters-to-install-visual-studio.md) visual studio strony.

::: moniker-end

* Użycie funkcji --config do zainstalowania obciążeń i składników z wcześniej zapisanego pliku konfiguracji instalacji:

  ```cmd
  vs_enterprise.exe --config "C:\.vsconfig" --installPath "C:\VS"
  ```

* Używanie funkcji --config do dodawania obciążeń i składników do istniejącej instalacji:

  ```cmd
  vs_enterprise.exe modify --installPath "C:\VS" --config "C:\.vsconfig"
  ```

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Zobacz też

* [Podręcznik administratora programu Visual Studio](visual-studio-administrator-guide.md)
* [Instalowanie programu Visual Studio za pomocą parametrów wiersza polecenia](use-command-line-parameters-to-install-visual-studio.md)
* [Tworzenie instalacji programu Visual Studio w trybie offline](create-an-offline-installation-of-visual-studio.md)
* [Identyfikatory obciążeń i składników programu Visual Studio](workload-and-component-ids.md)
