---
title: Znane problemy dotyczące kontenerów
description: Dowiedz się więcej o znanych problemach, które mogą wystąpić podczas Visual Studio Build Tools w kontenerze systemu Windows.
ms.date: 02/18/2020
ms.custom: seodec18
ms.topic: conceptual
ms.assetid: 140083f1-05bc-4014-949e-fb5802397c7a
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: a56d820805fa97f3672480c063ebfcc0fdc96fb6
ms.sourcegitcommit: 0499d813d5c24052c970ca15373d556a69507250
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/29/2021
ms.locfileid: "113046095"
---
# <a name="known-issues-for-containers"></a>Znane problemy dotyczące kontenerów

Podczas instalowania aplikacji w kontenerze platformy Docker Visual Studio kilka problemów.

## <a name="windows-container"></a>Kontener systemu Windows

Następujące znane problemy występują podczas instalowania Visual Studio Build Tools w kontenerze systemu Windows.

::: moniker range="vs-2017"

* Nie można zainstalować Visual Studio w kontenerze na podstawie obrazu mcr.microsoft.com/windows/servercore:10.0.14393.1593 . Obrazy oznaczone za pomocą wersji systemu Windows przed lub po 10.0.14393 powinny działać.

* Nie można zainstalować Windows SDK wersji 10.0.14393 lub starszej. Niektórych pakietów nie można zainstalować, a obciążenia, które są od nich zależne, nie będą działać.

::: moniker-end

* Przekaż `-m 2GB` (lub więcej) podczas budowania obrazu. Niektóre obciążenia wymagają większej ilości pamięci niż domyślna ilość 1 GB podczas instalacji.
* Konfigurowanie platformy Docker do używania dysków większych niż domyślne 20 GB.
* Przekaż `--norestart` polecenie w wierszu polecenia. W ramach tego pisania tego tekstu próba ponownego uruchomienia kontenera systemu Windows z poziomu kontenera wraca `ERROR_TOO_MANY_OPEN_FILES` do hosta.
* Jeśli obraz bazuje bezpośrednio na mcr.microsoft.com/windows/servercore, .NET Framework instalacji może nie zostać poprawnie zainstalowany i nie zostanie wskazany błąd instalacji. Kod zarządzany może nie zostać uruchomiony po zakończeniu instalacji. Zamiast tego należy bazować obraz na [microsoft/dotnet-framework:4.7.1](https://hub.docker.com/r/microsoft/dotnet-framework) lub nowszej. Na przykład podczas budowania za pomocą programu MSBuild może zostać wyświetlony błąd podobny do następującego:

  > C:\BuildTools\MSBuild\15.0\bin\Roslyn\Microsoft.CSharp.Core.targets(84,5): błąd MSB6003: Nie można uruchomić pliku wykonywalnego określonego zadania "csc.exe". Nie można załadować pliku lub zestawu "System.IO.FileSystem, Version=4.0.1.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a" lub jednej z jego zależności. W systemie nie można odnaleźć określonego pliku.

::: moniker range="vs-2017"

* Nie można zainstalować programu Visual Studio 2017 w wersji 15.8 lub starszej (żaden produkt) na mcr.microsoft.com/windows/servercore:1809 lub nowszym. Aby uzyskać więcej informacji, zobacz https://aka.ms/setup/containers/servercore1809.

::: moniker-end

## <a name="build-tools-container"></a>Kontener Narzędzi kompilacji

Podczas korzystania z kontenera narzędzi kompilacji mogą wystąpić następujące znane problemy. Aby sprawdzić, czy problemy zostały rozwiązane lub czy występują inne znane problemy, odwiedź [stronę Developer Community](https://aka.ms/feedback/suggest?space=8).

* IntelliTrace może nie działać w [niektórych scenariuszach](https://github.com/Microsoft/vstest/issues/940) w kontenerze.
* W starszych wersjach Docker for Windows domyślny rozmiar obrazu kontenera wynosi tylko 20 GB i nie będzie pasować do narzędzi kompilacji. Postępuj [zgodnie z instrukcjami, aby zmienić rozmiar obrazu](/virtualization/windowscontainers/manage-containers/container-storage#storage-limits) na co najmniej 127 GB.
Aby potwierdzić problem z przestrzenią dyskową, sprawdź pliki dziennika, aby uzyskać więcej informacji. Jeśli zabraknie miejsca na `vslogs\dd_setup_<timestamp>_errors.log` dysku, plik będzie zawierać następujące elementy: 
```
Pre-check verification: Visual Studio needs at least 91.99 GB of disk space. Try to free up space on C:\ or change your target drive.
Pre-check verification failed with error(s) :  SizePreCheckEvaluator.
```
[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Zobacz też

* [Instalowanie narzędzi do kompilacji w kontenerze](build-tools-container.md)
* [Zaawansowany przykład dotyczący kontenerów](advanced-build-tools-container.md)
* [Visual Studio Build Tools identyfikatory obciążeń i składników](workload-component-id-vs-build-tools.md)
