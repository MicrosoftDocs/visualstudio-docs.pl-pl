---
title: Znane problemy dotyczące kontenerów
description: Dowiedz się więcej o znanych problemach, które mogą wystąpić podczas instalowania Visual Studio Build Tools w kontenerze systemu Windows.
ms.date: 02/18/2020
ms.custom: seodec18
ms.topic: conceptual
ms.assetid: 140083f1-05bc-4014-949e-fb5802397c7a
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: cf8473a8de1c9afa5ed73ce9dcb6b9b8462e6548
ms.sourcegitcommit: 8a0d0f4c4910e2feb3bc7bd19e8f49629df78df5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/18/2020
ms.locfileid: "97668404"
---
# <a name="known-issues-for-containers"></a>Znane problemy dotyczące kontenerów

Podczas instalowania programu Visual Studio w kontenerze platformy Docker występuje kilka problemów.

## <a name="windows-container"></a>Kontener systemu Windows

Podczas instalowania Visual Studio Build Tools w kontenerze systemu Windows występują następujące znane problemy.

::: moniker range="vs-2017"

* Programu Visual Studio nie można zainstalować w kontenerze na podstawie obrazu Microsoft/windowsservercore: 10.0.14393.1593. Obrazy otagowane z wersjami systemu Windows przed lub po 10.0.14393 powinny być wykonane.

* Nie można zainstalować Windows SDK w wersji 10.0.14393 lub starszej. Nie można zainstalować niektórych pakietów, a obciążenia, które są zależne od tych pakietów, nie będą działać.

::: moniker-end

* Przekaż `-m 2GB` (lub więcej) podczas kompilowania obrazu. Niektóre obciążenia wymagają większej ilości pamięci niż domyślna 1 GB, gdy jest zainstalowana.
* Skonfiguruj platformę Docker tak, aby korzystała z dysków większych niż domyślna 20 GB.
* Przekaż `--norestart` w wierszu polecenia. Podczas tego pisania próba ponownego uruchomienia kontenera systemu Windows z wewnątrz kontenera powróci `ERROR_TOO_MANY_OPEN_FILES` do hosta.
* Jeśli zamierzasz oprzeć obraz bezpośrednio w firmie Microsoft/windowsservercore, .NET Framework może nie zostać zainstalowana prawidłowo i nie wskazano błędu instalacji. Kod zarządzany może nie działać po zakończeniu instalacji. Zamiast tego należy oprzeć obraz na [platformie Microsoft/dotnet-Framework: 4.7.1](https://hub.docker.com/r/microsoft/dotnet-framework) lub nowszym. Na przykład może zostać wyświetlony błąd podczas kompilowania przy użyciu programu MSBuild podobnego do poniższego:

  > C:\BuildTools\MSBuild\15.0\bin\Roslyn\Microsoft.CSharp.Core.targets (84, 5): błąd MSB6003: nie można uruchomić określonego pliku wykonywalnego zadania "csc.exe". Nie można załadować pliku lub zestawu "System. IO. FileSystem, Version = 4.0.1.0, Culture = neutral, PublicKeyToken = b03f5f7f11d50a3a" lub jednej z jego zależności. W systemie nie można odnaleźć określonego pliku.

::: moniker range="vs-2017"

* Nie można zainstalować programu Visual Studio 2017 w wersji 15,8 lub starszej (dowolny produkt) w systemie mcr.microsoft.com/windows/servercore:1809 lub nowszym. Aby uzyskać więcej informacji, zobacz https://aka.ms/setup/containers/servercore1809.

::: moniker-end

## <a name="build-tools-container"></a>Kontener narzędzi kompilacji

W przypadku korzystania z kontenera narzędzi kompilacji mogą wystąpić następujące znane problemy. Aby sprawdzić, czy problemy zostały rozwiązane lub czy istnieją inne znane problemy, odwiedź [społeczność deweloperów](https://aka.ms/feedback/suggest?space=8).

* IntelliTrace może nie funkcjonować w [niektórych scenariuszach](https://github.com/Microsoft/vstest/issues/940) w kontenerze.
* W starszych wersjach Docker for Windows domyślny rozmiar obrazu kontenera jest tylko 20 GB i nie będzie pasował do narzędzi kompilacji. Postępuj zgodnie [z instrukcjami, aby zmienić rozmiar obrazu](/virtualization/windowscontainers/manage-containers/container-storage#storage-limits) na 127 GB lub więcej.
Aby potwierdzić problem z miejscem na dysku, sprawdź pliki dziennika, aby uzyskać więcej informacji. Jeśli zabraknie `vslogs\dd_setup_<timestamp>_errors.log` miejsca na dysku, plik będzie zawierać następujące elementy: 
```
Pre-check verification: Visual Studio needs at least 91.99 GB of disk space. Try to free up space on C:\ or change your target drive.
Pre-check verification failed with error(s) :  SizePreCheckEvaluator.
```
[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Zobacz także

* [Instalowanie narzędzi do kompilacji w kontenerze](build-tools-container.md)
* [Zaawansowany przykład dotyczący kontenerów](advanced-build-tools-container.md)
* [Visual Studio Build Tools obciążenia i identyfikatory składników](workload-component-id-vs-build-tools.md)
