---
title: Znane problemy z kontenerami
description: Dowiedz się więcej o znanych problemach, które mogą wystąpić podczas instalowania narzędzi kompilacji programu Visual Studio w kontenerze systemu Windows.
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
ms.openlocfilehash: a864f1ef623197a44c7d816b051efd0106e86ece
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77611129"
---
# <a name="known-issues-for-containers"></a>Znane problemy z kontenerami

Istnieje kilka problemów podczas instalowania programu Visual Studio w kontenerze platformy Docker.

## <a name="windows-container"></a>Kontener systemu Windows

Następujące znane problemy występują podczas instalowania narzędzi kompilacji programu Visual Studio w kontenerze systemu Windows.

::: moniker range="vs-2017"

* Nie można zainstalować programu Visual Studio w kontenerze opartym na obrazie microsoft/windowsservercore:10.0.14393.1593. Obrazy oznaczone wersjami systemu Windows przed lub po 10.0.14393 powinny działać.

* Nie można zainstalować pakietu Windows SDK w wersji 10.0.14393 lub wcześniejszej. Niektóre pakiety nie można zainstalować i obciążeń, które zależą od tych pakietów nie będzie działać.

::: moniker-end

* Przekaż `-m 2GB` (lub więcej) podczas tworzenia obrazu. Niektóre obciążenia wymagają więcej pamięci niż domyślne 1 GB po zainstalowaniu.
* Skonfiguruj program Docker tak, aby używał dysków większych niż domyślne 20 GB.
* Przekaż `--norestart` wiersz polecenia. W chwili pisania tego zapisu, próbując ponownie uruchomić `ERROR_TOO_MANY_OPEN_FILES` kontener systemu Windows z poziomu kontenera zwraca do hosta.
* Jeśli obraz jest podstawą bezpośrednio na microsoft/windowsservercore, program .NET Framework może nie zostać poprawnie zainstalowany i nie jest wskazany błąd instalacji. Kod zarządzany może nie działać po zakończeniu instalacji. Zamiast tego oprzeć obraz na [microsoft/dotnet-framework:4.7.1](https://hub.docker.com/r/microsoft/dotnet-framework) lub nowszych. Na przykład może pojawić się błąd podczas tworzenia z MSBuild, który jest podobny do następującego:

  > C:\BuildTools\MSBuild\15.0\bin\Roslyn\Microsoft.CSharp.Core.targets(84,5): nie można uruchomić błędu MSB6003: nie można uruchomić określonego pliku wykonywalnego zadania "csc.exe". Nie można załadować pliku lub zestawu "System.IO.FileSystem, Version=4.0.1.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a" lub jednej z jego zależności. W systemie nie można odnaleźć określonego pliku.

::: moniker range="vs-2017"

* Nie można zainstalować programu Visual Studio 2017 w wersji 15.8 lub wcześniejszej (dowolny produkt) w mcr.microsoft.com/windows/servercore:1809 lub nowszym. Aby uzyskać więcej informacji, zobacz https://aka.ms/setup/containers/servercore1809.

::: moniker-end

## <a name="build-tools-container"></a>Kontener Narzędzi kompilacji

Następujące znane problemy mogą wystąpić podczas korzystania z kontenera Narzędzi kompilacji. Aby sprawdzić, czy problemy zostały rozwiązane lub https://developercommunity.visualstudio.comczy istnieją inne znane problemy, odwiedź stronę .

* IntelliTrace może nie działać w [niektórych scenariuszach](https://github.com/Microsoft/vstest/issues/940) w kontenerze.
* W starszych wersjach platformy Docker dla systemu Windows domyślny rozmiar obrazu kontenera wynosi tylko 20 GB i nie będzie pasować do narzędzi kompilacji. Postępuj zgodnie [z instrukcjami, aby zmienić rozmiar obrazu](/virtualization/windowscontainers/manage-containers/container-storage#storage-limits) na 127 GB lub więcej.
Aby potwierdzić problem z miejscem na dysku, sprawdź pliki dziennika, aby uzyskać więcej informacji. Plik `vslogs\dd_setup_<timestamp>_errors.log` będzie zawierał następujące informacje, jeśli zabraknie miejsca na dysku: 
```
Pre-check verification: Visual Studio needs at least 91.99 GB of disk space. Try to free up space on C:\ or change your target drive.
Pre-check verification failed with error(s) :  SizePreCheckEvaluator.
```
[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Zobacz też

* [Instalowanie narzędzi do kompilacji w kontenerze](build-tools-container.md)
* [Zaawansowany przykład dotyczący kontenerów](advanced-build-tools-container.md)
* [Obciążenie i identyfikatory składników narzędzi kompilacji programu Visual Studio](workload-component-id-vs-build-tools.md)
