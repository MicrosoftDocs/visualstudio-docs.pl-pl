---
title: Przykłady parametrów wiersza polecenia do instalacji
description: Dostosuj te przykłady, aby utworzyć własną instalację wiersza polecenia Visual Studio.
ms.date: 03/30/2019
ms.custom: seodec18
ms.topic: conceptual
ms.assetid: 837F31AA-F121-46e9-9996-F8BCE768E579
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 5685de34235dcd9b903cbf5be6371ebf3f1e84c3
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/17/2021
ms.locfileid: "112307547"
---
# <a name="command-line-parameter-examples-for-visual-studio-installation"></a>Przykłady parametrów wiersza polecenia Visual Studio instalacji

Aby zilustrować sposób używania parametrów wiersza polecenia do instalowania Visual Studio [,](use-command-line-parameters-to-install-visual-studio.md)poniżej przedstawiono kilka przykładów, które można dostosować do swoich potrzeb.

W każdym przykładzie , i reprezentują odpowiednią wersję programu inicjatora Visual Studio, który jest małym `vs_enterprise.exe` `vs_professional.exe` `vs_community.exe` plikiem (około 1 MB), który inicjuje proces pobierania. Jeśli używasz innej wersji, zastąp odpowiednią nazwę programu inicjjącego.

> [!NOTE]
> Wszystkie polecenia wymagają podniesienia uprawnień administracyjnych, a jeśli proces nie zostanie uruchomiony z wiersza z podwyższonym poziomem uprawnień, zostanie wyświetlony monit Kontrola konta użytkownika.
>
> [!NOTE]
> Można użyć znaku na końcu wiersza polecenia, aby zjednować `^` wiele wierszy w jednym poleceniu. Alternatywnie możesz po prostu umieścić te wiersze razem w jednym wierszu. W programie PowerShell odpowiednikiem jest znak znaku podtypki ( `` ` `` ).

Aby uzyskać listę obciążeń i składników, które można zainstalować przy użyciu wiersza polecenia, zobacz stronę [Visual Studio obciążenia i identyfikatorów](workload-and-component-ids.md) składników.

## <a name="using---installpath"></a>Korzystanie z --installPath

* Zainstaluj minimalne wystąpienie klasy Visual Studio bez monitów interakcyjnych, ale wyświetlany jest postęp:

  ```shell
   vs_enterprise.exe --installPath C:\minVS ^
   --add Microsoft.VisualStudio.Workload.CoreEditor ^
   --passive --norestart
  ```

* Zaktualizuj wystąpienie Visual Studio przy użyciu wiersza polecenia bez monitów interakcyjnych, ale wyświetlany jest postęp:

   ```shell
   vs_enterprise.exe --update --quiet --wait
   vs_enterprise.exe update --wait --passive --norestart --installPath "C:\installPathVS"
   ```

  > [!NOTE]
  > Zaleca się oba polecenia. Pierwsze polecenie aktualizuje Instalator programu Visual Studio. Drugie polecenie aktualizuje Visual Studio wystąpienie. Aby uniknąć okna dialogowego Kontrola konta użytkownika, uruchom wiersz polecenia jako administrator.

* Zainstaluj wystąpienie pulpitu usługi Visual Studio w trybie dyskretnym z pakietem języka francuskiego, zwracając tylko wtedy, gdy produkt jest zainstalowany.

  ```shell
   vs_enterprise.exe --installPath C:\desktopVS ^
   --addProductLang fr-FR ^
   --add Microsoft.VisualStudio.Workload.ManagedDesktop ^
   --includeRecommended --quiet --wait
  ```

## <a name="using---wait"></a>Korzystanie z --wait

* Użyj polecenia w plikach wsadowych lub skryptach, aby Visual Studio instalatora przed wykonaniem następnego polecenia. W przypadku plików wsadowych zmienna środowiskowa będzie zawierać wartość zwracaną polecenia zgodnie z dokumentem na stronie Instalowanie aplikacji przy `%ERRORLEVEL%` [użyciu Visual Studio](use-command-line-parameters-to-install-visual-studio.md) wiersza polecenia. Niektóre narzędzia poleceń wymagają dodatkowych parametrów do oczekiwania na ukończenie i uzyskania wartości zwracanej przez instalatora. Poniżej przedstawiono przykład dodatkowych parametrów używanych w poleceniu skryptu programu PowerShell "Start-Process":

   ```shell
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

* Pierwsza opcja "--wait" jest używana przez Instalator programu Visual Studio, a druga "-Wait" jest używana przez proces "Start-Process" do oczekiwania na ukończenie. Parametr "-PassThru" jest używany przez parametr "Start-Process" do użycia kodu zakończenia instalatora dla jego wartości zwracanej.

## <a name="using---layout"></a>Korzystanie z --layout

* Pobierz Visual Studio podstawowy edytor (najbardziej minimalna Visual Studio konfiguracji). Uwzględnij tylko pakiet językowy w języku angielskim:

  ```shell
   vs_community.exe --layout C:\VS ^
   --lang en-US ^
   --add Microsoft.VisualStudio.Workload.CoreEditor
  ```

* Pobierz obciążenia internetowe .NET desktop i .NET wraz ze wszystkimi zalecanymi składnikami i rozszerzeniem Usługi GitHub. Uwzględnij tylko pakiet językowy w języku angielskim:

  ```shell
   vs_community.exe --layout C:\VS ^
   --lang en-US ^
   --add Microsoft.VisualStudio.Workload.NetWeb ^
   --add Microsoft.VisualStudio.Workload.ManagedDesktop ^
   --add Component.GitHub.VisualStudio ^
   --includeRecommended
  ```

## <a name="using---all"></a>Korzystanie z --all

* Uruchom interaktywną instalację wszystkich obciążeń i składników, które są dostępne w Visual Studio Enterprise wersji:

   ```shell
   vs_enterprise.exe --all
   ```

## <a name="using---includerecommended"></a>Używanie --includeRecommended

* Zainstaluj drugie, nazwane wystąpienie programu Visual Studio Professional na maszynie z już Visual Studio Community edition z obsługą Node.js tworzenia aplikacji:

   ```shell
   vs_professional.exe --installPath C:\VSforNode ^
   --add Microsoft.VisualStudio.Workload.Node --includeRecommended --nickname VSforNode
  ```

## <a name="using---remove"></a>Za pomocą --remove

::: moniker range="vs-2017"

* Usuń składnik narzędzia profilowania z domyślnego zainstalowanego Visual Studio wystąpienia:

  ```shell
   vs_enterprise.exe modify ^
   --installPath "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise" ^
   --remove Microsoft.VisualStudio.Component.DiagnosticTools ^
   --passive
  ```

::: moniker-end

::: moniker range="vs-2019"

* Usuń składnik narzędzia profilowania z domyślnego zainstalowanego Visual Studio wystąpienia:

  ```shell
   vs_enterprise.exe modify ^
   --installPath "C:\Program Files (x86)\Microsoft Visual Studio\2019\Enterprise" ^
   --remove Microsoft.VisualStudio.Component.DiagnosticTools ^
   --passive
  ```

::: moniker-end

::: moniker range=">=vs-2022"

* Usuń składnik narzędzia profilowania z domyślnego zainstalowanego Visual Studio wystąpienia:

  ```shell
   vs_enterprise.exe modify ^
   --installPath "C:\Program Files\Microsoft Visual Studio\2022\Enterprise" ^
   --remove Microsoft.VisualStudio.Component.DiagnosticTools ^
   --passive
  ```

::: moniker-end

## <a name="using---path"></a>Korzystanie z --path

::: moniker range="vs-2017"

Te parametry wiersza polecenia są **nowe w 15.7.** Aby uzyskać więcej informacji na ich temat, zobacz [stronę Use command-line parameters to install Visual Studio](use-command-line-parameters-to-install-visual-studio.md) (Używanie parametrów wiersza polecenia do Visual Studio wiersza polecenia).

::: moniker-end

* Korzystając ze ścieżek instalacji, pamięci podręcznej i udostępnionych:

  `vs_enterprise.exe --add Microsoft.VisualStudio.Workload.CoreEditor --path install="C:\VS" --path cache="C:\VS\cache" --path shared="C:\VS\shared"`

* Używanie tylko ścieżek instalacji i pamięci podręcznej:

  `vs_enterprise.exe --add Microsoft.VisualStudio.Workload.CoreEditor --path install="C:\VS" --path cache="C:\VS\cache"`

* Używanie tylko ścieżek instalacji i udostępnionych:

  `vs_enterprise.exe --add Microsoft.VisualStudio.Workload.CoreEditor --path install="C:\VS" --path shared="C:\VS\shared"`

* Używając tylko ścieżki instalacji:

  `vs_enterprise.exe --add Microsoft.VisualStudio.Workload.CoreEditor --path install="C:\VS"`

## <a name="using-export"></a>Korzystanie z eksportu

::: moniker range="vs-2017"

To polecenie wiersza polecenia jest **nowe w 15.9.** Aby uzyskać więcej informacji na ten temat, zobacz stronę Instalowanie za [pomocą parametrów](use-command-line-parameters-to-install-visual-studio.md) wiersza Visual Studio wiersza polecenia.

::: moniker-end

* Za pomocą eksportu zapisz wybór z instalacji:

  ```shell
  "C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe" export --installPath "C:\VS" --config "C:\.vsconfig"
  ```

* Korzystanie z eksportu w celu zapisania wyboru niestandardowego od podstaw:

  ```shell
  "C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe" export --add Microsoft.VisualStudio.Workload.ManagedDesktop --includeRecommended --config "C:\.vsconfig"
  ```

## <a name="using---config"></a>Korzystanie z --config

::: moniker range="vs-2017"

Ten parametr wiersza polecenia jest **nowy w 15.9.** Aby uzyskać więcej informacji na ten temat, zobacz stronę Instalowanie za [pomocą parametrów](use-command-line-parameters-to-install-visual-studio.md) wiersza Visual Studio wiersza polecenia.

::: moniker-end

* Użycie --config do zainstalowania obciążeń i składników z wcześniej zapisanego pliku konfiguracji instalacji:

  ```shell
  vs_enterprise.exe --config "C:\.vsconfig" --installPath "C:\VS"
  ```

* Użycie --config do dodawania obciążeń i składników do istniejącej instalacji:

  ```shell
  vs_enterprise.exe modify --installPath "C:\VS" --config "C:\.vsconfig"
  ```

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Zobacz też

* [Visual Studio administratora](visual-studio-administrator-guide.md)
* [Korzystanie z parametrów wiersza polecenia do zainstalowania programu Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
* [Tworzenie instalacji w trybie offline programu Visual Studio](create-an-offline-installation-of-visual-studio.md)
* [Identyfikatory obciążeń i składników programu Visual Studio](workload-and-component-ids.md)
