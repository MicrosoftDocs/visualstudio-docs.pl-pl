---
title: Platforma docelowa i platforma docelowa MSBuild | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: df6517c5-edd6-4cc4-97ad-b3cdfc78e799
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c3cccb9bb87d03d1fb285babe2a02cf30cfb9ed9
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633203"
---
# <a name="msbuild-target-framework-and-target-platform"></a>Platforma docelowa i platforma docelowa MSBuild

Projekt można zbudować do pracy na *platformie docelowej*, która jest określoną wersją platformy .NET Framework i *platformą docelową*, która jest architekturą określonego oprogramowania.  Na przykład można kierować aplikację do uruchamiania w programie .NET Framework 2.0 na platformie 32-bitowej, która jest zgodna z rodziną procesorów 802x86 ("x86"). Połączenie struktury docelowej i platformy docelowej jest znane jako *kontekst docelowy.*

> [!IMPORTANT]
> W tym artykule przedstawiono stary sposób, aby określić platformę docelową. Projekty w stylu SDK umożliwiają różne targetframeworks, takie jak netstandard. Aby uzyskać więcej informacji, zobacz [struktury docelowe](/dotnet/standard/frameworks).

## <a name="target-framework-and-profile"></a>Struktura docelowa i profil

 Struktura docelowa jest określoną wersją programu .NET Framework, na których jest utworzony projekt. Specyfikacja struktury docelowej jest wymagana, ponieważ umożliwia funkcje kompilatora i odwołania do zestawu, które są wyłączne dla tej wersji struktury.

 Obecnie dostępne są następujące wersje programu .NET Framework:

- .NET Framework 2.0 (zawarte w programie Visual Studio 2005)

- Program .NET Framework 3.0 (uwzględniony w systemie Windows Vista)

- .NET Framework 3.5 (zawarte w programie Visual Studio 2008)

- .NET Framework 4.5.2

- .NET Framework 4.6 (zawarte w programie Visual Studio 2015)

- .NET Framework 4.6.1

- .NET Framework 4.6.2

- .NET Framework 4.7

- .NET Framework 4.7.1

- .NET Framework 4.7.2

- .NET Framework 4.8

Wersje programu .NET Framework różnią się od siebie na liście zestawów, które każdy udostępnia do odwołania. Na przykład nie można utworzyć aplikacji Programu Windows Presentation Foundation (WPF), chyba że projekt jest przeznaczony dla programu .NET Framework w wersji 3.0 lub wyższej.

Struktura docelowa jest `TargetFrameworkVersion` określona we właściwości w pliku projektu. Platformę docelową projektu można zmienić przy użyciu stron właściwości projektu w zintegrowanym środowisku programistycznym Programu Visual Studio (IDE). Aby uzyskać więcej informacji, zobacz [Jak: Target wersji programu .NET Framework](../ide/visual-studio-multi-targeting-overview.md). Dostępne wartości `TargetFrameworkVersion` to `v2.0` `v3.0`, `v3.5` `v4.5.2`, `v4.6` `v4.6.1`, `v4.6.2` `v4.7`, `v4.7.1` `v4.7.2`, `v4.8`, , , , , i .

```xml
<TargetFrameworkVersion>v4.0</TargetFrameworkVersion>
```

 *Profil docelowy* jest podzbiorem struktury docelowej. Na przykład profil klienta programu .NET Framework 4 nie zawiera odwołań do zestawów MSBuild.

 > [!NOTE]
 > Profile docelowe mają zastosowanie tylko do [przenośnych bibliotek klas](/dotnet/standard/cross-platform/cross-platform-development-with-the-portable-class-library).

 Profil docelowy jest `TargetFrameworkProfile` określony we właściwości w pliku projektu. Profil docelowy można zmienić przy użyciu formantu struktury docelowej na stronach właściwości projektu w IDE.

```xml
<TargetFrameworkVersion>v4.0</TargetFrameworkVersion>
<TargetFrameworkProfile>Client</TargetFrameworkProfile>
```

## <a name="target-platform"></a>Platforma docelowa

 *Platforma* to połączenie sprzętu i oprogramowania, które definiuje określone środowisko wykonawcze. Na przykład:

- `x86`wyznacza 32-bitowy system operacyjny Windows, który działa na procesorze Intel 80x86 lub jego odpowiedniku.

- `x64`wyznacza 64-bitowy system operacyjny Windows, który jest uruchomiony na procesorze Intel x64 lub jego odpowiedniku.

- `Xbox`wyznacza platformę Microsoft Xbox 360.

*Platforma docelowa* jest określoną platformą, na którą jest utworzony projekt. Platforma docelowa jest `PlatformTarget` określona we właściwości kompilacji w pliku projektu. Platformę docelową można zmienić przy użyciu stron właściwości projektu lub **programu Configuration Manager** w IDE.

```xml
<PropertyGroup>
   <PlatformTarget>x86</PlatformTarget>
</PropertyGroup>

```

*Konfiguracja docelowa* jest podzbiorem platformy docelowej. Na przykład `x86``Debug` konfiguracja nie zawiera większości optymalizacji kodu. Konfiguracja docelowa jest `Configuration` określona we właściwości kompilacji w pliku projektu. Konfigurację docelową można zmienić za pomocą stron właściwości projektu lub **programu Configuration Manager**.

```xml
<PropertyGroup>
   <PlatformTarget>x86</PlatformTarget>
   <Configuration>Debug</Configuration>
<PropertyGroup>

```

## <a name="see-also"></a>Zobacz też

- [Wielotargowe](../msbuild/msbuild-multitargeting-overview.md)
