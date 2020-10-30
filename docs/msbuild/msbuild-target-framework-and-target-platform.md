---
title: Struktura docelowa programu MSBuild i platforma docelowa | Microsoft Docs
description: Dowiedz się, jak utworzyć projekt MSBuild do uruchamiania w docelowej wersji .NET Framework oraz na platformie docelowej lub w architekturze oprogramowania.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: df6517c5-edd6-4cc4-97ad-b3cdfc78e799
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d29c4e4659e8e6a5564e3fb41f54615bf29171d2
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2020
ms.locfileid: "93049101"
---
# <a name="msbuild-target-framework-and-target-platform"></a>Platforma docelowa programu MSBuild

Projekt można skompilować do uruchamiania w *środowisku docelowym* , który jest określoną wersją .NET Framework i *platformą docelową* , która jest konkretną architekturą oprogramowania.  Można na przykład określić, że aplikacja ma być uruchamiana na .NET Framework 2,0 na platformie 32-bitowej, która jest zgodna z rodziną procesorów 80x86 ("x86"). Kombinacja struktury docelowej i platformy docelowej jest znana jako *kontekst docelowy* .

> [!IMPORTANT]
> W tym artykule przedstawiono stary sposób określania platformy docelowej. Projekty w stylu zestawu SDK umożliwiają różne TargetFrameworks, takie jak standard. Aby uzyskać więcej informacji, zobacz [Platformy docelowe](/dotnet/standard/frameworks).

## <a name="target-framework-and-profile"></a>Struktura docelowa i profil

 Platforma docelowa to określona wersja .NET Framework, do której projekt jest uruchamiany. Specyfikacja platformy docelowej jest wymagana, ponieważ włącza funkcje kompilatora i odwołania do zestawów, które są wyłącznie dla tej wersji platformy.

 Obecnie następujące wersje .NET Framework są dostępne do użycia:

- .NET Framework 2,0 (zawarte w Visual Studio 2005)

- .NET Framework 3,0 (uwzględniony w systemie Windows Vista)

- .NET Framework 3,5 (zawarte w Visual Studio 2008)

- .NET Framework 4.5.2

- .NET Framework 4,6 (zawarte w Visual Studio 2015)

- .NET Framework 4.6.1

- .NET Framework 4.6.2

- .NET Framework 4,7

- .NET Framework 4.7.1

- .NET Framework 4.7.2

- .NET Framework 4,8

Wersje .NET Framework różnią się od siebie na liście zestawów, które każda z nich udostępnia. Na przykład nie można kompilować aplikacji Windows Presentation Foundation (WPF), chyba że projekt jest przeznaczony dla .NET Framework w wersji 3,0 lub nowszej.

Struktura docelowa jest określona we `TargetFrameworkVersion` właściwości w pliku projektu. Można zmienić platformę docelową dla projektu przy użyciu stron właściwości projektu w zintegrowanym środowisku programistycznym (IDE) programu Visual Studio. Aby uzyskać więcej informacji, zobacz [How to: Target of a wersja .NET Framework](../ide/visual-studio-multi-targeting-overview.md). Dostępne wartości to,,,,,,,,, `TargetFrameworkVersion` `v2.0` `v3.0` `v3.5` `v4.5.2` `v4.6` `v4.6.1` `v4.6.2` `v4.7` `v4.7.1` `v4.7.2` , i `v4.8` .

```xml
<TargetFrameworkVersion>v4.0</TargetFrameworkVersion>
```

 *Profil docelowy* jest podzbiorem platformy docelowej. Na przykład profil klienta .NET Framework 4 nie zawiera odwołań do zestawów programu MSBuild.

 > [!NOTE]
 > Profile docelowe mają zastosowanie tylko do [bibliotek klas przenośnych](/dotnet/standard/cross-platform/cross-platform-development-with-the-portable-class-library).

 Profil docelowy jest określony we `TargetFrameworkProfile` właściwości w pliku projektu. Profil docelowy można zmienić przy użyciu formantu Target-Framework na stronach właściwości projektu w IDE.

```xml
<TargetFrameworkVersion>v4.0</TargetFrameworkVersion>
<TargetFrameworkProfile>Client</TargetFrameworkProfile>
```

## <a name="target-platform"></a>Platforma docelowa

 *Platformą* jest kombinacja sprzętu i oprogramowania, która definiuje określone środowisko uruchomieniowe. Przykład:

- `x86` Określa 32-bitowy system operacyjny Windows, który działa na procesorze Intel 80x86 lub jego odpowiedniku.

- `x64` Określa 64-bitowy system operacyjny Windows, który działa na procesorze Intel x64 lub jest równoważny.

- `Xbox` wyznacza platformę Microsoft Xbox 360.

*Platforma docelowa* to określona platforma, na której ma być uruchamiany projekt. Platforma docelowa jest określona we `PlatformTarget` Właściwości kompilacja w pliku projektu. Możesz zmienić platformę docelową, korzystając ze stron właściwości projektu lub **Configuration Manager** w IDE.

```xml
<PropertyGroup>
   <PlatformTarget>x86</PlatformTarget>
</PropertyGroup>

```

*Konfiguracja docelowa* jest podzbiorem platformy docelowej. Na przykład `x86` `Debug` Konfiguracja nie obejmuje większości optymalizacji kodu. Konfiguracja docelowa jest określona we `Configuration` Właściwości kompilacja w pliku projektu. Konfigurację docelową można zmienić przy użyciu stron właściwości projektu lub **Configuration Manager** .

```xml
<PropertyGroup>
   <PlatformTarget>x86</PlatformTarget>
   <Configuration>Debug</Configuration>
</PropertyGroup>

```

## <a name="see-also"></a>Zobacz też

- [Wielowersyjności kodu](../msbuild/msbuild-multitargeting-overview.md)
