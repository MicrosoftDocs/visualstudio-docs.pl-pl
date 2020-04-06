---
title: Instalacja poza folderem rozszerzeń za pomocą vsix v3 | Dokumenty firmy Microsoft
ms.date: 11/09/2016
ms.topic: conceptual
ms.assetid: 913c3745-8aa9-4260-886e-a05aecfb2225
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: aa2c7d97dda9bba139ec613b367eedbc6307848a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700183"
---
# <a name="install-outside-the-extensions-folder"></a>Instalowanie poza folderem rozszerzeń

Począwszy od programu Visual Studio 2017 i VSIX w wersji 3 (wersja 3), zasoby rozszerzeń można zainstalować poza folderem rozszerzeń. Obecnie następujące lokalizacje są włączone jako prawidłowe lokalizacje instalacji (gdzie [INSTALLDIR] jest mapowany do katalogu instalacji wystąpienia programu Visual Studio):

* [INSTALLDIR]\MSBuild
* [INSTALLDIR]\Xml\Schemas
* [INSTALLDIR]\Common7\IDE\PublicAssemblies
* [INSTALLDIR]\Licencje
* [INSTALLDIR]\Common7\IDE\ReferenceAssemblies
* [INSTALLDIR]\Common7\IDE\RemoteDebugger
* [INSTALLDIR]\Common7\IDE\VC\VCTargets (obsługiwane tylko w programie Visual Studio 2017; przestarzałe dla programu Visual Studio 2019 i nowszych)

> [!NOTE]
> Format VSIX nie zezwala na instalowanie poza strukturą folderów instalacji programu Visual Studio. 

Aby obsługiwać instalację w tych katalogach, VSIX musi być zainstalowany "na wystąpienie na komputerze". Można to włączyć, zaznaczając pole wyboru "wszyscy użytkownicy" w projektancie extension.vsixmanifest:

![sprawdź wszystkich użytkowników](media/check-all-users.png)

## <a name="how-to-set-the-installroot"></a>Jak ustawić installroot

Aby ustawić katalogi instalacji, można użyć okna **Właściwości** w programie Visual Studio. Na przykład można ustawić `InstallRoot` właściwość odwołania do projektu do jednej z powyższych lokalizacji:

![instalowanie właściwości głównych](media/install-root-properties.png)

Spowoduje to dodanie niektórych `ProjectReference` metadanych do odpowiedniej właściwości wewnątrz pliku csproj projektu VSIX:

```xml
 <ProjectReference Include="..\ClassLibrary1\ClassLibrary1.csproj">
        <Project>{69a979f1-eba2-43e7-9346-0e56e803508b}</Project>
        <Name>ClassLibrary1</Name>
        <InstallRoot>PublicAssemblies</InstallRoot>
 </ProjectReference>
```

> [!NOTE]
> Jeśli wolisz, możesz edytować plik csproj.

## <a name="how-to-set-a-subpath-under-the-installroot"></a>Jak ustawić ścieżkę podrzędną w obszarze InstallRoot

Jeśli chcesz zainstalować na podściecie pod `InstallRoot`ścieżką pod programem `VsixSubPath` , możesz `InstallRoot` to zrobić, ustawiając właściwość tak samo jak właściwość. Załóżmy na przykład, że chcemy, aby dane wyjściowe naszego odwołania do projektu zostały zainstalowane na '[INSTALLDIR]\MSBuild\MyCompany\MySDK\1.0'. Możemy to zrobić łatwo z projektantem nieruchomości:

![ustawianie podścieżki](media/set-subpath.png)

Odpowiednie zmiany .csproj będą wyglądać następująco:

```xml
<ProjectReference Include="..\ClassLibrary1\ClassLibrary1.csproj">
       <Project>{69a979f1-eba2-43e7-9346-0e56e803508b}</Project>
       <Name>ClassLibrary1</Name>
       <InstallRoot>MSBuild</InstallRoot>
       <VSIXSubPath>MyCompany\MySDK\1.0</VSIXSubPath>
</ProjectReference>
```

## <a name="extra-information"></a>Dodatkowe informacje

Zmiany projektanta właściwości dotyczą więcej niż tylko odwołań do projektu; można ustawić `InstallRoot` metadane dla elementów wewnątrz projektu, jak również (przy użyciu tych samych metod opisanych powyżej).
