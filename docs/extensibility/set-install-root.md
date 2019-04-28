---
title: Instalowanie poza folderem rozszerzeń o rozszerzeniu VSIX v3 | Dokumentacja firmy Microsoft
ms.date: 11/09/2016
ms.topic: conceptual
ms.assetid: 913c3745-8aa9-4260-886e-a05aecfb2225
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 09b3b23a89450bb1abac4f8ebb10d00396a251b2
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62433167"
---
# <a name="installing-outside-the-extensions-folder"></a>Instalowanie poza folderem rozszerzeń

Począwszy od programu Visual Studio 2017 i VSIX v3 (wersja 3) jest teraz obsługiwane Instalowanie rozszerzenia zasobów poza folderem rozszerzeń. Obecnie następujących lokalizacji są włączone jako lokalizacje prawidłowej instalacji (gdzie [INSTALLDIR] jest mapowany do katalogu instalacyjnego w wystąpieniu programu Visual Studio):

* \MSBuild [INSTALLDIR]
* [INSTALLDIR] \Xml\Schemas
* \Common7\IDE\PublicAssemblies [INSTALLDIR]
* \Licenses [INSTALLDIR]
* \Common7\IDE\ReferenceAssemblies [INSTALLDIR]
* \Common7\IDE\RemoteDebugger [INSTALLDIR]
* \Common7\IDE\VC\VCTargets [INSTALLDIR]

>**Uwaga:** VSIX format nie umożliwiają instalowanie poza strukturą folderu instalacji programu VS.

W celu obsługi instalacji tych katalogów, VSIX musi być zainstalowany "dla wystąpienia na komputerze". Tę można włączyć, zaznaczając pole wyboru "wszystkich użytkowników" w Projektancie extension.vsixmanifest:

![Zaznacz wszystkich użytkowników](media/check-all-users.png)

## <a name="how-to-set-the-installroot"></a>Jak ustawić element InstallRoot

Aby ustawić katalogi instalacyjne, można użyć **właściwości** okna w programie Visual Studio. Na przykład można ustawić `InstallRoot` właściwości odwołania projektu do jednej z powyższych lokalizacji:

![Zainstaluj właściwości katalogu głównego](media/install-root-properties.png)

Spowoduje to dodanie niektórych metadanych do odpowiednich `ProjectReference` właściwości wewnątrz pliku .csproj projekt VSIX:

```xml
 <ProjectReference Include="..\ClassLibrary1\ClassLibrary1.csproj">
        <Project>{69a979f1-eba2-43e7-9346-0e56e803508b}</Project>
        <Name>ClassLibrary1</Name>
        <InstallRoot>PublicAssemblies</InstallRoot>
 </ProjectReference>
```

>**Uwaga:** Możesz bezpośrednio edytować plik .csproj, jeśli użytkownik sobie tego życzy.

## <a name="how-to-set-a-subpath-under-the-installroot"></a>Jak ustawić podrzędną w ramach InstallRoot

Jeśli chcesz zainstalować podrzędną poniżej `InstallRoot`, możesz to zrobić, ustawiając `VsixSubPath` podobnie jak właściwość `InstallRoot` właściwości. Na przykład chcemy, aby nasz odwołania projektu danych wyjściowych, aby zainstalować "[INSTALLDIR]\MSBuild\MyCompany\MySDK\1.0". Firma Microsoft może łatwo to zrobić za pomocą projektanta właściwości:

![zestaw podrzędną](media/set-subpath.png)

Odpowiednie zmiany w pliku csproj będzie wyglądać następująco:

```xml
<ProjectReference Include="..\ClassLibrary1\ClassLibrary1.csproj">
       <Project>{69a979f1-eba2-43e7-9346-0e56e803508b}</Project>
       <Name>ClassLibrary1</Name>
       <InstallRoot>MSBuild</InstallRoot>
       <VSIXSubPath>MyCompany\MySDK\1.0</VSIXSubPath>
</ProjectReference>
```

## <a name="extra-information"></a>Dodatkowe informacje

Zmiany projektanta właściwości są stosowane do więcej niż tylko odwołania do projektu; Możesz ustawić `InstallRoot` metadanych dla elementów wewnątrz projektu również (przy użyciu tych samych metod opisanych powyżej).
