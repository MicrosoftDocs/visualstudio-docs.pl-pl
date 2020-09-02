---
title: Instalowanie poza folderem rozszerzeń z VSIX v3 | Microsoft Docs
ms.date: 11/09/2016
ms.topic: conceptual
ms.assetid: 913c3745-8aa9-4260-886e-a05aecfb2225
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: aa2c7d97dda9bba139ec613b367eedbc6307848a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80700183"
---
# <a name="install-outside-the-extensions-folder"></a>Instalowanie poza folderem rozszerzeń

Począwszy od programu Visual Studio 2017 i VSIX v3 (wersja 3), można zainstalować zasoby rozszerzeń poza folderem rozszerzeń. Obecnie następujące lokalizacje są włączone, ponieważ prawidłowe lokalizacje instalacji (gdzie [INSTALLDIR] są zamapowane na katalog instalacyjny wystąpienia programu Visual Studio):

* [INSTALLDIR] \MSBuild
* [INSTALLDIR] \Xml\Schemas
* [INSTALLDIR] \Common7\IDE\PublicAssemblies
* [INSTALLDIR] \Licenses
* [INSTALLDIR] \Common7\IDE\ReferenceAssemblies
* [INSTALLDIR] \Common7\IDE\RemoteDebugger
* [INSTALLDIR] \Common7\IDE\VC\VCTargets (obsługiwane tylko dla programu Visual Studio 2017; przestarzałe dla programu Visual Studio 2019 i nowszych)

> [!NOTE]
> Format VSIX nie pozwala na instalację poza strukturą folderu instalacji programu Visual Studio. 

Aby można było obsługiwać instalację do tych katalogów, należy zainstalować VSIX "na wystąpienie dla każdego komputera". Tę funkcję można włączyć, zaznaczając pole wyboru "Wszyscy użytkownicy" w projektancie rozszerzenia. vsixmanifest:

![Zaznacz wszystkich użytkowników](media/check-all-users.png)

## <a name="how-to-set-the-installroot"></a>Jak ustawić element InstallRoot

Aby ustawić katalogi instalacyjne, można użyć okna **Właściwości** w programie Visual Studio. Na przykład można ustawić `InstallRoot` Właściwość odwołania projektu na jedną z powyższych lokalizacji:

![Instalowanie właściwości głównych](media/install-root-properties.png)

Spowoduje to dodanie metadanych do odpowiedniej `ProjectReference` właściwości w pliku. csproj projektu VSIX:

```xml
 <ProjectReference Include="..\ClassLibrary1\ClassLibrary1.csproj">
        <Project>{69a979f1-eba2-43e7-9346-0e56e803508b}</Project>
        <Name>ClassLibrary1</Name>
        <InstallRoot>PublicAssemblies</InstallRoot>
 </ProjectReference>
```

> [!NOTE]
> Plik. csproj można edytować bezpośrednio, jeśli wolisz.

## <a name="how-to-set-a-subpath-under-the-installroot"></a>Jak ustawić ścieżkę podrzędną pod element InstallRoot

Jeśli chcesz zainstalować program w podścieżce poniżej, możesz to `InstallRoot` zrobić, ustawiając `VsixSubPath` Właściwość tak jak `InstallRoot` Właściwość. Na przykład załóżmy, że chcemy, aby nasze dane wyjściowe odwołania do projektu zostały zainstalowane do "[INSTALLDIR] \MSBuild\MyCompany\MySDK\1.0". Można to łatwo zrobić przy użyciu projektanta właściwości:

![Ustaw ścieżkę podrzędną](media/set-subpath.png)

Odpowiednie zmiany csproj będą wyglądać następująco:

```xml
<ProjectReference Include="..\ClassLibrary1\ClassLibrary1.csproj">
       <Project>{69a979f1-eba2-43e7-9346-0e56e803508b}</Project>
       <Name>ClassLibrary1</Name>
       <InstallRoot>MSBuild</InstallRoot>
       <VSIXSubPath>MyCompany\MySDK\1.0</VSIXSubPath>
</ProjectReference>
```

## <a name="extra-information"></a>Dodatkowe informacje

Zmiany projektanta właściwości dotyczą więcej niż tylko odwołań projektu; Możesz `InstallRoot` również ustawić metadane dla elementów wewnątrz projektu (przy użyciu tych samych metod opisanych powyżej).
