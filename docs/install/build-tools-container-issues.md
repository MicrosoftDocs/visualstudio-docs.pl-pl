---
title: Znane problemy z kontenerami
description: Dowiedz się więcej o znanych problemach, które mogą wystąpić podczas instalowania programu Visual Studio kompilacji narzędzia 2017 do kontenera Windows.
ms.date: 04/18/2018
ms.custom: seodec18
ms.prod: visual-studio-dev15
ms.topic: conceptual
ms.assetid: 140083f1-05bc-4014-949e-fb5802397c7a
author: heaths
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 62bbcabe25a4cbefed3e1e928eaac8942e3c8de2
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53905192"
---
# <a name="known-issues-for-containers"></a>Znane problemy z kontenerami

Istnieje kilka kwestii, podczas instalowania programu Visual Studio w kontenerze platformy Docker.

## <a name="windows-container"></a>Kontener Windows

Następujące znane problemy, które występują po zainstalowaniu programu Visual Studio kompilacji narzędzia 2017 do kontenera Windows.

* Nie można zainstalować programu Visual Studio w kontenerze, oparte na microsoft/windowsservercore:10.0.14393.1593 obrazu. Obrazy z wersji Windows tagiem przed lub po 10.0.14393 powinny działać.
* Nie można zainstalować zestaw Windows SDK w wersji 10.0.14393 lub wcześniej. Nie można zainstalować niektórych pakietów i obciążeń, które są zależne od tych pakietów nie będzie działać.
* Przekaż `-m 2GB` (lub więcej) podczas tworzenia obrazu. Niektóre obciążenia wymaga więcej pamięci niż domyślna 1 GB, podczas instalacji.
* Konfigurowanie platformy Docker, aby korzystać z dysków większych niż domyślne 20 GB.
* Przekaż `--norestart` w wierszu polecenia. Zgodnie z pisania tego dokumentu, podjęciem próby ponownego uruchomienia kontenera Windows z poziomu kontenera zwraca `ERROR_TOO_MANY_OPEN_FILES` do hosta.
* Jeśli obraz jest oparty bezpośrednio na microsoft/windowsservercore, .NET Framework nie może być poprawnie zainstalowany i błąd instalacji nie zostanie zgłoszony. Kod zarządzany może nie działać po zakończeniu instalacji. Zamiast tego należy utworzyć obraz na [microsoft/dotnet-framework:4.7.1](https://hub.docker.com/r/microsoft/dotnet-framework) lub nowszej. Na przykład może zostać wyświetlony błąd podczas kompilowania przy użyciu programu MSBuild, takich jak:

  > C:\BuildTools\MSBuild\15.0\bin\Roslyn\Microsoft.CSharp.Core.TARGETS(84,5): błąd MSB6003: Nie można uruchomić pliku wykonywalnego "csc.exe" określone zadanie. Nie można załadować pliku lub zestawu ' System.IO.FileSystem, wersja = 4.0.1.0, Culture = neutral, PublicKeyToken = b03f5f7f11d50a3a "lub jednej z jego zależności. W systemie nie można odnaleźć określonego pliku.

* Nie można zainstalować programu Visual Studio 2017 w wersji należy zachować 15,8 lub starszej (dowolny produkt) na mcr<span></span>.microsoft.com/windows/servercore:1809 lub nowszej. Aby uzyskać więcej informacji, zobacz https://aka.ms/setup/containers/servercore1809.

## <a name="build-tools-container"></a>Tworzenie kontenera narzędzia

Korzystając z narzędzia Build Tools kontenera, mogą wystąpić następujące znane problemy. Aby zobaczyć, czy problemy zostały rozwiązane w przypadku innych znanych problemach, odwiedź stronę https://developercommunity.visualstudio.com.

* IntelliTrace może nie działać [Niektóre scenariusze](https://github.com/Microsoft/vstest/issues/940) w kontenerze.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Zobacz także

* [Instalowanie narzędzi do kompilacji w kontenerze](build-tools-container.md)
* [Zaawansowany przykład dotyczący kontenerów](advanced-build-tools-container.md)
* [Visual Studio 2017 kompilacji narzędzia obciążeń i składników identyfikatorów](workload-component-id-vs-build-tools.md)
