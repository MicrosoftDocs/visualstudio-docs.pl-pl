---
title: Instalowanie poza folderem extensions za pomocą rozszerzenia VSIX w wersji 3 | Microsoft Docs
description: Dowiedz się więcej Visual Studio zasobów rozszerzenia zestawu SDK poza folderem rozszerzeń i sprawdź, które lokalizacje są prawidłowe.
ms.custom: SEO-VS-2020
ms.date: 11/09/2016
ms.topic: how-to
ms.assetid: 913c3745-8aa9-4260-886e-a05aecfb2225
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 24b1e1a73ff588e5531eec2025c8a3c9e94760a4
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112898451"
---
# <a name="install-outside-the-extensions-folder"></a>Instalowanie poza folderem rozszerzeń

Począwszy od Visual Studio 2017 i VSIX v3 (wersja 3), zasoby rozszerzeń można instalować poza folderem extensions. Obecnie następujące lokalizacje są włączone jako prawidłowe lokalizacje instalacji (gdzie [INSTALLDIR] jest mapowany Visual Studio katalogu instalacyjnego wystąpienia):

* [INSTALLDIR]\MSBuild
* [INSTALLDIR]\Xml\Schemas
* [INSTALLDIR]\Common7\IDE\PublicAssemblies
* [INSTALLDIR]\Licenses
* [INSTALLDIR]\Common7\IDE\ReferenceAssemblies
* [INSTALLDIR]\Common7\IDE\RemoteDebugger
* [INSTALLDIR]\Common7\IDE\VC\VCTargets (obsługiwane tylko w przypadku programu Visual Studio 2017; przestarzałe dla programu Visual Studio 2019 i nowszych)

> [!NOTE]
> Format VSIX nie pozwala na instalowanie poza strukturą Visual Studio instalacji. 

Aby zapewnić obsługę instalacji w tych katalogach, należy zainstalować vsix "na wystąpienie na maszynę". Można to włączyć, zaznaczając pole wyboru "wszyscy użytkownicy" w projektancie extension.vsixmanifest:

![sprawdzanie wszystkich użytkowników](media/check-all-users.png)

## <a name="how-to-set-the-installroot"></a>Jak ustawić katalog InstallRoot

Aby ustawić katalogi instalacji, możesz użyć okna **Właściwości** w Visual Studio. Na przykład można ustawić właściwość odwołania do `InstallRoot` projektu na jedną z powyższych lokalizacji:

![instalowanie właściwości głównych](media/install-root-properties.png)

Spowoduje to dodanie metadanych do odpowiedniej właściwości `ProjectReference` wewnątrz pliku csproj projektu VSIX:

```xml
 <ProjectReference Include="..\ClassLibrary1\ClassLibrary1.csproj">
        <Project>{69a979f1-eba2-43e7-9346-0e56e803508b}</Project>
        <Name>ClassLibrary1</Name>
        <InstallRoot>PublicAssemblies</InstallRoot>
 </ProjectReference>
```

> [!NOTE]
> Jeśli wolisz, możesz bezpośrednio edytować plik csproj.

## <a name="how-to-set-a-subpath-under-the-installroot"></a>Jak ustawić podścieżek w obszarze InstallRoot

Jeśli chcesz zainstalować na podścieżce poniżej ścieżki , możesz to zrobić, ustawiając właściwość `InstallRoot` tak samo jak właściwość `VsixSubPath` `InstallRoot` . Załóżmy na przykład, że chcemy, aby dane wyjściowe naszego odwołania do projektu się zainstalują w folderze "[INSTALLDIR]\MSBuild\MyCompany\MySDK\1.0". Możemy to łatwo zrobić za pomocą projektanta właściwości:

![set subpath](media/set-subpath.png)

Odpowiednie zmiany w .csproj będą wyglądać tak:

```xml
<ProjectReference Include="..\ClassLibrary1\ClassLibrary1.csproj">
       <Project>{69a979f1-eba2-43e7-9346-0e56e803508b}</Project>
       <Name>ClassLibrary1</Name>
       <InstallRoot>MSBuild</InstallRoot>
       <VSIXSubPath>MyCompany\MySDK\1.0</VSIXSubPath>
</ProjectReference>
```

## <a name="extra-information"></a>Dodatkowe informacje

Zmiany projektanta właściwości dotyczą nie tylko odwołań do projektu; Możesz również ustawić `InstallRoot` metadane dla elementów wewnątrz projektu (przy użyciu tych samych metod, które opisano powyżej).
