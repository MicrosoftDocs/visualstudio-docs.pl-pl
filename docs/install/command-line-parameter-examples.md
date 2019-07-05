---
title: Przykładowe parametry wiersza polecenia do zainstalowania
description: Dostosuj te przykłady do tworzenia własnych instalacji z wiersza polecenia programu Visual Studio.
ms.date: 03/30/2019
ms.custom: seodec18
ms.topic: conceptual
ms.assetid: 837F31AA-F121-46e9-9996-F8BCE768E579
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 0f35348e6704ffa822ba5dee93ad930f209004e1
ms.sourcegitcommit: 32144a09ed46e7223ef7dcab647a9f73afa2dd55
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/05/2019
ms.locfileid: "67586869"
---
# <a name="command-line-parameter-examples-for-visual-studio-installation"></a>Przykładowe parametry wiersza polecenia do zainstalowania programu Visual Studio

Aby zilustrować, jak [użyć parametrów wiersza polecenia, aby zainstalować program Visual Studio](use-command-line-parameters-to-install-visual-studio.md), poniżej przedstawiono kilka przykładów, które można dostosować do potrzeb.

W każdym przykładzie `vs_enterprise.exe`, `vs_professional.exe` i `vs_community.exe` reprezentują odpowiedniej wersji program inicjujący programu Visual Studio, czyli pliku małe (około 1 MB), który inicjuje proces pobierania. Jeśli używasz innej wersji, należy zastąpić nazwę odpowiedniego programu inicjującego.

> [!NOTE]
> Wszystkie polecenia wymaga podniesienia uprawnień administracyjnych oraz Kontrola konta użytkownika, jeśli proces nie jest uruchomiona w wierszu polecenia z podwyższonym poziomem uprawnień zostanie wyświetlony monit.
>
> [!NOTE]
> Możesz użyć `^` znak na końcu wiersza polecenia do łączenia wielu wierszy w pojedynczym poleceniu. Alternatywnie można po prostu umieścić te wiersze razem na jeden wiersz. W programie PowerShell odpowiednik to początkowych (`` ` ``) znaków.

Aby uzyskać listę obciążeń i składników, które można zainstalować przy użyciu wiersza polecenia, zobacz [identyfikatory obciążeń i składników programu Visual Studio](workload-and-component-ids.md) strony.

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

## <a name="using---wait"></a>Przy użyciu opcji--oczekiwania

* Umożliwia w plikach wsadowych lub skrypty poczekaj, aż Instalator programu Visual Studio w taki sposób, aby ukończyć przed wykonaniem polecenia dalej. W przypadku plików usługi batch `%ERRORLEVEL%` zmienna środowiskowa będzie zawierać wartość zwracaną przez polecenie, zgodnie z opisem w [użyć parametrów wiersza polecenia, aby zainstalować program Visual Studio](use-command-line-parameters-to-install-visual-studio.md) strony. Niektóre narzędzia polecenia wymaga dodatkowych parametrów, aby czekać na zakończenie i w celu uzyskania wartości zwracanej przez Instalator. Oto przykład dodatkowe parametry, które są używane z polecenia skryptu programu PowerShell "Procesu uruchamiania":

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

* Pierwszy "--oczekiwania" jest używany przez Instalatora programu Visual Studio, a drugi "-oczekiwania" jest używany przez "Procesu uruchamiania" czekać na zakończenie. "-PassThru" parametr jest używany przez "Procesu uruchamiania" na potrzeby Instalatora kod zakończenia jego zwracanej wartości.

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

## <a name="using---all"></a>Przy użyciu opcji--wszystko

* Rozpocznij instalacji interakcyjnej wszystkich obciążeń i składników, które są dostępne w programie Visual Studio Enterprise:

   ```cmd
   vs_enterprise.exe --all
   ```

## <a name="using---includerecommended"></a>Za pomocą--includeRecommended

* Zainstalować drugie wystąpienie nazwane programu Visual Studio Professional na komputerze z zainstalowanym, obsługę tworzenia aplikacji Node.js w wersji programu Visual Studio Community:

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
