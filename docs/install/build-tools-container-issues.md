---
title: Znane problemy z kontenerami
description: Dowiedz się więcej o znanych problemach, które mogą wystąpić podczas instalowania programu Visual Studio Build Tools w kontenerze Windows.
ms.date: 04/18/2018
ms.custom: seodec18
ms.topic: conceptual
ms.assetid: 140083f1-05bc-4014-949e-fb5802397c7a
author: heaths
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 9953a1c58ea6ddd13ca0555959ed621905ba710a
ms.sourcegitcommit: c7b9ab1bc19d74b635c19b1937e92c590dafd736
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/03/2019
ms.locfileid: "67552885"
---
# <a name="known-issues-for-containers"></a>Znane problemy z kontenerami

Istnieje kilka kwestii, podczas instalowania programu Visual Studio w kontenerze platformy Docker.

## <a name="windows-container"></a>Kontener Windows

Następujące znane problemy, które występują po zainstalowaniu programu Visual Studio Build Tools w kontenerze Windows.

::: moniker range="vs-2017"

* Nie można zainstalować programu Visual Studio w kontenerze, oparte na microsoft/windowsservercore:10.0.14393.1593 obrazu. Obrazy z wersji Windows tagiem przed lub po 10.0.14393 powinny działać.

* Nie można zainstalować zestaw Windows SDK w wersji 10.0.14393 lub wcześniej. Nie można zainstalować niektórych pakietów i obciążeń, które są zależne od tych pakietów nie będzie działać.

::: moniker-end

* Przekaż `-m 2GB` (lub więcej) podczas tworzenia obrazu. Niektóre obciążenia wymaga więcej pamięci niż domyślna 1 GB, podczas instalacji.
* Konfigurowanie platformy Docker, aby korzystać z dysków większych niż domyślne 20 GB.
* Przekaż `--norestart` w wierszu polecenia. Zgodnie z pisania tego dokumentu, podjęciem próby ponownego uruchomienia kontenera Windows z poziomu kontenera zwraca `ERROR_TOO_MANY_OPEN_FILES` do hosta.
* Jeśli obraz jest oparty bezpośrednio na microsoft/windowsservercore, .NET Framework nie może być poprawnie zainstalowany i błąd instalacji nie zostanie zgłoszony. Kod zarządzany może nie działać po zakończeniu instalacji. Zamiast tego należy utworzyć obraz na [microsoft/dotnet-framework:4.7.1](https://hub.docker.com/r/microsoft/dotnet-framework) lub nowszej. Na przykład może zostać wyświetlony błąd, podczas kompilowania przy użyciu programu MSBuild, który jest podobny do następującego:

  > C:\BuildTools\MSBuild\15.0\bin\Roslyn\Microsoft.CSharp.Core.targets(84,5): error MSB6003: Nie można uruchomić pliku wykonywalnego "csc.exe" określone zadanie. Nie można załadować pliku lub zestawu ' System.IO.FileSystem, wersja = 4.0.1.0, Culture = neutral, PublicKeyToken = b03f5f7f11d50a3a "lub jednej z jego zależności. W systemie nie można odnaleźć określonego pliku.

::: moniker range="vs-2017"

* Nie można zainstalować programu Visual Studio 2017 w wersji należy zachować 15,8 lub starszej (dowolny produkt) w mcr.microsoft.com/windows/servercore:1809 lub nowszym. Aby uzyskać więcej informacji, zobacz https://aka.ms/setup/containers/servercore1809.

::: moniker-end

## <a name="build-tools-container"></a>Tworzenie kontenera narzędzia

Korzystając z narzędzia Build Tools kontenera, mogą wystąpić następujące znane problemy. Aby zobaczyć, czy problemy zostały rozwiązane w przypadku innych znanych problemach, odwiedź stronę https://developercommunity.visualstudio.com.

* IntelliTrace może nie działać w [Niektóre scenariusze](https://github.com/Microsoft/vstest/issues/940) w kontenerze.
* W starszych wersjach platformy Docker for Windows domyślny rozmiar obrazu kontenera jest tylko 20 GB, a nie zmieści się narzędzia Build Tools. Postępuj zgodnie z [instrukcjami, aby zmienić rozmiar obrazu](https://docs.microsoft.com/virtualization/windowscontainers/manage-containers/container-storage#image-size) do 127 GB lub więcej.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Zobacz także

* [Instalowanie narzędzi do kompilacji w kontenerze](build-tools-container.md)
* [Zaawansowany przykład dotyczący kontenerów](advanced-build-tools-container.md)
* [Visual Studio Build Tools obciążeń i składników identyfikatorów](workload-component-id-vs-build-tools.md)
